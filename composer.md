# 项目编排入口（composer）

> 做一个完整项目时的**唯一入口**：一次访谈 → 委托各领域技能定档位与技术栈 → 汇总一份选型报告。
> 规则见 [conventions/solution-interview.md](conventions/solution-interview.md)（第一层）与
> [conventions/stack-interview.md](conventions/stack-interview.md)（第二层）。

## 1. 流程（两轮访谈，一次问清）

1. **第一层（业务）**：目的 × 规模 × 硬约束 → 每个涉及领域各定档位（membership L0~L3 /
   identity I0~I3 / quality-gate Q0~Q3 / vps A~D / subscription D0~D3）；
2. **第二层（技术）**：五问 → 按 stack-interview 决策表选语言/数据库/事件/缓存/部署/CI 观测；
3. **一致性校验**：跑 stack-interview §3，冲突要么换选型、要么写差分声明；
4. **汇总报告**：按下表模板输出，每个决策点带"利害 + 为什么不是另一个 + 未确认假设"。

## 2. 领域 → 技能 调度表

| 领域 | 技能 |
| --- | --- |
| 会员/订单/支付/积分/退款 | membership-system-builder |
| 注册/登录/会话/生命周期 | identity-system-builder |
| 边界与拆分评审 | subscription-splitter |
| 测试/压测/模拟器 | quality-gate-builder |
| 迁移/重建/恢复 | vps-migrator |
| 工程踩坑检索 | engineering-pitfalls |
| 技术执行层 | golang-* 技能族 / api-contract-typing / logging-system-builder |

## 3. 汇总报告模板

```text
# 选型报告
- 目的 / 规模 / 硬约束（未确认假设显式标注）

## 业务档位
| 领域 | 档位 | 理由 | 利害 |

## 技术选型
| 决策点 | 选择 | 依据 | 为什么不是另一个 | 利害 |

## 一致性校验
| 组合 | 结论（通过 / 差分声明） |

## 下一步
按各技能"生成构建技能"的入口，从档位最高的领域开始落地。
```

## 4. 纪律

- 每层访谈都遵守"一次问清、不答给推荐+理由、禁止静默默认"；
- 本文件不复制任何决策表，只做调度与汇总（单一权威在两个 conventions 与各技能）。
