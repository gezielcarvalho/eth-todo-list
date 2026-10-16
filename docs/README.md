# Current-state documentation

## Purpose

This repository is a learning DApp that records to-do tasks in a Solidity contract and interacts with it through a browser UI, Web3, Truffle artifacts, MetaMask, and a local Ganache-style Ethereum network.

## Current state

- Contract: `TodoList.sol` stores task content/completion state and emits creation/toggle events.
- Chain scope: local development configuration targets a node on `127.0.0.1:7545`.
- Frontend: static HTML/JavaScript, Bootstrap, jQuery, Web3, and Truffle Contract.
- Verification: Truffle tests cover deployment, initial task access, task creation, and completion toggle.
- Tooling: package lockfile, Truffle configuration, migrations, and a Lite Server script are present.
- Packaging issue: the package `test` script is intentionally not a usable test command; direct Truffle invocation is documented separately in the README.

## Decision

Retain as a blockchain fundamentals reference, not a portfolio flagship or public deployment candidate. Smart-contract and wallet-facing work needs a separate security, upgrade, network, and user-protection review before reuse.

See the [learning charter](project-charter.md), [architecture](architecture.md), and [quality handoff](delivery-and-quality.md).
