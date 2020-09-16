# Stargate Week  2 July 13th

## Key Activities

- Stargate Proposal 1 has launched for voting. <https://www.mintscan.io/proposals/27>.
- Iqlusion has begun out reach to initial, champion integration partners.
- The AIB team did a great job with the Stargate landing [page](https://stargate.cosmos.network/) and [gifs](https://twitter.com/cosmos/status/1284069967307198464?s=20).

# Risk Mitigation activities

- Fruitful discussion around network upgrades and IBC along with implementation work to support epochs in the light client.
[Abstract Height in IBC Clients by AdityaSripal · Pull Request #6686 · cosmos/cosmos-sdk · GitHub](https://github.com/cosmos/cosmos-sdk/pull/6686)

## Workstreams

### IBC team

- Planning for network upgrades how they integrate with IBC

### Tendermint Team

- Planning for Tendermint 0.34-rc1. 0.34 rc-1 will be the Stargate version. * All APIs except evidence handling will be frozen for the RC

### SDK team

- CLI Refactor + introduction of new testnet test framework, including in-process integration tests (<https://github.com/cosmos/cosmos-sdk/issues/6423>, <https://github.com/cosmos/cosmos-sdk/issues/6571>)
  - infrastructure done, module specific integration test migrations underway
- protobuf querier + grpc migrations for all sdk modules (<https://github.com/cosmos/cosmos-sdk/issues/5921>)
  - most querier services done, CLI query commands underway
- continuing infrastructure work for tx migration path (<https://github.com/cosmos/cosmos-sdk/issues/6213>)
  - Aaron leading this effort, with main current pieces underway being:
    - <https://github.com/cosmos/cosmos-sdk/pull/6614>
    - <https://github.com/cosmos/cosmos-sdk/pull/6470>

### Iqlusion team

- Stargate Project Management launched
- Governance proposal for Stargate finished.
- Selection and planning with champion integration partners.

![Distracted Devs](memes/distracted_devs.jpg)
