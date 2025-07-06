# realCrypto Token 🪙

A basic ERC-20 token implementation built as part of a smart contract development course.

## 🔍 Overview

This project demonstrates how to deploy a minimal ERC-20 token using OpenZeppelin’s standard library. The contract is written in Solidity and mints a fixed supply of 1,000 tokens (with 18 decimals) to the deployer's wallet.

## 🛠️ Technologies Used

- Solidity `^0.8.24`
- OpenZeppelin Contracts (ERC20)
- Remix or Hardhat (recommended for deployment and testing)

## 📄 Smart Contract

```solidity
// SPDX-License-Identifier: LGPL-3.0-only

pragma solidity 0.8.24;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract realCrypto is ERC20 {
    constructor(string memory name_, string memory symbol_) ERC20(name_, symbol_) {
        _mint(msg.sender, 1000 * 1e18);
    }
}
