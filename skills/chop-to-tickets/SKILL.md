---
name: chop-to-tickets
description: 把設計樹垂直切成作業票，一票一檔存進專案 docs 資料夾的 tickets 目錄
disable-model-invocation: true
---

# 拆成作業票
 
載入`docs/design-tree.md`，依照功能切分tickets，tickets 必須遵照 tracer-bullet 垂直切分，並且宣告ticket之間的相依、驗收方式。
若沒有`docs/design-tree.md`，請回饋使用者先使用`/system-project-design`

# 步驟

1. 讀`design-tree.md`。需要時讀專案目前的程式碼，了解現況。
2. 依據功能，垂直切分成tickets，每一張ticket須遵守：
  - 需要先整理現有程式碼才好做的前置重構，排在最前面成為獨立的票。
  - tracer-bullet，穿過該功能（資料、邏輯、介面、測試）的一條完整窄路徑。
  - deep module：小而簡單的Interface，後面藏著大量功能與複雜度。
  - 完成後，使用者可看見、可獨立驗收。
  - 宣告 `Blocked by`：哪些票必須先完成。沒有則寫 None。
  - 寫一行「學習目標」：這張票讓使用者練習哪個概念。
3. 替每一個tickets，取一個branch名，依照name-rule
4. 寫檔。一票一檔存成 `.scratch/tickets/<設計樹題目名>/NN-<票名>.md`，依相依順序從 `01` 編號（被依賴的票編號在前）。檔案內不放具體檔案路徑與程式碼片段，它們很快過時。

# named-rule

結構 : 類型/版本-tickets

- 類型 :
  1. feat : 新功能
  2. fix : 修復功能
  3. chore : 非程式碼任務，例如相依套件、文件更新

- 版本 : 
  vX.X.X

- tickets
  依照功能使用kebab-case描述

# 票的格式
 
```
# NN: <標題>
 
**Branch:** feat/v0.1.0-<票名>
**Blocked by:** None（前置阻擋任務，或列出票編號與標題）
**Status:** todo
**學習目標:** 這張票練習的概念
 
**What to build:** 從使用者角度描述的端到端行為。
 
- [ ] 驗收條件 1
- [ ] 驗收條件 2
```
 
`Status` 的值：`todo`、`doing`、`done`。

# 禁止

- 絕對禁止拆出純環境 Setup 的 Ticket。所有初始化與建置工作必須自動併入 Ticket #1。
- ticket切成淺薄的一層一票。