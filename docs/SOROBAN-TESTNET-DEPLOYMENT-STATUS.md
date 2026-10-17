# Soroban Testnet release — deployed 17 October 2026

**Three actual public governance contracts are deployed and code-verified on Stellar Testnet.** This is governance/configuration infrastructure only, not a privacy proof, fund-transfer bridge, token issuer, fiat payout or platform-fee collector.

## Contract identities

| Contract | Live Testnet C-address | Deployed ledger | Transaction |
| --- | --- | --- | --- |
| CorridorRegistry | `CDS6HBE6YJSZTRG3VR2HLCNHWJZMKB43BLFFEHEH3Z76WXAF46LW7JOB` | 5244269 | [`0ac409…43e5`](https://stellar.expert/explorer/testnet/tx/0ac4094247fd50872d079c9637b0975f825f99574e6722c9c69739d8c5c143e5) |
| PolicyRegistry | `CBXWEA5PMDTBN5AN7FJYGGAPIWLRKXYHWLVWG5WOXH3HSRDB4RYTJBN5` | 5244283 | [`34c2e8…e118`](https://stellar.expert/explorer/testnet/tx/34c2e84cad5be5181b7e1964d4e48e2c26ca021583373922f821c0038abce118) |
| GovernanceGate | `CD2KIMDRYJMKGO5SMIBOQP6ADPW5I4THNZFGXWYLIPGSXAI5NRXVAPKV` | 5244293 | [`946880…341`](https://stellar.expert/explorer/testnet/tx/9468801411a6bbb7fb2966c0225057bb4f3c8a7113aa687c0a0be744a7c5b341) |

- **Build provenance:** [CI run 39030590122](https://github.com/stealthbridge-labs/stealthbridge-contracts/actions/runs/39030590122), clean source revision `130c577ef6f44412a249d43e3e459cedecb5c970`.
- **Network:** Stellar Testnet; passphrase `Test SDF Network ; September 2015`. Observed protocol 29.
- **Signer and administrator:** `GC3YRVLB7IN7SNUYVWFUC6OD3QWJXCUZ4HOBNIPVGY7BZDVOYMDNX5TN`, configured as local CLI identity `operator_local` in OS secure storage. No private material was exported to the repository, CI or this report.
- **Earlier Freighter account:** `GBBCOFZZ3RDQHTC662EVM3UO5SAXQEZB6DL64HLEJYEYJ4KBVL3CDLTE` is **not** the administrator of this release.
- **Verification performed:** Stellar Testnet Horizon confirmed all deployment and upload transactions successful; independent read-only CLI commands fetched bytecode from the three C-addresses and checked their bytes against the reproducible artifacts; registry admins and paused states were read; GovernanceGate's actual two registry addresses and admin were read and matched exactly.

## Pinned bytecode

| Contract | On-chain SHA-256 of fetched WASM |
| --- | --- |
| CorridorRegistry | `588d17f99850272f2f18e6ee407d94329b4f8ae415c2f6b71993cf59f4139099` |
| PolicyRegistry | `856186ba3dca1feff010c670bd1ae9818bf69e284304273f943745603b9a7912` |
| GovernanceGate | `66b40fe5ee4f704a91acf39922ed130cc1eb4fc0cdc3c5ee5a30614921f4aa81` |

Review the full [Contracts deployment evidence](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/deployments/testnet/VERIFIED-GOVERNANCE-RELEASE-2026-10-17.md) and [machine-readable observation](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/deployments/testnet/governance-deployment-evidence.v2.json).

## What is *not* available

The legacy canonical deployment manifest v1 cannot represent three deployed contracts and **currently still says `not-deployed` for compatibility**. This stale old manifest must not be used as evidence that the chain deployments failed, and the new observation record must not be silently substituted into an incompatible backend or SDK client. Migrate consumers through a separately reviewed canonical schema-v2 release with real-time RPC revalidation.

**No private payment rail, custody, platform fee collection, fiat payout, user wallet signing, or Mainnet deployment is authorized or enabled by these contracts.** The proposed first platform fee is a 10 basis-point (0.10%) transparent SDK *quote*, capped at 50 basis points (0.50%), with zero collection ability until a separate tested token/settlement contract is approved. This commercial-rate proposal is not a currently charged fee.

The public contracts' on-chain storage can eventually expire; successful deployment does not replace TTL monitoring, pause/recovery drills, independent security review, asset issuer diligence and operator key management.
