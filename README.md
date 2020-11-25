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

We've now launched the Cosmos Hub Stargate testnet `cosmoshub-test-stargate` for the Stargate simulated upgrade on October 28, 2020

`cosmoshub-test-stargate` is based on Cosmos SDK-0.40-rc3.

The following features are live on the testnet.

- Legacy Amino
- IBC
- State-Sync
- Cosmovisor

This testnet is intended to be a simulation testnet for Cosmos Hub-3

### Simulated CosmosHub-3 Upgrade

A test migration command targeted the blockheight dated around 11/01/2020 for the migration was as follows:

Step 1:

```bash
cd ~/
git clone https://github.com/cosmos/gaia
git clone https://github.com/cosmosdevs/stargate
cd gaia
git checkout cosmoshub-test-stargate
make build
```

Step 2: The Cosmos Hub-3 genesis snapshot of hub at block height 3924406 is here: [ttps://storage.googleapis.com/stargate-genesis/3924406.cosmoshub-3.json](ttps://storage.googleapis.com/stargate-genesis/3924406.cosmoshub-3.json)

Step 3: There is a full copy of a cosmos hub full node here: [https://storage.googleapis.com/stargate-genesis/snapshot.tgz](https://storage.googleapis.com/stargate-genesis/snapshot.tgz)

Step 4: Using Gaia 2.0 and this cosmos node above,

```bash
gaiad export > 3924406.cosmos_hub_3.json
```

Step 5: Using the crowdsourced public keys from the Stargate repo:

```bash
build/gaiad migrate ~/3924406.cosmoshub-3.json --chain-id=cosmoshub-test-stargate-d --initial-height 3924407 --replacement-cons-keys ~/stargate/validator_replacement.json > migrated_genesis.json

jq . migrated_genesis.json > genesis.json
```

To simplify testing, we manually adjusted some governance parameters.

```json
{
  "tally_params": {
    "quorum": "0.010000000000000000",
    "threshold": "0.500000000000000000",
    "veto_threshold": "0.334000000000000000"
  },
  "votes": [],
  "voting_params": {
    "voting_period": "172800s"
  }
}
```

Outcome: The output should match the genesis file at https://storage.googleapis.com/stargate-genesis/genesis.json

shas256sum genesis.json

`b1ea6d4337d35adb43a14db2c302824e94b50071431750e10f4c00856f9c56e5`

**NOTE:**

1. `gaiad start` will preform an extensive audit of the genesis file state that takes > 1 hour. `gaiad start --x-crisis-skip-assert-invariants` skips the audits and starts a node in 15 min.

2. We manually went in and edited the quorum and voting period for governance to enable faster testing of the IBC related governance functions in this testnet.

#### Seed nodes

`c5e186e29d322788b8154723d04e1de018d38475@34.66.219.254:26656`

### Stargate-5 Testing

- Testing wallets, exchanges and block explorers against the legacy Amino REST interface
- Giving node operators and validators an opportunity to test their integrations against a work in progress version
- Playing with new Stargate features including IBC is possible now with the Akash realyer! Try it out at https://github.com/ovrclk/relayer/releases/tag/stargate-4

Our validator node for a persistent peer is available at

```bash
e096c06890c8de6c030c05833c88c65651e0abed@34.66.55.131:26656
```

For users who want to test state sync, our validator node has tendermint rpc open on `34.66.55.131:26657`and we are snapshotting every 1000 blocks.

As of 11/11/2020, the tagged `gaia` version is [cosmoshub-test-stargate](https://github.com/cosmos/gaia/tree/cosmoshub-test-stargate)

Remember this version now has a single binary instead of `gaiacli/gaiad` and much more configurable `app.toml`

```bash
git clone https://github.com/cosmos/gaia
git checkout cosmoshub-test-stargate
make build
```

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
