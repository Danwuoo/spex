# Professor-facing Repository Audit — spex

spex 有可審閱的研究證據管理文件與可執行的 ARC 本地開發基礎。18 項既有 fixture tests 本次通過，但完整 Stage 0 資料重現失敗；沒有真實模型、正式 benchmark 結果或已達成的研究 stage。適合展示「如何界定研究主張、建立可歸因與可重建的評估工程」。[來源：目前狀態](docs/current/PROJECT-STATE.md)、[Evaluator Core](docs/eval/ARC-AGI-1-Evaluator-Core-v0.md)、[G0/S1 Development](docs/eval/ARC-AGI-1-G0-S1-Development-v0.md)。

- 審閱日期：2026-10-11。
- 審閱 HEAD：`ff16a997e74e523baed067ef9743da562f1dcddc`。
- 文件角色：一次性外圍 repository audit；不變更 Problem Definition、evidence adjudication、ARC stage 或 winning hypothesis。
- 起始工作樹乾淨；本次只新增 README 與本文件，無程式、schema、資料、結果或既有治理文件變更。

## 評分與可核查依據

分數是本次 repository 審查判斷，不是研究成績。共用尺度：1＝入口或證據缺失；2＝部分具備且重要限制；3＝可沿文件核查但有公開前缺口；4＝易審閱且範圍內可重現；5＝獨立重現與個人歸屬完整。

