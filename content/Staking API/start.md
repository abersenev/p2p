# Getting Started

Set up node for staking using P2P infrastructure and check the status of the node.

A request example is provided using [cURL](https://curl.se/).

## Getting access

To start working with the Staking Platform APIs, follow these steps:

1. [Get an authentication token]().
1. Pass the token in the Authorization header in the following format:

   ```curl
   authorization: Bearer <token>
   ```

## 1. Set Up Node

To set up node for staking, send a POST request to `/api/v1/eth/staking/direct/nodes-request/create`. Follow these steps:

1. Prepare`id` that is an arbitrary UUID. Generate it in one of the following ways:

   - [Online UUID Generator](https://www.uuidgenerator.net/)
   - [uuid npm package](https://www.npmjs.com/package/uuid)

1. Pass the request with the following parameters:

```curl
curl --request POST \
     --url https://api.p2p.org/api/v1/eth/staking/direct/nodes-request/create \
     --header 'accept: application/json' \
     --header 'authorization: Bearer <token>' \
     --header 'content-type: application/json' \
     --data '
{
  "id": "3611b95c-e1b3-40c0-9086-3de0a4379943",
  "validatorsCount": 1,
  "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
  "nodesOptions": [
    {
      "location": "any"
    }
  ]
}
'
```

- `id` — arbitrary UUID. You can later use that UUID to check the status of the set-up operation.
- `validatorsCount` — number of validators. One validator is equal to 32 ETH.
- `withdrawalAddress` — withdrawal address for the validators.
- `nodesOptions`:

   - `location` — node location. Currently, only any is supported.

Example response:

```json
{
"error": null,
"result": true
}
```

## 2. Check The Node Status

To check the node status, send a GET request to `/api/v1/eth/staking/direct/nodes-request/status/{id}`:

```curl
curl --request GET \
     --url https://example.com/api/v1/eth/staking/direct/nodes-request/status/3611b95c-e1b3-40c0-9086-3de0a4379943 \
     --header 'accept: application/json' \
     --header 'authorization: Bearer <token>'
```

Example response:

```json
{
  "result": {
    "id": "3611b95c-e1b3-40c0-9086-3de0a4379943",
    "status": "ready",
    "validatorsCount": 1,
    "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
    "depositData": [
      {
        "pubkey": "0xac1e9969d7b87f3102549ab41558136674a7306b85b9f73cfbd7d9fdb7db85724569da3ebd4d7de9689f6ac058d7e2a3",
        "signature": "0xb656f9c771166c82a7891b930e6a920878d9736eb3f9f241753a15ea69d8e2f20a3740dfaf546c70e31bd323e14b341205d04e3227dd4cf2923644a375f6792875ac02c5f256f7a17c96b09bafcbce7e4443e1862356b1e90d78875d78e9a742",
        "depositDataRoot": "0xba013b4950b9aff0c3c19017ec5b6e0ed5b957b36f6ff03a545e5cc5605baff8"
      }
    ]
  },
  "error": {}
}
```

- `pubkey` — validator public key.
- `signature` — validator signature.
- `depositDataRoot` — transaction root hash.


## What's Next?

- Refer to [Staking API](/p2p/api/staking-api.html) reference.
- Explore [Examples](/p2p/staking-api/examples/) to learn how to use the API effectively.
