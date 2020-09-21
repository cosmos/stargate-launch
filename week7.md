# Stargate Week 7 August 19th

## Executive Summary

Massive progress in the Stargate Week 7

The biggest milestone is the Tendermint team has completed all test and integration milestones for Stargate.

Tendermint 0.34 rc3 is out and integrated into Cosmos SDK master. There are some important issues remaining like height preserving upgrades and filling out the SDK side of the State sync. The changes to Tendermint to allow upgrades to avoid reseting the block height to zero was a major feature requests from both the IBC team and cryptocurrency exchanges. Huge thanks to the Tendermint team for landing this.

The next big milestone is an initial Gaia v3.0 candidate was built for our internal testnet for our Stargate champions. We are getting started on integrations with Lunie.

We have also begun collecting keys from validators from first public integration net.

We are closely watching progress the [migration issue](https://github.com/cosmos/cosmos-sdk/pull/6839) and AiB's progress on the upgrade manager as major milestones towards a public testnet launch.

## Key Activities

* Continue Gaia Migration

* Collect production Validator Keys for testnet genesis files

* Launch testnet trial with Lunie

## Workstreams

### IBC team (Interchain GmbH)

* Winding up on IBC 1.0

* Not currently blocking any Stargate events

### Tendermint Team (Interchain GmbH)

* Finishing up Evidence handling and support SDK integration work with Tendermint 0.34 *

### SDK team (Regen)

* [migrate command is the main blocker on testnet launc](https://github.com/cosmos/cosmos-sdk/pull/6839)
* Ongoing process towards the milestone

### Supervisor Team(All in Bits)

* All in Bits is working on integration of the upgrade manager into the SDK directory and integrating cosmosd into the continuous integration system.

### Relayer(Akash)

* Akash is begining work on updating the relayer from the Game of Zones version to SDK master.

### Iqlusion team

* Gaia migration continued
* Validator keys for genesis files continued
* Lunie provided testnet branch
* Endpoint testing

### Testnet planning

* Lunie documented results for Monday
