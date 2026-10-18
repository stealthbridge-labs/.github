# StealthBridge — Organization hub

This is the special GitHub organization repository for **[StealthBridge](https://github.com/stealthbridge-labs)**.

> **GitHub renders [`profile/README.md`](profile/README.md) as our public organization homepage.**
> That is the product introduction. This root README is the maintainers' directory for organization-wide policies and architecture—not a second marketing profile.

## What belongs here

| Source of truth | Purpose |
| --- | --- |
| [`profile/README.md`](profile/README.md) | Public product mission, problems addressed, audiences, repo map, and ways to contribute |
| [`assets/`](assets/) · [brand guide](docs/BRAND.md) | Official landscape logo and symbol; consistent naming and presentation |
| [Platform vision](docs/PLATFORM-VISION-AND-ARCHITECTURE.md) | Product scope, security boundaries, architecture, and future capabilities |
| [Integration topology](docs/INTEGRATION-TOPOLOGY.md) | Frontend ↔ backend ↔ SDK ↔ deployed Soroban read path; ownership and verification gates |
| [Testnet contract evidence](docs/SOROBAN-TESTNET-DEPLOYMENT-STATUS.md) | Real governance contract IDs, receipts, verification methods, and limitations |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) · [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Shared contribution expectations |
| [`SECURITY.md`](SECURITY.md) · [`SUPPORT.md`](SUPPORT.md) | Vulnerability reporting and assistance |
| [`GOVERNANCE.md`](GOVERNANCE.md) | Organization decision-making |
| [Issue templates](.github/ISSUE_TEMPLATE/) · [PR template](.github/PULL_REQUEST_TEMPLATE.md) | Consistent reviews and work intake |

## Repository ownership

Product code and source-level specifications live in their respective repositories:

- [stealthbridge-frontend](https://github.com/stealthbridge-labs/stealthbridge-frontend) — Next.js experience, wallet UX, server-side bridge.
- [stealthbridge-backend](https://github.com/stealthbridge-labs/stealthbridge-backend) — Rust API, ledger observer, PostgreSQL, OpenAPI specification, runtime verification.
- [stealthbridge-contracts](https://github.com/stealthbridge-labs/stealthbridge-contracts) — Rust Soroban contracts and independently reproduced deployment evidence.
- [stealthbridge-sdk](https://github.com/stealthbridge-labs/stealthbridge-sdk) — Versioned typed consumer package and contract tests.

The organization profile should explain **why** StealthBridge exists; individual repos explain **how** their part works. This hub should link to those documents instead of copying their content.

## Documentation rules

Keep every statement about financial execution grounded in reproducible evidence. Stellar Testnet governance deployments do **not** imply that private transfers, custody, payouts, or fee collection are active. Distinguish code passing CI, successful Vercel builds, live runtime availability, and verified cryptographic/privacy properties. Never publish wallet seeds, private keys, database credentials, or internal provider access.

For cross-repository API changes, update backend OpenAPI, SDK validators and frontend consumers together; verify live integration at the actual deployment boundary. For contract changes, retain pinned WASM, release receipts and administrator-transition evidence. Changes to the public organization profile should be concise, comprehensible and appropriate for prospective businesses, users and contributors.
