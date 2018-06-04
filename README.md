<img src="https://github.com/0xcert/ethereum-erc20/raw/master/cover.png" />

![Build Status](https://travis-ci.org/0xcert/ethereum-erc20.svg?branch=master)&nbsp;[![NPM Version](https://badge.fury.io/js/@0xcert%2Fethereum-erc20.svg)](https://badge.fury.io/js/0xcert%2Fethereum-erc20)&nbsp;[![Dependencies Status](https://david-dm.org/0xcert/ethereum-erc20.svg)](https://david-dm.org/0xcert/ethereum-erc20)&nbsp;[![Bug Bounty](https://img.shields.io/badge/bounty-pending-2930e8.svg)](https://github.com/0xcert/ethereum-erc20/issues)

# ERC-20 Token

This is a complete implementation of the [ERC-20](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md) fungible token standard for the Ethereum blockchain. This is an open source project build with [Truffle](http://truffleframework.com) framework.

Purpose of this implementation is to provide a good starting point for anyone who wants to use and develop fungible tokens on the Ethereum blockchain. Instead of re-implementing the ERC-20 yourself you can use this code which has gone through multiple audits and we hope it will be extensively used by the community in the future.

## Structure

Since this is a Truffle project, you will find all tokens in `contracts/tokens/` directory.

## Requirements

* NodeJS 9.0+ recommended.
* Windows, Linux or Mac OS X.

## Installation

### NPM

This is an [NPM](https://www.npmjs.com/package/@0xcert/ethereum-erc20) module for [Truffle](http://truffleframework.com) framework. In order to use it as a dependency in your Javascript project, you must install it through the `npm` command:

```
$ npm install @0xcert/ethereum-erc20
```

### Source

Clone the repository and install the required `npm` dependencies:

```
$ git clone git@github.com:0xcert/ethereum-erc20.git
$ cd ethereum-erc20
$ npm install
```

Make sure that everything has been set up correctly:

```
$ npm run test
```

## Usage

### NPM

To interact with package's contracts within JavaScript code, you simply need to require that package's .json files:

```js
const contract = require("@0xcert/ethereum-erc20/build/contracts/FToken.json");
console.log(contract);
```

### Source

#### Creating smart contract

The easiest way to start is to create a new file under `contracts/tokens/` (e.g. `MyNFToken.sol`):

```sol
pragma solidity ^0.4.24;

import "../tokens/FToken.sol";

contract MyFToken is FToken {

  constructor(
    string _name,
    string _symbol
  )
    public
  {
    nftName = _name;
    nftSymbol = _symbol;
  }

  function mint(
    address _owner,
    uint256 _id
  )
    onlyOwner
    external
  {
    super._mint(_owner, _id);
  }

  function burn(
    address _owner,
    uint256 _tokenId
  )
    onlyOwner
    external
  {
    super._burn(_owner, _tokenId);
  }

}
```

That's it. Let's compile the contract:

```
$ npm run compile
```

The easiest way to deploy it locally and start interacting with the contract (minting and transferring tokens) is to deploy it on your personal (local) blockchain using [Ganache](http://truffleframework.com/ganache/). Follow the steps in the Truffle documentation which are described [here](http://truffleframework.com/docs/getting_started/project#alternative-migrating-with-ganache).

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to help out.

## Licence

See [LICENSE](./LICENSE) for details.
