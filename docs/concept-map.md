# 概念单一权威注册表（concept map）

> 一个概念只写一次。写新内容前先查这张表：**已存在 → 引用；不存在 → 先在权威处登记，再写**。

## 注册表

| 概念 | 唯一权威 | 引用处（只留指针） |
| --- | --- | --- |
| 幂等键通用机制（键随重复源 / 原子占位 / 结果回放 / 防重地图） | membership-system-builder：MSP spec §10 | ASP spec §1、MSP ledger §4（账本域键选型）、quality-gate simulators、subscription-splitter boundary-rules、engineering-pitfalls E-077/112/113（工程坑） |
| 设计判据 D-1~D-5（业务域 + 认证域表述 + 通过证据） | quality-gate-builder：`references/design-judgments.md` | membership conformance §3、identity conformance §3、membership master-craft §3（只保留出处溯源） |
| 选型访谈规则（三问 / 保守假设 / 理由要求） | agent-skills-index：`conventions/solution-interview.md` | 五个技能的 solution-tiers.md（各自保留档位表与领域取值） |
| 技术选型第二层访谈（五问 / 决策表 / 一致性校验） | agent-skills-index：`conventions/stack-interview.md` | membership `references/stack-selection.md`（样板）；其它技能一行指针 |
| 项目级编排（一次访谈 → 跨技能选型 → 汇总报告） | agent-skills-index：`composer.md` | 领域→技能调度表 |
| 时间模型（事实 / 派生 / 负债 / 触发器） | subscription-splitter：`references/time-model.md` | membership ledger/master-craft、course-platform domain-model |
| 账本域结构化幂等键 | membership-system-builder：ledger §4 | 领域专属，其它技能不复制 |
| 工程踩坑（单点小坑） | engineering-pitfalls：`references/log.md` | 各技能按 E-xxx 指针引用 |
| Outbox 实现机制（事务性发箱 / SKIP LOCKED / 死信 / 吞吐） | membership-system-builder：`references/outbox.md` | MSP spec INV-18/19/25、events.md §3（只留行为）；engineering-pitfalls E-079/082（坑）；course-platform platform/outbox（实例） |
| 认证边界 / principal | identity-system-builder：ASP spec §1 + MSP spec §1「身份边界」 | 业务技能只消费 principal |

## 结构骨架（允许重复，属于"独立仓库税"）

README / LICENSE / AUTHORS / CI validator / maintenance 骨架：每个开源仓库必须自包含，
允许逐仓复制；但骨架文本从模板生成、保持最短，不在其中放任何**语义原则**。

## 规则

1. 新增原则/概念前，先 `grep` 六个仓库：已有 → 引用，禁止复制；
2. 必须新写时，先在本表登记"唯一权威"位置，再动笔；
3. 冲突时以权威处为准，引用处不得私自改写语义；
4. 本表随每次新增/移动概念同步更新（与索引 README 同一提交）。
