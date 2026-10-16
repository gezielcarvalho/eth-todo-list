# Learning charter

## Objective

Practice the local development loop for a simple Ethereum DApp: Solidity contract authoring, migration, contract tests, local-chain deployment, Web3 interaction, and browser wallet authorization.

## Scope represented today

- Create and toggle tasks in a simple on-chain mapping.
- Emit task events and read contract state.
- Deploy with Truffle migrations to a local development network.
- Render and transact through a static browser UI and local wallet connection.
- Run focused contract tests through Truffle.

## Not in scope

- Mainnet/testnet deployment, production wallet support, token/value transfers, or real user accounts.
- Contract audits, access control, upgradeability, pausing, incident response, key management, or gas optimization guarantees.
- Hosted frontend, CI/CD, monitoring, terms/privacy, support, or data-retention policy.

## Ownership and decision gate

This is a personal learning archive. It must remain clearly framed as a local tutorial. Any plan to deploy or reuse a contract requires a separately approved security and product charter.

## Criteria for a future DApp effort

1. Choose a supported development toolchain and document exact versions/network targets.
2. Define user, wallet, transaction, error, and privacy expectations.
3. Complete security review, automated testing, and third-party audit appropriate to risk.
4. Add CI, reproducible deployment procedures, monitoring, and rollback/incident controls.
5. Obtain explicit owner approval before any public network or wallet-connected release.
