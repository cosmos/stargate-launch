# AminoREST and You

## How-To deal with Cosmos legacy interface in the Stargate

### Summary

The Cosmos Stargate Upgrade will provide 3 interfaces for sending and retrieving transactions.

1. Legacy AMINO JSON REST API
2. GRPC Clients
3. GRPC Gateway JSON REST.

The Legacy Amino interface provides an interface most similar to cosmoshub-3 and prior versions of the Cosmos SDK. This interface is available for both querying and sending transactions. It is implemented by executing Amino JSON serialization reflection over the new set of protobuf compatible structs.

The core finding of this audit is that while changes to the underlying structs result in an interface that is close to the prior version.

We would also like to emphasize the intent to deprecate the Amino interfaces in the the near future(~1 year). New features are unlikely to have Amino REST interfaces for them. We strongly recommend working on a migration.

### The Cosmos SDK Versions audited

[Cosmos SDK master](https://github.com/cosmos/cosmos-sdk)

[Cosmos SDK tag v0.37.13](https://github.com/cosmos/cosmos-sdk/tree/v0.37.13)

### Here are the High Priority Endpoints for Queries

* Staking
  * Validators
  * Delegators
* Bank
  * Balances
* Gov
* Auth
* Distributions

We intend to audit the Transaction Encoding/Broadcast interface shortly but we are waiting on [this issues](https://github.com/cosmos/cosmos-sdk/issues/6213) for a full audit.

### Audit Results

#### Bank

* **Endpoint Name:** QueryBalance
* **Endpoint Path:**
```"/bank/balances/{address}"```
* **What Changed:**
  * No Changes observed.
  * See [coin cross-chain transfer source tracing](https://github.com/cosmos/cosmos-sdk/pull/6662) for details on how on non-native IBC coins will written into the denom value. This will include a hash of source trace for each coin. The core decision if the hash should replace the denom or be prepended to the denom.

#### Validators

* **Endpoint Name:** QueryValidators
* **Endpoint Path:**
```"/staking/validators"```
* **What Changed:**
  * The fields ```"unbonding_height"``` and ```"jailed"``` are no longer supported
  * The fields in description are now omit if empty. Rather than returning fields with empty strings. We now don't return the field if the validator has chosen not to configure it. For instance at launch, no validator will have a security contact filled out and the field will only appear once they do.
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

****Sample JSON:**

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
  * ```“redelegation”``` which holds the sub-fields.
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

## Transaction constructions

Stargate offers two modes of constructing transactions.

1. Legacy Amino transactions that can be broadcast using http `POST` to `:1317/txs` endpoint as in previous Cosmos releases.
2. Protobuf transactions that operate using the  `26657/broadcast` endpoint on Tendermint RPC and use the new SIGN_MODE_DIRECT signing system.

Under the hood JSON Legacy Amino transactions are re-encoded as protobuf txs and encoded back to json during signature verification. If you have an existing integration with the Cosmos Hub or other Cosmos-SDK chains, you should expect that your signed and broadcast infrastructure will work without changes.

If you are building a new integration, you should consider if SIGN_MODE_DIRECT and direct protobuf encoding is a better fit for your use case.


## Querying Transactions

The `/txs/[hash]` endpoint will continue to be available but there are substantial changes to the JSON that cannot be hidden behind the legacy amino facade that other endpoints use.

A cosmoshub-3 response looks like this:
``` json

{
  "height": "3544383",
  "txhash": "BF68CD8E17F6F86996DAF6A667A5E04489A515CA5C1A06D4BD13E8D179A08DF5",
  "raw_log": "[{\"msg_index\":0,\"success\":true,\"log\":\"\",\"events\":[{\"type\":\"message\",\"attributes\":[{\"key\":\"sender\",\"value\":\"cosmos14kh20jtm3vpsxhh34lpg4g36clralearnp89u9\"},{\"key\":\"module\",\"value\":\"bank\"},{\"key\":\"action\",\"value\":\"send\"}]},{\"type\":\"transfer\",\"attributes\":[{\"key\":\"recipient\",\"value\":\"cosmos1hvsdf03tl6w5pnfvfv5g8uphjd4wfw2hsucxnd\"},{\"key\":\"amount\",\"value\":\"1uatom\"}]}]}]",
  "logs": [
    {
      "msg_index": 0,
      "success": true,
      "log": "",
      "events": [
        {
          "type": "message",
          "attributes": [
            {
              "key": "sender",
              "value": "cosmos14kh20jtm3vpsxhh34lpg4g36clralearnp89u9"
            },
            {
              "key": "module",
              "value": "bank"
            },
            {
              "key": "action",
              "value": "send"
            }
          ]
        },
        {
          "type": "transfer",
          "attributes": [
            {
              "key": "recipient",
              "value": "cosmos1hvsdf03tl6w5pnfvfv5g8uphjd4wfw2hsucxnd"
            },
            {
              "key": "amount",
              "value": "1uatom"
            }
          ]
        }
      ]
    }
  ],
  "gas_wanted": "200000",
  "gas_used": "40126",
  "tx": {
    "type": "cosmos-sdk/StdTx",
    "value": {
      "msg": [
        {
          "type": "cosmos-sdk/MsgSend",
          "value": {
            "from_address": "cosmos14kh20jtm3vpsxhh34lpg4g36clralearnp89u9",
            "to_address": "cosmos1hvsdf03tl6w5pnfvfv5g8uphjd4wfw2hsucxnd",
            "amount": [
              {
                "denom": "uatom",
                "amount": "1"
              }
            ]
          }
        }
      ],
      "fee": {
        "amount": [
          {
            "denom": "uatom",
            "amount": "1"
          }
        ],
        "gas": "200000"
      },
      "signatures": [
        {
          "pub_key": {
            "type": "tendermint/PubKeySecp256k1",
            "value": "A5k5Y+HnrqZeDb04fCOKVMw7/egVeAnA8J/WX4Sl2Dbo"
          },
          "signature": "WyIXcAUbVr/ILFHyMoS3p+WmZ34LVaIaye7i1BCZ5kciqyxLY9AjSzh12w6Pjq+zr6xi85meAOOhTKZUT57nkw=="
        }
      ],
      "memo": ""
    }
  },
  "timestamp": "2020-09-30T17:53:20Z",
  "events": [
    {
      "type": "message",
      "attributes": [
        {
          "key": "sender",
          "value": "cosmos14kh20jtm3vpsxhh34lpg4g36clralearnp89u9"
        },
        {
          "key": "module",
          "value": "bank"
        },
        {
          "key": "action",
          "value": "send"
        }
      ]
    },
    {
      "type": "transfer",
      "attributes": [
        {
          "key": "recipient",
          "value": "cosmos1hvsdf03tl6w5pnfvfv5g8uphjd4wfw2hsucxnd"
        },
        {
          "key": "amount",
          "value": "1uatom"
        }
      ]
    }
  ]
}
```

A new Stargate response looks like this:
```json
{
  "height": "111102",
  "txhash": "C29C87ED9FD1AA0DA3BDDB396EFE570FDE99D0EB24F10AAF00D46086A7284FCA",
  "data": "0A060A0473656E64",
  "raw_log": "[{\"events\":[{\"type\":\"message\",\"attributes\":[{\"key\":\"action\",\"value\":\"send\"},{\"key\":\"sender\",\"value\":\"cosmos1h2gacd88hkvlmz5g04md87r54kjf0klnwt25n9\"},{\"key\":\"module\",\"value\":\"bank\"}]},{\"type\":\"transfer\",\"attributes\":[{\"key\":\"recipient\",\"value\":\"cosmos1ne2g0hhejmd6gqy22erty8yt8nknygw026j72c\"},{\"key\":\"sender\",\"value\":\"cosmos1h2gacd88hkvlmz5g04md87r54kjf0klnwt25n9\"},{\"key\":\"amount\",\"value\":\"10000000umuon\"}]}]}]",
  "logs": [
    {
      "events": [
        {
          "type": "message",
          "attributes": [
            {
              "key": "action",
              "value": "send"
            },
            {
              "key": "sender",
              "value": "cosmos1h2gacd88hkvlmz5g04md87r54kjf0klnwt25n9"
            },
            {
              "key": "module",
              "value": "bank"
            }
          ]
        },
        {
          "type": "transfer",
          "attributes": [
            {
              "key": "recipient",
              "value": "cosmos1ne2g0hhejmd6gqy22erty8yt8nknygw026j72c"
            },
            {
              "key": "sender",
              "value": "cosmos1h2gacd88hkvlmz5g04md87r54kjf0klnwt25n9"
            },
            {
              "key": "amount",
              "value": "10000000umuon"
            }
          ]
        }
      ]
    }
  ],
  "gas_wanted": "200000",
  "gas_used": "53677",
  "tx": {
    "body": {
      "messages": [
        {
          "type": "cosmos-sdk/MsgSend",
          "value": {
            "from_address": "cosmos1h2gacd88hkvlmz5g04md87r54kjf0klnwt25n9",
            "to_address": "cosmos1ne2g0hhejmd6gqy22erty8yt8nknygw026j72c",
            "amount": [
              {
                "denom": "umuon",
                "amount": "10000000"
              }
            ]
          }
        }
      ]
    },
    "auth_info": {
      "signer_infos": [
        {
          "public_key": {
            "type": "tendermint/PubKeySecp256k1",
            "value": "AiSN1louJ7slmWEbfZWv1hmpV97PGnkwjGylRsWTFLTR"
          },
          "mode_info": {
            "Sum": {
              "type": "cosmos.tx.v1beta1.ModeInfo_Single",
              "value": {
                "single": {
                  "mode": 1
                }
              }
            }
          },
          "sequence": "13"
        }
      ],
      "fee": {
        "amount": [],
        "gas_limit": "200000"
      }
    },
    "signatures": [
      "9QQF8c0MNlk7mAXDcB1A3Rwih5iRP2leF/mibEX+n5ssj8f6zL/JRWhPOFNOf2f2RNENhX5Ic2nN3ydcG8iz6A=="
    ]
  },
  "timestamp": "2020-09-29T16:40:54Z"
}
```