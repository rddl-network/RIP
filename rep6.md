```
shortname: REP-6
name: Machine Authentication - EdDSA
type: standard
status: draft
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```

## **Abstract**
This REP defines the mechanisms that are utilized to let machines authenticate to RDDL infrastructure services.

## **Motivation**
 The goal of this REP is to describe the demand for RDDL infrastructure services and give the conceptual overview how machines are able to authenticate.


## **Problem Breakdown**

#### Definitions:
* ***M2M*** Machine to machine

RDDL Network enables machine based token economy. The machines notarize and tokenize data, are able to transfer and receive tokens, and can autonomously act upon such kind of events. Not all activities are on-chain but are executed off-chain e.g. Proof of Productivity, or other verification and proofing schemes. Therefore mechanisms to authenticate machines are needed.

1. The [CID-Resolver](./rep4.md#specification) allows network nodes to register CID to URL mappings. Everyone is able to query these but registration of mapping is only granted to nodes. 
1. The M2M communication protocol of RDDL Network being used during PoP is only accessible for legit network nodes. 

Both use-cases express the need for a network node authentication mechanism and access mechanism.
RDDL Network utilizes Planetmint using base58 encoded ED25519 key pairs. Therefore, EdDSA is used to perform the challenge-response authentication.

## **Specification**

The authentication service comes with two methods:

1. GET /auth?public_key=<machine planetmint public key> returns the challenge that is to be signed
1. POST auth/?public_key=<machine planetmint public key>&signature=<signature of the sha256 hashed challenge>' return a valid JWT token with a certain expiration time.

A challenge will expire after a certain amount of time.
The signature has to be created in the following way:
1. compute a hash of the challenge with sha256
1. sign the computed hash with the private key related to the machine public key

A sample implementation of the workflow can be found [here](https://github.com/rddl-network/0x21e8/blob/main/x21e8/utils/eddsa_auth.py)

### ***JWT***
The JWT header is defined as 
```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

The payload has the following structure
```json
{
  "actor": <machine planetmint public key>@m2m.rddl.io,
  "exp": <utc timestamp of expiration>
}
```

The payload got explicitly defined so that it supports the M2M communication protocol.
The initial authentication service is currently part of the [CID-resolver](https://github.com/rddl-network/cid-resolver) but will be migrated to ***auth.rddl.io***.



## **Implementation**
The implementations must be completed before any REP is given status "stable", but it need not be completed before the REP is accepted. While there is merit to the approach of reaching consensus on the REP and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.

## **Copyright Waiver**
Except for REP-1 (C4) and REP-2 (COSS), all REPs MUST be released to the public domain. To do that, the following block of HTML SHOULD be used in the REP's source Markdown file. ([HTML is valid Markdown](https://daringfireball.net/projects/markdown/syntax#html).)
