# Soroban governance contract deployment status — October 17, 2026

> **Not deployed.** StealthBridge's three Soroban governance contracts are
> compiled and reproducibly verified, but there are no independently attested
> Testnet contract addresses or submitted deployment transactions.

## What was verified

The [Contracts repository](https://github.com/stealthbridge-labs/stealthbridge-contracts)
publishes a three-contract WASM/ABI operator kit from
[successful CI run 39030590122](https://github.com/stealthbridge-labs/stealthbridge-contracts/actions/runs/39030590122)
at source commit `130c577ef6f44412a249d43e3e459cedecb5c970`.

| Contract | Locally verified WASM SHA-256 | Deployment |
| --- | --- | --- |
| CorridorRegistry | `588d17f99850272f2f18e6ee407d94329b4f8ae415c2f6b71993cf59f4139099` | Pending |
| PolicyRegistry | `856186ba3dca1feff010c670bd1ae9818bf69e284304273f943745603b9a7912` | Pending |
| GovernanceGate | `66b40fe5ee4f704a91acf39922ed130cc1eb4fc0cdc3c5ee5a30614921f4aa81` | Pending |

The CI provenance pins Rust 1.91.0, Soroban SDK 27.0.6,
Stellar CLI 27.1.0, `wasm32v1-none`, and two identical isolated WASM builds.
`verify_artifacts.py` and the offline `preflight_testnet.py` passed
against the exact CI kit. The planned public Testnet administrator exists
and was funded when checked on October 17, but ownership has not been
authenticated. This does not constitute signer authorization.

On the connected operator workstation, CLI v27.1.0 was installed and its
release archive hash checked. **No signing identity was configured**;
`operator_local` did not resolve. Live public Soroban RPC probes returned
HTTP 403 from this workstation, preventing confirmation of current RPC
network identity, protocol and ledger freshness. Nothing was deployed or
signed.

## Publication and integration boundary

Only publish **real** C-addresses, deployment transaction hashes, verified
contract WASM hashes, administrator state and governance-gate dependency
bindings after the local signing ceremony and independent Testnet
verification have succeeded. The current canonical
[deployment manifest](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/deployments/testnet/manifest.json)
correctly remains `not-deployed`. Its legacy schema v1 cannot attest all
three contracts; that validation gap must be resolved before upgrading the
canonical deployment statement.

The frontend, SDK and backend **must not infer on-chain availability** from
CI artifact success, a public wallet, or the contract source interface.
Privacy verification, token transfers, custody, cross-border payout and
financial settlement are still **not implemented or enabled**.

For the full SHA-256/ABI table, operator authorization gates and post-deploy
verification steps, use the [contracts release evidence](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/deployments/testnet/TESTNET-RELEASE-STATUS-2026-10-17.md)
and [operator runbook](https://github.com/stealthbridge-labs/stealthbridge-contracts/blob/main/deployments/testnet/OPERATOR-DEPLOYMENT-RUNBOOK.md).

**After a verified deployment**, this page should be revised with an evidence
table of all three real Testnet C-addresses and transaction hashes, independent
bytecode checks and the dependency references actually observed on-chain;
until then those fields are intentionally absent.
