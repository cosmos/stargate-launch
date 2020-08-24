# Stargate Week 7 August 36th

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

## Workstreams

### IBC team (Interchain GmbH)

Ongoing work aligning with Tendermint 0.34

### Tendermint Team (Interchain GmbH)

Finishing up evidence handling and integrating the Cosmos SDK with Tendermint 0.34

### SDK team (Regen)

* [migrate command is the main blocker on testnet launc](https://github.com/cosmos/cosmos-sdk/pull/6839)
* Ongoing process towards the milestone

### Supervisor Team(All in Bits)

* Supervisor is now merged with the Cosmos SDK. We need to figure out where gaia users will get supervisor.

### Relayer(Akash)

* Continue integr

### Iqlusion team

* Launch testnet
* Lunie integration feedback with Lunie
* Endpoint testing