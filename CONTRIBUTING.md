# Contributing to StealthBridge

Thank you for building confidential payments infrastructure on Stellar. We welcome thoughtful pull requests, reproducible security research, UX improvements, protocol reviews and documentation.

> **Testnet research only.** No real funds, private keys, account recovery phrases, private payment witnesses, real KYC records or live provider credentials in issues, pull requests, screenshots or test fixtures.

## Find a task

We have **10 initial scoped contributor issues** across the four repositories:

- [Frontend](https://github.com/stealthbridge-labs/stealthbridge-frontend/issues) — Next.js/TypeScript, wallet UX, design accessibility, corridor discovery.
- [Backend](https://github.com/stealthbridge-labs/stealthbridge-backend/issues) — Rust/Axum, settlement idempotency, RPC observation, organization authentication.
- [Contracts](https://github.com/stealthbridge-labs/stealthbridge-contracts/issues) — Soroban authorization/TTL and privacy feasibility research.
- [SDK](https://github.com/stealthbridge-labs/stealthbridge-sdk/issues) — client generation and wallet-owned privacy adapters.

Review issue scope and acceptance criteria and comment with your approach before major work. Comments do not imply formal assignment.

## Contribution workflow

1. Read the [organization overview](profile/README.md), target repository README and [protocol RFC](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/RFC-0001-PLATFORM-ARCHITECTURE.md).
2. Review the [threat model](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/THREAT-MODEL-v0.2.md), official [Stellar documentation](https://developers.stellar.org/docs) and exact SDK/protocol versions.
3. Create a branch in your fork, implement a bounded change and add appropriate tests.
4. Open a PR linking its issue, summarizing tradeoffs, including evidence and documenting limitations.
5. Apply maintainer review feedback; do not interpret passing CI as permission to deploy or move funds.

## Validation expectations

| Area | Baseline |
| --- | --- |
| Frontend | `npm run typecheck`, `npm run build`, accessibility, responsive and reduced-motion review |
| Backend | `cargo fmt --all -- --check`, `cargo test`, Clippy, tenant boundaries and concurrency tests |
| Contracts | `cargo test --workspace`, WASM build, auth/TTL/replay tests where applicable |
| SDK | `npm run typecheck`, `npm run build`, OpenAPI compatibility and no-secret guarantees |

Check repository instructions for exact versions and CI rules.

## Security and product integrity

- **Never invent runtime corridor data, rates, partners, balances, transactions, successful payouts or deployed contract IDs.** Synthetic inputs are acceptable only as labeled, isolated test fixtures.
- Distinguish *designed*, *implemented*, *verified on testnet*, *deployed* and *audited*. Document actual transactions when claiming on-chain behavior.
- Blockchain finality and fiat payout completion are separate events.
- Confidential spend keys, note secrets, recovery credentials and proof witnesses must not be sent to ordinary backend APIs.
- Changes to signing, custody, issuer roles, ZK verifier inputs or fund release need an approved threat-model review.
- Reusing prior-art smart contracts or skills requires license/security due diligence and attribution.
- Do not deploy contracts, provision accounts, connect external financial providers or use signing credentials without explicit maintainer authorization.

PRs should include screenshots for UI changes, tests, compatibility notes and a concise security/privacy impact assessment.

## Licensing and community

The code is developed publicly; licensing and security policies will be finalized through the organization's normal governance process.

Follow the [Code of Conduct](CODE_OF_CONDUCT.md). Send exploit reports privately via [SECURITY.md](SECURITY.md).
