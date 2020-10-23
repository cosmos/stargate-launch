# Cosmos Stargate Hub Upgrade Proposal 2
## by Iqlusion 

October 20, 2020

## Context
------------
Stargate is our name for the process of ensuring that the widely integrated public network known as the Cosmos Hub is able to execute the cosmoshub-3 -> cosmoshub-4 upgrade with the minimum disruption to its existing ecosystem. This upgrade will also realize the Internet of Blockchains vision from the Cosmos whitepaper.

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
The results of ecosystem participation and engagement are available in our [Stargate Ecosystem Readiness Report](https://github.com/cosmosdevs/stargate/blob/master/ecosystem_readiness.md). We list on this page ecosystem partners such as Validators that provided their validator public keys as well as infrastructure partners that confirmed their integration testing the Stargate testnet tags.

The Cosmos SDK, Tendermint, AiB, and IBC teams worked tirelessly to deliver the most robust software feature set that would make up the Cosmos Stargate release. Their review of their efforts are documented in their recap blog post ["How Seven Teams Collaborated To Deliver The Biggest Software Upgrade In The Cosmos Universe"](https://blog.cosmos.network/how-seven-teams-collaborated-to-deliver-the-biggest-software-upgrade-in-the-cosmos-universe-2288f4f9afe8). 

We are confident that we have and continue to achieve increased ecosystem engagement with the Stargate testnet.




### Critical Partner Support 
We delivered critical partner support to leading ATOM exchanges. Out of the exchange support efforts, we documented the [IBC Readiness Matrix](https://github.com/cosmosdevs/stargate/blob/master/ibc_readiness_matrix.md) that outlines the levels of readiness that exchanges may select as they upgrade to Cosmos Stargate. 

We also completed and delivered a completed legacy Amino Audit, [AminoRest & You](https://github.com/cosmosdevs/stargate/blob/master/audit.md). The core finding of this audit was that changes to the underlying structs result in an interface that is close to the prior version allowing legacy queries to return valid data.

### Documentation and Self-Certification
The upgrades with the most breaking changes such as legacy Amino have a complete audit with documentation on exceptions for blockchain API interfaces.

Most exchanges and wallets have taken self-certification on directly. Our team continues to provide real-time support on multiple partner slack channels and on the Cosmos #stargate Discord channel.

### Cosmos Stargate Integration Success



## Stargate Upgrade Steps
------------

## Time of the Upgrade
------------

## The git commit of Gaia that we are upgrading to
------------



## What we're doing from now until the Upgrade
------------


## What is the upgrade abort process
------------
Bugs
Commit hash changes
Other issues    