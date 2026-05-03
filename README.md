# Patchbay

**English** — Self-hosted relay and rules for **Telegram** (primary) and **Discord** (secondary): message routing, a web console, and webhooks. Defaults favour **loop prevention**, **safe fan-out**, and **observability**.

**简体中文** — 自托管 **Telegram（主）/ Discord（次）** 消息中继与规则引擎，含 Web 控制台与 Webhook；默认强调 **防循环、可控广播、可观测**。

| | |
|--|--|
| **Repository** | https://github.com/yclenove/patchbay |
| **Stack** | Go (`patchbay` binary) · Vue 3 · PostgreSQL · Docker Compose |
| **License** | [MIT](LICENSE) · Copyright (c) 2026 yclenove |

You must comply with Telegram and Discord terms of service and applicable laws. Scope and non-goals are described in [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) (Chinese; product source of truth).

---

## Documentation / 文档

| Doc | EN | 中文 |
|-----|----|------|
| [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) | Roadmap, stack, risks | 产品与技术规划 |
| [docs/DEV.md](docs/DEV.md) | Local dev, Docker Postgres | 本地开发与数据库 |
| [docs/LEGACY_REPOS.md](docs/LEGACY_REPOS.md) | Related prior repos & paths | 相关旧仓库与路径 |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute | 贡献说明 |
| [SECURITY.md](SECURITY.md) | Vulnerability reporting | 漏洞报告 |
| [docs/adr/](docs/adr/) | Architecture decision records | 架构决策记录 |

---

## Status / 状态

**EN** — Phase 0 in progress (compose, minimal API, console skeleton). Issues and PRs welcome.

**中文** — Phase 0 进行中。欢迎 Issue 与 PR。

---

## Quick start / 快速开始

```bash
git clone https://github.com/yclenove/patchbay.git
cd patchbay
# Full stack compose will be documented in docs/DEV.md when ready.
```

For a **PostgreSQL-only** dev instance, see [docs/DEV.md](docs/DEV.md).

---

## Contributing / 参与贡献

Read [CONTRIBUTING.md](CONTRIBUTING.md). **Commit messages should be written in Chinese** (简短、一事一条).

参与方式见 [CONTRIBUTING.md](CONTRIBUTING.md)。**提交说明请使用中文**。
