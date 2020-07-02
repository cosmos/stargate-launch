## Stargate Review meeting from June 30, 2020

# Stargate Week 1


### Big risks mitigated

Pruning/ in memory IAVL cache feature reverted.

Cosmosd will be integrated into the Cosmos plan.


### Critical activities

These two pull requests will define most of the integration breakage surface area for Stargate and it will be the difficult to fully scope the difficulty of migration until these issues are resolved.

Query Protobuf Migration: [Query Protobuf Migration · Issue #5921 · cosmos/cosmos-sdk · GitHub](https://github.com/cosmos/cosmos-sdk/issues/5921)

Proto Any Migration [Proto Any Tx migration · Issue #6213 · cosmos/cosmos-sdk · GitHub](https://github.com/cosmos/cosmos-sdk/issues/6213)

### Workstreams

#### IBC team
	Plan an upgrade of the Stargate testnet with live IBC channels
        On Going IBC 1.0 work

#### Tendermint Team
	Tendermint 0.34 Release

#### SDK team
     0.39 works and Cosmosd integration.
     Coordinate with the IBC team around how upgrades interact with IBC

### Iqlusion team
    Governance proposal for Stargate process.
    Plan next Stargate Command meeting

### Scope of Stargate

Stargate is focused on the impact of Cosmos software changes on wallets, exchanges and blockexplorers. Stargate is **not** focused on the developer migration path for zones from 0.38.* -> 0.39.* or the Launchpad release of an 0.38 LTS.

### Stargate Progress
As of Week 1, Stargate is

### What's Coming Next?
There will be an overview of the direction that the Cosmos Hub is taking to upgrade itself. This will be a DRAFT governance proposal that will be prepared for voting on Cosmos Hub.
