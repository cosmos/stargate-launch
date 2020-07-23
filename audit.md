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
* Distribution

### Audit Results
#### Validators
* **Endpoint Name:** QueryValidators
* **Endpoint Path:**
```"/staking/validators"```
* **What Changed:** 
  * The fields ```"unbonding_height"``` and ```"jailed"``` are no longer supported
* **Sample JSON:**
```JSON
{
      "commission": {
          "commission_rates": {
              "max_change_rate": "0.000000000000000000",
              "max_rate": "0.000000000000000000",
              "rate": "0.000000000000000000"
          },
          "update_time": "1970-01-01T00:00:00Z"
      },
      "consensus_pubkey": "cosmosvalconspub1zcjduepqwuxd2yevzmsrmrjx2su8kdlk44eqfdzeqx27zejuen6m0nkcpzps0qavpw",
      "delegator_shares": "0.000000000000000000",
      "description": {
          "details": "security",
          "identity": "identity",
          "moniker": "moniker",
          "security_contact": "details",
          "website": "website"
      },
      "min_self_delegation": "1",
      "operator_address": "cosmosvaloper1pcpl7xhxq0wm72e9ljls2sxr5h3vqwytnq44sr",
      "status": 1,
      "tokens": "0",
      "unbonding_time": "1970-01-01T00:00:00Z"

  }
```   
#### Delegators
* **Endpoint Name:** QueryDelegatorDelegations
* **Endpoint Path:** ```"/staking/delegators/delegations"```
* **What Changed:**
  * ```“balance”``` now is no longer a number. It is a field with two values: ```"amount"``` and ```"Denom”```

  * ```“delegator_address”``` is no longer a string. It’s a field called ```“delegation”``` with three values: ```"delegator_address", "shares", "validator_address"```

  * The old field ```“validator_address”``` is no longer used. A new field ```“validator_dst_address”``` and```“validator_src_address”``` replace this in the new ```“redelegation”``` field.



** **Sample JSON:**
```JSON
      {
          "balance": {
              "amount": "5",
              "denom": "stake"
          },
          "delegation": {
              "delegator_address": "cosmos1n2k9ygw2ws9sg86mrx84pdcre5geqd5ugt44h0",
              "shares": "5.000000000000000000",
              "validator_address": "cosmosvaloper155998a4hv5kqvuxr9jryjxrtnlydvqu8c0cy03"
          }
      }
```
<br/><br/>

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

* **Sample JSON:**
```JSON
{
    "entries": [
        {
            "balance": "5",
            "redelegation_entry": {
                "completion_time": "1969-12-31T16:00:00-08:00",
                "initial_balance": "5",
                "shares_dst": "5.000000000000000000"
            }
        },
        {
            "balance": "5",
            "redelegation_entry": {
                "completion_time": "1969-12-31T16:00:00-08:00",
                "initial_balance": "5",
                "shares_dst": "5.000000000000000000"
            }
        }
    ],
    "redelegation": {
        "delegator_address": "cosmos104yggz5x4ype50c59vu84ze2w36pc3swm2u698",
        "entries": null,
        "validator_dst_address": "cosmosvaloper1td8yl7g5662m0mpptaxjmcn9jtzvl0wgulvv23",
        "validator_src_address": "cosmosvaloper1gqv70e79a8q0yz5s5qhsjhdl2c79496faer0vz"
    }
}
```
<br/><br/>

* **Endpoint Name:** QueryUnbondingDelegation
* **Endpoint Path:**
```"/staking/unbondingDelegation"```
* **What Changed:**
  * The old field ```“creation_height"``` is no longer supported.

* **Sample JSON:**<br/><br/>

#### Distributions
* **Endpoint Name:** getQueriedValidatorOutstandingRewards
* **Endpoint Path:**
```"/distribution/validators/{validatorAddr}/outstanding_rewards"```
* **What Changed:**
  * The new field ```“rewards"``` is the new root level field for the output


* **Sample JSON:**
```JSON
{
  "rewards": [
    {
      "denom": "mytoken",
      "amount": "3.000000000000000000"
    },
    {
      "denom": "myothertoken",
      "amount": "0.000000300000000000"
    }
  ]
}
```
<br/><br/>

* **Endpoint Name:** getQueriedValidatorCommission
* **Endpoint Path:**
```"/distribution/validators/{validatorAddr}"```
* **What Changed:**
  * The new field ```“commission"``` is the new root level field for the output


* **Sample JSON:**
```JSON
  "commission": [
    {
      "denom": "token1",
      "amount": "4.000000000000000000"
    },
    {
      "denom": "token2",
      "amount": "2.000000000000000000"
    }
  ]
}
```
<br/><br/>

* **Endpoint Name:** getQueriedValidatorSlashes
* **Endpoint Path:**
```"/distribution/validators/{validatorAddr}"```
* **What Changed:**
  * No change
  <br/><br/>

* **Endpoint Name:** getQueriedDelegationRewards
* **Endpoint Path:**
```"/distribution/delegators/{delegatorAddr}/rewards"```
* **What Changed:**
  * No change

<br/><br/>
