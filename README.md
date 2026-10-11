# spex

spex 目前結合 **專門化與通用模型比較的研究文件**，以及 **ARC-AGI-1 開發用的本地評分／run 工件基礎**。已實作 strict task/prediction contract、local-reference evaluator、run manifest／成本記錄與 G0/S1 的 provider-independent 介面；沒有設定或呼叫真實模型，也沒有正式 ARC 結果。[目前狀態來源](docs/current/PROJECT-STATE.md) 的 Stage 2 acceptance 是工程進度，不能當研究 stage achievement。

## 教授閱讀路線

1. [Professor-facing Repository Audit](PROFESSOR_AUDIT.md)：本次 checkout 準備度與公開前阻礙。
2. [PROJECT-STATE](docs/current/PROJECT-STATE.md) → [Problem Definition v1](docs/current/Problem%20Definition%20v1.md)：研究問題與 G/M/S/H/N 等比較邊界。
3. [Evidence Adjudication 摘要](docs/current/Evidence-Adjudication-v1.md)：文獻證據如何縮窄主張；精確 record-level 欄位以 [Evidence Base](docs/current/Evidence-Base-v1.1.xlsx) 與 [Adjudication workbook](docs/current/Evidence-Adjudication-v1.xlsx) 為準。
4. [Evaluator Core](docs/eval/ARC-AGI-1-Evaluator-Core-v0.md) → [Run / Artifact Substrate](docs/eval/ARC-AGI-1-Run-Artifact-Substrate-v0.md) → [G0/S1 Development](docs/eval/ARC-AGI-1-G0-S1-Development-v0.md)：已存在程式與尚未完成的真實評估之間的邊界。

目前 evaluator 標為 `local-reference-non-official`，官方 scorer 仍 `Unavailable in checkout`，parity 尚未建立。Stage 0 有既知 `rules_snapshot_mismatch`；本次 clone 也沒有 [.gitignore](.gitignore) 排除的 `data/arc-datasets/`，歷史文件記錄的資料數量不等於本次資料可用。

## 可重現的本地檢查

在 repo 根目錄使用 Python 與 Git。既有 fixture tests 使用 Python 標準函式庫，會在系統臨時目錄產生測試資料與 run 工件，不呼叫模型或讀取 ARC 公開資料集：

```powershell
python -B -m unittest discover -s tests -p 'test_*.py' -v
```

本次於 2026-10-11、Python 3.14.7 執行，18 項既有測試全數通過。這可核查 parser、scoring、budget、resume 與 pairing contracts；fixture 的成功輸出不是 benchmark 成績。

Stage 0 完整資料身分檢查的現有命令是：

```powershell
python -B scripts/arc_a1_substrate.py validate
```

本次此命令失敗：rules hash 不符、dataset repository／tier 目錄／800 個 manifest task files 缺失。資料來源與 frozen commit 可查 [Substrate v0](docs/eval/ARC-AGI-1-Substrate-v0.md)；取得相符來源及解決 hash 衝突前，不能宣稱完整 dataset 重現。`generate` 會覆寫 manifest，不是消除既有衝突的驗證步驟，本次未執行。

## 關鍵程式閱讀導覽

| 順序 | 入口 | 重點 |
|---|---|---|
| 1 | [domain/arc_a1.py](src/spex_arc/domain/arc_a1.py) | `Task.solver_view` 只提供 test input；parser 將失敗保留為結構化資料。 |
| 2 | [evaluator/arc_a1.py](src/spex_arc/evaluator/arc_a1.py) | `load_evaluator_identity` → `score_task` → `serialize_submission`；Exact@1、native attempts 與 non-official 身分分開。 |
| 3 | [runner/arc_a1.py](src/spex_arc/runner/arc_a1.py) | `RunManifest`／`validate_run_manifest` → `ArcA1Runner.run` → `_ArtifactStore`；terminal task、成本與中斷紀錄如何留下。 |
| 4 | [solvers/arc_a1.py](src/spex_arc/solvers/arc_a1.py) 與 [baselines/arc_a1.py](src/spex_arc/baselines/arc_a1.py) | `ModelAdapter.prepare/complete`、request reservation／settlement、配對條件與 calibration proposal；尚無真實 provider。 |
| 5 | [既有 tests](tests/) | 對照 fixture、錯誤與重啟語意，避免把工程測試當能力證據。 |

本次僅加上閱讀入口與 audit，沒有修改程式、資料、規則或研究 adjudication。既有本人／AI／第三方的貢獻歸屬待確認；根目錄未找到 LICENSE，公開授權與第三方資料使用範圍仍需作者確認。
