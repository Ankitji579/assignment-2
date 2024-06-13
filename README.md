# MyToken Smart Contract

The MyToken smart contract is a simple implementation of a cryptocurrency token on the Ethereum blockchain. This contract allows for basic operations such as minting new tokens and burning existing tokens. The contract keeps track of the total supply and balances of each token holder.


## Description

Token Name: SpaceX
Token Abbreviation: SX
Total Supply: Publicly viewable and dynamically updated with minting and burning operations.
Minting: Create new tokens and assign them to an address.
Burning: Destroy tokens from an address.


## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // Public variables
    string public myTokenName = "SpaceX";
    string public myTokenAbb = "SX";
    uint public myTotal = 0;

    // Mapping of addresses to balances
    mapping(address => uint) public totalBalances;

    // Mint function
    function mint(address _address, uint _value) public {
        myTotal = myTotal + _value;
        totalBalances[_address] = totalBalances[_address] + _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        if (totalBalances[_address] > _value) {
            myTotal = myTotal - _value;
            totalBalances[_address] = totalBalances[_address] - _value;
        }
    }
}


```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the Mint and Burn functions. Call the mint function with the address to receive the tokens and the amount of tokens to be created.Call the burn function with the address from which the tokens will be burned and the amount of tokens to be destroyed.

## Authors

This smart contract was created by Ankit Vashisth.

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
