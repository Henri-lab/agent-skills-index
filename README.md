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

## 尚在 platform-kit 内、未独立开源的技能

| 技能 | 一句话描述 | 说明 |
| --- | --- | --- |
| logging-system-builder | 统一日志体系：trace_id/链路贯通/埋点/前端回流与防打点风暴 | 待独立 |
| engineering-pitfalls | 跨项目细碎工程踩坑经验库（shell/构建/数据库/工具链） | 待独立 |
| api-contract-typing | OpenAPI 成为前端 TS 类型的唯一来源（双向门禁/漂移检测） | 待独立 |
| server-hardening | 公网服务器加固（SSH 爆破/误绑 0.0.0.0/TLS 与安全头） | 待独立 |

## 跨技能的通用纪律

1. **选型访谈**：执行时先问目的 × 规模 × 硬约束，按档位矩阵选方案并说明理由，禁止静默默认；
2. **设计判据 D-1~D-5**：删表重建 / 审计 / 并发同发 / 重放 / 回滚，跨等级必检；
3. **持续进化**：`lessons-log.md` 追加经验、`maintenance.md` 决定合并/提升/废弃，技能越用越准；
4. **上游唯一**：每个技能以独立仓库为唯一上游，`platform-kit` 为 vendored 副本、`~/.codex/skills` 为安装副本，单向同步；
5. **署名**：MIT 保留版权声明，引用格式见各仓库 README。

## License

[MIT](LICENSE) © 2026 henrifox
