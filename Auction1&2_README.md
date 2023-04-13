# Solidity
Practice of writing basic smart contracts such as Greeter, Bidder, Auction, Coin, Simple storage

# **Auction Smart Contract**

This is a smart contract written in Solidity programming language for an auction system that allows bidders to bid on items using tokens. The contract has three items and four bidders, each bidder is given five tokens to bid. The contract owner is the beneficiary who can reveal the winners after the auction is over.

## **Installation**

1. Install **[Node.js](https://nodejs.org/en/)**
2. Install **[Truffle](https://www.trufflesuite.com/docs/truffle/getting-started/installation)**
3. Install **[Ganache](https://www.trufflesuite.com/ganache)** (a local blockchain for Ethereum development)

## **Running the Tests**

1. Open the terminal/command prompt.
2. Navigate to the project directory.
3. Run **`ganache-cli`**.
4. In a separate terminal, navigate to the project directory.
5. Run **`truffle test`**.

## **Contract Details**

### **Data**

### Items

**`Item`** is a structure to hold details of an item. Each item has an **`itemId`** and an array of **`itemTokens`** that represent tokens bid in favor of the item.

### Bidders

**`Person`** is a structure to hold the details of a bidder. Each bidder has **`remainingTokens`** that represent the number of tokens remaining with the bidder, a **`personId`** that serves as a **`tokenId`**, and an **`address`** of the bidder.

The **`bidders`** array contains four **`Person`** objects.

### Mappings

**`tokenDetails`** is a mapping that maps an **`address`** to a **`Person`**.

### **Functions**

### Constructor

The constructor initializes the **`beneficiary`** with the address of the smart contract's owner and initializes the **`items`** array with three items, one with an **`itemId`** of 0 and two with **`itemIds`** of 1 and 2.

### **`register()`** Function

The **`register()`** function allows a bidder to register for the auction. Each bidder is given five tokens to bid. The function initializes the **`address`** of the bidder and maps it to the corresponding **`Person`** object.

### **`bid()`** Function

The **`bid()`** function allows a bidder to bid tokens on an item. The function takes in two arguments, **`_itemId`** and **`_count`**, representing the **`itemId`** of the item and the number of tokens the bidder wants to bid, respectively.

The function first checks three conditions before proceeding with the bid. If the number of tokens remaining with the bidder is less than the count of tokens bidded, the function reverts. If there are no tokens remaining with the bidder, the function reverts. If the **`itemId`** is greater than 2 or less than 0, the function reverts.

If all the conditions are met, the function decrements the **`remainingTokens`** of the bidder by the number of tokens bid, stores the new value in a variable **`balance`**, updates the **`remainingTokens`** of the bidder and the corresponding **`Person`** object in the **`bidders`** array. Finally, it adds the **`personId`** of the bidder to the **`itemTokens`** array of the corresponding **`Item`** object in the **`items`** array.

### **`onlyOwner`** Modifier

The **`onlyOwner`** modifier is used to ensure that only the owner of the smart contract can perform certain operations. It requires that the **`msg.sender`** is equal to the **`beneficiary`**.

### **`revealWinners()`** Function

The **`revealWinners()`** function reveals the winners of the auction. It iterates over all the items present in the auction and if at least one person has placed a bid, it randomly selects the winner. The function then assigns the winner to the corresponding index of the `winners