| 面向 | 分數 | 本地依據與理由 |
|---|---:|---|
| Readiness | 2/5 | [README](README.md) 有展示路線；[PROJECT-STATE](docs/current/PROJECT-STATE.md) 的 global design 是 `Not ready`，provider、正式 run 與 sealed governance 缺失；本次資料集目錄也不存在。 |
| Readability | 3/5 | [README 程式導覽](README.md#關鍵程式閱讀導覽)、[Problem Definition](docs/current/Problem%20Definition%20v1.md) 與 [工程文件](docs/eval/ARC-AGI-1-Run-Artifact-Substrate-v0.md) 可對照概念與實作；[runner](src/spex_arc/runner/arc_a1.py) 較長，歷史 setup 紀錄仍需與本 checkout 狀態一起閱讀。 |
| Verifiability | 2/5 | [fixture tests](tests/) 本次 18 項通過；[Stage 0 validator](scripts/arc_a1_substrate.py) 失敗，rules hash 與資料身分不可完整重現。[Adjudication 摘要](docs/current/Evidence-Adjudication-v1.md) 不替代 workbook 或外部一手來源再查核。 |
| Technical Depth | 3/5 | [TaskView](src/spex_arc/domain/arc_a1.py)、[strict scoring](src/spex_arc/evaluator/arc_a1.py)、[manifest／atomic bundle／resume](src/spex_arc/runner/arc_a1.py)、[provider reservation 與配對](src/spex_arc/solvers/arc_a1.py) 有實作及測試；資源匹配與研究效果尚未實測。 |
| Individual Contribution | 1/5 | [研究文件](docs/current/Problem%20Definition%20v1.md)、[現有程式](src/spex_arc/runner/arc_a1.py) 沒有可核查的本人／AI／第三方逐項歸屬；[PROJECT-STATE](docs/current/PROJECT-STATE.md) 的 owner／decision authority 亦為 `TBD`。版本紀錄不能單獨證明全部由申請者完成。 |

## 內容與證據邊界

| 層次 | 現有入口 | 可以核查什麼 |
|---|---|---|
| 研究問題 | [Problem Definition v1](docs/current/Problem%20Definition%20v1.md) | Model/System/Hybrid/Narrow units、relative／frontier／persistent advantage 及外推限制。 |
| 既有文獻證據與裁決 | [Evidence Base v1.1](docs/current/Evidence-Base-v1.1.xlsx)、[Adjudication workbook](docs/current/Evidence-Adjudication-v1.xlsx)、[摘要](docs/current/Evidence-Adjudication-v1.md) | 既有來源與判讀工件存在；本次未逐儲存格重新核對 workbook，未重查外部論文，不能宣稱文獻結論獲本次獨立驗證。 |
| ARC 工程基礎 | [Evaluator](src/spex_arc/evaluator/arc_a1.py)、[Runner](src/spex_arc/runner/arc_a1.py)、[G0/S1](src/spex_arc/solvers/arc_a1.py) | Strict contract、local scoring、成本／失敗／中斷與配對邊界；fixture 可測，不代表真實 solver 能力。 |
| 真實研究結果 | [PROJECT-STATE §4–5](docs/current/PROJECT-STATE.md) | 正式 preregistration、模型配置、official score、ablation／stage decision 皆未有支持工件；保留 `Not evidenced`。 |

若討論未來 G0/S1，單位依 [G0/S1 contract](docs/eval/ARC-AGI-1-G0-S1-Development-v0.md) 分別為 `G`／`S`；本次沒有可成立的 advantage claim。ARC 測量是 benchmark proxy，held-out、OOD、temporal shift、cross-version transfer、independent replication 均未由本次檢查建立。

## 公開前必須處理

| 問題 | 依據 | 完成條件 |
|---|---|---|
| rules 與 manifest 身分衝突 | [rules.json](artifacts/arc-agi-1/rules.json)、[manifest.json](artifacts/arc-agi-1/manifest.json)、[Evaluator Core 記錄](docs/eval/ARC-AGI-1-Evaluator-Core-v0.md) | 由作者依治理完成 correction 或 adjudication，保留衝突來由；不要用重新 generate 覆寫來隱藏問題。 |
| Clone 沒有文件所述 ARC datasets／Toolkit | [.gitignore](.gitignore)、[歷史 Dataset/Toolkit Status](docs/eval/ARC-Dataset-Toolkit-Status-v0.md)、[Substrate](docs/eval/ARC-AGI-1-Substrate-v0.md) | 展示時明說歷史 setup 不等於新 clone；若宣稱完整 dataset 重現，需恢復相符 source commit/tree、檢查 task hashes 並解決 rules 衝突。現階段限 fixture demonstration。 |
| 缺實際 runtime／完整依賴重建紀錄 | [PROJECT-STATE §5](docs/current/PROJECT-STATE.md)、[現有測試](tests/test_arc_a1_substrate.py) | 本次可記錄 Python 3.14.7＋Git 的 fixture 檢查；不能把既有 toolkit 安裝紀錄當鎖定環境或官方 evaluator parity。 |
| 個人貢獻與第三方來源責任不明 | [PROJECT-STATE](docs/current/PROJECT-STATE.md)、[研究摘要](docs/current/Evidence-Adjudication-v1.md)、[程式](src/spex_arc/runner/arc_a1.py) | 作者確認研究選題、文獻查核、adjudication、實作、測試分別的本人／AI／第三方範圍；來源文獻成果不能算本人模型成果。 |
| 根目錄缺 LICENSE／公開使用範圍 | 本次檔案盤點；[既有資料來源紀錄](docs/eval/ARC-AGI-1-Substrate-v0.md) | 由權利人決定本專案授權，核對第三方資料、文獻工件的使用與展示條件；本次不新增授權或下載資料。 |
| 可能把工程 acceptance 當研究完成 | [PROJECT-STATE §4](docs/current/PROJECT-STATE.md)、[G0/S1 Development](docs/eval/ARC-AGI-1-G0-S1-Development-v0.md) | README／申請敘述一致標 development-only、non-official。研究、SOTA、效率或泛化宣稱須有已存在且相符的 formal report／decision；目前不做。 |

沒有真實 run 並非本次應補出的成果。所有 provider、sealed governance、預算及正式實驗均維持原狀。

## 可宣稱與不能宣稱

| 可由本 checkout 支持 | 目前不能支持 |
|---|---|
| 有精確區分比較單位、資源與時間的研究文件。[來源](docs/current/Problem%20Definition%20v1.md) | 已證明 specialist 普遍優於／劣於 generalist、已建立跨領域 scaling law。 |
| 有非官方 ARC local-reference evaluator 和開發用 run 工件實作。[來源](docs/eval/ARC-AGI-1-Run-Artifact-Substrate-v0.md) | 官方／parity-validated ARC 成績、sealed/private generalization 或已完成研究 stage。 |
| 本次 18 項 synthetic／replay fixture tests 通過。[來源](tests/) | 真實 G0/S1 superiority、實際 calibration 或模型推論能力。 |
| 保留既有文獻證據與裁決檔案。[來源](docs/current/Evidence-Adjudication-v1.md) | 這些第三方結果由申請者親自訓練或實驗取得；本次重新獨立驗證了全部來源。 |

既有本人／AI／第三方歸屬未確認。本次 README 與 audit 為 AI 協助撰寫，沒有新增或變更 empirical evidence／claim status。

## 本次驗證與限制

在 repo 根目錄、Python 3.14.7 執行：

```powershell
python -B -m unittest discover -s tests -p 'test_*.py' -v
python -B scripts/arc_a1_substrate.py validate
```

第一條：18 項既有測試全過。依 [tests](tests/)，使用本地 synthetic task、dummy solvers／replay adapter 與系統臨時目錄；Stage 0 fixtures 在臨時目錄建立測試 Git repository，不改本 repo 的 history。未呼叫模型、外部 provider 或公開 ARC task。

第二條：exit 1、`valid: false`；包含 `rules_snapshot_mismatch`、`repository_identity_unavailable`、`missing_tier_directory`、800 個 `missing_task_file` 與兩個 `task_inventory_count_mismatch`（actual 0、expected 400）。這同時確認既有 hash 衝突與 clone 不包含外部資料；本次未執行 `generate`，未修改 manifest／rules。

本次未重建乾淨 runtime、逐儲存格驗證 Excel 證據、重查外部研究、跑真實 baseline 或評分公開資料。`-B` 避免產生 Python bytecode；技術可讀性只加 [閱讀導覽](README.md#關鍵程式閱讀導覽)，保留全部核心程式。
