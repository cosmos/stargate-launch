# Stargate Week  3 July 20th

## Executive Summary
There are three prequsites for Testenet launch and they are in progress:
* [Tendermint .034rc](https://github.com/tendermint/tendermint/milestone/27)
* [Cosmos SDK 0.40rc](https://github.com/cosmos/cosmos-sdk/milestone/25)
* [State migration code](https://github.com/cosmos/cosmos-sdk/issues/5917)

We were anticipating 0.34 Tendermint within this week.. However, it won't be available until next week, July 20, 2020.

We are auditing the API changes this week: The most important discovery is the Amino JSON REST interface will be preserved, which substantially decreases the scope of integration changes. There will be 3 possible query interfaces to Stargate, REST-AMINO json, REST - GRPC Gateway JSON and GPRC>


## Key Activities
* Stargate Proposal 1 has reched 23% with 41MM ATOMs voting Yes. https://hubble.figment.network/cosmos/chains/cosmoshub-3/governance/proposals/27


* [Stargate IBC Support Matrix](https://github.com/cosmosdevs/stargate/pull/7) for Crypto-Exchanges created. Work in Progress on a flow of funds document for IBC.

* Regen & Cosmos SDK architecture review completed

* Collection of Public keys will begin on July 27th for the Stargate Testnet.


## Workstreams

### IBC team
* Scoping the relayer activities in support of Stargate. Realistically a Stargate compatible relayer is 3 weeks out from RC1. Stargate participants should expect there to be some time between the launch of the Stargate testnet and when IBC integrations can practically be tested. 

### Tendermint Team
* 

### SDK team
* The SDK team is writing the software changes for the migration
* ADR updates will come out of the Regen & Cosmos SDK review



### Iqlusion team
* Lunie and Iqlusion shared slack launched
* Intial meetings with exchanges.
* Genesis file construction Validator Key JSON document created
* Iqlusion Gaia migration pushed back to favor audit between Tendermint 0.32 and 0.34 and Cosmos 0.37 and 0.40 and indicate what has changed
* Jack Zampolin debrief on IBC requirements and reyaler status started
