# Agent Skills Index 🔎 技能索引

> 本组织所有 agent 技能的导航入口：仓库链接、一句话描述、协议/版本与状态。
> 每个技能都是"协议/经验 + 构建器"形态：选型访谈 → 按档位落方案 → 生成可执行构建技能 → 持续进化。

## 已独立开源的技能（各自仓库）

| 技能 | 仓库 | 协议 / 版本 | 一句话描述 | 状态 |
| --- | --- | --- | --- | --- |
| membership-system-builder | [Henri-lab/membership-system-builder](https://github.com/Henri-lab/membership-system-builder) | MSP v0.4.0 | 会员订阅 + 付费内容 + 支付的选型与构建技能：个人收款码（金额指纹/截图审核/聚合）到官方网关，64 条测试向量 + 5 条设计判据判定"可用" | 活跃 |
| identity-system-builder | [Henri-lab/identity-system-builder](https://github.com/Henri-lab/identity-system-builder) | ASP v0.1.0 | 用户认证构建技能：注册/登录/服务端会话/验证码/重置/封禁，P2 含 TOTP 与 OIDC；认证/授权/权益三分离 | 活跃 |
| vps-migrator | [Henri-lab/vps-migrator](https://github.com/Henri-lab/vps-migrator) | v0.1.0 | GitHub + Docker 的服务器迁移/重建/灾难恢复：先 Plan（只读扫描）后 Apply（备份→部署→健康检查→DNS 切换与回滚窗口） | 活跃 |
| quality-gate-builder | [Henri-lab/quality-gate-builder](https://github.com/Henri-lab/quality-gate-builder) | v0.1.0 | 企业级质量门禁：测试流水 + 压测流水 + 三个模拟器（支付回调/并发用户/订单流程），复用 MSP/ASP 符合性向量 | 活跃 |
| subscription-splitter | [Henri-lab/subscription-splitter](https://github.com/Henri-lab/subscription-splitter) | v0.1.0 | 订阅系统边界与拆分决策：六概念时间模型（事实/派生/负债/触发器）+ 拆分四问与三个灵魂拷问 | 活跃 |
| engineering-pitfalls | [Henri-lab/engineering-pitfalls](https://github.com/Henri-lab/engineering-pitfalls) | v0.1.0 | 跨项目细碎工程踩坑库（E-001~E-111）：shell/构建部署/SQL/docker/工具链，动手前先搜、踩完就记 | 活跃 |
| api-contract-typing | [Henri-lab/api-contract-typing](https://github.com/Henri-lab/api-contract-typing) | v0.1.0 | 后端契约（OpenAPI）成为前端 TS 类型的唯一来源：双向路由门禁/required 补齐/漂移检测/按域拆分 | 活跃 |
| logging-system-builder | [Henri-lab/logging-system-builder](https://github.com/Henri-lab/logging-system-builder) | v0.1.0 | 统一日志体系：trace_id/module/func/caller、链路贯通、埋点、前端回流与防打点风暴 | 活跃 |
| server-hardening | [Henri-lab/server-hardening](https://github.com/Henri-lab/server-hardening) | v0.1.0 | 公网服务器加固：SSH 爆破/误绑 0.0.0.0/TLS 与安全响应头，每步带可复核验证 | 活跃 |

## 跨技能的通用纪律

1. **选型访谈**：执行时先问目的 × 规模 × 硬约束，按档位矩阵选方案并说明理由，禁止静默默认；
2. **设计判据 D-1~D-5**：删表重建 / 审计 / 并发同发 / 重放 / 回滚，跨等级必检；
3. **持续进化**：`lessons-log.md` 追加经验、`maintenance.md` 决定合并/提升/废弃，技能越用越准；
4. **上游唯一**：每个技能以独立仓库为唯一上游、`~/.codex/skills` 为安装副本，单向同步；`platform-kit` 只维护共享代码模块；
5. **署名**：MIT 保留版权声明，引用格式见各仓库 README。

另有两份治理文档（本仓库维护）：

- [conventions/solution-interview.md](conventions/solution-interview.md) —— 选型访谈规则的唯一权威；
- [conventions/stack-interview.md](conventions/stack-interview.md) —— 技术选型第二层访谈（每个决策点的选项/适合/代价与一致性校验）；
- [conventions/knowledge-evolution.md](conventions/knowledge-evolution.md) —— **知识演化策略**：使用回填、证据等级、提升规则（决策表变准的路线图）；
- [composer.md](composer.md) —— **项目编排入口**：一次访谈 → 跨技能定档位与技术栈 → 汇总选型报告；
- [docs/concept-map.md](docs/concept-map.md) —— **概念单一权威注册表**：哪个概念写在哪、别处只引用不复制。

## License

[MIT](LICENSE) © 2026 henrifox
