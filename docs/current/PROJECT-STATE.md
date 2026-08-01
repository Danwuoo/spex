# PROJECT STATE

**State version:** v0.3  
**Last updated:** 2026-08-01  
**State basis:** `Problem Definition v1.md`, `Evidence-Base-v1.1.xlsx`, `Evidence-Adjudication-v1.xlsx`, `Evidence-Adjudication-v1.md`, `ARC-Eval-Definition-v0.md`  
**Evidence cutoff:** Evidence Base v1.1 / Evidence Adjudication v1；ARC external-source snapshot accessed through 2026-07-31  
**Document role:** 專案入口、狀態索引與讀取路由。它不取代任何上位定義、證據記錄、裁決或 evaluation specification。  
**Current lifecycle:** Problem definition stabilized → evidence adjudicated → ARC-specific evaluation specification drafted → ARC-AGI-1 pre-implementation setup  
**Current operational stage:** ARC-AGI-1 pre-implementation setup。這是依 ARC 執行順序與目前附件缺少 run artifacts 所作的狀態推定，不是已達成的 stage status。  
**Global experiment-design readiness:** `Not ready`（Evidence Adjudication v1）  
**ARC-specific design readiness:** `Draft for implementation`（ARC Evaluation Definition v0.1，2026-07-31）  
**Project owner / decision authority:** `TBD`  
**State maintainer:** `TBD`  

---

## 0. How to use this file

每次任務先讀本檔，再依「Task-to-source routing」載入最低必要來源。除非任務是全局審計、版本升級、contradiction adjudication、evidence-base reconstruction 或跨文件一致性檢查，否則不預設通讀全部文件。

本檔中的狀態分為三種：

- **Source-stated：** 權威文件明確記錄的內容。
- **State inference：** 由文件版本、階段順序或缺少 artifact 所推定的工作狀態；不構成 empirical claim。
- **TBD / Unknown：** 來源尚未決定、未提供或不足以支持判定。

遇到本檔與來源文件不一致時，以來源文件為準，並更新本檔；不得用本檔覆寫 evidence record、decision record 或上位 problem definition。

---

## 1. Current authoritative artifacts

| Role | Artifact | Version / status | Authority and use |
|---|---|---|---|
| Current empirical problem | [`docs/current/Problem Definition v1.md`](./Problem%20Definition%20v1.md) | v1.0 / Current project problem definition | 定義目前可由已裁決證據支持的 empirical problem、術語、scope、最低判讀規則與 falsification conditions。 |
| Record-level evidence repository | [`Evidence-Base-v1.1.xlsx`](./Evidence-Base-v1.1.xlsx) | v1.1 | 保存 Evidence、Source、Benchmark、Claim、Counterexample、Gap、Definition、Verification 與 Change records。 |
| Current claim adjudication | [`Evidence-Adjudication-v1.xlsx`](./Evidence-Adjudication-v1.xlsx) | v1 | 保存 claim、counterexample、contradiction、boundary condition、gap、problem-definition impact 與 decision log 的結構化裁決。 |
| Human-readable adjudication summary | [`Evidence-Adjudication-v1.md`](./Evidence-Adjudication-v1.md) | v1 | 提供 DR2 後的裁決摘要、claim-level interpretation、remaining gaps 與 readiness assessment。 |
| Current domain evaluation program | `ARC-Eval-Definition-v0.md` | v0.1 / Draft for implementation / 2026-07-31 | 定義 ARC-AGI-1 → 2 → 3 的研究與工程評估規格；受 Problem Definition v1 約束。 |
| Project state index | `docs/current/PROJECT-STATE.md` | v0.3 | 提供狀態與讀取路由；不具有獨立 empirical authority。 |

### 1.1 Authority resolution

不同文件負責不同種類的決定，不使用單一線性順位混合處理：

1. **研究問題、scope、術語與最低 claim rules：** `Problem Definition v1.md`。
2. **目前 claim、counterexample、contradiction、boundary condition 與 gap 的裁決狀態：** `Evidence-Adjudication-v1.xlsx`；`.md` 為摘要。
3. **Evidence_ID、Source_ID、Benchmark_ID、原始欄位與 verification provenance：** `Evidence-Base-v1.1.xlsx`。
4. **ARC 執行規格、資料治理、metrics、stage gates 與 SOTA claim taxonomy：** `ARC-Eval-Definition-v0.md`。
5. **未來 preregistration、run manifest、實驗報告與官方 evaluator output：** 只裁決其特定 run；不得無聲改寫上位 problem definition 或 evidence adjudication。
6. **歷史 Problem Definition v0、Vanta 文件及其他 legacy artifacts：** 僅作歷史經驗、先前假設、失敗案例與工程教訓；不得填補目前的 Unknown / TBD，也不得覆寫 current-project decisions。

### 1.2 Conflict handling

- 同一角色有多個版本時，優先使用明確標示為 Current、Accepted、official 或較新且已完成 decision record 的版本。
- 下位文件與上位文件衝突時，不自行調和；記錄 conflict，新增 decision record，必要時升級上位文件版本。
- 新 evidence 不能只在本檔改變 claim status；必須先進入 Evidence Base / Verification Log，再由 Evidence Adjudication 裁決。
- 合理解釋不等於 empirical resolution。未有 discriminating evidence 時，contradiction 仍維持 unresolved、measurement issue、boundary condition 或 temporal issue。

---

## 2. Executive project state

### 2.1 Current empirical position

目前可支持的問題不是「specialization 是否有效」，而是：

