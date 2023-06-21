```
shortname: REP-5
name: Machine Registry
type: standard
status: raw
editor: Lorenz Herzberger lorenzherzberger@gmail.com
contributors:
```

## **Abstract**
This REP defines the mechanism that is utilized to verify machines on RDDL infrastructure services throught attestation.

## **Motivation**
 The goal of this REP is to describe a Machine Registry that is utilized to store information about a device on chain that is vital to verifying that a machine is actually part of the network.


## **Problem Breakdown**

#### **Definitions**
* ***Machine Registry***

Only attested machines are allowed to issue transactions on the RDDL network. The Machine Registry holds vital information about the attested machine or device. The following mechanisms are needed by the Machine Registry:
1. Machine Identity: A machine can only be attested to the RDDL network if it has a pre-attested Trust Anchor attache and is able to sign the JSON object of the attestation process with the Trust Anchor ID (machine identity). The Trust Anchor registry and Trust Anchors will be covered by REP-7 and REP-8.
3. Machine provisioning: The process of giving a machine a unique identity. This is done by creating a key-pair with a mnemonic phrase. A machine owner is required to store the mnemonic phrase if a machine or device needs to be replaced. The seed that is used to create all necessary keys is derived from this phrase.
4. Machine attestation: A machine will be attested to the RDDL network with a machine identity together with information about the machine or device and all public keys that are linked with it. This information contains the GPS location, device information and an asset definition and is signed by an identity providing device. 

If a machine fails to function the owner can restore access with to the assets with the mnemonic phrase.

## **Specification**

The machine registry service accepts these messages and queries:

1. AttestMachine
2. GetMachineByID
3. GetMachineByPlanetmintKey
4. GetMachineByLiquidKey

The AttestMachine message must contain the following information:
```json
{
  "name": <Name of the asset>,
  "ticker": <Ticker symbol>,
  "public_url": <url that is linked to the legal entity owning the machine>,
  "issued": <yes/no>,
  "amount": <amount of tokens>,
  "precision": <precision of the token denomination>,
  "issuerPlanetmint": <planetmint public key>,
  "issuerLiquid": <liquid public key>,
  "metadata": {
    "GPS": <position of the machine>,
    "device": <information describing the machine>,
    "assetDefinition": <attestation definition>,
    "additionalDataCID": <cid of additional metadata>
  },
  "machineId": <public-key of a pre-attested Trust-Anchor>,
  "machineIDSig": <signature of this json object with the 'machineIDSig' set to an empty string ''>
}
```
A machine can be queried by its ID, the planetmint public key or the liquid public key. This is to provide a mechanism to verify a machine has been registered.

## **Implementation**
The implementations must be completed before any REP is given status "stable", but it need not be completed before the REP is accepted. While there is merit to the approach of reaching consensus on the REP and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.

## **Copyright Waiver**
Except for REP-1 (C4) and REP-2 (COSS), all REPs MUST be released to the public domain. To do that, the following block of HTML SHOULD be used in the REP's source Markdown file. ([HTML is valid Markdown](https://daringfireball.net/projects/markdown/syntax#html).)
