```
shortname: REP-14
name: Security Concepts (Ante Handler vs Msg Server)
type: standard
status: draft
editor: Lorenz Herzberger <lorenzherzberger@gmail.com>
contributors:
```

## **Abstract**
This REP delineates the criteria for securing message types either through ante handlers (for high-frequency or role-based messages) or via message servers (for application state-based messages).

## **Motivation**
The purpose of this REP is to establish a systematic framework for determining whether a message type should be intercepted by an ante handler (i.e., before dissemination to other validators) or by a message server, thereby committing the message's result to the chain.

## **Problem breakdown**
Planetmint employs two distinct methods to prevent invalid messages from instigating state changes:
  
  1. During the `CheckTx` phase, where messages are vetted by `Ante Handlers`.
  2. During the `DeliverTx` phase, where messages undergo validation by `Message Servers`.

  The distinction lies in the fact that transactions are only propagated to other peers if they pass the `CheckTx` stage.


### CheckTx (Ante Handler)
Upon receiving a transaction, a node forwards it to the application via a `CheckTx` ABCI call. The application then validates the transaction using Ante Handlers. If all validations succeed, the transaction is added to the mempool and subsequently broadcasted to other peers. Otherwise, the transaction is discarded.

### DeliverTx (Message Servers)
When a block is proposed, each full node executes a `DeliverTx` ABCI call for every transaction in the block. Ante Handlers are invoked once more, and in addition, the messages within a transaction are dispatched to their corresponding message servers. Further validations take place here. If all checks pass, a state change is enacted. Otherwise, all state changes are rolled back.

## **Specification**
Given that certain transactions are automatically triggered by machines at high frequencies, it is preferable to intercept them before dissemination to other nodes. Similarly, restricted messages, which are exclusive to validators, should be intercepted preemptively. Hence, transactions of these types should be intercepted by the `Ante Handler`. All other message validations are to be performed on a per-message server basis.

Files containing `Ante Handlers` responsible for checking role permissions should be renamed to `check_<role>...go`.

Ante Handlers validating messages based on application state should be relocated to their respective message servers.