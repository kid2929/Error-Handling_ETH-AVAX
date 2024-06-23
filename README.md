# TaskManagementSystem Smart Contract

## Overview
The `TaskManagementSystem` is a Solidity-based smart contract designed for managing tasks with rewards on the Ethereum blockchain. This contract allows an owner to create tasks, assign them to users, and reward users upon task completion. It also provides functionalities for users to manage their balances.

## Prerequisites
- Solidity version: ^0.8.26
- Ethereum development environment (e.g., Truffle, Hardhat)
- Ethereum client (e.g., Ganache for local testing)

## Contract Details

### Task Structure
Each task is represented by a struct with the following properties:
- `description` (string): A brief description of the task.
- `assignedTo` (address): The address of the user to whom the task is assigned.
- `reward` (uint256): The reward in wei for completing the task.
- `completed` (bool): A flag indicating whether the task has been completed.

### State Variables
- `owner` (address): The owner of the contract.
- `taskCount` (uint256): The total number of tasks created.
- `tasks` (mapping(uint256 => Task)): A mapping from task ID to Task.
- `balances` (mapping(address => uint256)): A mapping from user address to balance in wei.

### Events
- `TaskCreated(uint256 taskId, string description, uint256 reward)`: Emitted when a new task is created.
- `TaskAssigned(uint256 taskId, address assignee)`: Emitted when a task is assigned to a user.
- `TaskCompleted(uint256 taskId)`: Emitted when a task is completed.
- `BalanceUpdated(address indexed user, uint256 newBalance)`: Emitted when a user's balance is updated.

### Modifiers
- `onlyOwner`: Ensures that the function can only be called by the owner.
- `taskExists`: Ensures that the task with the given ID exists.

### Constructor
The constructor sets the deployer as the owner and initializes their balance to 1000 wei.

### Functions

#### `createTask(string memory description, uint256 reward) public onlyOwner`
Creates a new task with the given description and reward. Only the owner can call this function.

#### `assignTask(uint256 taskId, address assignee) public onlyOwner taskExists(taskId)`
Assigns a task to a user. The assignee must be a valid address, and the task must not be completed. Only the owner can call this function.

#### `completeTask(uint256 taskId) public taskExists(taskId)`
Marks a task as completed. Only the assigned user can complete the task. The user is rewarded with the task's reward amount, and their balance is updated.

#### `deposit(uint256 amount) public`
Deposits the specified amount into the user's balance. The amount must be greater than zero.

#### `withdraw(uint256 amount) public`
Withdraws the specified amount from the user's balance. The user must have a sufficient balance.

#### `transfer(address to, uint256 amount) public`
Transfers the specified amount from the caller's balance to another address. Both the caller and the recipient's balances are updated accordingly.

## Deployment
To deploy the contract:
1. Ensure you have a development environment set up (e.g., Truffle, Hardhat).
2. Compile the contract.
3. Deploy the contract using your preferred method (e.g., Truffle migration script, Hardhat deployment script).

## Example Usage
1. **Create a task:**
    ```solidity
    taskManagementSystem.createTask("Task Description", 100);
    ```
2. **Assign a task:**
    ```solidity
    taskManagementSystem.assignTask(0, userAddress);
    ```
3. **Complete a task:**
    ```solidity
    taskManagementSystem.completeTask(0);
    ```
4. **Deposit balance:**
    ```solidity
    taskManagementSystem.deposit(500);
    ```
5. **Withdraw balance:**
    ```solidity
    taskManagementSystem.withdraw(200);
    ```
6. **Transfer balance:**
    ```solidity
    taskManagementSystem.transfer(anotherUserAddress, 100);
    ```

## License
This project is licensed under the MIT License.
