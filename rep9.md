```
shortname: REP-9
name: Hardware Compatibility
type: standard
status: Stable
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```


## **Abstract**
This REP defines the hardware compatibility requirements.

## **Motivation**
RDDL Compatibility Requirements are defined below. It is crucial to verify the 
* Integration of libRDDL
* on the RDDL Testnet.


## Specification

RDDL Network maintains a reference implementation of hardware supporting all the basic functionalities to participate in the RDDL Network protocol.
* Support of a unique machine identifier (Machine ID) in the form of a public-private key pair. This key pair works as the anchor of Trust and can reside in a hardware-based  or within a unique firmware.
* Network configuration needs to be possible so that the Testnet and Mainnet can be configured for the device:
  * ChainID: the chainid of the network the device is connected against.
  * API: the API of a node or validator
  * Denominator token: TRDDL vs RDDL 
  * Key initialization: setting of a Mnemonic to recover in the case of disaster recovery.
* Behavioural configuration
  * Manual Machine Attestation
  * Asset attestation periodicity
* Actionability
  * Export public keys to enable account funding on Planetmint
  * Attest itself to the network
  * Attest assets/CIDs
  * Store CIDs and corresponding data for at least 45 days
  * Implement the PoP related commands for MQTT/XMPP as defined in the reference implementation at the [RDDL-Tastmota](https://github.com/rddl-network/Tasmota) repository.