> model-level specialization 為何經常改善自己的 base，卻較少被可靠證明能在 broad、resource-comparable、contemporary 且跨時間的條件下維持 frontier superiority；同時，system-level、hybrid 與 formal/narrow solvers 又為何能在明確有界的工作流或問題空間中形成強優勢。

現有證據同時支持：

1. **Model-level same-backbone relative gain 是 recurring observation。**
2. **該 relative gain 不會自動成為 broad、contemporary、resource-matched frontier superiority。**
3. **System-level、hybrid 與 formal/verifier-bound specialization 可在 bounded workflow、environment 或 formal problem space 形成強優勢。**
4. **以上三種現象不矛盾，但必須按 unit、advantage type、capability construct、resources 與 time index 分開解讀。**

### 2.2 Current program decision

第一個 evaluation domain 為 **ARC benchmark series**，順序為：

1. `ARC-AGI-1`：建立可重建、可歸因、成本可見的靜態抽象推理基線。
2. `ARC-AGI-2`：測試方法是否能承受更深、多步與更高複雜度，並辨識 A1 → A2 transfer。
3. `ARC-AGI-3`：在互動式未知環境同時進行 controlled scientific evaluation 與 competition SOTA engineering。

ARC 是第一個受控案例域，不是整個研究問題。ARC-only 結果不得單獨支持跨領域 specialization scaling law、broad professional capability 或 AGI 結論。

### 2.3 Readiness summary

| Layer | Current status | Interpretation |
|---|---|---|
| Problem Definition v1 | Ready with conditions / Current | 研究問題已完成結構性拆分；仍保留 prevalence、durability、scaling、replication 與 resource matching 的未知。 |
| Formal research questions | Ready with conditions | 可依 model/system/formal、resources、durability、construct 與 scaling 分題；不得把 gaps 當前提。 |
| Competing hypothesis formation | Ready with conditions | 可建立相互競爭的機制假說，但必須保留 G0004、G0007 等 blockers。 |
| Global experiment design | Not ready | matched comparator、private coding tasks、point-in-time finance data、inference budget 與 generalization thresholds 未完成。 |
| ARC-specific evaluation specification | Draft for implementation | 已建立可工作的 domain spec，但有 10 項 implementation TBD，且尚未達 v1 acceptance criteria。 |
| ARC runs / stage achievements | Not evidenced | 目前提供的 authoritative artifacts 中沒有正式 preregistration、run manifest、official score 或 stage-completion record。 |

---

## 3. Evidence corpus snapshot

### 3.1 Evidence Base v1.1 inventory

| Record class | Count | ID range |
|---|---:|---|
| Evidence records | 65 | E0001–E0065 |
| Sources | 49 | S0001–S0049 |
| Benchmarks | 43 | B0001–B0043 |
| Claims | 22 | C0001–C0022 |
| Counterexamples | 10 | CE0001–CE0010 |
| Evidence gaps | 12 | G0001–G0012 |
| Verification records | 12 | V0001–V0012 |

### 3.2 Adjudication inventory

| Record class | Count | ID range |
|---|---:|---|
| Claim adjudications | 22 | C0001–C0022 |
| Counterexample adjudications | 10 | CE0001–CE0010 |
| Contradictions | 14 | K0001–K0014 |
| Boundary conditions | 17 | BC0001–BC0017 |
| Evidence gaps | 12 | G0001–G0012 |
| Problem-definition impacts | 14 | PDI0001–PDI0014 |
| Decisions | 14 | D0001–D0014 |

### 3.3 Current claim-status distribution

| Status | Count |
|---|---:|
| Supported | 9 |
| Conditionally supported | 5 |
| Partially supported | 2 |
| Indeterminate | 3 |
| Contradicted | 1 |
| Unsupported | 1 |
| Needs split | 1 |

Confidence distribution：`High 13`、`Medium 8`、`Low 1`。

### 3.4 DR2 adjudication delta

- 24 筆既有 Evidence_ID 有實質更新。
- 新增 10 筆 experiment-level records：E0056–E0065。
- 7 筆既有 claims 發生狀態變更。
- 新增 C0021（evaluation realism）與 C0022（frontier drift）。
- 8 筆 contradiction records 改變或明顯縮窄解讀。
- 12 個 gaps 中：0 完全解決、2 部分解決、3 縮窄、5 仍開放、2 重要性上升。
- 原先最可能構成直接衝突的 K0007、K0009、K0010、K0013，沒有任何一筆被 evidence 完全解決。

---

## 4. Stable empirical decisions

### 4.1 Supported

1. **Same-backbone relative gain recurring。** Model-level specialization 經常改善 adapted base 在 target task 或 benchmark family 的表現。
2. **Unit split mandatory。** Model-level、system-level、hybrid、formal/narrow solver 不可聚合為單一 specialist/generalist 結論。
3. **Relative gain ≠ frontier superiority。** 兩者使用不同 comparator，可同時成立。
4. **Benchmark score 是 partial proxy。** Leaderboard dominance 不能單獨證明 broad domain expertise 或 professional workflow capability。
5. **Frontier claims 必須 time-indexed。** Cross-generation comparison 只能支持歷史 snapshot。
6. **Tools、retrieval、access、environment、context 與 inference resources 是 material confounders。**
7. **Universal generalist dominance 已被 counterexamples 否定。**
8. **Finance temporal control 與 public benchmark contamination 會改變 ranking 的可解釋性。**
9. **Specialist/generalist 二元標籤在文獻中 operationally unstable；必須記錄 mechanism 與 system boundary。**

### 4.2 Conditionally supported

