# StealthBridge Governance — Early Development

**Provisional framework.** Legal structure, named maintainer roster, repository release authority, contributor licensing and community governance have not been ratified.

## Engineering decisions

- Propose substantial changes in focused issues or architecture RFCs.
- Demonstrate financial security/privacy properties through reproducible tests.
- Keep SDK, API and contract binding changes versioned with a compatibility matrix.
- Privileged signing, custody, issuer controls, fund-release logic, ZK verifier modification and external provider integration require explicit maintainer security review.
- Never deploy or authorize real-value operations solely because CI succeeds.

## Contributions and reviews

Contributors propose and test changes through PRs. Maintainers with repository permissions review for correctness, evidence, scope and the threat model. Formal approval and release rules will be published before production-readiness milestones.

## Open development

Technical decisions, issue proposals and code reviews are managed openly wherever confidentiality and responsible security disclosure permit.

Use public issue/ADR discussion where possible; confidential security discussions must remain private.
