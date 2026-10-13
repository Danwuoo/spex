# spex

spex 研究如何公平比較專門化與通用模型／系統，並以 ARC-AGI-1 建立第一套本地評估工程。Repository 包含研究問題、文獻證據與裁決工件，以及 strict task/prediction contracts、local-reference evaluator、run manifests、成本紀錄和 provider-independent G0/S1 介面。

目前尚未設定或呼叫真實模型，也沒有正式 ARC benchmark 結果。完整狀態與來源路由見 [PROJECT-STATE](docs/current/PROJECT-STATE.md)。其中 Stage 2 acceptance 指開發用工程基礎，不代表研究 stage 或模型優勢已成立。

## 兩條閱讀路線

| 路線 | 入口 | 內容 |
| --- | --- | --- |
| 研究問題 | [Problem Definition v1](docs/current/Problem%20Definition%20v1.md) | 區分 generalist、model specialist、system specialist、hybrid 與 narrow/formal solver；拆開同 backbone 改善、frontier 優勢與持續優勢。 |
| 證據與裁決 | [Evidence Adjudication 摘要](docs/current/Evidence-Adjudication-v1.md)、[Evidence Base](docs/current/Evidence-Base-v1.1.xlsx)、[Adjudication workbook](docs/current/Evidence-Adjudication-v1.xlsx) | 來源、反例、限制與主張狀態。精確 record-level 欄位以 workbook 為準；第三方文獻結果不是本庫自行訓練取得的結果。 |
| 評估工程 | [Evaluator Core](docs/eval/ARC-AGI-1-Evaluator-Core-v0.md) → [Run / Artifact Substrate](docs/eval/ARC-AGI-1-Run-Artifact-Substrate-v0.md) → [G0/S1 Development](docs/eval/ARC-AGI-1-G0-S1-Development-v0.md) | 已實作的評分、失敗／成本紀錄、resume 與配對介面。 |

## 原碼導覽

```text
task / solver view → model adapter → prediction contract
                 → evaluator → run artifacts / resource ledger
```

| 入口 | 主要內容 |
| --- | --- |
| [domain/arc_a1.py](src/spex_arc/domain/arc_a1.py) | `Task.solver_view` 僅提供 test input；parser 保留結構化失敗。 |
| [evaluator/arc_a1.py](src/spex_arc/evaluator/arc_a1.py) | Evaluator identity、`score_task`、submission serialization 與 exact scoring。 |
| [runner/arc_a1.py](src/spex_arc/runner/arc_a1.py) | `RunManifest`、atomic artifact bundle、terminal task、resume 與資源紀錄。 |
| [solvers/arc_a1.py](src/spex_arc/solvers/arc_a1.py)、[baselines/arc_a1.py](src/spex_arc/baselines/arc_a1.py) | `ModelAdapter.prepare/complete`、request reservation／settlement、配對條件與 calibration proposal。 |
| [tests/](tests/) | Synthetic／replay fixtures、錯誤處理與重新啟動語意。 |

## 最小離線檢查

從 repository 根目錄使用 Python 與 Git 執行：

```sh
python -B -m unittest discover -s tests -p 'test_*.py' -v
```

既有 fixture tests 使用 Python 標準函式庫，在系統臨時目錄建立資料及 run artifacts，不呼叫模型或讀取公開 ARC task。Dummy solvers／ReplayAdapter 的預定輸出只檢查契約，不能當成 G0/S1 比較結果或模型能力證據。

## 正式資料檢查與限制

完整 Stage 0 身分檢查入口為：

```sh
python -B scripts/arc_a1_substrate.py validate
```

執行前需要取得 [Substrate v0](docs/eval/ARC-AGI-1-Substrate-v0.md) 指定的外部資料與 frozen source；[.gitignore](.gitignore) 排除的 `data/arc-datasets/` 不隨一般 clone 提供。歷史 setup 記錄的 task 數量不表示目前本機已有資料。

[Rules](artifacts/arc-agi-1/rules.json) 與 [manifest](artifacts/arc-agi-1/manifest.json) 存在已記錄的 `rules_snapshot_mismatch`。資料缺失與規則身分衝突是不同問題；不要以 `generate` 覆寫 manifest 來消除原始衝突。未解決前不能將完整資料檢查視為通過。

Evaluator 目前標為 `local-reference-non-official`，官方 scorer 尚未提供，parity 尚未建立。正式 provider/model、sealed governance、數值 compute tiers 與 formal-run approvals 仍有缺口。ARC fixture 通過不支持 official score、OOD／跨版本泛化、specialist superiority 或跨領域／AGI 結論。

## 文件與開發

依 [AGENTS.md](AGENTS.md) 和 PROJECT-STATE 的 task-to-source routing 修改文件。README 不更動 Problem Definition、Evidence Adjudication、研究主張或 stage 狀態。Repository 目前未附 LICENSE；第三方資料與文獻工件的使用範圍需保持來源區分。
