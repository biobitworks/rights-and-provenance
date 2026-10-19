# Licensing FCO/FCG contract v0.1 — portfolio successor

**Status:** PROPOSED shared graph contract. An offline synthetic prototype and executed notebook are available in a separate local review package. **No live admission gateway, ownership finding, signed grant or legal opinion is implemented by this document.**

## Predecessors (immutable)

- [Canonical rights policy, version 2026-10-18.1](https://github.com/biobitworks/rights-and-provenance)
- [Portfolio adoption register and predecessor Merkle/MMR seal](https://github.com/biobitworks/license-adoption-audit-20261018)
- [SeedGraph license/source-asset custody adapter](https://github.com/biobitworks/seedgraph/blob/main/docs/LICENSE_SOURCE_ASSET_PROOF_ADAPTER.md): snapshot bytes → source/content proof; claim ceiling `LICENSE_GOVERNANCE_ONLY`; no live fetch or writeback.
- [BioCustody rights/IP/FTO lane](https://github.com/biobitworks/biocustody/blob/main/docs/IP_AWARE_FCG_COMMERCIALIZATION.md): scientific and rights decisions remain orthogonal.
- [GettingScienceDone cryptographic rights contract](https://github.com/biobitworks/gettingsciencedone/blob/main/docs/CRYPTO_RIGHTS_SCIENTIFIC_CUSTODY_CONTRACT_v1.md): RIGHTS_POLICY_ID / LICENSE_ID / root / signing and verification states.

## Principle

**Both** licensing FCOs and a licensing FCG are required. Content identity is separate from occurrence identity. A custody proof authenticates captured bytes under a declared construction; it does not prove legal title, grant authority, permission scope, downstream redistribution rights, causal attribution or patent freedom to operate.

Source/evidence → independently addressable rights FCO → typed FCG edge → use-context FCO → evaluated decision FCO → enforcement receipt → governed output/artifact.

## Minimal FCO types

| Kind | Identity and required semantic fields |
| --- | --- |
| `LicenseTextFCO` | Exact snapshot bytes SHA-256, source locator, text version, source license classification (SPDX if applicable), custody receipt reference. |
| `RightsHolderAssertionFCO` / `AuthorityEvidenceFCO` | Claimed authorizer, relationship to the covered rights, documentary proof, reviewer, verification status, private vault handle. A claim is **not** proof of title. |
| `PermissionFCO` | License/consent/contract instrument identity and exact authorized scope; actor, action, version, territory, purpose, recipient, field-of-use, environment, validity, conditions, sublicensing, output rights, patent status, retraction and precedence. |
| `AssetFCO` | Exact asset/version and contents identity; code, dataset, media, model weights, model output, database extraction or derived publication. |
| `OccurrenceFCO` | Separate encounter/context identifier: where and when the same content was obtained, transformed, signed, published or served. |
| `RightsPolicyFCO` | First-party default policy and predecessor identity; **never** silently overrides prior express grants or upstream rights. |
| `UseContextFCO` | Actual requester, requested operation, deployment, commercial/research purpose, environment, intended distribution, date and recipient. |
| `RightsDecisionFCO` | Rule version, exact rights graph root, evaluated context, evidenced grants, missing/denied rights, reason codes, claim ceiling, reviewer, runtime enforcement result, signature and custody states. |

Content identity and context/occurrence identity MUST be separately recomputable. A private agreement may be held in a controlled vault; the public graph holds only permitted references/attestations, not raw protected terms.

## Typed FCG relationships

`GOVERNED_BY`, `HAS_TERMS`, `ASSERTS_OWNERSHIP`, `GRANTS_SCOPE_FOR`, `EVIDENCED_BY`, `PERMITS_ACTION_IN_CONTEXT` (evaluated, not inferred), `DENIES_ACTION_IN_CONTEXT`, `DERIVED_FROM`, `TRAINED_ON`, `DISTRIBUTED_AS`, `HOSTED_UNDER`, `RELEASED_TO`, `SUPERSEDES`, `REVOKED_BY`, `REVIEWED_BY`, `DECISION_BASED_ON`, and `ENFORCED_AT`.

A typed edge is a declaration with provenance, **not** causality. The permission relation is higher-order: `permission × asset/version × actor × action × purpose × environment × time × recipient/territory`. Reify the scope as a node with multiple evidenced relationships rather than incorrectly attaching a single inherited license string to an entire FCG.

## Negative propagation rules

1. No permission is inferred from public visibility, provenance hashes, citation, a GitHub `LICENSE` badge, or the mere existence of an FCG path.
2. Derived assets do not automatically inherit unrestricted commercial rights; check every covered input and relevant model/provider-output term, with rights propagation determined by the actual license and transformation.
3. A source terms snapshot and separately reported additional permission are **distinct FCOs** until the exact permission instrument, authorized signer and grant scope are independently reviewed.
4. A verified SPDX identifier is not an independently verified right to use an external asset; contradictory metadata must become a review-required successor.
5. Previously granted licenses are not retroactively revoked merely by publishing a new policy. Negative findings and revoked grants preserve predecessors.
6. `UNKNOWN`, `REVIEW_REQUIRED`, `DENIED`, `FAILED`, `NOT_TESTED`, `NOT_COMPUTED` and `NOT_SIGNED` are real states, not missing positive outcomes.
7. No release, export, model training, deployment or commercial use may bypass the required **runtime** rights admission controller. This specification does **not** attest that such a gate is deployed.
8. No signature is `SIGNED` without independent public-key verification; no MMR is `COMMITTED` without ordered leaves, peaks/root, construction and receipt.

## Concrete cross-domain stress scenarios

- ImYoo public Zenodo terms versus a separate cofounder approval: verify precisely which entity/asset/version, persons, actions, commercial derivative uses, sharing and time the latter authorizes before any promotion.
- HPA release-versus-version versus incorporated third-party material: attach rights to **individual source/version occurrences**, not an entire atlas by brand name.
- HydraDB AGPL, SeedGraph AGPL/commercial grants, Vitaology Apache/CC BY split: model software, datasets and hosted outputs separately. Record existing grants unchanged.
- Zenodo publication metadata, connected model outputs, provider terms, patents/public disclosure and external citation graphs: treat as distinct rights-bearing objects and typed relations, not implied permissions.

## Verification and implementation gates

Prototype-level tests should prove content/occurrence distinction, fail-closed missing snapshot and permission, explicit denial precedence, version/time mismatch, model/derivative nonpropagation, ref-integrity, cycle rejection, deterministic graph root, mutated leaf control and synthetic commercial misuse rejection. The project requires a reproducible Jupyter notebook for protocol replay.

Before production: ingest real exact license snapshots via the existing SeedGraph adapter, bind authority evidence and approved scope, evaluate actual third-party terms, enforce access at read/export/train/serve endpoints, red-team direct bypass, execute on two independent hosts, compute a successor Merkle/MMR receipt with full ordered construction and verify any signing identity. Do not rewrite the predecessor portfolio seal or claim legal clearance from metadata alone.

**Status:** source-adapter code OBSERVED in SeedGraph; this integrated portfolio contract PROPOSED; cross-repo runtime enforcement NOT_TESTED.