1. Model-level same-backbone gains 經常不會自動轉化為 contemporary frontier superiority；實際 prevalence 仍未知。
2. Benchmark-local model-level frontier superiority 可以發生；SaulLM 是最可信案例，MMedIns 仍是 author-program、partially matched evidence。
3. System-level specialization 可在 bounded workflows/environments 中超過 frontier agents 或 experts。
4. Formal/verifier-bound solver superiority 可非常強，但受 formalization、verifier、search 與 test-time compute 限制。
5. 最強 specialist wins 在目前 corpus 中多半 bounded，而非已證明 broad and durable。
6. 後續 frontier generations 有時會超過既有 specialist milestones；這支持 frontier drift，不支持 specialist capability 必然衰退。

### 4.3 Unsupported / contradicted / indeterminate

- **Contradicted：**「generalist dominance 是 universal cross-domain law」。
- **Unsupported：**「specialization 是獨立於 total compute、model scale 與 system resources 的跨領域 scaling axis」。
- **Needs split：**「strong-backbone、high-resource specialization 可以達到或超越 domain frontier」必須拆成 model-level、system-level、hybrid、formal units。
- **Indeterminate：**
  - evaluation realism 是否一致有利於 specialists；
  - frontier post-training / test-time compute 是否是 specialists 落後的 causal explanation；
  - 工具、retrieval、search、verification 等因素的跨案例 universal causal effect。

---

## 5. Mandatory analytical taxonomy

任何 evidence record、run、comparison、counterexample 或 public claim，至少必須標記以下四組欄位。

### 5.1 Evaluation unit

| Code | Unit | Definition | Allowed claim |
|---|---|---|---|
| `G` | Generalist baseline | 未對 ARC 或 target distribution 做同等專門化的 model/system configuration | 當期未專門化 baseline |
| `M` | Model specialist | 主要介入位於 weights：continued training、finetuning、LoRA、RL、test-time parameter update 等 | same-backbone model-level gain；條件滿足時才可討論 model-level frontier superiority |
| `S` | System specialist | weights 固定；主要介入為 prompt、RAG、tools、DSL、search、memory、verifier、routing、agent scaffold、environment | fixed-backbone system gain 或 bounded workflow outcome |
| `H` | Hybrid specialist | weights 與 system stack 同時專門化，貢獻無法乾淨拆分 | configuration-level outcome |
| `N` | Narrow / formal solver | 固定 DSL、formal language、exact verifier、手工 primitive 或受限搜尋空間 | 該窄問題空間中的 solver superiority |

Unit 必須對稱。`S` 或 `H` 擊敗裸 `G` 只能稱 configuration advantage，不能歸因於 weights。

### 5.2 Advantage type

1. **Same-backbone relative gain**
2. **Contemporary frontier superiority**
3. **Persistent superiority**
4. **Configuration-level superiority**
5. **Cost / efficiency advantage**

一種 advantage 成立不得自動推出其他種類成立。

### 5.3 Capability construct

1. **Benchmark proxy**
2. **Broad domain capability**
3. **Professional workflow capability**
4. **Formalized / bounded task capability**

不同 construct 的 ranking 不構成直接 contradiction，也不能互相替代。

### 5.4 Generalization and temporal status

分別記錄：

- held-out task
- OOD task family / environment / institution / jurisdiction
- temporal shift
- cross-version transfer
- independent replication
- single-setting stability
- persistence across frontier checkpoints
- contamination / exposure status

沒有 evidence 時標記 `Unknown / not evaluated`，不得自動標為成功或失敗。

---

## 6. Minimum comparator and claim fields

每一個 superiority、frontier、SOTA、efficiency 或 generalization claim 至少需要：

- evaluation unit；
- specialist exact configuration；
- comparator exact configuration；
- model/system version或 snapshot；
- evaluation date；
- benchmark / evaluator version；
- capability construct；
- own-base、public generalist 或 contemporary frontier comparator class；
- prompt / policy / scaffold；
- tools、retrieval、database、environment 與 context access；
- training data / specialization data / post-training stages；
- inference token、call、rollout、search、wall-clock、ensemble 與 retry budget；
- public / sealed / semi-private / private status；
- contamination / exposure status；
- resource parity；
- temporal status；
- generalization / replication status；
- 最窄可支持 proposition；
- 明確禁止的 extrapolation。

缺少 exact version、date、unit 或 system boundary 時，結果必須降為 `historical`、`partially matched`、`system-configuration advantage`、`single-setting`、`public-exposed` 或 `not interpretable`。

---

## 7. Current counterexample map

| ID | System | Current unit | Current strength | Exact scope | Key limitation |
|---|---|---|---|---|---|
| CE0001 | SaulLM | Model-level | Strong | 可信的 legal benchmark-level counterexample | Exact GPT-4 snapshot 不明；缺 broad legal workflow 與 independent replication |
| CE0002 | MMedIns-Llama 3 | Model-level | Moderate | same-program、benchmark-local medical win | Author-program benchmark/data ownership、partial matching、無獨立當代 replication |
| CE0003 | FinTral-DPO-T&R | Hybrid / system-level | Boundary-condition only | author-owned finance suite 的部分 task-family system win | Tools、retrieval、multimodality 與 asymmetric resources bundled；不能隔離 model effect |
| CE0004 | PaperQA2 | System-level | Strong | bounded scientific literature workflow | Agentic RAG、多模型呼叫、search/rerank/summarization integral；缺 matched-budget attribution |
| CE0005 | Aviary | System / environment-bound | Moderate | designed scientific environments 內的 system advantage | Environment-external transfer、scaffold parity 與 inference-budget parity 未知 |
| CE0006 | AlphaProof / AlphaGeometry 2 | Formal/verifier-bound solver | Boundary-condition only | formalized exact-verifier olympiad problem space | Manual formalization、search、multi-day compute；非 matched natural-language model comparison |
| CE0007 | Gemini Deep Think | Hybrid general capability system | Not interpretable as specialist counterexample | later frontier / temporal context | 非 specialist model-level comparison；system details 與 compute 不完整 |
| CE0008 | BERTimbau-LoRA | Narrow task-specific solver | Moderate | narrow Brazilian legal classification | 無 broad/OOD legal evidence；非當代 frontier workflow comparison |
| CE0009 | Code Llama-Python 7B | Model-level | Moderate | HumanEval / MBPP narrow code generation | 低 workflow fidelity、可能 exposure、無 repo-level engineering evidence |
| CE0010 | Nature Medicine 2026 clinical-tools comparison | System-level comparison | Boundary/generalist-dominance case | contemporary benchmark + real physician-query comparison | Browser-only specialist access、hidden resource parity、非 patient-outcome evidence |

