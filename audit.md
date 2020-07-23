# AminoREST and You
## How-To deal with Cosmos legacy interface in the Stargate

### Summary

The Cosmos Stargate Upgrade will provide 3 interfaces for sending and retrieving transactions.

1. Legacy AMINO JSON REST API
2. GRPC Clients
3. GRPC Gateway JSON REST.

The Legacy Amino interface provides an interface most similar to cosmoshub-2 and prior versions of the Cosmos SDK. This interface is available for both querying and sending transactions. It is implemented by executing Amino JSON serialization refliection over the new set of protobuf compatible structs.

The core finding of this audit is that while changes to the underlying structs result in an interface that is close to the prior version.

We would also like to emphasize the intent to deprecate the Amino interfaces in the the near future(~1 year). New features are unlikely to have Amino REST interfaces for them. We strongly reccomend working on a migration.


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

We intend to audit the Transaction Encoding/Broadcaste interface shortly but we are waiting on [this issues](https://github.com/cosmos/cosmos-sdk/issues/6213) for a full audit.

### Audit Results
#### Validators
* **Endpoint Name:** QueryValidators
* **Endpoint Path:**
```"/staking/validators"```
* **What Changed:** 
  * The field ```"unbonding_height"``` and ```"jailed"``` are no longer supported
* Sample JSON:

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
          
* **Endpoint Name:** QueryDelegatorDelegations
* **Endpoint Path:** ```"/staking/delegators/delegations"```
* ****What Changed:****
  * ```“balance”``` now is no longer a number. It is a field with two values: ```"amount"``` and ```"Denom”```

  * ```“delegator_address”``` is no longer a string. It’s a field called ```“delegation”``` with three values: ```"delegator_address", "shares", "validator_address"```

  * The old field ```“validator_address”``` is no longer used. A new field ```“validator_dst_address”``` and```“validator_src_address”``` replace this in the new ```“redelegation”``` field.



* Sample JSON from master: 

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

* Sample JSON<br/><br/>


* **Endpoint Name:** QueryUnbondingDelegation
* **Endpoint Path:**
```"/staking/unbondingDelegation"```
* **What Changed:**
  * The old field ```“creation_height"``` is no longer supported.

* Sample JSON<br/><br/>