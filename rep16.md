```
shortname: REP-16
name: Quality Assurance - Exceeding the scope of unit testing
type: standard
status: draft
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```

## **Abstract**
RDDL Network executes a protocol on top of Planetmint and the Liquid layer-2-chain of Bitcoin.
The protocol is surrounded by some microservices taking care about certain workflows that are not based on on-chain primitives. This REP summaries all the final tests that are needed to verify a working deployment onto the Testnet and Mainnet.


## **Motivation**
In order to overcome the limitations of unit tests and the currently not existing integration tests, a dedicated test set is crafted within this REP to guide everyone through a meaningful scope of tests that garantee the correct working of the protocol. 


## **Problem Breakdown**

1. Machine ID/Trust Anchor registration
1. Machine ID/Trust Anchor attestment ( faucet, machine ID/machine address relation handling)
1. Machine notarizes data [notarize command on Tasmota] (planetmint interaction)
1. PoP init with machines -> observe if machines execute PoP properly and if PoPResult is notarized (mqtt, TAs)
1. Reissuance verification
1. Distribution verification
1. Dao-Distribution-Service : 10% distribution verifizieren (rddl-2-plmnt, SCS, SSS)
1. RDDL-Claim service [machine requests claims]  (TA, planemtint, claim-service)


