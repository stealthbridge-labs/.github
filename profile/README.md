<div align="center">

<a href="https://stealthbridge.vercel.app/">
  <img src="https://raw.githubusercontent.com/stealthbridge-labs/.github/main/assets/stealthbridge-logo.svg" alt="StealthBridge — Confidential payments. Without borders." width="620" />
</a>

### Confidential payments. Without borders.

**One connected cross-border payments experience, designed to protect legitimate personal and commercial information.**

[Explore the product](https://stealthbridge.vercel.app/) · [Personal Send](https://stealthbridge.vercel.app/send) · [Business](https://stealthbridge.vercel.app/business) · [Our approach](https://stealthbridge.vercel.app/platform)

</div>

---

## What we're building

Global payments should not force a choice between usable software, operational accountability and reasonable privacy. Individuals need a straightforward way to prepare cross-border transfers, while businesses need clear organization access, controlled payment workflows and reliable reconciliation without exposing sensitive commercial information unnecessarily.

**StealthBridge is building a customer-first product on Stellar, with confidential settlement infrastructure as its long-term goal.** The design distinguishes sensitive information from necessary issuer, regulatory, audit and risk-management access. Privacy needs independently reproduced cryptographic evidence; neither a marketing claim nor a successful ledger query is sufficient.

## Product experiences

| Experience | For whom | What works now |
| --- | --- | --- |
| **[Personal Send](https://stealthbridge.vercel.app/send)** | Individuals and families | Explore actual configured Testnet routes, check a public recipient with consent, and prepare local transfer details |
| **[Business](https://stealthbridge.vercel.app/business)** | Organizations, treasury and payment teams | Signed-in, Neon-backed pending applications and membership views; individual and batch payment planning |
| **[Platform](https://stealthbridge.vercel.app/platform)** | Developers and future payment integrators | Read-only Testnet API and TypeScript SDK, public Soroban governance observation, and an explicit roadmap to secure integration |

The authenticated app is organized into **Home**, **Personal**, **Business**, and **Account** areas. The Business workspace keeps onboarding and team access distinct from the single-payment and CSV batch planners. Missing data is shown as unavailable or empty, never as a fabricated payment, quote or balance.

[Current product structure and customer journey](https://github.com/stealthbridge-labs/stealthbridge-frontend/blob/main/docs/PRODUCT-ARCHITECTURE-AND-JOURNEYS.md).

## One system, four engineering repositories

| Repository | Responsibility |
| --- | --- |
| **[Frontend](https://github.com/stealthbridge-labs/stealthbridge-frontend)** | Next.js customer product, consent-based wallet sign-in, responsive UX and authenticated API bridge |
| **[Backend](https://github.com/stealthbridge-labs/stealthbridge-backend)** | Rust/Axum Testnet RPC reads, Neon/PostgreSQL-backed account and organization records, corridor metadata and operational journal |
| **[TypeScript SDK](https://github.com/stealthbridge-labs/stealthbridge-sdk)** | Pinned, strict read-only API response models and safe exact-value utilities |
| **[Soroban contracts](https://github.com/stealthbridge-labs/stealthbridge-contracts)** | Rust/WASM public governance, source-level policy tests and separately bounded smart-account/privacy research |

```text
Customer-facing Next.js app
   ├─ Local amount/recipient/reference draft state
   ├─ SEP-53-style signed wallet challenge → authenticated session
   └─ Same-origin public/account API → Rust/Axum service
                                            ├─ Stellar Testnet RPC
                                            └─ Neon PostgreSQL
TypeScript SDK → reviewed, read-only protocol models
Three public Soroban governance contracts → separately verified Testnet records
Future audited smart accounts + confidential rail + issuer + payout reconciliation
```

All four repositories use strict Testnet-only verification and do not grant financial execution just because infrastructure responds successfully.

## Delivered engineering foundations

- Deployed Next.js product with real customer and business account routes, verified signed-message sign-in and account preferences.
- Real Neon-backed pending organization applications, current membership views and optional viewer invitations.
- Server-filtered Testnet corridor discovery, public recipient presence lookup, fresh network and database preflight, and browser-only individual/CSV batch planning.
- Rust API with structured errors, safe query bounds, production schema migration controls and a testable authenticated browser-to-backend boundary.
- **12/12 SQLx migrations recorded as applied to production Neon on October 31, 2026** through a protected workflow. Schema readiness does not grant payment approval.
- Three **public** Soroban governance contracts independently verified on Stellar Testnet after the October 17, 2026 deployment.
- Pinned **read-only** smart-account WASM, WebAuthn verifier and policy preflight with live TTL checks. **No StealthBridge customer smart account has been deployed by that preflight.**

The canonical v1 manifest is a legacy integration record and needs a separately approved replacement; newly added contract source methods are **not automatically deployed** to historical instances.

Read the [cross-repository topology](docs/INTEGRATION-TOPOLOGY.md), [architecture and product direction](docs/PLATFORM-VISION-AND-ARCHITECTURE.md), and [governance release record](docs/SOROBAN-TESTNET-DEPLOYMENT-STATUS.md).

## What isn't enabled

**StealthBridge does not yet offer real-money deposits, confidential fund transfers, a trusted FX quote, verified liquidity, regulated bank payouts, automated fee claiming, operational customer custody, or a cryptographically verified privacy rail.** The customer application is a **Testnet account-management and payment-planning foundation**.

Before an actual customer-money pilot, we must demonstrate independently verified confidentiality; real asset issuer and payout relationships; reviewed smart-account authorization, passkey binding and lost-device recovery; compliant organization/recipient eligibility; signed and expiring quotes; chain finality and external payout reconciliation; and operational audit/security evidence.

## Work with us

We welcome technical and product contributions in **Rust/Soroban, TypeScript, accessibility, Stellar smart-account security, payment integrations, privacy verification and documentation**. Each repository README has accurate setup and release boundaries. Contributions must not include operator wallets, recovery phrases, secrets, private witnesses or fake customer payment states.

[Contribution guide](CONTRIBUTING.md) · [Security reporting](SECURITY.md) · [Repository directory](https://github.com/orgs/stealthbridge-labs/repositories)

<div align="center">

---

**Build trust into payments. Protect what matters.**

[Website](https://stealthbridge.vercel.app/) · [Engineering organization](https://github.com/stealthbridge-labs)

</div>
