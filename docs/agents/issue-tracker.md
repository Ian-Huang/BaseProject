# 問題追蹤系統：本地 Markdown (Local Markdown)

此專案的 Issue 和規格 (specs) 以 markdown 檔案的形式存放在 `.scratch/` 中。

## 慣例

- 每個功能 (feature) 一個資料夾：`.scratch/<feature-slug>/`
- 規格檔案為 `.scratch/<feature-slug>/spec.md`
- 實作的 Issue 為每個 ticket 一個檔案，位於 `.scratch/<feature-slug>/issues/<NN>-<slug>.md`，編號從 `01` 開始，絕對不要把所有 ticket 寫在同一個檔案裡。
- 分類狀態 (Triage state) 記錄在每個 Issue 檔案頂部附近的 `Status:` 行 (角色字串請參閱 `triage-labels.md`)。
- 留言和對話歷史附加在檔案底部的 `## Comments` 標題下。

## 當技能要求「發布到問題追蹤系統 (publish to the issue tracker)」時

在 `.scratch/<feature-slug>/` 下建立一個新檔案 (若資料夾不存在請先建立)。

## 當技能要求「取得相關的 ticket (fetch the relevant ticket)」時

讀取參考路徑中的檔案。使用者通常會直接提供路徑或 Issue 編號。

## 尋路操作 (Wayfinding operations)

由 `/wayfinder` 使用。**地圖 (map)** 是一個檔案，每個 ticket 有一個對應的**子 (child)** 檔案。

- **地圖**：`.scratch/<effort>/map.md` (包含筆記 / 目前的決定 / 迷霧主體)。
- **子 ticket**：`.scratch/<effort>/issues/NN-<slug>.md`，編號從 `01` 開始，問題寫在內文中。`Type:` 行記錄 ticket 類型 (`research`/`prototype`/`grilling`/`task`)；`Status:` 行記錄 `claimed`/`resolved`。
- **阻擋 (Blocking)**：頂部附近的 `Blocked by: NN, NN` 行。當一個 ticket 列出的所有檔案都標為 `resolved` 時，該 ticket 才解除阻擋。
- **前線 (Frontier)**：掃描 `.scratch/<effort>/issues/` 尋找狀態為 open、unblocked 且 unclaimed 的檔案；編號越小的優先。
- **認領 (Claim)**：在開始任何工作前，設定 `Status: claimed` 並存檔。
- **解決 (Resolve)**：在 `## Answer` 標題下附加答案，設定 `Status: resolved`，然後在 `map.md` 的「目前的決定 (Decisions-so-far)」中附加一個上下文指標 (gist + 連結)。
