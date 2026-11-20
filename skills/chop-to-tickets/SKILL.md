---
name: chop-to-tickets
description: 把決策樹垂直切成作業票，一票一檔存進專案 docs 資料夾的 tickets 目錄
disable-model-invocation: true
---

# 拆成作業票
 
輸入是 `docs/decision-tree.md`。

# 步驟

1. 讀決策樹。需要時讀專案目前的程式碼，了解現況。
2. 依據功能，垂直切分成tickets，必須遵守deep module深模組概念每一張票遵守：
- 穿過所有層（資料、邏輯、介面、測試）的一條完整窄路徑。
- 完成後，使用者可看見、可獨立驗收。
- 需要先整理現有程式碼才好做的前置重構，排在最前面成為獨立的票。
- 圍繞深模組(deep module)：少量介面後面放大量行為。每張票交付一個模組的完整行為，避免切成淺薄的一層一票。
- 宣告 `Blocked by`：哪些票必須先完成。沒有則寫 None。
- 寫一行「學習目標」：這張票讓使用者練習哪個概念。
3. 替每一個tickets，取一個branch名，必須遵守取名原則
4. 寫檔。一票一檔存成 `.scratch/tickets/<決策樹題目名>/NN-<票名>.md`，依相依順序從 `01` 編號（被依賴的票編號在前）。檔案內不放具體檔案路徑與程式碼片段，它們很快過時。

# 取名原則

結構 : 類型/版本-tickets

- 類型 :
  1. feat : 新功能
  2. fix : 修復功能

- 版本 : 
  vX.X.X

- tickets
  依照功能使用kebab-case描述

# 票的格式
 
```
# NN: <標題>
 
**Branch:** feat/v0.1.0-<票名>
**Blocked by:** None（前置阻擋任務，或列出票編號與標題）
**Blocks:** None (後續阻擋任務，或列出票編號與標題)
**Status:** todo
**學習目標:** 這張票練習的概念
 
**What to build:** 從使用者角度描述的端到端行為。
 
- [ ] 驗收條件 1
- [ ] 驗收條件 2
```
 
`Status` 的值：`todo`、`doing`、`done`。

# 禁止

禁止拆出infra-only/setup-only的ticket