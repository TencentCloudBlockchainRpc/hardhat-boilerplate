require("@nomicfoundation/hardhat-toolbox");

// The next line is part of the sample project, you don't need it in your
// project. It imports a Hardhat task definition, that can be used for
// testing the frontend.
require("./tasks/faucet");

/** @type import('hardhat/config').HardhatUserConfig */
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
    // select the appropriate network. Take polygon_mumbai as an example
    mumbai:{
      // Fill with the uri got from tencent cloud blockchain RPC. https://console.intl.cloud.tencent.com/bcrpc/terminal
      url: `https://www.tencentcloud-rpc.com/v1/polygon_mumbai/{API_KEY}`,
      // Fill with your test private key for deployment, the address corresponding to the key will have 1000000 Tencent Rpc Token(TRT)
      accounts: [`{ACCOUNT_PRIVATE_KEY}`],
      // Fill with the appropriate network id. Common network id mappings can be found at https://chainlist.org/?testnets=true
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
