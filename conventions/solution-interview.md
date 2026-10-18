# 选型访谈通用约定（solution interview，唯一权威）

> 平台技能族（membership / identity / quality-gate / subscription-splitter / vps-migrator）
> 的公共前门。**访谈规则只在这里**；各技能只保留自己的档位表与理由模板实例，不再复述规则。

## 1. 三问（一次问清，≤3 个问题）

| # | 问题 | 用途 |
| --- | --- | --- |
| 1 | **目的**是什么 | 定档位主轴（验证 / 自用 / 商业 / 基础设施，取值按技能自定） |
| 2 | **规模**多大 | 定档位落点（量级、团队、预算，按技能自定） |
| 3 | **硬约束**有哪些 | 修正取值（合规、技术栈、已有系统，按技能自定） |

## 2. 硬规则

1. **一次问清**，不反复追问；用户答不出就给推荐档位 + 理由，让用户只需点头；
2. **禁止静默默认**：未回答的项按**最保守假设**选档，并在产出中显式标注"未确认"；
3. 用户已明确给出的约束永远优先；
4. 理由必须**可复核**：写明"为什么这个档位、为什么不是上一档/下一档"；
5. 档位表、换档触发器属于各技能自己的领域资产，不在本约定内。

## 3. 理由模板（通用格式）

```text
档位：<X>
依据：目的=<…>；规模=<…>；硬约束=<…>
理由：<为什么这个档位>
为什么不是上一档：<…>
为什么不是下一档：<…>
未确认假设：<无 / 列出按保守假设处理的项>
```

## 4. 各技能的档位表索引

| 技能 | 档位 | 文档 |
| --- | --- | --- |
| membership-system-builder | L0~L3（最小验证→可复用基础设施） | `references/solution-tiers.md` |
| identity-system-builder | I0~I3（内嵌最小→统一身份服务） | `references/solution-tiers.md` |
| quality-gate-builder | Q0~Q3（最小门禁→企业级） | `references/solution-tiers.md` |
| subscription-splitter | D0~D3（边界确认→多系统治理） | `references/solution-tiers.md` |
| vps-migrator | A/B/C/D（整机迁移/重建/恢复/多机） | `references/solution-tiers.md` |
