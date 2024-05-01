# CrytpoZombies - Team ABCD

## Team Members

1. Ashil Shah
2. Tejaskumar Pareshbhai Patel - 885174433 - tejas.p@csu.fullerton.edu
3. Rudra Mankad
4. Zhiyuan Yang


## Improvements Made

1. Deploy to other testnet - Sepolia
2. Build a nicer website.
3. Add images to demo zombies in a better way.
4. Change the starter code to NOT hard-coded.


## 1. Deploy to Other Testnet - sepolia 
# Installation and Configuration (Public Testnet Sepolia)
- Download the starter code and unzip in local directory.
1. Setup Infura IO
2. Setup MetaMask Wallet in browser
3. Edit truffle-config.js
4. Setup npm local server

[//]: # ()
[//]: # (## Ganache Setup)

[//]: # ()
[//]: # (1. Install Ganache for windows)

[//]: # (   &#40;https://archive.trufflesuite.com/ganache/&#41;)

[//]: # (2. Setup ethereum workspace.)

[//]: # (3. Note Port No. and Network Id.)

## Setup Infura IO

1. Signup / Login https://app.infura.io/login
2. Activate the Key for Sepolia Blockchain Network
   1. Go to "My First Key > add Etherium Sepolia support"
   2. Save Changes
   3. Copy the whole URL 
      ex: ```https://sepolia.infura.io/v3/XXXXXXXXXXXXXXXXXXXXXXXX```
3. Save this URL for further configs in truffle-configs.js.



[//]: # (## MetaMask Browser Wallet Setup - For Ganache)

[//]: # ()
[//]: # (1. Install MetaMask Chrome Extension)

[//]: # (   &#40;https://metamask.io/&#41;)

[//]: # (2. Create account / login with pass phrase)

[//]: # (3. Select the connected account for current network.)

[//]: # (3. Add Ganache Network)

[//]: # (   1. Go to Settings > Network > Add a Network)

[//]: # (   2. Go to "Add Network")

[//]: # (   3. Set:)

[//]: # (      1. Network Name: Ganache)

[//]: # (      2. RPC URL: Noted URL from 1 of Ganache)

[//]: # (      3. CHain ID: Network ID from 1 of Ganache)

[//]: # (      4. Currency Symbol: ETH)

[//]: # (   4. Save )

## MetaMask Browser Wallet Setup - For Sepolia

1. Install MetaMask Chrome Extension
   (https://metamask.io/)
2. Create account / login with pass phrase
3. Select the connected account for current network.
3. Select Sepolia Network
4. Save

[//]: # (## Edit truffle-config.js - For Ganache)

[//]: # ()
[//]: # (1. Configure to work with Ganache local blockchain network)

[//]: # (   1. Configure network settings: &#40;As of Ganache&#41;)

[//]: # (      ```)

[//]: # (      development: )

[//]: # (      {)

[//]: # (      host: "127.0.0.1",      //Localhost &#40;default: none&#41; )

[//]: # (      port: 7545,            // Standard Ethereum port &#40;default: none&#41; )

[//]: # (      network_id: "1337",       // Any network &#40;default: none&#41;)

[//]: # (      }```)

[//]: # (      )
## Edit truffle-config.js for Seplia Support

1. Configure to interface with Sepolia Public Testnet blockchain network
   1. Configure network settings: (As of Sepolia)
      ``` 
      sepolia: {
      provider: () => new HDWalletProvider({
        mnemonic: {
          phrase: "<METAMASK HD WALLET PASS PHRASE>"
        },
        providerOrUrl: "<COPIED URL FROM INFURA SETUP>",
        // derivationPath: "m/44'/1'/0'/0/"
      }),
      network_id: 11155111, // Sepolia's network ID
      gas: 4000000, // Adjust the gas limit as per your requirements
      gasPrice: 10000000000, // Set the gas price to an appropriate value
      confirmations: 2, // Set the number of confirmations needed for a transaction
      timeoutBlocks: 5000, // Set the timeout for transactions
      skipDryRun: true // Skip the dry run option
    }```


## Setup local npm http server

1. Install npm  http server

   ```npm install http-server```

2. Add npm start script to package.json

   ```"start": "http-server -c-1 -p 8080"```


# Compile and Run

1. Smart Contracts Compile and Deploy
2. Run Frontend

## Contract Compile and Deploy

1. From root directory, compile and deploy contracts to blockchain network

   ```truffle compile```
   
2. Deploy:
   ```truffle migrate  --reset --network sepolia```

   - Copy the ```contract address```, for the deployed contract



## Frontend Configuration and run

1. Add the copied ```contract address```, under ```startApp()```.
2. Run ```npm start```


## 2. Build a nicer website

## 3. Add Images to demo zombies in a better way

## 4. Change the starter code to NOT hard-coded

1. Added support for external ```secrets.json``` file to import apikeys and wallet passphrase
2. Modified ```truffle-config.js``` tto import keys from ```secrets.json```

```
const fs = require('fs');
let rawData = fs.readFileSync("secrets_file.json");
let secrets = JSON.parse(rawData);
const passHhrase = secrets["passphrase"];
const apiKey = secrets["apikey"];

...
...
...
 provider: () => new HDWalletProvider({
        mnemonic: {
          phrase: passHhrase,
        },
        providerOrUrl: apiKey,
        // derivationPath: "m/44'/1'/0'/0/"
      }),
```
