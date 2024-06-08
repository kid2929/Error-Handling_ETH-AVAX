# ErrorHandlingExample Solidity Contract

## Overview

The `ErrorHandlingExample` contract demonstrates the use of `require()`, `assert()`, and `revert()` statements for error handling in Solidity. The contract allows the owner to deposit and withdraw ether, and includes functionality to change the contract owner and check the contract balance.

## License

This contract is licensed under the MIT License.

## Prerequisites

- Solidity ^0.8.26
- Ethereum wallet or any Ethereum development environment (e.g., Remix, Truffle, Hardhat)

## Installation

1. **Using Remix:**
   - Open [Remix](https://remix.ethereum.org/).
   - Create a new file and copy the contract code into it.
   - Compile the contract using the Solidity compiler version ^0.8.26.
   - Deploy the contract.

2. **Using Truffle or Hardhat:**
   - Install Truffle or Hardhat.
   - Create a new project and add this contract to your project's contracts directory.
   - Compile and deploy the contract using the respective framework's deployment scripts.

## Contract Details

### State Variables

- `address public owner`: The address of the contract owner.
- `uint public balance`: The balance of ether held by the contract.

### Constructor

- `constructor()`: Initializes the contract, setting the deployer as the owner and the initial balance to 0.

### Functions

1. `deposit() public payable`
   - Allows any user to deposit ether into the contract.
   - Emits a `DepositMade` event.

2. `withdraw(uint amount) public`
   - Allows the owner to withdraw a specified amount of ether from the contract.
   - Reverts if the caller is not the owner, if the contract has insufficient balance, or if the withdrawal amount is zero.
   - Emits a `WithdrawalMade` event.

3. `changeOwner(address newOwner) public`
   - Allows the owner to change the ownership of the contract to a new owner.
   - Reverts if the caller is not the owner or if the new owner address is the zero address.
   - Emits an `OwnerChanged` event.

4. `getBalance() public view returns (uint)`
   - Returns the current balance of the contract.

### Events

- `event DepositMade(address indexed sender, uint amount)`: Emitted when ether is deposited into the contract.
- `event WithdrawalMade(address indexed sender, uint amount)`: Emitted when ether is withdrawn from the contract.
- `event OwnerChanged(address indexed newOwner)`: Emitted when the owner is changed.

## Usage

1. **Depositing Ether:**
   - Call the `deposit` function from any Ethereum wallet or interface to send ether to the contract.

2. **Withdrawing Ether:**
   - The owner can call the `withdraw` function with the desired amount to withdraw ether from the contract.

3. **Changing Owner:**
   - The owner can call the `changeOwner` function with the new owner's address to transfer ownership.

4. **Checking Balance:**
   - Any user can call the `getBalance` function to check the contract's current balance.

## Example

Here's an example of how to interact with the contract using Remix:

1. **Deploying the Contract:**
   - Copy the contract code into a new file in Remix.
   - Compile and deploy the contract.
   - The deployer's address will be set as the owner.

2. **Depositing Ether:**
   - Select the deployed contract and use the `deposit` function.
   - Specify the amount of ether to deposit in the "Value" field and confirm the transaction.

3. **Withdrawing Ether:**
   - Ensure you are connected with the owner's address.
   - Use the `withdraw` function with the amount of ether to withdraw.
   - Confirm the transaction.

4. **Changing Owner:**
   - Use the `changeOwner` function with the new owner's address.
   - Confirm the transaction.

5. **Checking Balance:**
   - Use the `getBalance` function to view the contract's balance.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
