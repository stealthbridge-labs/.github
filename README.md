# StealthBridge · Organization Community Hub

[![StealthBridge](https://raw.githubusercontent.com/stealthbridge-labs/.github/main/assets/stealthbridge-logo.svg)](https://github.com/stealthbridge-labs)

**Confidential payments. Without borders.**

This repository powers the [StealthBridge GitHub organization profile](https://github.com/stealthbridge-labs) and provides shared community guidance.

> The public-facing organization introduction is in [`profile/README.md`](profile/README.md). GitHub displays that file on the organization's Overview page.

## Community files

| File | Purpose |
| --- | --- |
| [Organization profile](profile/README.md) | Mission, products, repos, architecture and contributor issues |
| [Contributing guide](CONTRIBUTING.md) | Getting started and code review practices |
| [Code of conduct](CODE_OF_CONDUCT.md) | Respectful collaboration |
| [Security](SECURITY.md) | Responsible vulnerability reporting |
| [Support](SUPPORT.md) | Development help and bug reports |
| [Governance](GOVERNANCE.md) | Project decision-making and future maintainership |
| [Brand guide](docs/BRAND.md) | Official logo source, tagline and design principles |
| [Issue templates](.github/ISSUE_TEMPLATE/) | Consistent contribution intake |
| [PR template](.github/PULL_REQUEST_TEMPLATE.md) | Code review and verification checklist |

Repository-specific guides and security policies take precedence over organization defaults.

## Platform direction and architecture

StealthBridge is being built as one Testnet-first system, not four unrelated code samples. The organization hub owns the cross-repository explanation, common terminology and public security promises; each implementation repository owns its actual code, roadmap and verification evidence.

**Start here:** [Platform vision, system diagrams and phased delivery](docs/PLATFORM-VISION-AND-ARCHITECTURE.md) · [Integration topology and API ownership](docs/INTEGRATION-TOPOLOGY.md).

| Now | Next | Later, after independent review |
| --- | --- | --- |
| Public website, read-only Testnet preview, Rust API, managed PostgreSQL schema, private TypeScript SDK, three locally tested Soroban contracts | Verified end-to-end staging connectivity, Testnet governance deployment with real IDs, signed wallet challenge and tenant roles | Independently verified privacy rails, reviewed transaction signing, operational settlement providers, reconciliation and eventually assessed Mainnet eligibility |

**Release rule:** a passing CI run, backend build, wallet connection or public governance flag never implies that confidential payments or fiat payouts work. Every capability must be proven at its actual trust boundary.

### Architecture review guide

1. An HTTP change begins in the [backend OpenAPI](https://github.com/stealthbridge-labs/stealthbridge-backend/blob/main/api/openapi.yaml), then updates the SDK and frontend consumer tests.
2. A contract change begins in the [Soroban source](https://github.com/stealthbridge-labs/stealthbridge-contracts), with reproducible WASM, ABI checks, admin/TTL tests and a reviewed Testnet manifest.
3. A wallet feature distinguishes public address lookup, wallet connection, signed identity and explicit transaction approval.
4. A corridor candidate, privacy primitive or future payout provider cannot be advertised as live without independent evidence and appropriate authorizations.

For planning and code review, prefer small milestones with a named owner, prerequisites, failure behavior, security impact, tests and rollback procedure. Never place database URLs, RPC keys, wallet secrets, provider access tokens or private witnesses in documentation.

## Codebases

- [Frontend](https://github.com/stealthbridge-labs/stealthbridge-frontend)
- [Backend](https://github.com/stealthbridge-labs/stealthbridge-backend)
- [Soroban contracts](https://github.com/stealthbridge-labs/stealthbridge-contracts)
- [TypeScript SDK](https://github.com/stealthbridge-labs/stealthbridge-sdk)

**Stellar Testnet research and development.** There is no audited production confidential-payments system, real-money transfer service or live fiat payout operation.

Our development is public, with shared contribution and security guidance. Repository license selection remains a separate governance decision.
