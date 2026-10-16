# Contract and local-chain boundaries

## Components

| Component | Current responsibility |
| --- | --- |
| `contracts/TodoList.sol` | Stores tasks, increments IDs, toggles completion, and emits events. |
| `migrations/` | Deploys the migration helper and todo contract through Truffle. |
| `test/TodoList.js` | Tests basic deployment and task behaviors against a development chain. |
| `src/app.js` / `src/index.html` | Loads Web3, requests browser-wallet accounts, reads tasks, and sends create/toggle transactions. |
| `truffle-config.js` | Points the development network to a local RPC endpoint. |
| `package.json` | Declares the historical frontend and Truffle tooling dependencies. |

## Local interaction flow

1. A local Ethereum node provides accounts and RPC service.
2. Truffle compiles/migrates the contract and produces its artifacts.
3. The browser UI requests access to a local wallet account.
4. Web3 reads task state and sends signed task mutations through the local provider.
5. The UI reloads after mutations to show current chain state.

## Security and product boundaries

Every stored task is public to the configured chain; the contract has no per-user ownership, authorization, deletion, edit, input-size guard, pause control, or upgrade path. The UI assumes a local RPC address and development wallet workflow. These are tutorial constraints, not a safe public-service design.

Do not import a real private key into a browser wallet solely to run this repository. Use only disposable local-chain accounts and test data.
