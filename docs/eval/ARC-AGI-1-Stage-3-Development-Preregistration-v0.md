# ARC-AGI-1 Stage 3 Development Preregistration v0

- **Version:** v0.1
- **Date:** 2026-08-07
- **Status:** Partially approved development preregistration; external execution not approved
- **Scope:** First fixed-policy decisions for provider-backed `G0` calibration and a matched `G0`/`S1` development comparison
- **Approval source:** User approval in the 2026-08-07 working session
- **Decision authority boundary:** This approval authorizes the frozen development-policy choices below. The project owner remains `TBD`; this record does not authorize a provider, credentials, paid use, or a model call.
- **Authoritative evaluation definition:** [ARC Evaluation Definition v0](./ARC-Eval-Definition-v0.md), sections 5–9 and 13–18
- **Implementation record:** [ARC-AGI-1 G0/S1 Development v0](./ARC-AGI-1-G0-S1-Development-v0.md)

## 1. Interpretation boundary

This is a `development-only`, local-reference preregistration and partial approval record. All resulting observations must be labelled `public-exposed` because the selected ARC-AGI-1 training tasks and model exposure are public or cannot be excluded. The evaluator is `local-reference-non-official` and is not parity-validated against an official scorer.

This record is not a formal confirmatory preregistration, provider approval, cost authorization, run manifest, score report, official or sealed evaluation, superiority decision, ARC stage achievement, or empirical adjudication. No provider-backed execution may begin until every field in [Section 8](#8-unresolved-execution-approvals) is approved and frozen.

The pre-existing Stage 0 `rules_snapshot_mismatch` remains unresolved. It must be resolved or formally adjudicated before any provider-backed ARC run is interpreted as reproducible run evidence.

## 2. Frozen configurations

The existing prompt policies are approved without modification:

| Configuration | Unit | Policy ID | Policy SHA-256 | Frozen intervention |
|---|---|---|---|---|
| `G0` | `G` | `arc-a1-g0-minimal-v1` | `c5037d4cd67a62ba75226caf2c3c9a3651e84488c0b6567038be9620e62a3283` | Minimal direct task instruction and candidate-set JSON protocol |
| `S1` | `S` | `arc-a1-s1-structured-v1` | `e4800e3306a8cd3fa7f323306056c52db561460d312422783dce3548e0c2bb4a` | Fixed object/component and transformation-checklist prompt |

The evaluation unit is `G` for `G0` and `S` for `S1`. Any observed difference is a fixed-backbone system-configuration difference attributable only to the frozen prompt intervention under the matched boundary; it is not a model-weights result.

## 3. Approved information and execution boundary

| Field | Approved value |
|---|---|
| Tools | None |
| Retrieval, browsing, search, memory, verifier | None |
| Network | Only the subsequently approved model-provider endpoint; no other network access |
| Context | One task per request; training input/output pairs and test inputs only; no test outputs, retrieved context, or cross-task state |
| Persistent memory | None |
| Retry policy | `max_retries=0`; transport or provider retries may not create an unrecorded duplicate request |
| Concurrency | `1` |
| Initial calibration attempts | `1` |
| Initial calibration model calls per task | `1` |
| Initial calibration rollouts per task | `1` |
| Initial calibration seed | `0` |

If the selected provider does not support an effective seed, the run must record `provider-side nondeterministic`; seed `0` remains the manifest seed and no best-seed selection is allowed. A single-seed Stage 3 result is a development observation only and is not eligible as a primary scientific result.

Credentials must be injected at runtime through an approved secret mechanism and must never be committed, embedded in a manifest, or written to prompts, predictions, failures, deviations, costs, or logs. The concrete provider, secret mechanism, and credential variable or handle remain `TBD`.

## 4. Calibration task set

Calibration uses only the A1 `training` tier. It does not query `public_evaluation`, so this approval does not add an event to the development-query log. Any later use of `public_evaluation` must be logged before interpretation and may not be repeatedly queried to select an architecture.

The twelve tasks were selected from `artifacts/arc-agi-1/manifest.json` without reading task solutions or model results:

1. sort the 400 training records by `(size_bytes, path)`;
2. include the global minimum-size and maximum-size records;
3. divide the sorted records into ten contiguous strata of 40 records;
4. within each stratum, select the record with the lexicographically smallest SHA-256 of `arc-a1-stage3-calibration-v1:<path>`.

| Stratum | Task ID | Manifest size (bytes) |
|---|---|---:|
| minimum | `6150a2bd` | 294 |
| 1 | `3c9b0459` | 476 |
| 2 | `c59eb873` | 1,015 |
| 3 | `dc1df850` | 1,483 |
| 4 | `f25fbde4` | 1,793 |
| 5 | `0ca9ddb6` | 2,209 |
| 6 | `ded97339` | 2,681 |
| 7 | `6a1e5592` | 2,918 |
| 8 | `673ef223` | 5,265 |
| 9 | `36fdfd69` | 6,749 |
| 10 | `6d58a25d` | 10,041 |
| maximum | `3631a71a` | 27,746 |

The task list and selection rule are frozen. Changing either requires a new approval record before execution.

## 5. Calibration and budget-proposal rule

The initial calibration is a `G0` resource-observation run on the twelve frozen tasks. It may measure usage and structured failures, but its scores may not be used to modify either prompt, select an architecture, or establish superiority.

`Low`, `Matched`, and `High` proposals will be derived from the completed G0 bundle's observed per-task maxima using these approved multipliers:

| Tier | Multiplier |
|---|---:|
| `Low` | `1.00` |
| `Matched` | `1.25` |
| `High` | `2.00` |

The implemented derivation utility rounds discrete limits upward. A larger proposed call or rollout ceiling does not authorize retries or additional G0/S1 calls: the frozen Stage 3 solvers remain single-call and the actual ledger must record observed use. The derived values remain proposals until they receive a separate numerical-tier and cost approval.

Provider-specific input/output token limits, wall-clock limit, per-task cost ceiling, and total calibration cost ceiling remain `TBD`. They must be large enough to admit every frozen request under the selected provider tokenizer and must be approved before dispatch.

## 6. Paired G0/S1 development run

The paired run must use identical:

- task IDs and deterministic ordering;
- manifest seed;
- provider, model ID, identifiable snapshot or weights identifier, and request date;
- non-secret request parameters;
- input/output tokens, attempts, model-call, rollout, wall-clock, concurrency, and cost ceilings;
- provider endpoint, tool, network, data, context, retry, memory, search, and verifier boundaries;
- evaluator, rules, dataset manifest, solver commit, and dependency identity.

The only allowed substantive difference is the frozen `S1` prompt intervention. Run IDs, configuration IDs, the `G`/`S` unit labels, and the corresponding policy objects and hashes may differ as required to identify that intervention. Any other mismatch invalidates the paired interpretation.

## 7. Allowed and prohibited statements

Allowed after a valid run:

- a `development-only`, `public-exposed`, local-reference observation;
- task-level `G0`/`S1` differences under the exact frozen configuration;
- observed resource and cost use;
- non-authoritative budget proposals derived by the approved rule.

Prohibited:

- `official`, `sealed`, `private-clean`, verified, benchmark-complete, SOTA, or ARC-solved language;
- superiority, generalization, persistent-superiority, model-specialization, broad-capability, professional-capability, AGI, or cross-domain claims;
- treating calibration scores as architecture-selection evidence;
- treating a proposed compute tier as approved before its numerical values and costs are separately approved.

## 8. Unresolved execution approvals

Provider-backed execution remains blocked until a follow-up approval freezes all of the following:

| Required field | Status |
|---|---|
| Provider and approved endpoint | `TBD` |
| API model ID | `TBD` |
| Identifiable model snapshot or weights identifier | `TBD` |
| Request/execution date | `TBD` |
| Non-secret provider request parameters | `TBD` |
| Provider adapter ID and implementation | `TBD` |
| Secure credential-injection mechanism | `TBD` |
| Input-token and output-token ceilings | `TBD` |
| Wall-clock limit | `TBD` |
| Per-task and total calibration cost ceilings | `TBD` |
| Derived numerical `Low`/`Matched`/`High` tiers | `TBD` pending calibration and separate approval |
| Stage 0 rules-manifest conflict resolution or adjudication | `TBD` |

Official scorer material, sealed validation, and private access are not prerequisites for this local-reference Stage 3 development exercise, but their absence prohibits official, verified, sealed, generalization, or benchmark-complete interpretations.

## 9. Status impact

- **Empirical claim impact:** none.
- **Evidence adjudication impact:** none.
- **ARC stage-status impact:** none. Stage 3 remains partially implemented and unexecuted.
- **Winning-hypothesis impact:** none.
- **Reversible-if condition:** supersede this record before execution if the frozen prompt hashes, task-selection procedure, data tier, provider boundary, or matched-pair policy is found incompatible with the authoritative ARC Evaluation Definition or the selected provider's reproducible request contract.

## 10. Change log

| Date | Version | Change | Status impact |
|---|---|---|---|
| 2026-08-07 | v0.1 | Recorded the approved provider-independent prompt, boundary, calibration-set, seed, initial-call, multiplier, and paired-comparison policies; preserved external execution inputs as `TBD`. | Partial development approval only; no model call, result, empirical claim, or ARC stage change. |
