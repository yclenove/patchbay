# Patchbay

自托管 **Telegram（主） / Discord（次）** 消息中继与规则引擎，带 Web 控制台与 Webhook 扩展；强调 **防循环、防炸群、可观测**。

- **仓库**：https://github.com/yclenove/patchbay  
- **技术栈**：Go（`patchbay` 单二进制）+ Vue 3 + PostgreSQL + Docker Compose  
- **产品规划**：[docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)  
- **历史代码索引**（对照用）：[docs/LEGACY_REPOS.md](docs/LEGACY_REPOS.md)  
- **Claude Code** 请先读根目录 [CLAUDE.md](CLAUDE.md)

## 文档索引

| 文档 | 说明 |
|------|------|
| [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) | 产品与技术规划（Phase、栈、风险） |
| [docs/LEGACY_REPOS.md](docs/LEGACY_REPOS.md) | 旧实现仓库与本机路径 |
| [docs/DEV.md](docs/DEV.md) | 本地开发（占位，随代码补充） |
| [docs/adr/](docs/adr/) | 架构决策（ADR）目录，有决策时新增 `xxx.md` |
| [CONTRIBUTING.md](CONTRIBUTING.md) | 贡献方式与 PR 约定 |
| [SECURITY.md](SECURITY.md) | 漏洞报告方式 |
| [LICENSE](LICENSE) | MIT |
| [`.cursor/rules/`](.cursor/rules/) | Cursor 规则（`.mdc`，与 `CLAUDE.md` 配套） |
| [AGENTS.md](AGENTS.md) | 与 Claude 约定对齐，供读 `AGENTS.md` 的工具使用 |

## 状态

仓库初始化中：Phase 0（Compose、最小 API、控制台骨架）尚未完成。欢迎 Star / Issue。

## 快速开始（占位）

```bash
git clone https://github.com/yclenove/patchbay.git
cd patchbay
# 待 docker-compose.yml 就绪后：
# docker compose up -d
```

## 许可证

[MIT License](LICENSE)（Copyright (c) 2026 yclenove）。使用本软件须自行遵守 Telegram、Discord 等平台服务条款及所在地法律法规；详见仓库内规划文档中的免责声明与「不支持」说明。
