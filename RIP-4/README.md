```
shortname: RIP-4
name: Trust Anchor Requirements
type: standard
status: raw
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```

**Abstract**. This RIP defines the requirements a Trust Anchor needs to satisfy in order to be compliant to the RDDL network Proof of Productivity.

**Motivation**. The goal of this RIP is to list the requirements in a comprehensive and way that can be easily understood.


**Problem Breakdown** Trust Anchors contain a business logic that interacts with a machine, a smart meter, the network, and most likely at least one storage solution. The purpose of Trust Anchors is to 
1. notarize data, to
1. prove origin and provenance of data, to
1. prove integrity and authenticity of data, and to
1. participate in the POP of RDDL Network.
 
The Trust Anchor needs to manage a BIP44 wallet in order 
* to notarize 
* prove origin and provenance
* prove integrity and authenticity 
of data.

A data management and mapping logic and functionality is needed to successfully participate in the POP.

**Specification**:

***BIP44 Wallet*** It is recommended that a the [0x21e8 Service](https://github.com/rddl-network/0x21e8) is used as the reference [BIP44 wallet](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki). 

***Data management & mapping***

POP expects that: 
1. all notarized CID hashes can be looked up via cid-resolver.io.
1. given a CID, a valid download link for the CID data can be retrieved via the [cid-resolver](https://cid-resolver.rddl.io)
1. the CID data can be downloaded
1. the downloaded data results in the CID that is equal to the one used for the lookup


***cid-resolver.rddl.io***
Details about the restful service can be found at 
* [API docs](https://cid-resolver.rddl.io/docs)
* [Source code](https://github.com/rddl-network/cid-resolver)


The technical specification should describe the syntax and semantics of any new feature. The specification must address the exact issues described in the solution breakdown and should describe how it addresses them. The specification should be detailed enough to allow competing, interoperable implementations. It MAY describe the impact on data models, API endpoints, security, performance, end users, deployment, documentation, and testing.

1. **Rationale**. The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.


1. **Implementation**. The implementations must be completed before any RIP is given status "stable", but it need not be completed before the RIP is accepted. While there is merit to the approach of reaching consensus on the RIP and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.

1. **Copyright Waiver**. Except for RIP-1 (C4) and RIP-2 (COSS), all RIPs MUST be released to the public domain. To do that, the following block of HTML SHOULD be used in the RIP's source Markdown file. ([HTML is valid Markdown](https://daringfireball.net/projects/markdown/syntax#html).)
