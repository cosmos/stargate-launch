# Stargate Week 9 September 9th

## Executive Summary

Big week for the Stargate initiative with the launch of the first `stargate-1` testnet.

This testnet has been humming along nicely for last week. We've seen both **Akash** and **Agoric** projects adopt the stargate codebase for forth coming release. Blockscape, Everstake and IRIS have joined Iqlusion in running `stargate-1` validators. Jack and the `Akash` team are hard at work updating the IBC relayer to run on the testnet.

We've encountered, documented and worked with the SDK and IBC team to fix a number of bugs encountered with running work-in-progress stargate code.

We are looking forward to stability and better documentation of the legacy amino interface before we start on boarding larger developer teams.

## Key Activities

## Workstreams

### IBC team (Interchain GmbH)

* Final parts of protobuf migration, testcases & general cleanup
* Implementation updates to allow safe future IBC protocol upgrades
* Minor protocol updates for asynchronous acknowledgement support

### Tendermint Core team (Interchain GmbH)

* Light client evidence handling - simplifying, verifying, and reimplementing
* Integrating Cosmos SDK with the latest Tendermint 0.34 release candidate
  * This includes integrating the state sync feature and ironing out any bugs
* Ensuring that Tendermint docs are up to date for 0.34

### SDK team (Regen)

* PubKey migration to protobuf still underway, with continued complications
* gRPC gateway & last querier handling blocked on [#7195](https://github.com/cosmos/cosmos-sdk/issues/7195)
* non-zero initial height complete [#7089](https://github.com/cosmos/cosmos-sdk/pull/7089)
* Synced with Tendermint team on handling of Light client evidence
* Follow progress towards RC on [Stargate RC tracking issue](https://github.com/cosmos/cosmos-sdk/issues/7152)

### Supervisor Team(All in Bits)

### Relayer(Akash)

* Begun work on migrating the relayer to v0.40 of the SDK
* Implementation work in [ovrclk/relayer](https://github.com/ovrclk/relayer/pull/278)
* Code is now compiling, tests run but fail.
* Worked with SDK team to fix [gas issue](https://github.com/cosmos/cosmos-sdk/pull/7207) and [ibc proto registration issues](https://github.com/cosmos/cosmos-sdk/pull/7210)

### Iqlusion team

* Stargate-1a Gaia release tagged after various updates
* Stargate release support with Figment, Lunie, and Trustwallet
* Ongoing collection of validator keys continues
* Stargate Testnet Office Hours launched
