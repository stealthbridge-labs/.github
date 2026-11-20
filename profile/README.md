<div align="center">

<a href="https://stealthbridge.vercel.app/">
  <img src="https://raw.githubusercontent.com/stealthbridge-labs/.github/main/assets/stealthbridge-logo.svg" alt="StealthBridge — Privacy-Preserving Financial Infrastructure on Stellar" width="620" />
</a>

### Open-source privacy-preserving financial infrastructure built on Stellar.

**Connected Personal transfers, Business settlement operations, and Soroban protocol rails — designed for verifiable confidentiality and accountable compliance.**

[Product Preview](https://stealthbridge.vercel.app/) · [Personal Send](https://stealthbridge.vercel.app/send) · [Business](https://stealthbridge.vercel.app/business) · [Privacy & Trust](https://stealthbridge.vercel.app/platform) · [Release Readiness Report](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/MILESTONE-6-RELEASE-READINESS-REPORT.md)

</div>

---

## What StealthBridge Is Building

Cross-border financial systems force individuals and organizations to choose between radical public exposure on transparent blockchains and opaque proprietary intermediaries. **StealthBridge bridges both worlds on Stellar** by separating:

1. **StealthBridge Personal (`/send`, `/app/send`, `/app/instructions`, `/app/settings`)** — Everyday cross-border transfers designed for ordinary users: corridor discovery, Protocol 30 (`G`/`M`/`C`/CAP-84 `W`) recipient book (`account_beneficiaries`), Web Crypto client-encrypted payment instructions (`AES-256-GCM` / `PBKDF2-HMAC-SHA256`), controlled Testnet settlement progression, CSV/JSON audit exports, and non-custodial wallet/smart-account readiness checks.
2. **StealthBridge Business (`/business`, `/app/business`, `/app/business/[id]`, `/app/business/payments`, `/app/business/batch`)** — Financial operations infrastructure for teams: organization onboarding workflows, role-based membership & invitations, beneficiary management, client-side CSV batch corridor validation (up to 50 rows / 8 corridors), unsigned SHA-256 approval envelope hashing, reconciliation exports, and developer API readiness.
3. **Open Developer & Soroban Ecosystem** — Typed TypeScript ESM SDK (`@stealthbridge/sdk`), Rust/Axum/SQLx backend orchestration, deterministic WASM builds, and reproducible Stellar Testnet contract tooling.

---

## Why Stellar & How the Architecture Works

Stellar combines deterministic 5-second finality, native Classic/SAC asset representation, **Protocol 30 CAP-84 `W...` muxed contract accounts**, Soroban smart-contract extensibility, Smart Account Kit (`secp256r1` passkeys + policy limits), and Protocol 25+ cryptographic host primitives (BN254 pairing / Poseidon2) without reinventing base-layer settlement.

### End-to-End Protocol & Application Architecture

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ 1. CUSTOMER & BUSINESS LAYER (stealthbridge-frontend · Next.js / React)   │
│    • Freighter / SEP-53 signed challenge sessions + Device Passkey checks  │
│    • Personal (/app/send) · Business (/app/business, /batch) · /platform   │
│    • Strictly BFF-backed account data (zero localStorage for account state)│
└─────────────────────────────────┬──────────────────────────────────────────┘
                                  │ HTTPS Same-Origin BFF (/api/account/*)
                                  │ CSRF Origin + Signed Session + HMAC-SHA256
┌─────────────────────────────────▼──────────────────────────────────────────┐
│ 2. ORCHESTRATION & LEDGER SERVICE (stealthbridge-backend · Rust / Axum)   │
│    • Strict Protocol 30 StrKey (G/M/C/W) & asset amount validation         │
│    • PostgreSQL / SQLx persistence (17 additive migrations + outbox/events)│
│    • Single-use nonce replay guards · Controlled Testnet lifecycle states  │
│    • Bounded Stellar Testnet Horizon/RPC observer & privacy rail registry  │
└──────────────┬─────────────────────────────────────────┬───────────────────┘
               │ Strict Wire Contracts & Validators      │ Testnet RPC Reads
┌──────────────▼──────────────────┐     ┌────────────────▼───────────────────┐
│ 3. DEVELOPER TOOLKIT            │     │ 4. SOROBAN & CRYPTOGRAPHY LAYER    │
│    (stealthbridge-sdk · TS ESM) │     │    (stealthbridge-contracts · Rust)│
│    • OpenAPI v0.3 wire codegen  │     │    • Deployed Testnet Governance:  │
│    • Client Web Crypto vault    │     │      Corridor/Policy/GovernanceGate│
│    • Canonical SHA-256 intents  │     │    • Protocol Workspace (WASM):    │
│    • Exact i128 asset math      │     │      SettlementAdapter, FeeVault,  │
│    • Isolated consumer builds   │     │      PrivacyRail PoCs, SmartKit audit│
└─────────────────────────────────┘     └────────────────────────────────────┘
```

Read the full traceability matrix in [`CROSS-REPO-INTEGRATION-MAP.md`](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/CROSS-REPO-INTEGRATION-MAP.md).

---

## Repositories

| Repository | Purpose | Tech Stack | CI Verification |
| --- | --- | --- | --- |
| **[stealthbridge-frontend](https://github.com/stealthbridge-labs/stealthbridge-frontend)** | Public site, Personal & Business product UX, same-origin authenticated BFF proxy | Next.js 16, React, TypeScript, Playwright | Typecheck, ESLint, 107 unit tests, 75 landing + 96 preview Playwright tests |
| **[stealthbridge-backend](https://github.com/stealthbridge-labs/stealthbridge-backend)** | Rust orchestration API, SQLx PostgreSQL persistence, Stellar RPC & Horizon observer | Rust, Axum, SQLx, PostgreSQL 16 | Clippy `-D warnings`, 142+ unit/Postgres integration tests, OpenAPI & SQLx parity |
| **[stealthbridge-contracts](https://github.com/stealthbridge-labs/stealthbridge-contracts)** | Soroban contracts, ZK privacy PoCs, Smart Account preflight, deployment verification | Rust (`wasm32v1-none`), Soroban SDK 27.0.6, Stellar CLI 27.1.0 | Workspace tests, source-boundary Rust audits, 90 Python artifact/privacy checks |
| **[stealthbridge-sdk](https://github.com/stealthbridge-labs/stealthbridge-sdk)** | Dependency-free TypeScript ESM client, strict runtime decoders, Web Crypto vault | TypeScript ESM, Web Crypto, esbuild | Deterministic OpenAPI codegen check, 300 tests across Node & Next.js consumers |

---

## Privacy & Smart-Account Architecture

StealthBridge maintains strict technical honesty between cryptographic primitives and marketing claims:

- **Personal Privacy (`private-payments` evaluation):** Targets shielded commitment trees + nullifier sets (*Stellar Private Payments*). Protects counterparty linkage within a shielded pool, while edge deposits/withdrawals, ASP checks, and fee-payer addresses remain observable unless explicitly blinded.
- **Business Confidentiality (`confidential-token` evaluation):** Targets Pedersen / TwElGamal / Sigma amount confidentiality (*OpenZeppelin Stellar Contracts*) paired with authorized auditor viewing keys and regulated issuer controls. Counterparty graph topology remains distinct from encrypted amounts.
- **Encrypted Draft Vaults ≠ On-Chain Privacy:** Client-side AES-256-GCM vault records protect browser/database drafts at rest; on-chain confidentiality requires verified ZK verifiers and approved confidential assets (`productionReady: false` until verified).
- **Smart Accounts:** Built around pinned upstream Smart Account Kit artifacts (`account`, `webauthn`, `threshold`, `spendingLimit` policies) verified read-only via RPC TTL monitoring (`GET /v1/wallet/smart-account-kit`), moving toward live Testnet WebAuthn (`secp256r1`) deployment and time-locked multi-device recovery.

---

## Verified Current Status vs. Unverified Boundaries

### Working & Verified on Stellar Testnet
- **Public Governance Contracts (deployed Oct 17, 2026):** `CorridorRegistry` (`CDS6HBE6YJSZTRG3VR2HLCNHWJZMKB43BLFFEHEH3Z76WXAF46LW7JOB`), `PolicyRegistry` (`CBXWEA5PMDTBN5AN7FJYGGAPIWLRKXYHWLVWG5WOXH3HSRDB4RYTJBN5`), `GovernanceGate` (`CD2KIMDRYJMKGO5SMIBOQP6ADPW5I4THNZFGXWYLIPGSXAI5NRXVAPKV`) with byte-for-byte WASM verification.
- **Protocol 30 (`CAP-84`) Compatibility:** Strict StrKey validation & parsing for `G...`, `M...`, `C...`, and `W...` across backend, SDK, and frontend.
- **Connected Full-Stack Services:** Authenticated Freighter session login, Neon/PostgreSQL account profiles, saved beneficiaries (`account_beneficiaries`), AES-256-GCM encrypted instructions (`customer_payment_instructions`), pending business onboarding & team invitations, batch CSV route validation, and controlled Testnet settlement lifecycle verified up to live Testnet transaction finality (`tx`: `f7bc8714748f7cd4a466e50d5784abc6d870269b0f8d18822eecf402e2d27cfb`, ledger `5818583`).

### Explicitly Disabled / Blocked Before Mainnet
- **Real-money execution & Mainnet (`mainnet_enabled: false`, `payment_execution_enabled: false`)**
- **Live FX conversion & liquidity quotes (`live_fx_enabled: false` — pauses at `quote_unavailable`)**
- **Fiat banking / payout partners (`fiat_payouts_enabled: false`)**
- **Production ZK verifier deployments, customer smart-account custody/recovery, and independent external security audits.**

See [MILESTONE-6-RELEASE-READINESS-REPORT.md](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/MILESTONE-6-RELEASE-READINESS-REPORT.md) and [`docs/SOROBAN-TESTNET-DEPLOYMENT-STATUS.md`](docs/SOROBAN-TESTNET-DEPLOYMENT-STATUS.md).

---

## Getting Started Locally

```bash
# 1. Contracts (Rust + wasm32v1-none + Stellar CLI 27.1.0)
git clone https://github.com/stealthbridge-labs/stealthbridge-contracts.git
cd stealthbridge-contracts && cargo test --workspace --locked

# 2. Backend (Rust + PostgreSQL 16 + sqlx-cli)
git clone https://github.com/stealthbridge-labs/stealthbridge-backend.git
cd stealthbridge-backend && sqlx migrate run && cargo test --all-targets --locked

# 3. SDK (Node >= 22)
git clone https://github.com/stealthbridge-labs/stealthbridge-sdk.git
cd stealthbridge-sdk && npm ci && npm run verify

# 4. Frontend (Next.js + Playwright)
git clone https://github.com/stealthbridge-labs/stealthbridge-frontend.git
cd stealthbridge-frontend && npm install && npm run typecheck && npm test
```

---

## Contributing & Security

StealthBridge welcomes contributors across **Soroban/Rust**, **Applied Cryptography & ZK**, **Smart Accounts**, **Axum/SQLx Backend**, **TypeScript SDK**, **Next.js UX & Accessibility**, and **Documentation**.

1. Read our [Organization Contribution Guide](CONTRIBUTING.md), [Architecture Topology](docs/INTEGRATION-TOPOLOGY.md), and the target repository's `CONTRIBUTING.md`.
2. Browse open issues tagged `good first issue`, `help wanted`, `soroban`, `zero knowledge`, `smart accounts`, `backend`, `sdk`, or `frontend`. *(Cryptographic circuits, auth, and fund-release controls are never tagged `good first issue`.)*
3. Follow our [Code of Conduct](CODE_OF_CONDUCT.md) and report security vulnerabilities privately via [SECURITY.md](SECURITY.md).

<div align="center">

---

**Build verifiable confidentiality on Stellar — without hidden assumptions.**

[Web App](https://stealthbridge.vercel.app/) · [GitHub Organization](https://github.com/stealthbridge-labs) · [Architecture ADR-0007](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/adr/0007-protocol-execution-and-zk-stack.md)

</div>
