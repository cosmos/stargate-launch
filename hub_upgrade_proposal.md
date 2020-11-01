# Cosmos Stargate Hub Upgrade Proposal 2
## by Iqlusion 

October 31, 2020

Current Status: Draft
Blocked on Final Code Hashes from the IBC, Tendermint and SDK teams.

## Key Results
------------
If passed, this governance proposal would commit the Cosmos Hub to upgrading to halting the `cosmoshub-3` at 06:00 UTC on Nov 19 exporting the state and starting `cosmoshub-4` based on gaia 3.0.


## Context
------------

In proposal 27, Iqlusion proposed a comprehensive process to translate the unprecented surface area of this upgrade. We called this process Stargate. 

Iqlusion is pleased to report that the Stargate Process has been successfully executed. We believe the chevrons are unlocked and that Hub can safely step throught the Stargate.

After the success of the community approval of the first Stargate Upgrade proposal, we now follow-up with the second Stargate proposal for the Cosmos Hub that will outline the results of the first proposal and the process for upgrading the Hub.

## The Stargate Plan
------------
The purpose of the Stargate effort was to ensure that Cosmos can fulfill the vision of an Internet of Blockchains in 2020 while mitigating the risks outlined above. It was also an attempt to create a process for complex future on-chain upgrades on the Cosmos Hub. That included the following steps:

1. Run the Stargate Testnet and use this as an integration testing target with widest possible ecosystem participation to help confirm the readiness of the release software.

2. Engage and support critical partners during the integration process so that partners are able to actively participate in the testing process and provide insights into their success with the upgrade.

3. Dedicate significant resources in terms of full time human resources and documentation efforts to ensure that everyone integrated into the Cosmos Hub can self-certify as Stargate-ready.

4. Report back to the Hub on the success of the integration process.
  a. We expect that the primary responsibility of the Cosmos Hub is to assess whether we have mitigated the above risks sufficiently.

  b. Provide a written report of the entire Stargate effort to enable Hub governance to make an informed decision.

5. At conclusion, we will indicate why we have confidence that an upgrade won't be disruptive to the Hub’s ecosystem.


## Stargate Plan Results
------------

### 1. Ecoystem Participation:
The results of ecosystem participation and engagement are available in our [Stargate Ecosystem Readiness Report](https://github.com/cosmosdevs/stargate/blob/master/ecosystem_readiness.md). We list on this page ecosystem partners such as Validators that provided their validator public keys as well as infrastructure partners that confirmed their integration testing the Stargate testnet tags. Validators, exchanges, and wallets have made up the most responsive of their results completing integration testing of the stargate releases.

The Cosmos SDK, Tendermint, AiB, and IBC teams worked tirelessly to deliver the most robust software feature set that would make up the Cosmos Stargate release. Their review of their efforts are documented in their post ["How Seven Teams Collaborated To Deliver The Biggest Software Upgrade In The Cosmos Universe"](https://blog.cosmos.network/how-seven-teams-collaborated-to-deliver-the-biggest-software-upgrade-in-the-cosmos-universe-2288f4f9afe8).

Integration testing continued through the release of the Cosmos SDK v0.40.0-rc2 that makes up the Cosmos-hub Stargate testnet tag for a simulated upgrade of the CosmosHub-3 to CosmosHub-4. Also, the AiB team continues to deliver simulation testing of Cosmos Stargate to ensure that any possible chain bug issues can be detected and documented. 

We are confident that we have and continue to achieve increased ecosystem engagement with the Stargate testnet.

### 2. Critical Partner Support 
We delivered critical partner support to leading ATOM exchanges. Out of the exchange support efforts, we documented the [IBC Readiness Matrix](https://github.com/cosmosdevs/stargate/blob/master/ibc_readiness_matrix.md) that outlines the levels of readiness that exchanges may select as they upgrade to Cosmos Stargate. 

We also completed and delivered a completed legacy Amino Audit, [AminoRest & You](https://github.com/cosmosdevs/stargate/blob/master/audit.md). The core finding of this audit was that changes to the underlying structs result in an interface that is close to the prior version allowing legacy queries to return valid data.

### 3. Documentation and Self-Certification
Documentation was a success for the Cosmos Stargate effort. The upgrades with the most breaking changes such as legacy Amino have a complete audit with documentation on exceptions for blockchain API interfaces.

Most exchanges and wallets have taken self-certification on directly. Our team continues to provide real-time support on multiple partner slack channels and on the Cosmos [#stargate Discord](https://discord.gg/W8trcGV) channel.


### Cosmos Stargate Integration Success
Cosmos Stargate integration success with exchanges and wallet providers reflects the quality of the code developed by the various Cosmos teams.

## Stargate Upgrade Steps
------------
The upgrade steps for the simulated upgrade of the current Cosmoshub mainnet to Cosmos Stargate includes the following steps:

This section is with the current `gaia 2.0.*` implementation.

  1. Validators should set their `gaia` with a halt time of `1605765600`ie. 06:00 UTC on Nov 19th in Unix time.

  2. Validators should then export the current cosmos state with `gaiad export > cosmoshub-3-export.json`

  3. Validators should determine the height the last block.


This section is with the upgrade `gaia 3.0.*` implemenataion.

  1. Validators should then migrate the exported genesis state. `gaiad migrate cosmoshub-3-export.json --chain-id=cosmoshub-test-stargate --initial-height [last_cosmoshub-3-block+1]`
  2. 

## Time of the Upgrade
------------
We propose scheduling the Cosmoshub-3 to Cosmoshub-4 simulated upgrade for Thursday November 5th, 2020 at [XX00 UTC]

## The git commit of Gaia that we are upgrading to
------------



## What we're doing from now until the Upgrade
------------


## What is the upgrade abort process
------------
Bugs
Commit hash changes
Other issues