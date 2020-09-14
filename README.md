
# Stargate upgrade
[Join the Cosmos Stargate announcements channel!](Cosmos Stargate announcements channel!)

If you’re running a block explorer, wallet, exchange, validator, or any other service (eg. custody provider) that depends upon the Cosmos Hub or Cosmos ecosystem, you’ll want to pay attention, because this upgrade will involve substantial changes.

- [Inter-Blockchain Communication (IBC)– cross-chain transactions](https://figment.network/resources/cosmos-stargate-upgrade-overview/#ibc)
- [Protobuf Migration – blockchain performance & dev acceleration](https://figment.network/resources/cosmos-stargate-upgrade-overview/#proto)
- [State Sync – minutes to sync new nodes](https://figment.network/resources/cosmos-stargate-upgrade-overview/#sync)
- [Full-Featured Light Clients](https://figment.network/resources/cosmos-stargate-upgrade-overview/#light)
- [Chain Upgrade Module – upgrade automation](https://figment.network/resources/cosmos-stargate-upgrade-overview/#upgrade)

Help us to get the word out–this is a major leap for the Cosmos Network and we want everyone on board 🚀

## Testnet

We've launched the second public alpha testnet `stargate-2` for the Stargate Upgrade on Tuesday September 8th.

This release fixes issues with Legacy Amino that were discovered in `stargate-1`. We believe that this version is now good to test for exchanges and wallets.

This testnet is intended for:

* Testing wallets, exchanges and block explorers against the legacy Amino REST interface
* Giving node operators and validators an opportunity to test their integrations against a work in progress version
* Playing with new Stargate features including IBC but real testing of IBC will wait on Akash updating the Relayer and possibly a future testnet.

We anticpate restarting this testnet with future integration targets. Once we have a migration script, we will launch a testnet with a simulated upgrade from cosmoshub-3.



Our validator node for a persistent peer is available at

``` bash
00d8e9c0df367296436854b580d9b069d3f1a5fd@34.123.30.100:26656
```

As of 08/31/2020, the tagged `gaia` version is [stargate-2](https://github.com/cosmos/gaia/releases/tag/stargate-2)

Remember this version now has a single binary instead of `gaiacli/gaiad` and much more configurable `app.toml`

``` bash
git checkout https://github.com/cosmos/gaia
git checkout stargate-2
make build
```

The genesis file is available [here](genesis.json)

## Statesync Configuration Options
State sync rapidly bootstraps a new node by discovering, fetching, and restoring a state machine snapshot from peers instead of fetching and replaying historical blocks. Requires some peers in the network to take and serve state machine snapshots. State sync is not attempted if the node has any local state (LastBlockHeight > 0). The node will have a truncated block history, starting from the height of the snapshot.

``` bash
enable = {{ .StateSync.Enable }}
```

Additionally, some nodes in the network must take state sync snapshots, which are configured in app.toml: 

Snapshot-interval specifies the block interval at which local state sync snapshots are taken (0 to disable). Must be a multiple of pruning-keep-every.

``` bash
snapshot-interval = {{ .StateSync.SnapshotInterval }}
```

Snapshot-keep-recent specifies the number of recent snapshots to keep and serve (0 to keep all).

``` bash
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
- [Project Board](https://github.com/orgs/cosmosdevs/projects/1)
