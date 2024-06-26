# ETH-PROOF

# MyToken Contract

Overview

This Solidity contract implements a simple token system with minting and burning functionalities. The contract stores the details of the token, manages balances of addresses, and allows minting and burning of tokens.

Requirements

1. Public Variables:
   - Token Name
   - Token Abbreviation
   - Total Supply

2. Mapping:
   - A mapping of addresses to their respective balances.

3. Mint Function:
   - Takes an address and a value.
   - Increases the total supply by the specified value.
   - Increases the balance of the specified address by the same value.

4. Burn Function:
   - Takes an address and a value.
   - Decreases the total supply by the specified value.
   - Decreases the balance of the specified address by the same value.
   - Ensures that the balance of the specified address is greater than or equal to the value to be burned.

Contract Details

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.7;

contract MyToken {

    // Public variables to store token details
    string public tokenName;
    string public tokenAbbrv;
    uint public totalSupply; 

    // Mapping to store balances of addresses
    mapping (address => uint) public balances;

    // Mint function to create new tokens
    function mintFunc(address address_, uint value) public {
        totalSupply += value;
        balances[address_] += value;
    }

    // Burn function to destroy tokens
    function burnFunc(address address_, uint value) public {
        if (balances[address_] >= value) {
            totalSupply -= value;
            balances[address_] -= value;
        }        
    }
}
```

Deploying the Contract

1. Compile the contract using a Solidity compiler (e.g., Remix, Truffle).
2. Deploy the contract to an Ethereum network.

Interacting with the Contract

- Minting Tokens: Call the `mintFunc` with the address and the amount of tokens to mint.
  ```solidity
  mintFunc(0xYourAddress, 100);
  ```

- Burning Tokens: Call the `burnFunc` with the address and the amount of tokens to burn.
  ```solidity
  burnFunc(0xYourAddress, 50);
  ```



