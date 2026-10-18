<div align="center">

<a href="https://stealthbridge.vercel.app/">
  <img src="https://raw.githubusercontent.com/stealthbridge-labs/.github/main/assets/stealthbridge-logo.svg" alt="StealthBridge" width="620" />
</a>

### Confidential payments. Without borders.

**Privacy-conscious cross-border payments for businesses, people, and developers.**

[Explore StealthBridge](https://stealthbridge.vercel.app/) · [For businesses](https://stealthbridge.vercel.app/business) · [For individuals](https://stealthbridge.vercel.app/send) · [Platform](https://stealthbridge.vercel.app/platform)

</div>

---

## The problem we're solving

International payments connect markets, but the systems behind them often expose commercially sensitive information, fragment the payment journey across providers, and make settlement activity difficult to reconcile. Businesses need stronger control over how payment information is shared; people deserve a simpler cross-border experience without unnecessary exposure.

**StealthBridge is building one connected infrastructure layer for moving value across borders with privacy by design, verifiable settlement state, and accountable controls.** Confidentiality should protect legitimate financial information—not obscure required compliance, risk management, or audit access.

## One platform. Three experiences.

| Experience | Built for | What we're creating |
| :-- | :-- | :-- |
| **[StealthBridge Business](https://stealthbridge.vercel.app/business)** | Payment companies, treasury teams, and businesses | Confidentiality-oriented B2B settlement workflows, corridor discovery, operational controls, and reconciliation |
| **[StealthBridge Send](https://stealthbridge.vercel.app/send)** | Individuals and families | A clear, wallet-aware remittance journey with privacy-conscious payment relationships |
| **[StealthBridge Platform](https://stealthbridge.vercel.app/platform)** | Developers and payment integrators | APIs, TypeScript tooling, Stellar observations, governance, and future payment integrations |

## Built as one connected system

StealthBridge is developed across four specialized codebases that share a common product direction:

| Repository | Responsibility |
| :-- | :-- |
| **[Frontend](https://github.com/stealthbridge-labs/stealthbridge-frontend)** | Next.js web experiences, accessible interfaces, wallet UX, and server-side API bridge |
| **[Backend](https://github.com/stealthbridge-labs/stealthbridge-backend)** | Rust/Axum APIs, Stellar ledger and contract observations, policy reads, and operational persistence |
| **[Smart contracts](https://github.com/stealthbridge-labs/stealthbridge-contracts)** | Rust/Soroban governance and the security foundations for future on-chain financial execution |
| **[TypeScript SDK](https://github.com/stealthbridge-labs/stealthbridge-sdk)** | Typed integration surface and independently validated read-only API consumers |

```text
 Business • Send • Developer applications
                    |
         Next.js product frontend
                    | safe server-side GET bridge
                    v
        Rust/Axum platform API <------ TypeScript SDK
                    |
       +------------+-------------+
       |                          |
 Stellar RPC + deployed       Neon PostgreSQL
 Soroban governance           observations / journal
```

Our long-term design combines privacy-preserving payment technology with explicit authorization, ledger observability, risk controls, and real-world corridor integrations.

## What is real today—and what comes next

**Implemented engineering foundations:** a public website, connected frontend/SDK read models, backend APIs and reconciliation foundations, and three deployed **public Soroban governance contracts** on Stellar Testnet: `CorridorRegistry`, `PolicyRegistry`, and `GovernanceGate`. Their deployment receipts and public code observations are documented independently.

**In progress:** resilient observer and reconciliation operations, a canonical signed contract-release manifest, wallet identity and operator recovery, proof of privacy primitives, and independently verified staging and security acceptance.

**Read-only integration verified:** our deployed Rust API answers health, real Testnet network, and public Soroban governance requests; the frontend preview successfully reads the backend's same-ledger governance snapshot. Observer availability and financial execution have separate acceptance gates.

**Not yet offered:** private-value transfers, real-money remittances, custody, fiat payouts, and on-chain platform-fee collection. Deployment of public governance contracts is **not** proof that a confidential-payments rail is operational.

Discover the [system architecture](https://github.com/stealthbridge-labs/.github/blob/main/docs/PLATFORM-VISION-AND-ARCHITECTURE.md), [cross-repository integration map](https://github.com/stealthbridge-labs/.github/blob/main/docs/INTEGRATION-TOPOLOGY.md), and [verified governance deployment record](https://github.com/stealthbridge-labs/.github/blob/main/docs/SOROBAN-TESTNET-DEPLOYMENT-STATUS.md).

## Build with us

We welcome thoughtful contributions in **Rust, Soroban, TypeScript, product design, accessibility, developer tooling, documentation, and security**. Start with our [contribution guide](https://github.com/stealthbridge-labs/.github/blob/main/CONTRIBUTING.md), browse the [organization repositories](https://github.com/orgs/stealthbridge-labs/repositories), or use our [security reporting guide](https://github.com/stealthbridge-labs/.github/blob/main/SECURITY.md).

<div align="center">

---

**Move value. Not exposure.**

[Website](https://stealthbridge.vercel.app/) · [GitHub](https://github.com/stealthbridge-labs) · [Contribute](https://github.com/stealthbridge-labs/.github/blob/main/CONTRIBUTING.md)

</div>
