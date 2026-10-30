---
name: chop-to-tickets
description: 當決策樹完成，把功能切分成tickets
---

# 步驟
1. 將上述決策樹，依據功能，垂直切分成tickets，必須遵守deep module深模組概念
2. 替每一個tickets，取一個branch名，必須遵守取名原則

# 取名原則
結構 : 類型/版本-tickets

- 類型 :
  1. feat : 新功能
  2. fix : 修復功能

- 版本 : 
  vX.X.X

- tickets
  依照功能使用kebab-case描述
