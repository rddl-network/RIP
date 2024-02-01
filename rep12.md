```
shortname: REP-12
name: On-Chain Governance
type: standard
status: stable
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```
## **Abstract**
The behavior of the RDDL Protocol and Network can be configured. The proper configuration of all the parameters has to be orchestrated and might be tampered with to influence the protocol in a certain way. 
Moving crucial parameters to on-chain parameters solves this issue.


## **Motivation**
The goal of this REP is the description of purpose and the functionality of on-chain parameters.


## **Problem Breakdown**
The RDDL Network relies on certain configuration parameters that have to be equal on all nodes. The synchronization and coordinated deployment of these parameters is a challenge. The usage off the on-chain governance primitives of the [COSMOS SDK on-chain governance module](https://docs.cosmos.network/main/build/modules/gov) enables RDDL Network to avoid these constraints and challenges.
 
## **Specification**
The parameters of a chain can be defined by the genesis file. Their state can be updated via proposals and votes as menionted at [docs.rddl.io](https://docs.rddl.io/rddl-network/workflows-and-governance/voting-on-chain-parameters) and [Cosmos SDK](https://docs.cosmos.network/main/build/modules/gov)

### Current set of on-chain parameters
The following lines list the onchain parameter that got added by RDDL by module in alphabetical order:

#### DAO module
*  claim_address (string): The address that is allowed to report the number of confirmation on Liquid for the transfer of redeemed RDDLs.
*  claim_denom (string): Te denominator on Planetmint that is used to indicate how many RDDLs can be claimed.
*  distribution_address_dao (string): The address on Liquid that represents the DAO wallet.
*  distribution_address_early_inv (string): The address on Liquid that represents the Early Investor wallet.
*  distribution_address_investor (string): The address on Liquid that represents the Investor wallet.
*  distribution_address_pop (string): The address on Liquid that represents the wallet related to the PoP rewards.
*  distribution_address_strategic (string): The address on Liquid that represents the the address to hold funds for strategic investments.
*  distribution_offset (int64): The offset in epochs (blocks) to wait for the distribution of the tokens to the different wallets after the token reissuance.
*  fee_denom (string): The Fee denomination string.
*  mint_address (string): The address that is allowed to created and broadcast minting requests.
*  mqtt_response_timeout (int64): The amount of milliseconds to be waited for the availability response of machines before they are assigned to a PoP.
*  pop_epochs (int64): The periodicity of the Proof of Productivity in epochs (blocks).
*  reissuance_asset (string): The asset ID of the reissued token on Liquid.
*  reissuance_epochs (int64): The periodicity of the token reissuance in epochs (blocks).
*  staged_denom (string): The denominator of the staged RDDL claims.
*  token_denom (string): The denominator of the token (RDDL).
*  tx_gas_limit (uint64): The maximal transaction gas of an transaction that can be exectued on chain.

#### Machine module
*  asset_registry_domain (string): The domain of the asset registry service.
*  asset_registry_path (string): The URI path after the asset registry.
*  asset_registry_scheme (string): The http communication scheme (https/http).
