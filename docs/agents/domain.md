# 領域文件 (Domain Docs)

工程技能在探索此專案的程式碼庫時，應如何取用此專案的領域文件。

## 在探索之前，請閱讀以下內容

- 專案根目錄的 **`GLOSSARY.md`**，或者
- 如果專案根目錄有 **`GLOSSARY-MAP.md`**：它會指向每個情境 (context) 的 `GLOSSARY.md`。請閱讀與目前主題相關的每個檔案。
- **`docs/adr/`**：閱讀涉及您即將工作領域的架構決策紀錄 (ADRs)。在多情境 (multi-context) 專案中，也請檢查 `src/<context>/docs/adr/` 中特定情境的決策。

如果這些檔案不存在，**請保持沉默並繼續**。不要標記它們的缺失；不要在前期建議建立它們。`/domain-modeling` 技能 (可透過 `/grill-with-docs` 和 `/improve-codebase-architecture` 呼叫) 會在詞彙或決策真正確立時自動延遲建立它們。

## 檔案結構

單一情境專案 (大多數專案)：

```text
/
├── GLOSSARY.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

多情境專案 (根目錄存在 `GLOSSARY-MAP.md`)：

```text
/
├── GLOSSARY-MAP.md
├── docs/adr/                          ← 系統層級的決策
└── src/
    ├── ordering/
    │   ├── GLOSSARY.md
    │   └── docs/adr/                  ← 特定情境的決策
    └── billing/
        ├── GLOSSARY.md
        └── docs/adr/
```

## 使用術語表中的詞彙

當您的輸出命名了一個領域概念時 (在 Issue 標題、重構提案、假設、測試名稱中)，請使用 `GLOSSARY.md` 中定義的術語。不要偏離使用術語表明確避免的同義詞。

如果您需要的概念尚未出現在術語表中，這是一個訊號：這表示您正在發明專案未使用的新詞彙 (請重新考慮)，或者這裡確實有一個缺口 (請記錄下來供 `/domain-modeling` 參考)。

## 標記 ADR 衝突

如果您的輸出與現有的 ADR 相矛盾，請明確地提出來，而不是默默地覆蓋：

> _與 ADR-0007 (event-sourced orders) 相矛盾，但值得重新討論，因為..._
