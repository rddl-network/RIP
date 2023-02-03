```
shortname: REP-4
name: Trust Anchor Requirements
type: standard
status: raw
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```

## **Abstract**
This REP defines the requirements a Trust Anchor needs to satisfy in order to be compliant to the RDDL network Proof of Productivity.

## **Motivation**
 The goal of this REP is to list the requirements in a comprehensive way so that the requirements can be easily understood.


## **Problem Breakdown**

#### Definitions:
* ***CID*** Content identifier as defined at [IPFS](https://docs.ipfs.tech/concepts/content-addressing/#what-is-a-cid)
* ***CID-data*** The data that results in the given CID.

Trust Anchors contain a business logic that interacts with a machine, a smart meter, the network, and most likely at least one storage solution. The purpose of Trust Anchors is to 
1. notarize data, to
1. prove origin and provenance of data, to
1. prove integrity and authenticity of data, and to
1. participate in the POP of RDDL Network.
 
The Trust Anchor needs to manage a BIP44 wallet in order to
* notarize,
* prove origin and provenance, and
* prove integrity and authenticity 
of data.

A data management and mapping logic and functionality is needed to successfully participate in the POP.
The POP and others actor want to verify and challenge the attested data and CIDs. This process is as follows:
1. A CID is read from the ledger
1. The URL to download the CID-data is looked up at https://cid-resolver.rddl.io 
1. The CID-data is downloaded by issuing a GET request to the retrieved URL
1. The CID' of the CID-data is computed and compared to the CID of step one. 
1. The CID - CID--ata is valid if the comparison CID == CID' is True.

## **Specification**

### ***BIP44 Wallet***
It is recommended that a the [0x21e8 Service](https://github.com/rddl-network/0x21e8) is used as the reference [BIP44 wallet](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki). 

### ***Data management & mapping***

POP expects that: 
1. The Trust Anchor registers a valid key/value pair at https://cid-resolver.rddl.io with CID being the key and the value being a valid URL returning the CID-data for the given CID.
1. All notarized CIDs can be looked up via https://cid-resolver.rddl.io.
1. Given a CID, a valid download URL for the CID-data can be retrieved via the [cid-resolver](https://cid-resolver.rddl.io/docs)
1. The CID-data can be retrieved by executing a GET request to the retrieved download URL
1. the downloaded CID-data results in a CID that is equal to the one used for the lookup


#### ***cid-resolver.rddl.io***
Details about the restful service can be found at 
* [API docs](https://cid-resolver.rddl.io/docs)
* [Source code](https://github.com/rddl-network/cid-resolver)

The CID resolver stores < CID, URL > pairs like
```json
{
  "cid": "bafkreignwcoye67vn6edp23mj4llhpzzkgyuefu7xesjzjxcv2bz3p4nfm",
  "url": "https://bafkreignwcoye67vn6edp23mj4llhpzzkgyuefu7xesjzjxcv2bz3p4nfm.ipfs.w3s.link"
}
```
and enables actors to lookup download links for CID-data for a given CID.
```
https://cid-resolver.rddl.io/entry/cid?cid=bafkreignwcoye67vn6edp23mj4llhpzzkgyuefu7xesjzjxcv2bz3p4nfm
```

#### ***CID-data resolver***

Whatever DB/storage solution is use by the Trust Anchor or the operator. The only task being asked by the network is to resolve a CID to its CID-data.
Hence, a simple service with the following API should be sufficient to suit the needs of the RDDL protocol:

* GET /cid-data/<cid> 


## **Implementation**
The implementations must be completed before any REP is given status "stable", but it need not be completed before the REP is accepted. While there is merit to the approach of reaching consensus on the REP and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.

## **Copyright Waiver**
Except for REP-1 (C4) and REP-2 (COSS), all REPs MUST be released to the public domain. To do that, the following block of HTML SHOULD be used in the REP's source Markdown file. ([HTML is valid Markdown](https://daringfireball.net/projects/markdown/syntax#html).)
