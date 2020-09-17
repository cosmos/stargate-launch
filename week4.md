# Stargate Week 4 July 27th

## Executive Summary

The core goal of the Stargate team is to ensure that ecosystem integration efforts can make progress in parallel with Tendermint/Cosmos SDK release candidates.

We are pivoting to an integration testnet that will be presented to Lunie and then opened up to other partners as verification/validation of the Legacy Amino interface progresses.

The integration testnet is currently blocked on completing [Proto Tx migration](https://github.com/cosmos/cosmos-sdk/issues/6213). Completion of this issue will allow integration partners to test their integrations with the Legacy AMINO interface for TX creation and signing. We expect this to be a very important API surface area for exchanges.

We would strongly prefer to be operating the integration testnet off of Tendermint 0.34-rc* or Tendermint `master` and we looking toward the merging of this [Marko's PR](https://github.com/cosmos/cosmos-sdk/pull/6471) as well.  

## Key Activities

* Stargate Proposal 1 has reched 47% with 486.563M ATOMs voting [Yes](https://hubble.figment.network/cosmos/chains/cosmoshub-3/governance/proposals/27). Thank you to everyone who helped make this proposal a success.

* [Amino Legacy Audit DRAFT](https://github.com/cosmosdevs/stargate/pull/8) published and in community review. This audit provides guidance to integration partners for preserving functionality after the upgrade.

* [Review of ADR 001 completed](https://github.com/cosmos/cosmos-sdk/pull/6662)

* A number of exchanges have expressed concern about how the blockheight reset on Tendermint upgrade interacts with their accounting systems. We explored with the Tendermint team the possibility of enabling Tendermint to start at an arbitrary blockheight.

* A discussion of Rosetta support for Coinbase for all Cosmos SDK applications is being discussed [here](https://github.com/cosmos/cosmos-sdk/issues/6831).

## Workstreams

### IBC team

* Coin tracking ADR appears to be final. Waiting on integration between the Cosmos SDK and Tendermint `master` for final AMINO removal from IBC internals.

* The Iqlusion team has been providing assistance to Akash around planning support for the Golang relayer in Stargate.

### Tendermint Team

* There is a lot of discussion on the final [event hashing](https://github.com/tendermint/tendermint/pull/5134) API. This is currently blocking an 0.34 release because master implements hashing all events into the the block header.

### SDK team

* We've communicated our preference to the SDK team to have the full Proto internal/Legacy AMINO Rest interface completed as soon as possible. Then the 0.39 to 0.40 migrate command so that we can support a simulated upgrade testnet. These preferences have been accepted and we are watching closely.

### Iqlusion team

* Lunie & Iqlusion agree to a internal 4-Nodes x 3 (A-B-C) stargate testnet
* Amino endpoints Audit DRAFT completed and submitted to Coinbase for review
* Flow of Funds Diagram for IBC Mastery level 0 is work in progress.

### Testnet planning

* Discussing with the Regen team about interest groups in the steady state Stargate testnet outside of integration partners. For example, Informal is likely to be an early consumer of GRPC for their relayer. Other Zones are likely to be interested in running zones with active IBC connections to the Stargate steady state testnet.
