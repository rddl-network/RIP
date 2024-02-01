```
shortname: REP-8
name: Trust Anchor Registry
type: standard
status: Stable
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```

## **Abstract**
This REP defines the register new identities of supported hardware devices to the RDDL Network. 

## **Motivation**
 The goal of this REP is to enable 3rd parties to register new device identities on the RDDL Network. 
 Having done that, the devices will be able to attest themselves and start participating in the Proof of Productivity. 

In order to do so, trusted 3rd parties are able to register new device- or TrustAnchor-Identities on RDDL Networks Planetmint.

## **Specification**

RDDL Network exposes a service to download default RDDL-Compatible Tasmota firmwares. These firmwares can be used for ESP32 and ESP32C3 MCUs. 
These firmware get a random private key injected. The corresponding public key is registered with the Network.
The firmware needs to answer a challenge in order to attest the machine related to the EPS32 or ESP32C3 MCU on the RDDL Network.

The challenge is as follows:
The firmware needs to prove that is capable of signing the the Public Key associated with the machine with the corresponding private key.

This signature is expected to be put to the machineIdSignature Attribute of the Machine object defined at https://github.com/planetmint/planetmint-go/blob/main/proto/planetmintgo/machine/machine.proto.
The machineIdSignature is expected to be send as string containing the hexadecimal bytes values of the signature. 

Reference code can be found at https://github.com/rddl-network/librddl and https://github.com/rddl-network/rddl-sdk.



