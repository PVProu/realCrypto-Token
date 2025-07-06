# RealCrypto Token

## Introduction

**RealCrypto** is a simple ERC20-compliant token built on the Ethereum blockchain using the OpenZeppelin library. Upon deployment, it automatically mints an initial supply of tokens to the deployer's wallet.

## Installation

To set up this project locally:

1. Clone this repository or copy the contract code.
2. Ensure you have a development environment with:
   - Node.js and npm
   - Hardhat or Truffle
3. Install the required dependencies:

```bash
npm install @openzeppelin/contracts
```

## Usage

To deploy the token contract using Hardhat:

```javascript
const RealCrypto = await ethers.getContractFactory("realCrypto");
const token = await RealCrypto.deploy("RealCrypto Token", "RCT");
await token.deployed();

console.log("Token deployed to:", token.address);
```

Upon deployment, `1000 * 10^18` tokens (1000 tokens with 18 decimals) will be minted to the deployer’s address.

## Features

- Fully ERC20 compliant
- Built with OpenZeppelin’s audited contracts
- Mints an initial token supply at deployment
- Token name and symbol are customizable at deployment

## Dependencies

- [Solidity v0.8.24](https://docs.soliditylang.org/en/v0.8.24/)
- [OpenZeppelin Contracts](https://github.com/OpenZeppelin/openzeppelin-contracts) (`@openzeppelin/contracts`)

## Configuration

No special configuration is needed. Provide the token name and symbol when deploying the contract:

```solidity
constructor(string memory name_, string memory symbol_) ERC20(name_, symbol_) {
    _mint(msg.sender, 1000 * 1e18);
}
```

## Documentation

This contract inherits from OpenZeppelin’s ERC20 implementation, which includes:

- `totalSupply()`
- `balanceOf(address)`
- `transfer(address, uint256)`
- `approve(address, uint256)`
- `transferFrom(address, address, uint256)`
- `allowance(address, address)`

Refer to the [OpenZeppelin ERC20 documentation](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20) for more details.

## Examples

Example of checking the balance using Ethers.js:

```javascript
const [owner] = await ethers.getSigners();
const balance = await token.balanceOf(owner.address);
console.log("Owner balance:", ethers.utils.formatEther(balance)); // Should print 1000.0 RCT
```

## Troubleshooting

- **Compiler Errors**: Ensure you're using Solidity 0.8.24 or adjust the pragma line accordingly.
- **Import Errors**: Make sure `@openzeppelin/contracts` is installed via npm.
- **Insufficient Balance**: The initial balance is only minted to the deployer’s address.

## Author

- PVProu

## License

This project is licensed under the **GNU Lesser General Public License v3.0 only (LGPL-3.0-only)**.

For more information, see the [LICENSE](https://www.gnu.org/licenses/lgpl-3.0.html) file or the official GNU page.