Counterexample 必須同時寫明「反駁的精確命題」與「未反駁的命題」。任何一筆 counterexample 都不得單獨支持跨 unit、跨 construct 或跨時間的普遍結論。

---

## 8. Contradiction state

| ID | Current classification | Current interpretation / consequence |
|---|---|---|
| K0001 | Resolved by conditioning | same-backbone gain 與 frontier superiority 是不同 outcome。 |
| K0002 | Resolved by conditioning | system/formal wins 與 model-level scarcity 屬不同 units。 |
| K0003 | Measurement issue | workflow realism 增加 system components 的重要性，但沒有一致 ranking 方向。 |
| K0004 | Boundary condition | narrow wins 與 broad weakness 可在 task-scope conditioning 下並存。 |
| K0005 | Temporal / frontier drift | ranking reversal 多為 time-indexed frontier drift，不等於 capability decay。 |
| K0006 | Resolved by conditioning | 無 mechanism 與 system-boundary fields 時，binary specialist/generalist labels 不可辯護。 |
| K0007 | Weakened as contradiction | MMedIns benchmark-local model result 與 Nature Medicine deployed-tool evaluation 使用不同 unit/construct；仍需 shared external replication。 |
| K0008 | Boundary condition | SaulLM 反駁 universal legal benchmark dominance；broad workflow leadership 仍 mixed。 |
| K0009 | Measurement issue | finance ranking 受 system resources 與 temporal controls 主導；缺 matched contradiction。 |
| K0010 | Temporal / frontier drift | SWE-RL same-backbone historical gain 保留；later frontier progress + contamination 阻止 direct contradiction。 |
| K0011 | Measurement issue | science/clinical workflow evidence 的方向差異主要來自 unit/construct。 |
| K0012 | Boundary condition | tools/verifier/search 是部分 workflow/formal tasks 的強 moderator，不是所有 benchmark-local model wins 的必要條件。 |
| K0013 | Still unresolved | MMedIns、SaulLM、FinTral 等 author-linked cases 仍缺 independent replication。 |
| K0014 | Measurement issue | temporal leakage、access asymmetry、contamination 限定 ranking，而非提供相反 capability result。 |

---

## 9. Boundary conditions after DR2

### 9.1 Strong boundary conditions

- `BC0001` Specialization level / unit split
- `BC0004` Comparator generation / time-indexed frontier
- `BC0008` Benchmark ownership and independence
- `BC0009` Finance temporal control
- `BC0010` Benchmark contamination control
- `BC0011` Software task scope
- `BC0015` Formalization and verification

### 9.2 Experimentally supported moderator

- `BC0006` Tool and retrieval parity：FinRetrieval 顯示相同模型的 structured API 與 web search 可產生巨大差異。

### 9.3 Suggestive moderators

- `BC0002` Task-distribution width
- `BC0005` Backbone strength
- `BC0007` Inference compute and search budget
- `BC0012` Legal scope
- `BC0016` Specialization intensity / diminishing returns / saturation

### 9.4 Descriptive or indeterminate

- `BC0003` Evaluation fidelity / workflow realism
- `BC0013` Medical evaluation construct
- `BC0014` Generalization distance
- `BC0017` Interface / access parity

目前沒有足夠證據把任何跨案例 boundary condition 升級為普遍 causal law。

---

## 10. Evidence gaps and resolution queue

| Gap | Category | Current status | Priority | What remains unknown | Required resolution |
|---|---|---|---|---|---|
| G0001 Contemporary matched specialist/generalist comparisons | Problem-definition blocker | Still open | Critical | matched contemporary model-level comparisons scarce | matched contemporary evaluation |
| G0002 Matched tools/retrieval/context/environment access | Problem-definition blocker | Narrowed | Critical | matched access across specialist/generalist systems missing | matched-access factorial study |
| G0003 Matched inference compute/search budget | Experiment-design gap | Still open | Critical | token、rollout、wall-clock、search budgets unmatched across systems | matched-compute cost-quality curve |
| G0004 Controlled specialization scaling | Hypothesis blocker | Partially resolved | Critical | independence from total compute、cross-domain replication、frontier extrapolation | cross-domain controlled scaling |
| G0005 Benchmark versus professional workflow construct | Problem-definition blocker | Narrowed | Critical | paired same-system benchmark/workflow evaluations rare | paired construct-validity evaluation |
| G0006 OOD / cross-task / longitudinal durability | Problem-definition blocker | Still open | High | independent cross-task and cross-time durability of major wins | OOD + longitudinal replication |
| G0007 Model/system component ablations | Hypothesis blocker | Still open | Critical | PaperQA2、Aviary、FinTral、formal solver factorial attribution | fixed-backbone factorial ablation |
| G0008 Benchmark contamination audits | Experiment-design gap | Made more important | Critical | fresh private coding rankings and per-model contamination | fresh/private/post-cutoff benchmark |
| G0009 Point-in-time finance controls | Experiment-design gap | Narrowed | Critical | matched point-in-time specialist/generalist comparison | point-in-time matched-access benchmark |
| G0010 Primary-source extraction | Problem-definition blocker | Partially resolved | High | remaining DR1 corpus and exact bibliography incomplete | targeted primary-source extraction |
| G0011 Proprietary comparator metadata | Problem-definition blocker | Still open | High | exact snapshots、prompts、inference budgets unknown | versioned reproducible API evaluation |
| G0012 Independent replication of author-built benchmarks | Problem-definition blocker | Made more important | High | independent contemporary MMedIns、SaulLM、FinTral replication | blinded external replication |

