# Install Node.js

Go to https://nodejs.org/en/, and install the newest version of Node.js

# Install Truffle

Make sure you have Node.js installed properly, and run
```sh
npm install -g truffle
```
If you encounter any permission problem, run the command above with sudo
```sh
sudo npm install -g truffle
```

# Configure network

[Add network configuration](http://truffleframework.com/docs/advanced/configuration) to `truffle.js`:
```js
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 8545,
      network_id: "*" // Match any network id
    }
  }
};
```

# Run Ethereum client and migrate the contract

I will use truffle develop. To run truffle develop, run:
```sh
truffle develop
``` 
After the client is run, you should see a truffle console, in which you can execute [truffle commands](http://truffleframework.com/docs/advanced/commands) or [interact with the contract](http://truffleframework.com/docs/getting_started/contracts) using javascript. But before we can interact with the contract, we will have to migrate the contract to the Ethereum network(here we are using the develop network, which is a private network for testing purpose). To migrate, simply execute:
```sh
migrate
```
Now the contract should be ready.

# Interact with the contract

The following examples are from [here](http://truffleframework.com/docs/getting_started/contracts)
For example, now we want to look up the metacoin balance in this address `0x627306090abab3a6e1400e9345bc60c78a8bef57`, we can run:
```js
var account_one = "0x627306090abab3a6e1400e9345bc60c78a8bef57";
```
to declare a variable, and run:
```
var meta;MetaCoin.deployed().then(function(instance) {var meta = instance;return meta.getBalance.call(account_one, {from: account_one});}).then(function(balance) {console.log(balance.toNumber());}).catch(function(e) {})
```
the balance of this address (by default 10000) will then be printed out.
