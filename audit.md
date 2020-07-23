# AminoREST and You
## How-To deal with Cosmos legacy interface in the Stargate

### Summary
New chain features, post the Stargate launch will unlikely support AminoREST. You can stick with the legacy AminoREST and not change your code very much. However, you should work towards the support for the new interface because if you want to take advantage of the new features in Cosmos. This document will help you get there with a review of the AminoREST support in Stargate.

This document is a simple review of the REST API endpoint changes between Cosmos SDK Master and Cosmos SDK v0.37.13

### The Cosmos SDK Versions audited
[Cosmos SDK master](https://github.com/cosmos/cosmos-sdk)

[Cosmos SDK tag v0.37.13](https://github.com/cosmos/cosmos-sdk/tree/v0.37.13)


### Here are the High Priority Endpoints for Queries:
* Staking
  * Validators
  * Delegators
* Bank
  * Balances
* Gov
* Auth 

### Audit Results
#### Validators
* **Endpoint Name:** QueryValidators
* **Endpoint Path:**
```"/staking/validators"```
* **What Changed:** 
  * The field ```"unbonding_height"``` is no longer supported
* Sample JSON<br/><br/>
* **Endpoint Name:** QueryDelegatorDelegations
* **Endpoint Path:** ```"/staking/delegators/delegations"```
* ****What Changed:****
  * ```“balance”``` now is no longer a number. It is a field with two values: ```"amount"``` and ```"Denom”```

  * ```“delegator_address”``` is no longer a string. It’s a field called ```“delegation”``` with three values: ```"delegator_address", "shares", "validator_address"```

  * The old field ```“validator_address”``` is no longer used. A new field ```“validator_dst_address”``` and```“validator_src_address”``` replace this in the new ```“redelegation”``` field.


* Sample JSON<br/><br/>

* **Endpoint Name:** QueryRedelegations
* **Endpoint Path:**
```"/staking/redelegations"```
* **What Changed:** The following old fields are now sub fields of a new field called ```“redelegation_entry”```:
  * ```"completion_time"```
  * ```"initial_balance"```
  * ```"shares_dst"```
* The old field ```“creation_height"``` is no longer supported.
* The following are new fields:
    *  ```“redelegation”``` which holds the sub-fields.
        * ```delegator_address``` (new)
        * ```entries``` (new)
        * ```valdiator_dst_address```
        * ```validator_src_address```

* Sample JSON<br/><br/>


* **Endpoint Name:** QueryUnbondingDelegation
* **Endpoint Path:**
```"/staking/unbondingDelegation"```
* **What Changed:**
  * The old field ```“creation_height"``` is no longer supported.

* Sample JSON<br/><br/>