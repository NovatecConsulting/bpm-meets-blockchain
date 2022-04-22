# Private Blockchain Data

This is a proof of concept repository for discovering the topic "BPM meets Blockchain".

Resources used:

- [Running a Private Ethereum Blockchain using Docker](https://medium.com/scb-digital/running-a-private-ethereum-blockchain-using-docker-589c8e6a4fe8)

- [How to Setup a Local Solidity Development Environment With VSCode, Remix, and Truffle Suite](https://betterprogramming.pub/how-i-set-up-my-local-solidity-development-environment-with-vscode-remix-and-truffle-suite-addd20ef9c)

## Useful commands and results

### Check generated User:

```sh
curl --location --request POST 'localhost:8545' \
      --header 'Content-Type: application/json' \
      --data-raw '{"jsonrpc": "2.0", "id": 3, "method": "eth_accounts", "params": []}'
```

**Result:** `{"jsonrpc":"2.0","id":3,"result":["0x003f5c33d67499ed9098e0957f104caf4e05dc92"]}` _(Address of OG account)_

### Check ETH Balance for User:

```sh
curl --location --request POST 'localhost:8545' \
      --header 'Content-Type: application/json' \
      --data-raw '{"jsonrpc": "2.0", "id": 4, "method": "eth_getBalance", "params": ["0x003f5c33d67499ed9098e0957f104caf4e05dc92", "latest"]}'
```

**Result:** `{"jsonrpc":"2.0","id":4,"result":"0x1a589ad90fc7d80000"}` _(ETH Balance)_

### Create new User:

```sh
curl --location --request POST 'localhost:8545' \
      --header 'Content-Type: application/json' \
      --data-raw '{"jsonrpc": "2.0", "id": 5, "method": "personal_newAccount", "params": ["test5678"]}'
```

**Result:** `{"jsonrpc":"2.0","id":5,"result":"0x10676daa004e2ed07a7345d820735da67c3906d9"}` _(Address of new account)_

### Activate User for Sending & Receiving:

```sh
curl --location --request POST 'localhost:8545' \
      --header 'Content-Type: application/json' \
      --data-raw '{"jsonrpc": "2.0", "id": 6, "method": "personal_unlockAccount", "params": ["0x003f5c33d67499ed9098e0957f104caf4e05dc92", "test1234"]}'
```

**Result:** `{"jsonrpc":"2.0","id":6,"result":true}` _(Boolean if unlocked or not)_