### 10.1 Highest-priority evidence work

1. Clean contemporary model-level comparisons with matched comparator generation.
2. Matched tool/access/context/environment and matched inference/search budgets.
3. MMedIns independent contemporary external replication.
4. SaulLM broader legal-workflow replication.
5. PaperQA2 / Aviary matched-budget component ablations.
6. Fresh private/post-cutoff coding tasks.
7. Matched specialization-intensity curves across domains.
8. OOD and longitudinal durability.
9. Point-in-time finance evaluation.
10. Remaining primary-source and comparator-metadata extraction.

---

## 11. Current unresolved research questions

1. Same-backbone relative gain 在何種條件下能轉化為 contemporary frontier superiority，而非只縮小差距？
2. 當 scale、information access、tools、context、scaffold 與 inference budget 可比較時，現有 ranking 會保留多少？
3. Model-level、system-level 與 hybrid specialization 的優勢分別落在哪些 capability constructs？
4. Benchmark proxy、broad domain capability 與 professional workflow capability 是否存在可重複的 ranking divergence？
5. Specialist wins 在 held-out tasks、OOD distributions、不同制度/語言、independent replication 與 later frontier checkpoints 中可維持多少？
6. Formal/verifier-bound 與 narrow solvers 的結果可在何種邊界內視為 specialization evidence？
7. 現有 local specialization curves 是設定內收益與 saturation，還是可跨領域重現的獨立 scaling effect？
8. Contamination、temporal leakage、author-owned evaluation 與 proprietary metadata 缺失，對 prevalence 判斷造成多大偏差？

以上是未知空間，不是已選定的 formal hypotheses。

---

## 12. Decision register

| Decision | Current decision |
|---|---|
| D0001 | MMedIns 分類為 benchmark-local、partially matched model-level win。 |
| D0002 | Nature Medicine 2026 clinical-tools comparison 升級為 contemporary generalist-dominance boundary case。 |
| D0003 | SaulLM 保留為強 legal benchmark counterexample；unsupported exact GPT-4 date 移除。 |
| D0004 | FinTral 重分類為 asymmetric-resource hybrid/system evidence。 |
| D0005 | SWE-RL frontier comparison 改為 historical near-parity；same-backbone gain 保留。 |
| D0006 | PaperQA2 分類為 scientific workflow/system-level specialization。 |
| D0007 | Aviary 分類為 bounded environment specialization。 |
| D0008 | AlphaProof/AlphaGeometry 分離為 formal/verifier-bound solver class。 |
| D0009 | FinRetrieval 作為 system-resource moderator 的直接 evidence。 |
| D0010 | Look-Ahead-Bench 主要作為 temporal-validity evidence。 |
| D0011 | 拒絕 specialization 是 independent scaling axis 的強命題；local effects 保留。 |
| D0012 | Workflow-realism 的 ranking direction 明確維持 indeterminate。 |
| D0013 | 每一個 frontier-superiority claim 強制 time-indexed。 |
| D0014 | Generalization 分成 held-out、OOD、temporal shift、independent replication，不以 task count 推導 breadth。 |

---

## 13. Falsification triggers for the current framing

目前 empirical framing 必須在以下 evidence 出現時重大修訂：

- **F1：** 跨多個獨立 domains/model families 顯示 model-level specialization 對 own base 並無 recurring positive gain。
- **F2：** 多個獨立 domains 出現 contemporary、unit-matched、resource-visible comparisons，顯示 model-level specialists 經常在 broad domain/workflow capability 超越最強 generalists，且可獨立重現。
- **F3：** 目前最強 model/system/formal wins 在 independent OOD tasks、不同 environments/constructs 與 later frontier checkpoints 持續保持。
- **F4：** Matched component evidence 顯示 PaperQA2、Aviary、FinTral 等主要優勢可由 specialized weights alone 重現。
- **F5：** Paired independent evaluations 持續顯示 benchmark proxy 與 professional workflow capability 測量相同 construct 並產生一致 ranking。
- **F6：** Specialist advantages 在 materially stronger later frontier generations 仍持續保持，或歷史 ranking 變動主要由 benchmark invalidity 而非 comparator progression 解釋。

反駁必須針對相同 unit、construct 與 superiority type；單一 benchmark win 或 formal solver milestone 不足以反駁 model-level transition-gap framing。

---

## 14. ARC evaluation program state

### 14.1 Program objectives

**Scientific objective：**

> 在版本固定、資源可見且比較單位對稱的條件下，測量 ARC specialization 的增益、成本、component attribution、cross-version transfer 與 persistence。

**Engineering objective：**

> 建立可逐步擴展到 ARC-AGI-3 competition 的 solver/agent platform，最終取得當期有效規則下最高可驗證 private-evaluation score。

兩種 success 必須分開：

- `Research-qualified`
- `Benchmark-complete`

