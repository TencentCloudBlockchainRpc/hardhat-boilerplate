# Hardhat Boilerplate

This repository contains a sample project that you can use as the starting point
for your Ethereum project. It's also a great fit for learning the basics of
smart contract development.

This project is intended to be used with the
[Hardhat Beginners Tutorial](https://hardhat.org/tutorial), but you should be
able to follow it by yourself by reading the README and exploring its
`contracts`, `tests`, `scripts` and `frontend` directories.

## Quick start

The first things you need to do are cloning this repository and installing its
dependencies:

```sh
git clone https://github.com/TencentCloudBlockchainRpc/hardhat-boilerplate.git
cd hardhat-boilerplate
git checkout trpc_dev
npm install
```

Once installed, let's run Hardhat's testing network:

```sh
npx hardhat node
```

Then, on a new terminal, go to the repository's root folder and run this to
deploy your contract:

```sh
npx hardhat run scripts/deploy.js --network localhost
```

Finally, we can run the frontend with:

```sh
cd frontend
npm install
npm start
```

Open [http://localhost:3000/](http://localhost:3000/) to see your Dapp. You will
need to have [Coinbase Wallet](https://www.coinbase.com/wallet) or [Metamask](https://metamask.io) installed and listening to
`localhost 8545`.

## Deploy to Public Chain with T-RPC
After completing development and local debugging. You can deploy the project
to public chain with [Tencent Cloud Blockchain RPC](https://www.tencentcloud.com/products/rpc?from_qcintl=122150301).

### Prerequisites
* [Register a Tencent Cloud account](https://www.tencentcloud.com/account/register)
* [Sign in Blockchain RPC console](https://console.tencentcloud.com/bcrpc/terminal)
* Create New Application
* Get the API Key/URL of the Testnet

### Set up your network config
* Identify the network you want to deploy which you can find in [ChainList](https://chainlist.org/)
* Get the RPC-URL of the network from the [terminal](https://console.tencentcloud.com/bcrpc/terminal)
* Fill the network configuration params and accounts in the **`hardhat.config.js`** 
* Fill the EtherScan api-key if you want to verify & publish your contract

The following is a sample configuration based on Polygon-Mumbai. You need to
replace the following params based on your situation: `{API_KEY}`, `{ACCOUNT_PRIVATE_KEY}` 
and `{ETHERSCAN_API_KEY}`


```js
module.exports = {
  solidity: {
    version: "0.8.17",
    settings: {
      optimizer: {
        enabled: true,
        runs: 200
      }
    }
  },
  networks:{
    mumbai:{
      url: `https://www.tencentcloud-rpc.com/v1/polygon_mumbai/{API_KEY}`,
      accounts: [`{ACCOUNT_PRIVATE_KEY}`],
      chainId: 80001
    },
  },
  etherscan: {
      apiKey: {
          mumbai: "{ETHERSCAN_API_KEY}"
      },
      customChains: [
         {
              network: "mumbai",
              chainId: 80001,
              urls: {
                  apiURL: "https://api-testnet.polygonscan.com/api",
                  browserURL: "https://mumbai.polygonscan.com/"
              }
          },
      ]
  },
  
};

```
### Deploy to public network
Then, on a new terminal, go to the repository's root folder and run this to
deploy your contract:

```sh
npx hardhat run scripts/deploy.js --network mumbai
```

You will receive the contract address as output.
Suppose the console display an address : ```0xB6b558EF8CAb7d0037a6539074dabfaC36Ffd6ea```
The contract address needs to be configured in ```frontend/src/contracts/contract-address.json```
```json
{
  "Token": "0x66f397997185Ee210107140254F2DBe00EFe2b35"
}
```
Finally, we can run the frontend with:

```sh
cd frontend
npm start
```

If you want to verify & publish your contract,
open a new terminal, go to the repository's root folder and run 
the following command:
```sh
npx hardhat verify --network mumbai 0x66f397997185Ee210107140254F2DBe00EFe2b35
```

**Happy _building_!**
