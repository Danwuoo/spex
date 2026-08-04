# PROJECT STATE

- **State version:** v0.4
- **Last updated:** 2026-08-02
- **Evidence cutoff:** Evidence Base v1.1 / Evidence Adjudication v1; ARC external-source snapshot through 2026-07-31
- **Operational snapshot:** ARC dataset and Toolkit checks through 2026-08-02
- **Document role:** Primary project entrypoint, high-value state record, and source router. It does not replace the Problem Definition, evidence records, adjudication, or ARC evaluation specification.
- **Current lifecycle:** Problem definition stabilized → evidence adjudicated → ARC evaluation specification drafted → ARC-AGI-1 pre-implementation setup
- **Current operational stage:** ARC-AGI-1 pre-implementation setup. Public A1/A2 data and the A3 Toolkit are locally available, but the canonical snapshot, evaluator, governance, and run infrastructure are not frozen.
- **Global experiment-design readiness:** `Not ready`
- **ARC-specific design readiness:** `Draft for implementation`
- **Project owner / decision authority:** `TBD`
- **State maintainer:** `TBD`

> The project has a current empirical problem and a draft ARC evaluation program, but no authoritative artifact supports any ARC stage achievement, official score, winning hypothesis, or cross-domain/AGI conclusion. The immediate task is to freeze the A1 evaluation substrate and establish reproducible run infrastructure before executing the baseline ladder.

---

## 0. Start here

