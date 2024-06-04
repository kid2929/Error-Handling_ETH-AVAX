# Error Handling Example

## Description
This Solidity smart contract demonstrates the use of `require()`, `assert()`, and `revert()` statements for error handling and invariant checking. It allows users to deposit and withdraw Ether from the contract and change the owner.

## Usage
1. Deploy the contract.
2. Call the `deposit()` function to deposit Ether into the contract.
3. Call the `withdraw(uint amount)` function to withdraw Ether from the contract. Only the owner can withdraw Ether, and there must be sufficient balance.
4. Call the `changeOwner(address newOwner)` function to change the owner of the contract. Only the current owner can perform this action.
5. Call the `checkInvariant()` function to check the invariant of the contract (balance is non-negative).

## License
This project is licensed under the terms of the MIT license.

## Author
[Vardaan Gill]

