# Stargate Week 8 August 26th

## Executive Summary

We believe it's time to launch the Stargate public testnet this week.

We've accomplished several key milestones. We have an initial [Gaia build](https://github.com/cosmos/gaia/pull/456) with Stargate functionality. The legacy endpoints and Tendermint changes are stable.

Unfortunately the key milestone we were looking over the last week isn't completed yet. The `migrate` [command](https://github.com/cosmos/cosmos-sdk/pull/6839) is still not ready to go.

Thus are first public testnet will be a fresh genesis file that we will release on Tuesday. A simulated upgrade of the Cosmos Hub will wait on the migrate command completion.

By releasing this testnet, the ecosystem can build up experience with IBC, the new SDK binaries and new transaction construction.

## Key Activities

Deploy [Gaia 3.0 alpha 1](https://github.com/cosmos/gaia/pull/456) version

Launch public testnet.

Continue integration case study with Lunie.

Welcome integration participation with Figment

Prepare documentation for the next phase of testnet participation

Check in with exchange partners on compliance impact of Stargate Readiness Level 0

## Workstreams

### IBC team (Interchain GmbH)

Ongoing work aligning with Tendermint 0.34

### Tendermint Team (Interchain GmbH)

Finishing up evidence handling and integrating the Cosmos SDK with Tendermint 0.34

### SDK team (Regen)

* [migrate command is the main blocker on testnet launc](https://github.com/cosmos/cosmos-sdk/pull/6839)
* Main 3 outsanding pieces are as follows:
  * enabling gRPC gateway
  * migrating PubKey to protobuf based extensible address format
  * Tendermint 0.34 updates (including support for non-zero initial height)
* Tracking issue for Cosmos SDK's Stargate release candidate can be found [here](https://github.com/cosmos/cosmos-sdk/issues/7152)

### Supervisor Team(All in Bits)

* Supervisor is now merged with the Cosmos SDK. We need to figure out where gaia users will get supervisor.

### Relayer(Akash)

* Continue integr

### Iqlusion team

* Launch testnet
* Lunie integration feedback with Lunie
* Endpoint testing
* Ongoing validator key collection