1. Read this file first.
2. Use [Task-to-source routing](#6-task-to-source-routing) to open only the minimum required source.
3. Treat `docs/current/` and `docs/eval/` as the complete document bundle available to the GPT Chat Project.
4. If a routed source or run artifact is absent from those folders, report `Unavailable in project context`; do not reconstruct it from memory, legacy material, or inference.

State labels used here:

- **Source-stated:** explicitly recorded by the authoritative source.
- **Directly observed:** verified from the local checkout or a controlled setup check; not an empirical research result.
- **State inference:** inferred from stage order or missing artifacts; not an empirical claim.
- **TBD / Unknown / Not evidenced:** not decided, unavailable, or unsupported by the current artifact set.

When this file conflicts with a routed source, the routed source wins. New evidence cannot change a claim status here first; it must enter the Evidence Base and Evidence Adjudication workflow.

---

## 1. Executive state

### 1.1 Current empirical position

The stable empirical puzzle is:

> Why do model-level specialization interventions frequently produce same-backbone gains, yet only a smaller set of cases reliably establish broad, contemporary, resource-comparable, and persistent frontier superiority; while system-level, hybrid, and formal/narrow specialization can produce strong advantages in bounded workflows or problem spaces?

Current evidence supports four high-level conclusions:

1. Model-level same-backbone relative gain is recurring.
2. Relative gain does not automatically establish contemporary or persistent frontier superiority.
3. System, hybrid, and formal/verifier-bound wins can be strong but remain unit- and boundary-specific.
4. Unit, advantage type, capability construct, resources, exposure, and time index must remain separate.

ARC is the first controlled evaluation domain, not the full research problem. ARC-only results cannot independently support cross-domain specialization laws, broad professional capability, AGI, or general capability claims.

### 1.2 Current readiness

| Layer | Status | Meaning |
|---|---|---|
| Problem Definition v1 | Current / ready with conditions | The empirical problem, taxonomy, minimum rules, and falsification conditions are defined. |
| Evidence Base v1.1 | Current | Record-level evidence and provenance are available. |
| Evidence Adjudication v1 | Current | Claims, counterexamples, contradictions, boundary conditions, gaps, and decisions are adjudicated. |
| Global experiment design | Not ready | Comparator, private-task, temporal, resource, and generalization controls remain incomplete. |
| ARC Evaluation Definition v0.1 | Draft for implementation | Working ARC program exists, with unresolved implementation decisions and unmet v1 gates. |
| Local ARC data and Toolkit | Available for implementation setup | A1/A2 public data, A3 imports, local smoke test, and remote discovery were verified. |
| ARC formal runs and stage achievements | Not evidenced | No formal preregistration, run manifest, official score, ablation, or stage-completion record is present. |

### 1.3 Evidence corpus index

| Artifact | Compact inventory |
|---|---|
| Evidence Base v1.1 | 65 evidence records, 49 sources, 43 benchmarks, 22 claims, 10 counterexamples, 12 gaps, 12 verification records |
| Evidence Adjudication v1 | 22 claim adjudications, 10 counterexample adjudications, 14 contradictions, 17 boundary conditions, 12 gaps, 14 decisions |
| Claim-status distribution | Supported 9; conditionally supported 5; partially supported 2; indeterminate 3; contradicted 1; unsupported 1; needs split 1 |

Detailed records, status reasoning, counterexample scope, contradiction maps, and gap queues remain in the evidence and adjudication artifacts; they are not duplicated here.

---

## 2. Authority and source navigation

### 2.1 Current document set

| Role | Current artifact | Authority |
|---|---|---|
| Empirical problem, scope, terminology, minimum claim rules, falsification | [Problem Definition v1](./Problem%20Definition%20v1.md) | Highest authority for the current research problem |
| Record-level evidence, IDs, provenance, benchmark metadata, verification | [Evidence Base v1.1](./Evidence-Base-v1.1.xlsx) | Highest authority for record-level evidence fields |
| Structured claim and gap adjudication, decision log | [Evidence Adjudication v1 workbook](./Evidence-Adjudication-v1.xlsx) | Highest authority for current adjudication status |
| Human-readable adjudication and readiness summary | [Evidence Adjudication v1 summary](./Evidence-Adjudication-v1.md) | Readable summary; workbook controls exact structured status |
| ARC design, governance, metrics, stage gates, and claim taxonomy | [ARC Evaluation Definition v0](../eval/ARC-Eval-Definition-v0.md) | Highest authority for the ARC evaluation program |
| Dataset inventory, Toolkit configuration, imports, environments, smoke test | [ARC Dataset and Toolkit Status v0](../eval/ARC-Dataset-Toolkit-Status-v0.md) | Operational setup record; not run evidence or empirical authority |
| Project entrypoint and navigation | `PROJECT-STATE.md` | State index only; no independent empirical authority |

### 2.2 Authority rules

- Research problem, terms, and extrapolation rules come from the Problem Definition.
- Claim, counterexample, contradiction, boundary-condition, and gap status come from Evidence Adjudication.
- Record IDs, provenance, benchmark metadata, and verification details come from the Evidence Base.
- ARC metrics, data governance, run requirements, stages, and SOTA taxonomy come from ARC Evaluation Definition.
- A preregistration, run manifest, evaluator output, or experiment report can adjudicate only its run; it cannot silently rewrite an upper-level source.
- Operational installation success does not establish benchmark validity, scorer correctness, model capability, or stage completion.
- When sources conflict, record the conflict and follow the responsible source; do not silently reconcile it in this index.

### 2.3 GPT Chat Project boundary

The GPT Chat Project contains only `docs/current/` and `docs/eval/`. Therefore:

- all navigation required for interpretation must terminate in these folders;
- research/archive files are not prerequisites for normal project work;
- repository code, data, scripts, and external services are represented here only through explicit current/eval status records;
- if a new run, dataset manifest, rule snapshot, or decision must be available to the Chat Project, add a durable current/eval artifact rather than relying on a workspace-only path.

---

## 3. Mandatory analytical guardrails

### 3.1 Evaluation unit

| Code | Unit | Minimum interpretation |
|---|---|---|
| `G` | Generalist baseline | Non-specialized model/system comparator for the target distribution |
| `M` | Model specialist | Primary intervention is in weights; supports same-backbone model-level claims when system boundaries are matched |
| `S` | System specialist | Weights fixed; intervention is prompt, retrieval, tools, search, memory, verifier, routing, scaffold, or environment |
| `H` | Hybrid specialist | Weights and system stack are both specialized and effects cannot be cleanly separated |
| `N` | Narrow/formal solver | Fixed DSL, exact verifier, handcrafted primitives, narrow format, or bounded search space |

Tools, retrieval, search, verification, memory, context, routing, scaffolds, and environment access must not be attributed to specialized weights.

### 3.2 Keep these dimensions separate

- **Advantage:** same-backbone relative gain; contemporary absolute superiority; persistent superiority; configuration-level superiority; cost/efficiency advantage.
- **Capability construct:** benchmark proxy; broad domain capability; professional workflow capability; formalized/bounded task capability.
- **Generalization:** held-out task; OOD; temporal shift; cross-version transfer; independent replication.
- **Validity context:** exact model/system snapshot; evaluator; date; resources; public/sealed/private status; contamination/exposure.

One dimension does not imply another. Missing evidence must remain `Unknown`, `Not evaluated`, `Indeterminate`, or `Source does not support`.

### 3.3 Minimum claim discipline

Any superiority, frontier, SOTA, efficiency, or generalization claim must identify at least:

- evaluation unit and exact specialist/comparator configurations;
- model/system snapshot and evaluation date;
- benchmark/evaluator and capability construct;
- tools, information access, context, scaffold, and inference policy;
- token, call, rollout, search, retry, wall-clock, and hardware boundary where relevant;
- public/sealed/private and contamination/exposure status;
- resource parity, temporal status, and generalization/replication status;
- narrowest supported proposition and prohibited extrapolation.

Without these fields, downgrade to language such as `historical`, `partially matched`, `configuration-level`, `single-setting`, `public-exposed`, or `not interpretable`.

---

## 4. ARC program state

### 4.1 Program sequence

1. **ARC-AGI-1:** establish a reproducible, attributable, cost-visible static abstraction baseline.
2. **ARC-AGI-2:** test deeper/multistep complexity and A1 → A2 transfer.
3. **ARC-AGI-3:** evaluate interactive capability systems through controlled science and competition engineering.

Research-qualified and benchmark-complete are separate outcomes. Public results alone cannot establish verified completion.

### 4.2 Dataset and Toolkit snapshot

| Substrate | Directly observed status | Formal interpretation |
|---|---|---|
| A1 public training | 400 JSON files available | Local data available; canonical snapshot/hash not frozen |
| A1 public evaluation | 400 JSON files available | Public-exposed development/evaluation substrate only |
| A2 public training | 1,000 JSON files available | Local data available; canonical snapshot/hash not frozen |
| A2 public evaluation | 120 JSON files available | Public-exposed portion only; semi-private/private not established |
| A3 root Toolkit | `arc-agi 0.9.9`; `arc_agi` and `arcengine` imports passed | Toolkit installation ready for implementation work |
| A3 offline smoke | Two bundled test environments; reset and one legal action passed | Local API path works; not a benchmark run |
| A3 remote discovery | 25 environments returned on 2026-08-02 using root `.env` | Time-indexed catalogue access; not an immutable rules or evaluator snapshot |

See [ARC Dataset and Toolkit Status v0](../eval/ARC-Dataset-Toolkit-Status-v0.md) for paths, environment IDs, commands, configuration scope, and smoke-test details.

### 4.3 Stage status

| Stage family | Current status | Missing decisive artifacts |
|---|---|---|
| A1 Research/Public/Verified | Not evidenced | Frozen baseline, paired result, ablation, run manifest, official/sealed score |
| A2 Research/Public/Verified | Not evidenced | A1 frozen port, A1-port/A2-adapted comparison, matched-compute curve, private/sealed result |
| A3 Research/Competition/SOTA/Solved | Not evidenced | Controlled ablation, official scorer output, runtime/container validation, private leaderboard result |

`Not evidenced` means the current document bundle does not support the status; it does not infer hidden progress.

### 4.4 Immediate blockers and next sequence

| Work item | Status | Blocks |
|---|---|---|
| Pin A1 canonical repository/data snapshot and hashes | Open | Formal A1 runs and reproducibility |
| Pin official parser, scorer, evaluator, and rules | Open | Valid scores and cross-run comparison |
| Define sealed validation, custodian, and evaluation firewall | TBD | Generalization and verified completion |
| Implement run manifest, registry, output archive, and cost/deviation logging | Not evidenced | Attribution and reproducibility |
| Calibrate Low/Matched/High compute tiers and seed policy | TBD | Resource-matched claims |
| Decide first-round scope: fixed-backbone system only or include model adaptation | TBD | Baseline ladder and eligible claims |

Shortest implementation sequence:

1. Freeze A1 data/evaluator/rules and governance.
2. Establish run, resource, cost, and output infrastructure.
3. Execute `G0 → S1 → S2 → S3`; add `M1 → H1` only if model adaptation is in scope.
4. Perform at least one key ablation, then issue a formal decision record before A2 transfer work.

Detailed metrics, baseline definitions, run-manifest fields, stage gates, unresolved decisions, and v1 acceptance criteria remain in ARC Evaluation Definition v0.

---

## 5. Required artifacts not yet evidenced

| Need | Durable artifact class |
|---|---|
| Data identity | A1 data manifest, hashes, canonical source/release pin |
| Evaluator identity | Parser/scorer/evaluator snapshot and immutable rules record |
| Governance | Sealed-validation protocol, access/custodian record, contamination/query ledger |
| Run infrastructure | Machine-readable run-manifest schema, experiment registry, dependency lock/container |
| Result trace | Per-task outputs, failed-run/deviation log, cost ledger |
| First formal experiment | A1 preregistration, G0 run manifest, baseline report, key ablation |
| Decision control | Structured ARC decision log with allowed/prohibited claims and reversible-if condition |

Additional project-level `TBD`s include ownership, state maintenance, compute/procurement boundaries, approved model/API policy, retention, security/secrets, publication approval, and incident response.

These are implementation requirements, not evidence that any stage has failed or succeeded.

---

## 6. Task-to-source routing

| Task | Read first | Read next only if needed | Do not assume |
|---|---|---|---|
| Current status / shortest orientation | `PROJECT-STATE.md` §1 and §4 | Routed source for the specific question | State index has independent empirical authority |
| Research problem / scope / falsification | [Problem Definition v1](./Problem%20Definition%20v1.md) §2–3, §7, §10 | PD §8–9 | Legacy framing is current |
| Units / advantage / constructs / minimum rules | PD §4–6 | Evidence Base definitions | `specialist` implies superiority |
| Claim status / counterexample / contradiction / boundary / gap | [Evidence Adjudication v1 summary](./Evidence-Adjudication-v1.md) §4–10 | Structured workbook, then relevant Evidence IDs | A plausible explanation resolves a contradiction |
| Record IDs / provenance / benchmark metadata / verification | [Evidence Base v1.1](./Evidence-Base-v1.1.xlsx) | Adjudication workbook for current status | Repository presence establishes authority |
| ARC design / metrics / governance / stage gate | [ARC Evaluation Definition v0](../eval/ARC-Eval-Definition-v0.md) | PD minimum rules and relevant adjudicated gaps | ARC-only supports cross-domain or AGI conclusions |
| Dataset counts / Toolkit / environments / configuration / smoke test | [ARC Dataset and Toolkit Status v0](../eval/ARC-Dataset-Toolkit-Status-v0.md) | Actual code/data only when executing in the repository | Installation equals evaluator or stage validation |
| A1 implementation | ARC Eval §6–9, §13–19 | Dataset/Toolkit status and new durable implementation artifacts | Current public data fills sealed/compute TBDs |
| A2 transfer | ARC Eval §10 and §12 | Frozen A1 runs and manifests | Testing only a new best A2 system establishes transfer |
| A3 science / competition | ARC Eval §11 and §13–19 | Current official scorer/rules snapshot when added | Public development score equals private/final SOTA |
| Run interpretation | Preregistration + run manifest + evaluator output | ARC claim taxonomy and decision record | Aggregate score replaces per-task/per-environment outputs |
| Publication / external claim | Formal report + decision record | PD, adjudication, ARC claim rules | Date, unit, resources, exposure, or verification can be omitted |
| State update | Responsible authoritative source + this file | Change log and downstream routes | `PROJECT-STATE.md` can change adjudication by itself |

If a preregistration, manifest, evaluator output, report, or decision record is not in `docs/current/` or `docs/eval/`, mark it `Unavailable in project context` for GPT Chat Project work.

---

## 7. State update protocol

Update this file when any of the following occurs:

- a current authoritative document changes version or location;
- evidence/adjudication changes a claim, contradiction, boundary, gap, or decision;
- ARC Eval, official rules, evaluator, or dataset snapshot changes;
- a formal preregistration, run manifest, result, reproducibility package, or stage decision is added;
- operational substrate changes materially enough to affect routing or implementation readiness;
- a current/eval artifact is added, moved, renamed, or removed.

Every update must:

1. increment `State version` and `Last updated`;
2. identify the responsible source and whether the statement is source-stated, directly observed, inferred, or unknown;
3. update affected readiness, blockers, routes, and downstream impact;
4. add a change-log entry;
5. state empirical claim, ARC stage, and winning-hypothesis impact explicitly;
6. avoid changing empirical status here without the evidence/adjudication sequence.

---

## 8. Change log

| Date | Version | Change | Impact |
|---|---|---|---|
| 2026-08-01 | v0.1 | Established the integrated project-state index from Problem Definition v1, Evidence Base v1.1, Evidence Adjudication v1, and ARC Eval v0. | Initial index |
| 2026-08-01 | v0.2 | Aligned document topology, authority, and task routing. | No empirical adjudication change |
| 2026-08-01 | v0.3 | Removed short-lived repository/integration identity from current state and separated repository workflow from empirical state. | No empirical, ARC stage, or scope change |
| 2026-08-02 | v0.4 | Reduced the state file to a high-value record and navigation layer; moved dataset/Toolkit details to ARC Dataset and Toolkit Status v0; recorded verified A1/A2 counts, A3 installation, offline smoke, and remote discovery; made current/eval the complete GPT Chat Project routing boundary. | Operational readiness updated. Empirical claim impact: none. ARC stage impact: none. Winning-hypothesis impact: none. |
