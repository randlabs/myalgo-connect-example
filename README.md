# Wallet My Algo

* [Overview](#Overview)
* [How does it work?](#How-does-it-work?)
* [Installation](#Installation)
* [API Usage](#API-Usage)
  * [Connect to My Algo](#Connect-to-My-Algo)
  * [Sign Transaction](#Sign-Transaction)
* [Contributing](#Contributing)
* [Copyright and License](#Copyright-and-License)

### Overview

Wallet My Algo is a Javascript library developed by Rand Labs to securely sign transactions with [My Algo](https://wallet.myalgo.com)

### How does it work?

### Installation  

The library can be installed via npm:
```sh
npm install wallet-myalgo-js
```

### API Usage  

#### Connect to My Algo  

```js

import { MyAlgoWallet } from 'wallet-myalgo-js';


const myAlgoWallet = new MyAlgoWallet();
// const myAlgoWallet = new MyAlgoWallet('https://dev.myalgo.com/bridge');

const connectToMyAlgo = async() => {
  try {
    const accounts = await myAlgoWallet.connect();

    const addresses = accounts.map(account => account.address);
    
  } catch (err) {
    console.error(err);
  }
}
```

#### Sign Transaction


```js

import algosdk from 'algosdk';

const algodClient = new algosdk.Algodv2(algodToken, algodServer, algodPort);


(async () => {
  try {

    const from = addresses[0]; // Select address
    const to: '...';
    const amount = 1000000; // microalgos
  
    let txn = await algodClient.getTransactionParams().do();
      
    txn = {
    ...txn,
    fee: 1000,
    flatFee: true,
    type: 'pay',
    from,
    to,
    amount
    };
  
    let signedTxn = (await myAlgoWallet.signTransaction(txn));
    console.log(signedTxn.txID);
  
    await algodClient.sendRawTransaction(signedTxn.blob).do();

  
  }catch(err) {
    console.error(err); 
  }
})();

```


### Contributing  


### Copyright and License  

