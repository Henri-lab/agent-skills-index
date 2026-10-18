# 技术选型第二层访谈（stack interview，唯一权威）

> 第一层（业务档位）见 [solution-interview.md](solution-interview.md)；本层在**档位确定后**决定技术栈。
> 核心原则：**每个决策点给开发者选择权 + 说明利害**；开发者不答时给推荐 + 理由 + 保守默认，并在产出标注"未确认"。
> 本表的"适合/代价"是经验起点，靠**使用回填**变准（证据等级与提升规则见 [knowledge-evolution.md](knowledge-evolution.md)）。

## 1. 五问（一次问清）

| # | 问题 | 取值（示例） | 决定什么 |
| --- | --- | --- | --- |
| 1 | 团队语言能力 | Go / Node-TS / 已有栈 / 无偏好 | 语言 |
| 2 | 部署形态 | 单机 compose / 多机·k8s / PaaS / serverless | 托管与编排 |
| 3 | 数据与流量规模 | 单量级、数据量、实例数 | 数据库 / 缓存 / MQ |
| 4 | 实时性与事件需求 | 跨进程扇出？多团队消费？每秒量级？ | 事件形态 |
| 5 | 预算 / 合规 / 托管偏好 | 云厂商、备案、费用上限 | CI / 观测 / 托管商 |

## 2. 决策表（每个决策点：选项 / 适合 / 代价）

### 2.1 语言

| 选项 | 适合 | 代价 |
| --- | --- | --- |
| Go | 并发与类型安全、单二进制部署、与 golang-* 技术技能族配套 | 学习曲线、生态偏工程 |
| Node/TS | 前后端同语言、api-contract-typing 全栈闭环、生态快 | CPU 密集弱、长期可维护性看纪律 |
| 已有栈 | 改造项目 | 继承既有技术债 |

推荐：新建 + 无偏好 → Go；已有 Next 前端且团队只熟 TS → Node 全栈减少心智；改造 → 沿用现有栈。

### 2.2 数据库

| 选项 | 适合 | 代价 |
| --- | --- | --- |
| Postgres | 约束/JSONB/唯一索引幂等/outbox SKIP LOCKED 全套 | 单点写扩展靠分区/读写分离 |
| MySQL | 团队运维熟悉、云上便宜 | JSON 与约束能力弱、部分索引/唯一语义差异 |
| SQLite | 单机小站零运维 | 并发写弱，不适合多实例 |

推荐：默认 Postgres（MSP 的不变量与幂等索引均按它书写）；换 MySQL 需在差分声明里写清唯一语义差异。

### 2.3 事件 / MQ

| 选项 | 适合 | 代价 |
| --- | --- | --- |
| 无 MQ（outbox 直连） | 模块化单体默认 | 扇出/缓冲/消费进度要自造（outbox §13.1） |
| 真 MQ | 每秒上千 / 跨机房 / 多团队独立消费 | Kafka 运维重；RabbitMQ 路由强但吞吐弱些；NATS 轻量 |
| Postgres 兼职（River） | 同库异步任务 | N 个消费者放大生产库读压力 |

推荐：默认无 MQ；出现升级信号再上真 MQ（见 membership outbox.md §12）。

### 2.4 缓存 / 会话

| 选项 | 适合 | 代价 |
| --- | --- | --- |
| 无缓存 | 默认 | Postgres 扛不住才加 |
| Redis | 会话、限流、热点、分布式锁 | 多一个运维件 + 一致性心智 |
| 进程内存 | 单实例 | 多实例下失效 |

推荐：需要会话/限流时上 Redis；目录缓存单实例可用内存。

### 2.5 部署形态

| 选项 | 适合 | 代价 |
| --- | --- | --- |
| 单机 compose | 起步默认（vps-migrator 场景 B/C） | 单点 |
| 多机 / k8s | 高可用、团队有能力 | 运维成本陡增 |
| PaaS（Railway/Fly/Render 等） | 省运维 | 厂商锁定、费用 |
| serverless | 突发无状态 | outbox relay 长驻需外部调度、冷启动 |

推荐：单机 compose 起步；换档触发器见 vps-migrator。

### 2.6 CI 与观测

| 选项 | 适合 | 代价 |
| --- | --- | --- |
| GitHub Actions | 同仓默认 | 私有仓库分钟配额 |
| Jenkins | 自建多机矩阵 | 自维护 |
| 日志/追踪 | logging-system-builder + golang-observability | 需要一次接入成本 |
| 错误上报 | Sentry（课程站 G5 经验） | 第三方依赖 |
| 压测 | k6（默认）vs Locust（Python 团队） | 见 quality-gate load-testing |

## 3. 组合一致性校验（选完必跑）

| 组合 | 冲突 / 前提 |
| --- | --- |
| 官方回调 | 需营业执照 + ICP 备案域名（无则只能个人码/聚合/截图审核） |
| serverless + outbox | relay 长驻需外部定时触发/独立调度器 |
| 金额指纹 | 单一收款账户（多系统共用需分区金额空间） |
| 多产品 | 身份层独立（identity I2 起） |
| k8s | 团队运维能力到位，否则是负债 |
| MySQL 替代 Postgres | 幂等唯一索引的 NULL 语义差异要显式兜底 |

冲突时二选一：换选型，或在产出"差分声明"写明风险与缓解，不得静默。

## 4. 理由模板（每项选型都写"为什么不是另一个"）

```text
决策点：语言 → Go
依据：团队会 Go；档位 L1；无 Node 依赖
利害：选 Node 会减少前后端两套语言的心智，但并发/类型安全与本技能族配套弱
为什么不是 Node：<…>
未确认假设：<无>
```

## 5. 技术栈委托表（选型 → 执行技能）

| 选型 | 执行层技能 |
| --- | --- |
| Go 后端 | golang-database / concurrency / testing / observability / benchmark / lint |
| 前后端契约 | api-contract-typing |
| 日志与链路 | logging-system-builder |
| 公网加固 | server-hardening |
| 测试/压测门禁 | quality-gate-builder |
| 迁移/重建 | vps-migrator |
