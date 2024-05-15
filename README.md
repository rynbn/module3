# MyToken 

MyToken is an ERC20 token contract that allows for the creation, transfer, and management of tokens. It is built on the [OpenZeppelin](https://www.openzeppelin.com/) library and follows the ERC20 standard.

## Features

- Creation of tokens with a specified name and symbol.
- Token transfers between addresses.
- Ability to burn tokens, reducing the total supply.
- Minting of tokens by the contract owner.
- Approval and delegation of token transfers.

## USAGE

###  Deployment 

To deploy the contract, follow these steps:

1. Deploy the Contract
- Open Remix IDE (remix.ethereum.org).
- Paste the smart contract code into a new Solidity file.
- Compile the contract using the Solidity compiler.
- Deploy the contract.

2. Initial Token Minting
- Once deployed, the contract automatically mints 1 token to the deployer’s address.

3. Mint Additional Tokens
- Use the mintTokens function to mint additional tokens.
- Specify the recipient address and the amount.

4. Burn Tokens
- Use the burnTokens function.
- Specify the amount of tokens you want to burn from your own balance.

5. Transfer Tokens
- Use the transferTokens function.
- Specify the recipient address and the amount of tokens to transfer.

## Token Functionalities 

### Transfers 
Tokens can be transferred from one address to another using the `transfer` function. Before a transfer is executed, the contract checks if the sender has sufficient balance to cover the transfer amount. If not, an error is raised.
```solidity
function transferTokens(address to, uint256 amount) public {
    require(to != address(0), "Invalid address");
    require(balanceOf(msg.sender) >= amount, "Not enough tokens to transfer");
    _transfer(msg.sender, to, amount);
}
```

### Burning Tokens 
The contract allows for the burning of tokens, reducing the total supply. The `burn` function enables an address to burn a specified amount of their tokens. The sender's balance is reduced, and the total supply is updated accordingly.
```solidity
function burnTokens(uint256 amount) public {
    require(balanceOf(msg.sender) >= amount, "Not enough tokens to burn");
    _burn(msg.sender, amount);
}
```

### Minting Tokens 

The contract owner can mint new tokens by using the `mint` function. This function increases the balance of the specified address and updates the total supply.
```solidity
function mintTokens(address to, uint256 amount) public onlyOwner {
    _mint(to, amount);
}
```

##  Events 

The contract emits the following events:

- `Transfer`: Triggered when tokens are transferred between addresses.
- `Burn`: Triggered when tokens are erased by a user.
- `Mint`: Triggered when tokens are minted by the owner.

**Authors**

- Ryan Lester Aban
- email: 422004489@ntc.edu.ph

**License**
This project is licensed under the Ryan Lester Aban License
