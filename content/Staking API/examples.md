# Examples

Let's explore a few examples of staking using the Staking API.

## Interact Directly With Ethereum Smart Contract

In this example, we will demonstrate how to gather deposit data, which can then be utilized for direct interaction with Ethereum smart contracts.

1. [Get an authentication token]() and pass it in the following format:

   ```curl
   authorization: Bearer <token>
   ```

2. Send a POST request to `/api/v1/eth/staking/direct/nodes-request/create` with the following parameters:

   ```curl
   curl --request POST \
        --url https://api.p2p.org/api/v1/eth/staking/direct/nodes-request/create \
        --header 'accept: application/json' \
        --header 'authorization: Bearer <token>' \
        --header 'content-type: application/json' \
        --data '
   {
     "id": "3611b95c-e1b3-40c0-9086-3de0a4379943",
     "validatorsCount": 2,
     "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
     "nodesOptions": [
       {
         "location": "any"
       }
     ]
   }
   '
   ```

   Response:

   ```json
   {
     "error": null,
     "result": true
   }
   ```

3. Send a GET request to `/api/v1/eth/staking/direct/nodes-request/status/{id}` with the following parameters:

   ```curl
   curl --request GET \
        --url https://example.com/api/v1/eth/staking/direct/nodes-request/status/3611b95c-e1b3-40c0-9086-3de0a4379943 \
        --header 'accept: application/json' \
        --header 'authorization: Bearer <token>'
   ```

   Response:

   ```json
   {
     "error": null,
     "result": {
       "id": "3611b95c-e1b3-40c0-9086-3de0a4379943",
       "status": "ready",
       "validatorsCount": 2,
       "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
       "depositData": [
         {
           "pubkey": "0xac1e9969d7b87f3102549ab41558136674a7306b85b9f73cfbd7d9fdb7db85724569da3ebd4d7de9689f6ac058d7e2a3",
           "signature": "0xb656f9c771166c82a7891b930e6a920878d9736eb3f9f241753a15ea69d8e2f20a3740dfaf546c70e31bd323e14b341205d04e3227dd4cf2923644a375f6792875ac02c5f256f7a17c96b09bafcbce7e4443e1862356b1e90d78875d78e9a742",
           "depositDataRoot": "0xba013b4950b9aff0c3c19017ec5b6e0ed5b957b36f6ff03a545e5cc5605baff8"
         },
         {
           "pubkey": "0x8afd7a7791098eb045d0031b0df0a612b0d6d5c03d7636368f473657b7d0bc3087d0335ff5ad523b3102d9310c342cf8",
           "signature": "0x8a3ca4cdd09491241966b6cd9e6f96dd13f92de53f51761b50d152f6165113c215ec1b8d170f9f6ebb8c03efd506bde4121263bf361f01ef41664a59d03665b49409c37fa19bcc788d0ca738ff45e37dbb4bbfb2e3f5a8bc743ac424e0a0a0b5",
           "depositDataRoot": "0x7766cd52c96e3f3fb99f6fb4ba1276ad49e864bc7935b3cd30a6b5ee39801ed2"
         }
       ]
     }
   }
   ```

