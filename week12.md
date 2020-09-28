# Stargate Week 12 September 23rd

## Executive Summary

Momentus week for the stargate effort. 

Stargate-3 has near final versions of all of the key Stargate features. 

We are closing in on final release candidates for all software. This includes Tendermint and the Cosmos SDK. We anticipate focusing on stargate-3 and lining up an extensive promotional campaign and call to action to get people sign up.

The timeline in my mind is Oct 31st for a final upgrade governance proposal and we are working at pace towards that.


## Key Activities

* [Fixes for querying txs by hash were finally merged.](https://github.com/cosmos/cosmos-sdk/pull/7276) This unblocks explorers and wallets.
* [Legacy amino tx broadcast merged](https://github.com/cosmos/cosmos-sdk/pull/7285) This enables wallets and exchanges to complete testing Legacy Amino support


## Workstreams

### IBC team (Interchain GmbH)



### Tendermint Core team (Interchain GmbH)
- Released v0.34.0-rc4: https://github.com/tendermint/tendermint/releases/tag/v0.34.0-rc4 
    - This RC is feature complete. Future RCs will only include bug fixes. 
    - See [the changelog](https://github.com/tendermint/tendermint/blob/v0.34.0-rc4/CHANGELOG.md#v0340-rc4) for a full list of changes between RC3 and RC4. 

### SDK team (Regen)

### Upgrade Supervisor Team(All in Bits)


### Relayer(Akash)
- Continued relayer debugging. Waiting on https://github.com/tendermint/tendermint/issues/5367 for streaming relayer support
- Completed denom disambiuation for human readable denoms
- Working on ADR for typed events in the SDK

### Iqlusion team

- Promote Stargate Testnet 3

