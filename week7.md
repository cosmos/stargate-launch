# Stargate Week 7 August 19th

## Executive Summary

Massive progress in the Stargate Week 7

The biggest milestone is the Tendermint team has completed all test and integration milestones for Stargate.

Tendermint 0.34 rc3 is out and integrated into Cosmos SDK master. There are some important issues remaining like height preserving ugprades and filling out the SDK side of the State sync. The changes to Tendermint to allow upgrades to avoid reseting the block height to zero was a major feature requests from both the IBC team and cryptocurrency exchanges. Huge thanks to the Tendermint team for landing this.

The next big milestone is an initial Gaia v3.0 candidate was built for our internal testnet for our Stargate champions. We are getting started on integrations with Lunie.

We have also begun collecting keys from validators from first public integration net.

We are closely watching progress the [migration issue](https://github.com/cosmos/cosmos-sdk/pull/6839) and AiB's progress on the [upgrade manager](https://github.com/cosmos/cosmos-sdk/pulls?page=2&q=is%3Apr+is%3Aopen) as major milestones towards a public testnet launch.


## Workstreams

### Tendermint Team (Interchain GmbH)

- Working towards finalizing the evidence workflow and final release.

### SDK team (Regen)

- Finishing up the migrate command.
- Making a breaking change to tranasctions serialization to include sequence numbers for better error messages on signature verification failure.