Public high score 只能標為 `public-benchmark result`；沒有 private/semi-private support 時，不得標為 verified completion。

### 14.2 Current ARC stage status

| Stage | Status in provided artifacts | Notes |
|---|---|---|
| A1-Research-Qualified | Not evidenced | 尚無 frozen baseline、paired result、ablation、rebuild record 或 run manifest。 |
| A1-Public-Complete | Not evidenced | 尚無 public score record。 |
| A1-Verified-Complete | Not evidenced | 尚無 official/sealed score record。 |
| A2-Research-Qualified | Not evidenced | 尚無 A1 frozen port / A1-port / A2-adapted comparison。 |
| A2-Public-Complete | Not evidenced | 尚無 score record。 |
| A2-Verified-Complete | Not evidenced | 尚無 private evaluation record。 |
| A3-Research-Qualified | Not evidenced | 尚無 fixed-backbone component ablation 或 official scorer output。 |
| A3-Competition-Ready | Not evidenced | 尚無 official runtime/container validation。 |
| A3-SOTA | Not evidenced | 尚無 official private leaderboard result。 |
| A3-Solved | Not evidenced | 尚無 official private 100% result。 |

`Not evidenced` 不等同已確認未開始；僅代表目前權威附件中沒有支持該狀態的 artifact。

### 14.3 A1 baseline ladder

A1 正式工作至少需要：

1. `G0` direct generalist baseline
2. `S1` same model + structured prompting / representation
3. `S2` same model + executable transformation / program synthesis
4. `S3` same model + search / verification
5. `M1` ARC-adapted weights without specialized scaffold
6. `H1` best adapted weights + best system stack

若第一輪不做 weight adaptation，`M1` 可暫缺，但不得對 model-level specialization 下結論。

### 14.4 Required modes

- **Science Mode：** attribution、same-backbone comparison、cost-quality curve、generalization。
- **Open Engineering Mode：** 探索高分 system；結果要形成 scientific claim，必須回到 fixed-backbone、matched-resource ablation。
- **Official / Competition Mode：** 依當次 official evaluator、private split、runtime、network、hardware、submission 與 disclosure rules。

### 14.5 Data-governance state

ARC Eval v0 已定義：

- Training tier
- Development tier
- Sealed validation tier
- Public evaluation tier
- Semi-private / private tier
- Evaluation firewall
- Contamination statuses

但以下 implementation artifacts 尚未提供：

- A1 sealed split specification
- custodian / access-control record
- data manifests and hashes
- contamination log
- official evaluator snapshot
- development-query ledger

### 14.6 ARC metrics and reporting rules

A1/A2 primary metrics：

- `Exact@1`
- `Exact@K_native`
- cost-normalized accuracy

Required diagnostics：

- pixel accuracy
- output-shape accuracy
- candidate-generation ceiling
- candidate-selection accuracy
- train-pair consistency
- invalid-output / timeout / OOM rate
- first-attempt solve / salvage rate
- per-task compute distribution

Statistical requirements：

- deterministic solver：至少一個 full frozen run + per-task outputs
- stochastic solver：預設 5 seeds；高成本可降到 3 但必須標記
- 95% CI
- paired bootstrap 或 McNemar
- exploratory 與 confirmatory 分開
- 不以 best seed 作 primary scientific result

### 14.7 Required run manifest fields

每個 formal run 至少需要：

```yaml
run_id:
benchmark:
benchmark_snapshot:
evaluator_version:
evaluation_date:
unit:
model_provider:
model_id:
model_snapshot:
weights_hash:
prompt_policy_hash:
solver_commit:
training_data_manifest:
synthetic_data_manifest:
tools:
verifier:
memory_policy:
search_policy:
num_attempts:
max_input_tokens:
max_output_tokens:
max_model_calls_per_task:
max_rollouts_per_task:
wall_clock_limit:
hardware:
network_access:
random_seed:
estimated_cost:
contamination_status:
result_status:
```

缺 model snapshot、evaluator version、resource fields 或 dataset status 的 run，不得支持 frontier、SOTA、efficiency 或 attribution claim。

---

## 15. ARC v0 unresolved implementation decisions

以下全部維持 `TBD`，不得以推測填入：

1. ARC-AGI-1 sealed validation 的具體切分與保管人。
2. A1/A2 Low、Matched、High compute 的數值。
3. Stochastic runs 的最終 seed 數與成本上限。
4. Private / semi-private evaluation access path。
5. ARC-AGI-3 competition scorer 的 per-level cap discrepancy。
6. ARC-AGI-3 Kaggle runtime、hardware、submission quota 的 pinned rule snapshot。
7. ARC-AGI-3 failure taxonomy annotation protocol。
8. 第一輪是否納入 model-level adaptation，或先做 system-level specialization。
9. Synthetic task/environment generator leakage audit。
10. 對外 SOTA publication 的 independent reproduction requirement。

### 15.1 Additional project-level TBDs

以下資訊未出現在目前 authoritative artifacts：

- project owner / final decision authority
- state maintainer
- implementation code location
- experiment registry location
- artifact storage and retention policy
- sealed-data custodian
- compute budget and procurement boundary
- approved model/API list
- security and secrets handling
- publication/release approval process
- incident and contamination-response owner

---

## 16. ARC Eval v1 acceptance gate

ARC Evaluation Definition v0 可升級為 v1，至少需要：

