# Ethereum Todo List DApp

A decentralized application (DApp) for managing a todo list on the Ethereum blockchain. This project demonstrates how to build a full-stack blockchain application using Solidity smart contracts, Truffle framework, and Web3.js.

## Features

- ✅ Create new tasks on the blockchain
- ✅ Toggle task completion status
- ✅ Persistent storage on Ethereum
- ✅ MetaMask integration for transaction signing
- ✅ Real-time updates from blockchain

## Technology Stack

- **Smart Contracts**: Solidity (v0.5.1)
- **Blockchain Development**: Truffle Framework
- **Frontend**: HTML, CSS, JavaScript, Bootstrap 4
- **Web3 Integration**: Web3.js v1.7.0
- **Local Blockchain**: Ganache
- **Dev Server**: Lite-server

## Prerequisites

Before running this application, make sure you have the following installed:

1. **Node.js and npm** (v12 or higher)

   - Download from: https://nodejs.org/

2. **Ganache** (for local blockchain simulation)

   - Download Ganache GUI from: https://trufflesuite.com/ganache/
   - OR install Ganache CLI: `npm install -g ganache-cli`

3. **MetaMask Browser Extension**

   - Install from: https://metamask.io/
   - Available for Chrome, Firefox, Brave, and Edge

4. **Truffle Framework** (optional, already in devDependencies)
   - Can install globally: `npm install -g truffle`

## Installation

1. **Clone the repository** (if not already done):

   ```bash
   git clone <repository-url>
   cd eth-todo-list
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

## Setup and Running the Application

### Step 1: Start Ganache

**Option A: Using Ganache GUI**

1. Open Ganache application
2. Click "New Workspace" or "Quickstart"
3. Ensure the RPC Server is running on `HTTP://127.0.0.1:7545`
4. Note the port number (default: 7545)

**Option B: Using Ganache CLI**

```bash
ganache-cli -p 7545
```

### Step 2: Compile Smart Contracts

Compile the Solidity smart contracts:

```bash
npx truffle compile
```

This will create the contract artifacts in the `build/contracts/` directory.

### Step 3: Deploy Smart Contracts to Ganache

Deploy the contracts to your local blockchain:

```bash
npx truffle migrate --reset
```

You should see output showing the deployment of:

- `Migrations.sol`
- `TodoList.sol`

**Important**: Note the contract address of `TodoList` - this confirms successful deployment.

### Step 4: Configure MetaMask

1. **Open MetaMask** in your browser
2. **Add Ganache Network**:

   - Click on the network dropdown (top of MetaMask)
   - Select "Add Network" → "Add a network manually"
   - Enter the following details:
     - **Network Name**: Ganache Local
     - **RPC URL**: `http://127.0.0.1:7545`
     - **Chain ID**: `1337` (or `5777` depending on your Ganache version)
     - **Currency Symbol**: ETH
   - Click "Save"

3. **Import Ganache Account**:
   - In Ganache, copy the private key of the first account
   - In MetaMask, click the account icon → "Import Account"
   - Paste the private key and click "Import"
   - You should see ~100 ETH balance

### Step 5: Start the Development Server

Run the lite-server to serve the frontend:

```bash
npm run dev
```

This will:

- Start the local web server
- Automatically open your browser at `http://localhost:3000`
- Serve files from the `src/` directory
- Make contract ABIs available from `build/contracts/`

### Step 6: Interact with the DApp

1. **Connect MetaMask**:

   - When the page loads, MetaMask will prompt you to connect
   - Click "Connect" to authorize the application
   - Ensure you're on the Ganache network and using the imported account

2. **View Existing Tasks**:

   - You should see the default task: "ENIAC Devs rule the world!"
   - Your connected account address appears in the top navigation

3. **Create New Tasks**:

   - Type a task in the input field
   - Press Enter or click outside the field
   - MetaMask will prompt you to confirm the transaction
   - Click "Confirm" to submit the transaction
   - Wait for the transaction to be mined (~1-2 seconds)
   - The page will reload and display your new task

4. **Toggle Task Completion**:
   - Click the checkbox next to any task
   - Confirm the transaction in MetaMask
   - The page will reload
   - Completed tasks appear at the bottom with strikethrough styling

## Project Structure

```
eth-todo-list/
├── contracts/              # Solidity smart contracts
│   ├── Migrations.sol     # Truffle migrations contract
│   └── TodoList.sol       # Main todo list contract
├── migrations/            # Deployment scripts
│   ├── 1_initial_migration.js
│   └── 2_deploy_contracts.js
├── src/                   # Frontend files
│   ├── app.js            # Web3 integration logic
│   └── index.html        # Main HTML page
├── test/                  # Smart contract tests
│   └── TodoList.js
├── build/                 # Compiled contract artifacts (generated)
├── bs-config.json        # Lite-server configuration
├── truffle-config.js     # Truffle configuration
└── package.json          # Node dependencies
```

## Smart Contract Overview

### TodoList.sol

**State Variables**:

- `taskCount`: Total number of tasks created
- `tasks`: Mapping of task IDs to Task structs

**Struct**:

```solidity
struct Task {
    uint id;
    string content;
    bool completed;
}
```

**Functions**:

- `createTask(string _content)`: Creates a new task
- `toggleCompleted(uint _id)`: Toggles task completion status

**Events**:

- `TaskCreated`: Emitted when a new task is created
- `TaskCompleted`: Emitted when a task is toggled

## Testing

Run the smart contract tests:

```bash
npx truffle test
```

This will execute tests in the `test/` directory against a clean blockchain instance.

## Troubleshooting

### MetaMask not connecting

- Ensure you're on the correct network (Ganache Local)
- Refresh the page and try reconnecting
- Check that Ganache is running on port 7545

### Transaction fails

- Ensure you have sufficient ETH in your account
- Check that the contract is deployed (run `truffle migrate --reset`)
- Verify the contract address in the browser console

### Page not loading

- Check that lite-server is running (`npm run dev`)
- Ensure port 3000 is not blocked by firewall
- Try clearing browser cache and reloading

### "Nonce too high" error

- Reset your MetaMask account: Settings → Advanced → Reset Account
- This clears the transaction history

### Contract changes not reflecting

- Recompile: `npx truffle compile`
- Redeploy: `npx truffle migrate --reset`
- Hard refresh browser: Ctrl+Shift+R (Windows/Linux) or Cmd+Shift+R (Mac)

## Development Tips

1. **Watch Ganache Logs**: Monitor transaction activity in the Ganache GUI
2. **Check Console**: Open browser DevTools to see Web3 connection status
3. **Reset State**: Use `truffle migrate --reset` to redeploy with fresh state
4. **Account Balance**: Each transaction costs gas - watch your account balance

## Gas Costs

Approximate gas costs for operations:

- Creating a task: ~100,000 gas
- Toggling completion: ~50,000 gas

Note: These are local blockchain costs. Mainnet would be significantly higher.

## Future Enhancements

- Edit task content
- Delete tasks
- Task priority levels
- Due dates
- Multi-user task assignment
- IPFS integration for larger task data

## License

ISC

## Author

geziel.natal@gmail.com

## Resources

- [Truffle Documentation](https://trufflesuite.com/docs/truffle/)
- [Solidity Documentation](https://docs.soliditylang.org/)
- [Web3.js Documentation](https://web3js.readthedocs.io/)
- [MetaMask Documentation](https://docs.metamask.io/)
- [Ganache Documentation](https://trufflesuite.com/docs/ganache/)
