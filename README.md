# Stargate upgrade

[Join the Cosmos Stargate announcements channel!](Cosmos Stargate announcements channel!)

If you’re running a block explorer, wallet, exchange, validator, or any other service (eg. custody provider) that depends upon the Cosmos Hub or Cosmos ecosystem, you’ll want to pay attention, because this upgrade will involve substantial changes.

- [Collection of breaking changes from changelogs](breaking_changes.md)
- [Inter-Blockchain Communication (IBC)– cross-chain transactions](https://figment.network/resources/cosmos-stargate-upgrade-overview/#ibc)
- [Protobuf Migration – blockchain performance & dev acceleration](https://figment.network/resources/cosmos-stargate-upgrade-overview/#proto)
- [State Sync – minutes to sync new nodes](https://figment.network/resources/cosmos-stargate-upgrade-overview/#sync)
- [Full-Featured Light Clients](https://figment.network/resources/cosmos-stargate-upgrade-overview/#light)
- [Chain Upgrade Module – upgrade automation](https://figment.network/resources/cosmos-stargate-upgrade-overview/#upgrade)

Help us to get the word out–this is a major leap for the Cosmos Network and we want everyone on board 🚀

## Testnet

### Uncoordinated Upgrade Completed 02-02-2021

Upgrade instructions:

1. Stop your gaia v3 instance 

```
killall gaiad
```

2. Backup your `.gaia` folder

3. Install gaia v4 binary

```
git checkout v4.0.0
make install
```

4. Start gaia v4.0.0 binary


### Joining

We are launching the final stargate testnet. We

- [Genesis file](genesis.json)

```
git clone https://github.com/cosmos/gaia
git checkout v4.0.0
make install
```

Our validator node for a persistent peer is available at

```bash
6ae55f60f0951247985ccd52773312aa89413d1c@34.71.170.158:26656
```

Please familiarize your self with the [Running a Node](https://github.com/cosmos/cosmos-sdk/tree/master/docs/run-node) documentation.


- Legacy Amino
- IBC
- State-Sync
- Cosmovisor




## Statesync Configuration Options

State sync rapidly bootstraps a new node by discovering, fetching, and restoring a state machine snapshot from peers instead of fetching and replaying historical blocks. Requires some peers in the network to take and serve state machine snapshots. State sync is not attempted if the node has any local state (LastBlockHeight > 0). The node will have a truncated block history, starting from the height of the snapshot.

In the Tendermint config file there is a state-sync section. Some of these fields must be filled in order to use state-sync.

To find out how to fill in this information please visit: <https://docs.tendermint.com/master/tendermint-core/state-sync.html>

Additionally, some nodes in the network must take state sync snapshots, which are configured in `app.toml`:

Snapshot-interval specifies the block interval at which local state sync snapshots are taken (0 to disable). Must be a multiple of pruning-keep-every.

> NOTE: Please set this value to a non-zero value. This is required in order for other nodes to be able to utilize state-sync.

```bash
snapshot-interval = {{ .StateSync.SnapshotInterval }}
```

Snapshot-keep-recent specifies the number of recent snapshots to keep and serve (0 to keep all).

```bash
snapshot-keep-recent = {{ .StateSync.SnapshotKeepRecent }}
```

These are disabled by default, out of caution - this is new code, and we wouldn't want it to cause a chain-wide halt or data corruption. Eventually we can consider enabling them by default.

- [Week 1 Status July 2nd, 2020](week1.md)
- [Week 2 Status July 11th, 2020](week2.md)
- [Week 3 Status July 17th, 2020](week3.md)
- [Week 4 Status July 27th, 2020](week4.md)
- [Week 5 Status August 7th, 2020](week5.md)
- [Week 6 Status August 12th, 2020](week6.md)
- [Week 7 Status August 19th, 2020](week7.md)
- [Week 8 Status August 26th, 2020](week8.md)
- [Week 9 Status September 6th, 2020](week9.md)
- [Week 10 & 11 Status September 16th, 2020](week10_11.md)
- [Week 12 Status September 23, 2020](week12.md)

- [Project Board](https://github.com/orgs/cosmosdevs/projects/1)