1. A1 canonical repository、evaluator 與 data manifests 凍結。
2. A1 baseline ladder 至少執行一次。
3. Run manifest schema 由實際 pipeline 驗證。
4. Public / sealed / private data governance 落地。
5. Compute tiers 由 baseline calibration 數據定義。
6. A2 porting test 可執行。
7. A3 official scorer discrepancy 由 scorer source 核對。
8. Competition rules snapshot 保存。
9. Claim taxonomy 至少在一份正式 experiment report 中使用。
10. 所有重大偏差進入 decision log。

---

## 17. Source-derived next-action sequence

以下是由 ARC stage criteria 與 v1 acceptance criteria推導的最短實作順序，不代表已核准的 resource plan：

### Phase A — Freeze the A1 evaluation substrate

1. Pin A1 canonical repository commit / release。
2. Pin official parser、scorer、submission format 與 evaluator version。
3. 建立 data manifest、hashes 與 contamination-status registry。
4. 決定 sealed-validation split、custodian、access policy 與 evaluation firewall。
5. 建立 immutable rule snapshot。

### Phase B — Establish the run and cost infrastructure

6. 實作 machine-readable run manifest。
7. 記錄 model snapshot、prompt/policy hash、solver commit、tools、search、hardware、network 與 cost。
8. 校準 Low / Matched / High compute tiers。
9. 決定 stochastic seed policy 與 cost cap。
10. 建立 per-task outputs、failed-run 與 deviation logging。

### Phase C — Execute the A1 baseline ladder

11. 先執行 frozen `G0`。
12. 執行 `S1 → S2 → S3`，固定 backbone 並逐步增加 system components。
13. 進行至少一個 key component ablation。
14. 若納入 weights adaptation，執行 `M1`，再測 `H1`。
15. 產生 paired comparison、CI、cost-quality curve 與 contamination disclosure。

### Phase D — Gate the result

16. 依 A1-Research-Qualified criteria 建立 formal decision record。
17. 將 allowed claim 與 prohibited claim 寫入 experiment report。
18. 驗證 clean checkout reproducibility。
19. 若無 private/sealed evaluation，只標 `public-benchmark result`。
20. 完成後才進入 A2 frozen-port / transfer-first comparison。

---

## 18. Active work queue

### 18.1 Immediate blockers

| Work item | Status | Blocks |
|---|---|---|
| A1 repository/evaluator/data snapshot freeze | Open | 所有正式 A1 runs |
| Sealed validation design and custodian | TBD | Generalization / verified completion |
| Compute-tier calibration | TBD | Matched-resource claims |
| Run manifest implementation | Not evidenced | Reproducibility / attribution |
| Baseline `G0` execution | Not evidenced | A1 baseline ladder |
| First key ablation | Not evidenced | A1-Research-Qualified |
| Private/semi-private access path | TBD | Verified benchmark completion |
| Model-level adaptation scope | TBD | `M1` and model-level claim eligibility |

### 18.2 Recommended first decision record

第一筆 ARC implementation decision 應回答：

> 第一輪 A1 是否只做 fixed-backbone system specialization，或同時納入 model-level adaptation？

Decision record 至少需要：

- Decision_ID
- Benchmark
- Question
- chosen scope
- rejected alternatives
- resource impact
- claim impact
- reversible-if condition
- owner
- date

本檔不替該決定選擇答案。

---

## 19. Output and claim rules

### 19.1 Safe language

可使用：

- same-backbone gain
- benchmark-local win
- historical comparison
- contemporary time-indexed comparison
- bounded system superiority
- formal/verifier-bound solver result
- configuration-level outcome
- public-exposed result
- private/semi-private verified result
- conditionally supported
- not evaluated / unknown
- partially matched
- evidence does not isolate the mechanism

### 19.2 Prohibited or downgraded language

除非有相應 evidence，不得使用：

- universal generalist dominance
- broad domain superiority
- persistent frontier superiority
- weights caused the full system gain
- generalizable / stable / repeatable（無明確 evidence dimension）
- benchmark solved（僅 public score）
- final SOTA（僅 public leaderboard）
- verified（僅 community result）
- AGI capability（僅 ARC result）
- independent scaling law（僅 local curves）
- contradiction resolved（只有 plausible explanation）
- contemporary frontier（缺 snapshot/date）

### 19.3 ARC-specific claim taxonomy

- `Public-dev best`
- `Community result`
- `Competition public-LB`
- `Competition private-LB`
- `Verified generalist`
- `Scientific ablation`

使用「SOTA」時必須同時包含：

- leaderboard type
- benchmark / competition year
- evaluation date
- public / private
- system unit
- scorer version
- cost / compute boundary
- verified status

---

## 20. Task-to-source routing

