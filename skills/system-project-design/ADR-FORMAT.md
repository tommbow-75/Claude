# ADR FORMAT
嚴格遵循ADR的架構及不可變動性、純文字
ADRs 存放在 `docs/adr/`, 並且以此規則命名 : `001-slug.md`,`002-slug.md`, etc
推翻舊有ADR時，舊ADR必須變更狀態

# status
ADRs有以下幾種狀態
1. `Accepted` : 採納
2. `Superseded by ..` : 被取代

## 架構
```markdown
---
status : {status}
---

## Context
{3~5句話講解脈絡}

## Decision
{1~2句話直述決策內容}

## Consequences
{誠實列出正面效益與負面代價}
```