4. To interact with Ethereum deposit smart contract directly:

   1. Construct transaction with the validator deposit data.
   2. Send transaction to [Ethereum deposit smart contract](https://etherscan.io/address/0x00000000219ab540356cBB839Cbe05303d7705Fa).

## Use P2P Smart Contract

In this example, we will demonstrate how to gather deposit data, and use P2P smart contract to deposit validator deposit data.

1. [Get an authentication token]() and pass it in the following format:

   ```curl
   authorization: Bearer <token>
   ```

2. Send a POST request to `/api/v1/eth/staking/direct/nodes-request/create` with the following parameters:

   ```curl
   curl --request POST \
        --url https://api.p2p.org/api/v1/eth/staking/direct/nodes-request/create \
        --header 'accept: application/json' \
        --header 'authorization: Bearer <token>' \
        --header 'content-type: application/json' \
        --data '
   {
     "id": "3611b95c-e1b3-40c0-9086-3de0a4379943",
     "validatorsCount": 2,
     "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
     "nodesOptions": [
       {
         "location": "any"
       }
     ]
   }
   '
   ```

   Response:

   ```json
   {
     "error": null,
     "result": true
   }
   ```

3. Send a GET request to `/api/v1/eth/staking/direct/nodes-request/status/{id}` with the following parameters:

   ```curl
   curl --request GET \
        --url https://example.com/api/v1/eth/staking/direct/nodes-request/status/3611b95c-e1b3-40c0-9086-3de0a4379943 \
        --header 'accept: application/json' \
        --header 'authorization: Bearer <token>'
   ```

   Response:

   ```json
   {
     "error": null,
     "result": {
       "id": "3611b95c-e1b3-40c0-9086-3de0a4379943",
       "status": "ready",
       "validatorsCount": 2,
       "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
       "depositData": [
         {
           "pubkey": "0xac1e9969d7b87f3102549ab41558136674a7306b85b9f73cfbd7d9fdb7db85724569da3ebd4d7de9689f6ac058d7e2a3",
           "signature": "0xb656f9c771166c82a7891b930e6a920878d9736eb3f9f241753a15ea69d8e2f20a3740dfaf546c70e31bd323e14b341205d04e3227dd4cf2923644a375f6792875ac02c5f256f7a17c96b09bafcbce7e4443e1862356b1e90d78875d78e9a742",
           "depositDataRoot": "0xba013b4950b9aff0c3c19017ec5b6e0ed5b957b36f6ff03a545e5cc5605baff8"
         },
         {
           "pubkey": "0x8afd7a7791098eb045d0031b0df0a612b0d6d5c03d7636368f473657b7d0bc3087d0335ff5ad523b3102d9310c342cf8",
           "signature": "0x8a3ca4cdd09491241966b6cd9e6f96dd13f92de53f51761b50d152f6165113c215ec1b8d170f9f6ebb8c03efd506bde4121263bf361f01ef41664a59d03665b49409c37fa19bcc788d0ca738ff45e37dbb4bbfb2e3f5a8bc743ac424e0a0a0b5",
           "depositDataRoot": "0x7766cd52c96e3f3fb99f6fb4ba1276ad49e864bc7935b3cd30a6b5ee39801ed2"
         }
       ]
     }
   }
   ```

4. Send a POST request to `/api/v1/eth/staking/direct/tx/deposit` with the following parameters:

   ```curl
   curl --request POST \
        --url https://api.p2p.org/api/v1/eth/staking/direct/nodes-request/create \
        --header 'accept: application/json' \
        --header 'authorization: Bearer <token>' \
        --header 'content-type: application/json' \
        --data '
   {
     "withdrawalAddress": "0x9B52b9033ecbb6635f1c31A646d5691B282878aA",
     "depositData": [
       {
         "pubkey": "0xac1e9969d7b87f3102549ab41558136674a7306b85b9f73cfbd7d9fdb7db85724569da3ebd4d7de9689f6ac058d7e2a3",
         "signature": "0xb656f9c771166c82a7891b930e6a920878d9736eb3f9f241753a15ea69d8e2f20a3740dfaf546c70e31bd323e14b341205d04e3227dd4cf2923644a375f6792875ac02c5f256f7a17c96b09bafcbce7e4443e1862356b1e90d78875d78e9a742",
         "depositDataRoot": "0xba013b4950b9aff0c3c19017ec5b6e0ed5b957b36f6ff03a545e5cc5605baff8"
       },
       {
         "pubkey": "0x8afd7a7791098eb045d0031b0df0a612b0d6d5c03d7636368f473657b7d0bc3087d0335ff5ad523b3102d9310c342cf8",
         "signature": "0x8a3ca4cdd09491241966b6cd9e6f96dd13f92de53f51761b50d152f6165113c215ec1b8d170f9f6ebb8c03efd506bde4121263bf361f01ef41664a59d03665b49409c37fa19bcc788d0ca738ff45e37dbb4bbfb2e3f5a8bc743ac424e0a0a0b5",
         "depositDataRoot": "0x7766cd52c96e3f3fb99f6fb4ba1276ad49e864bc7935b3cd30a6b5ee39801ed2"
       }
     ]
   }
   '
   ```

   Response:

   ```json
   {
      "error": null,
      "result": {
         "transaction": "0x02f9047705808304a46685021b1dd4b683030d4094681a1b3441c6bfb12f91651efd9f02c83c0702938903782dace9d9000000b904444f498c73000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000001a0000000000000000000000000000000000000000000000000000000000000028000000000000000000000000000000000000000000000000000000000000003e00000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000000000000000000000000000000000a00000000000000000000000000000000000000000000000000000000000000030ac1e9969d7b87f3102549ab41558136674a7306b85b9f73cfbd7d9fdb7db85724569da3ebd4d7de9689f6ac058d7e2a30000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000308afd7a7791098eb045d0031b0df0a612b0d6d5c03d7636368f473657b7d0bc3087d0335ff5ad523b3102d9310c342cf80000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000200100000000000000000000009b52b9033ecbb6635f1c31a646d5691b282878aa00000000000000000000000000000000000000000000000000000000000000200100000000000000000000009b52b9033ecbb6635f1c31a646d5691b282878aa0000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000000000000000000000000000000000c00000000000000000000000000000000000000000000000000000000000000060b656f9c771166c82a7891b930e6a920878d9736eb3f9f241753a15ea69d8e2f20a3740dfaf546c70e31bd323e14b341205d04e3227dd4cf2923644a375f6792875ac02c5f256f7a17c96b09bafcbce7e4443e1862356b1e90d78875d78e9a74200000000000000000000000000000000000000000000000000000000000000608a3ca4cdd09491241966b6cd9e6f96dd13f92de53f51761b50d152f6165113c215ec1b8d170f9f6ebb8c03efd506bde4121263bf361f01ef41664a59d03665b49409c37fa19bcc788d0ca738ff45e37dbb4bbfb2e3f5a8bc743ac424e0a0a0b50000000000000000000000000000000000000000000000000000000000000002ba013b4950b9aff0c3c19017ec5b6e0ed5b957b36f6ff03a545e5cc5605baff87766cd52c96e3f3fb99f6fb4ba1276ad49e864bc7935b3cd30a6b5ee39801ed2c0"
      }
   }
   ```

5. Sign and broadcast transaction:

   ```javascript
   require("dotenv").config();
   const ethers = require("ethers");
   
   async function signAndBroadcast() {
     console.log("Started");
   
     // Enter the serialized transaction
     const rawTransaction = process.env.RAW_TRANSACTION;
   
     // Enter the private key of the address used to transfer the stake amount
     const privateKey = process.env.PRIVATE_KEY;
   
     // Enter the selected RPC URL
     const rpcURL = process.env.RPC_URL;
   
     // Initialize the provider using the RPC URL
     const provider = new ethers.providers.JsonRpcProvider(rpcURL);
   
     // Initialize a new Wallet instance
     const wallet = new ethers.Wallet(privateKey, provider);
   
     // Parse the raw transaction
     const tx = ethers.utils.parseTransaction(rawTransaction);
   
     tx.nonce = await provider.getTransactionCount(wallet.address);
   
     // Enter the max fee per gas and prirorty fee
     tx.maxFeePerGas = ethers.utils.parseUnits(
       process.env.MAX_FEE_PER_GAS_IN_GWEI,
       "gwei"
     );
     tx.maxPriorityFeePerGas = ethers.utils.parseUnits(
       process.env.MAX_PRIORITY_FEE_IN_GWEI,
       "gwei"
     );
   
     // Sign the transaction
     const signedTransaction = await wallet.signTransaction(tx);
   
     // Send the signed transaction
     const transactionResponse = await provider.sendTransaction(signedTransaction);
   
     return transactionResponse;
   }
   
   signAndBroadcast()
     .then((transactionResponse) => {
       console.log(
         "Transaction broadcasted, transaction hash:",
         transactionResponse.hash
       );
     })
     .catch((error) => {
       console.error("Error:", error);
     })
     .finally(() => {
       console.log("Finished");
     });
   
   ```

## What's Next?

- [Getting Started](/p2p/staking-api/start/).
- Refer to [Staking API](/p2p/api/staking-api.html) reference.