| Task | Read first | Read next only if needed | Do not assume |
|---|---|---|---|
| 目前研究問題 / shortest statement | `PROJECT-STATE.md` §2 + `Problem Definition v1` §2–3 | PD §8–10 | 不從 legacy 文件重建問題 |
| 術語 / unit / advantage / capability construct | PD §4–6 | Evidence Base `Definitions`, `Specialization_Taxonomy` | `specialist` 標籤本身不代表 superiority |
| Claim status | Adjudication `Claim_Adjudication` | Evidence Base `Claims`, `Evidence_Records`, `Verification_Log` | 不以單篇 paper 改寫 current status |
| Counterexample scope | Adjudication `Counterexample_Adjudication` | Evidence Base `Counterexamples`, relevant Evidence_IDs | 不把一個反例外推到其他 proposition |
| Contradiction | Adjudication `Contradiction_Adjudication` | relevant Evidence_IDs + Decision_Log | plausible explanation 不等於 resolution |
| Boundary condition / moderator | Adjudication `Boundary_Conditions` | Verification_Log / primary Evidence_IDs | moderator 不等於 universal causal law |
| Evidence gap / research priority | Adjudication `Evidence_Gaps` | Evidence Base `Evidence_Gaps` | partial resolution 不等於 closed |
| 問題定義版本修改 | PD + `Problem_Definition_Impact` | Claim/Gap/Decision records | 下位文件不得無聲改寫 PD |
| ARC experiment design | ARC Eval Definition | PD minimum rules + relevant gaps | ARC-only 不等於 cross-domain conclusion |
| A1 implementation | ARC §6–9、§13–17 | official repo/evaluator/rule snapshot | 不以目前文件填補 compute/sealed-data TBD |
| A2 transfer | ARC §10、§12 | A1 frozen runs and manifests | 不直接只測全新最佳 system |
| A3 science / competition | ARC §11、§13–17 | current official scorer and competition rules | public-LB 不等於 final/private SOTA |
| Run interpretation | preregistration + run manifest + evaluator output | ARC claim taxonomy + Decision Log | aggregate score 無法替代 per-task outputs |
| Publication / external claim | formal report + Decision Log | PD/Adjudication/ARC claim rules | 不省略 date、unit、resources、verification |
| Research provenance / earlier synthesis | Current artifact 的 evidence-basis section | `docs/research/round-*`；必要時再查 `docs/archive/*` | research / archive 文件不得直接改變 current claim status |
| 全局版本升級 | 所有 current authoritative artifacts | Change_Log + source provenance | 不覆寫歷史版本 |

---

## 21. Required project artifacts not yet evidenced

在開始可裁決的 ARC implementation 前，應建立或定位下列 artifacts：

- `ARC-A1-DATA-MANIFEST.yaml`
- `ARC-A1-EVALUATOR-SNAPSHOT.md`
- `ARC-A1-SEALED-VALIDATION-PROTOCOL.md`
- `ARC-COMPUTE-TIERS-v0.md`
- `RUN-MANIFEST-SCHEMA.yaml`
- `EXPERIMENT-REGISTRY.csv` 或等價系統
- `A1-BASELINE-PREREGISTRATION.md`
- `A1-G0-RUN-MANIFEST.yaml`
- `A1-BASELINE-REPORT.md`
- `ARC-DECISION-LOG.csv` 或等價結構化紀錄
- dependency lock / container definition
- per-task output archive
- cost ledger
- contamination and deviation log

上述檔名是建議性 artifact names，不是來源文件已指定的固定命名。

---

## 22. State update protocol

更新本檔的必要觸發事件：

1. Problem Definition 新版本成為 Current。
2. Evidence Base 新增或更正 Evidence_ID / Source_ID / Benchmark_ID。
3. Evidence Adjudication 改變 claim、counterexample、contradiction、boundary condition 或 gap status。
4. 新 decision record 產生 downstream impact。
5. ARC Eval Definition 升版或 official rule snapshot 改變。
6. A1/A2/A3 stage status 發生變化。
7. 新 preregistration、run manifest、official score 或 reproducibility package 完成。
8. Contamination、leakage、scorer discrepancy 或 resource asymmetry 被發現。
9. External frontier update 使既有 contemporary claim 轉為 historical。
10. Public statement / publication 被核准。
11. Current artifacts 被新增、移動、重新命名或移除。

每次更新必須：

- 修改 `Last updated` 與 `State version`；
- 更新 authoritative artifact table；
- 更新受影響的 status、gap、decision、stage 與 next action；
- 在 Change Log 新增一列；
- 不刪除歷史狀態，必要時連結 superseded state；
- 明確標記 source-stated、inference、Unknown / TBD；
- 若只更新本檔但未更新上位 source，不能改變 empirical adjudication。

---

## 23. Change log

| Date | State version | Change | Basis | Affected sections |
|---|---|---|---|---|
| 2026-08-01 | v0.1 | 建立完整專案狀態索引；整合 Problem Definition v1、Evidence Base v1.1、Evidence Adjudication v1 與 ARC Eval Definition v0。 | Current authoritative artifacts | All |
| 2026-08-01 | v0.2 | 對齊 `spex/docs` repository topology；pin `main` snapshot；驗證四份 current attachments 與 repo blobs 一致；補入 current/research/archive roles、artifact integration gap、正確路徑與 repository-specific routing。未改變 empirical claim adjudication。 | `Danwuoo/spex@676dbdfd4856cf373349afe0106730b1a58fb42f` + v0.1 state basis | Metadata、§0–2、§15、§18、§20–24 |
| 2026-08-01 | v0.3 | 將短期 repository snapshot、commit/blob identity 與 integration tracking 移出 PROJECT STATE；repository/Codex Work mode 規則改由 root `AGENTS.md` 管理。未改變 empirical claim adjudication、ARC stage status 或 research scope。 | Repository operating-model decision | Metadata、§0–2、§15、§18、§20–24 |

---

## 24. Current one-paragraph operational statement

> 本專案目前已完成 empirical problem 的分層定義與 DR2 evidence adjudication，並將第一個受控 evaluation domain 定為 ARC-AGI-1 → ARC-AGI-2 → ARC-AGI-3。現階段最合理的工作狀態是 ARC-AGI-1 pre-implementation setup：先凍結 canonical repository、evaluator、data governance、compute tiers 與 run manifest，再建立 fixed-backbone baseline ladder、component ablations、cost-quality curves 與 reproducibility package。任何結果都必須依 model/system/formal unit、capability construct、resource parity、data exposure、evaluator snapshot、private verification 與 time index 分級解讀；目前沒有來源支持任何 ARC stage 已達成，也不應選擇 winning hypothesis 或外推 cross-domain/AGI 結論。Repository 與 Codex Work mode 操作規則由 root `AGENTS.md` 管理。
