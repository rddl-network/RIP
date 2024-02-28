```
shortname: REP-14
name: Security Concepts (Ante Handler vs Msg Server)
type: standard
status: draft
editor: Lorenz Herzberger <lorenzherzberger@gmail.com>
contributors:
```

## **Abstract**
This REP defines which message types should be secured by the ante handler (high frequency or role based) or in the message servers (application state based).

## **Motivation**
The goal of this REP is to define a dogmatic outline for deciding if a message type should be blocked by an ante handler (i.e. before being gossiped to other validators) or by a message server thus writing the result of the message to the chain.

## **Problem breakdown**
Planetmint uses two distinct ways to block invalid messages from triggering a state change: 

1. during `CheckTx` when messages are validated by `Ante Handlers`
2. during `DeliverTx` when messages are validated by `Message Servers`

The difference being that transactions are only gossiped to other peers if the `CheckTx` stage is passed.

### CheckTx (Ante Handler)
When a node receives a transaction it sends it to the application with a `CheckTx` ABCI call. The application then validates the transaction using the Ante Handlers. If all checks are successful then it will be delivered to the mempool and thus broadcasted to other peers in the network. Otherwise the transaction will be discarded.

### DeliverTx (Message Servers)
When a block is is proposed each full-node runs a `DeliverTx` ABCI call for each transaction in said block. The `Ante Handlers` are run again, however in addition to this the messages inside a transactiona are delivered to their respective message servers. Here additional checks can be made. If all checks are successful a state change will be triggered. Otherwise all state changes will be reverted.

## **Specification**
Since some transactions will be automatically triggered by machines in high frequencies it is preferred to block them before they are gossiped to other nodes. The same goes for restricted messages which are only allowed to be sent by validators. Thus these kinds of transactions shall be blocked by the `Ante Handler`.

All other message validations shall be performed on a per message server basis.
