# Stargate Week 6 August 12th

## Executive Summary
Gaia migration continues.

We are working on getting the MVP gaia migration story done. As we started the gaia migration this week, we realized that there were a lot cosmetic changes to the Cosmos SDK. Package names have been altered as files moved. These changes are frequently cosmetic but trying to bring Gaia up to date we realized that the change set would probably result in nearly every line changing.

So we are trying an alternative approach, we are going to take SimApp and turn it into a Gaia app. This will be a somewhat odd commit history. We aren't sure if this strategy might be precedent setting for future updates.

Gaia is only a few thousand lines of code but reviewing as diff against simapp seems much more approachable than.

Our big goals for the forth coming week now launching the Lunie testnet and collecting public keys for the simulated upgrade network.

The other big miletstone is Amino was finally fully removed from IBC.


## Key Activities
* Start Gaia migration

* IBC Flow of funds next steps

* Collect production Validator Keys for testnet genesis files


## Workstreams


### IBC team (Interchain GmbH)

Complete Amino removal and upgrade to Tendermint 0.34 integration candidates

### Tendermint Team (Interchain GmbH)

Debugging issues found in integration testing.


### SDK team (Regen)

Amazing progress on genesis migrationa and prep for the simulated upgrade network.


### Iqlusion team

* Follow up with partners on IBC flow of funs
* Gaia migration continued
* Validator keys for genesis files

### Testnet planning

* Lunie Testnet planned for next Tuesday
