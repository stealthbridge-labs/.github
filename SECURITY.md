# StealthBridge Security Policy

**Stellar Testnet research only.** There is no audited, mainnet-ready StealthBridge settlement service. Do not use these repositories to secure real assets or move fiat funds.

## Responsible reports

We appreciate findings involving Soroban authorization bypass, replay and proof binding, seed/note exposure, misleading privacy claims, tenant data leaks, settlement idempotency, forged provider callbacks and financial reconciliation.

**Do not publish exploitable vulnerabilities in public issues or PRs.** If the affected repository has **Security → Report a vulnerability** enabled, use GitHub's private vulnerability reporting. Otherwise, contact a confirmed maintainer through an existing private communication channel; do not invent an email address or expose secret data in public.

Include the affected repo/commit, expected security property, impact, and test-only reproducible steps. Never attach real private keys, payment credentials or personal KYC.

We do not currently advertise a bounty, guaranteed response SLA, dedicated security email or formal vulnerability-disclosure safe harbor. These require explicit governance decisions.

Do not attack other parties' contracts, wallet extensions, providers or production systems without permission. See our [threat model](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/docs/THREAT-MODEL-v0.2.md).
