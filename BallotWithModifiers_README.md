# Solidity
Practice of writing basic smart contracts such as Greeter, Bidder, Auction, Coin, Simple storage

**Ballot Smart Contract**
This is a smart contract implemented using the Solidity programming language. The purpose of this contract is to create a ballot with multiple proposals and allow registered voters to cast their votes for their preferred proposal. The winning proposal is determined based on the number of votes it receives.

**Requirements**
Solidity compiler version: ^0.5.9

**Contract Overview**
This contract defines a Ballot structure with the following attributes:

**Voter**: a struct representing a voter, which includes their weight, whether they have voted, and the proposal they voted for.

**Proposal**: a struct representing a proposal, which includes the number of votes it has received.

**Stage**: an enum representing the current stage of the ballot, which can be Init, Reg, Vote, or Done.

**Chairperson**: the address of the chairperson who creates the ballot.

**Voters**: a mapping of addresses to Voter structs.

**Proposals**: an array of Proposal structs.

**Event**: a votingCompleted event, triggered when the voting period ends.

**The contract includes three functions:**

**Constructor**: initializes the ballot with a given number of proposals, sets the chairperson as the sender, and sets the stage to the registration stage.

**Register**: allows the chairperson to register a voter to participate in the ballot, granting them a weight of 1. The registration function can only be called during the registration stage, and the voter must not have already voted.

**Vote**: allows registered voters to cast their vote for a specific proposal. Voters can only vote once and the function can only be called during the voting stage. The vote count for the selected proposal is increased by the weight of the voter. If the voting period ends, the stage is updated to Done and the votingCompleted event is emitted.

**WinningProposal**: returns the proposal with the highest number of votes. This function can only be called after the voting stage has ended.

**Usage**

To use this contract, follow these steps:

**1)**Compile the contract using the Solidity compiler version ^0.5.9.

**2)**Deploy the contract to the Ethereum network.

**3)**Call the constructor function with the number of proposals you want to include in the ballot.

**4)**Use the register function to add voters to the ballot during the registration stage.

**5)**Once all voters are registered, start the voting stage.

**6)**Use the vote function to allow registered voters to cast their vote for a specific proposal.

**7)**Once the voting period ends, use the winningProposal function to determine the winning proposal.


**Note**
|This contract is intended for educational purposes only and is not production-ready. Please use at your own risk.|
