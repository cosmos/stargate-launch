# Stargate Week 5 August 7th

## Executive Summary

The release of Tendermint 34.rc2 advances Stargate private testnet preparation. Marko is making rapid progress integrating the latest Tendermint with the cosmos SDK. The Block endpoint in the legacy api is one of the big missing pieces in our Amino audit. With this integration happening, the Iqlusion team can tie up this issue as well.

The transaction generation endpoints have all been migrated to use Protobuf internally. We are now able to test for API breakage for wallets and the Ledger app and will be adding this to the audit report.

We are putting our effort into completing a port of Gaia to the SDK master for a testnet with Lunie.

## Key Activities

* Start Amino audit of Tendermint endpoints in Master and Tendermint 0.33

* Secure feedback for exchange partners on flow of funds with the IBC and ICS20 active showing creation and destruction of fund before the reach an exchange wallet

## Workstreams

### IBC team (Interchain GmbH)

Integration with Tendermint 0.34 and complete removal of Amino from IBC

### Tendermint Team (Interchain GmbH)

Work on getting height retaining upgrades and further evidence handling improvements into Tendermint 0.34 final in time for the final phases of the Stargate testnet.

Thank you to the Tendermint team for the integration target RC!

### SDK team (Regen)

Bringing the Comsos upgrade manager into the SDK for upgrades.

Completing the remaining work towards an SDK release candidate.
  
Ran the first SDK Community call

### Iqlusion team

* Update DRAFT flow of funds for exchange partners
* Cosmos SDK Community calls completed

### Testnet planning

* Focusing on the Lunie integration testnet
