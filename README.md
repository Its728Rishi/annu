# AnnuToken Solidity Smart Contract
Overview

The AnnuToken contract is an ERC20 token built using the OpenZeppelin library, with additional functionality for redeeming items using tokens. It allows the contract owner to mint and transfer tokens, and users can burn tokens or redeem them for predefined items. The contract also keeps track of redeemed items for each user.

Features

Minting: The contract owner can mint new tokens to any address.

Burning: Any user can burn their own tokens, reducing the total supply.

Transferring: The owner can transfer tokens to any address.

Item Redemption: Users can redeem tokens for specific items. These items have a set cost, and once an item is redeemed, the tokens are burned.

Redeemed Items Tracking: The contract tracks which items a user has redeemed and prevents multiple redemptions of the same item.

# Functions

1. mintAnnuToken(address to, uint256 amount)
   
Description: Allows the owner to mint new tokens to the specified address.

Parameters:

to: The address to receive the minted tokens.

amount: The number of tokens to be minted.

Access: Only the contract owner can execute this function.

3. burnAnnuToken(uint256 amount)
   
Description: Allows any user to burn their own tokens.

Parameters:

amount: The number of tokens to be burned.

Access: Executable by any user.

5. transferAnnuTokens(address to, uint256 amount)
   
Description: Allows the owner to transfer tokens to a specific address.

Parameters:

to: The address receiving the tokens.

amount: The number of tokens to transfer.

Access: Only the contract owner can execute this function.

7. redeemAnnuItem(uint256 itemId)
   
Description: Allows users to redeem tokens for a specific item. The cost of the item is deducted by burning tokens.

Parameters:

itemId: The ID of the item being redeemed.

Conditions:

The item must exist.

The user must have sufficient token balance.

The item cannot be redeemed more than once by the same user.

9. getAnnuRedeemedItems(address user)
    
Description: Returns a list of boolean values indicating whether each item has been redeemed by the specified user.

Parameters:

user: The address of the user whose redeemed items are being queried.

Returns: A list of boolean values corresponding to whether each item has been redeemed or not.

Data Structures

Item Struct

Defines the structure of redeemable items:

name: A string representing the item's name.

cost: A uint256 value representing the token cost to redeem the item.

annuRedeemableItems Array

Holds the list of redeemable items.

# annuItemRedeemed Mapping

A mapping that tracks whether a user has redeemed a specific item. The key is an address, and the value is a mapping of item IDs to booleans.

# Redeemable Items

The contract starts with four pre-initialized items:

Item 1: Cost = 100 Annu
Item 2: Cost = 200 Annu
Item 3: Cost = 300 Annu
Item 4: Cost = 400 Annu

These items are initialized in the initializeAnnuRedeemableItems function and can be redeemed by calling the redeemAnnuItem function.

# Libraries Used

The contract makes use of the OpenZeppelin libraries for security and standard functionality:

ERC20: Implements the ERC20 standard for token creation.

Ownable: Provides ownership control, limiting certain functions to the contract owner.

# Deployment
To deploy the contract:

Compile the contract in Remix IDE.

Deploy the contract to an Ethereum-compatible network using Remix or other deployment tools like Truffle or Hardhat.

Example Usage

## Minting Tokens

```solidity
mintAnnuToken(0x1234..., 1000);
```

## Burning Tokens
```solidity
burnAnnuToken(500);
```

## Redeeming an Item
```solidity
redeemAnnuItem(0); // Redeems "Annu Item 1" for 100 tokens
```

##License

This project is licensed under the MIT License.
