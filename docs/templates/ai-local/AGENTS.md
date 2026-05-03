# AGENTS.md — Patchbay

> **使用方式**：复制到仓库根目录 `AGENTS.md`（已 `.gitignore`，不提交远端）。  
> 本文件供 **读取 `AGENTS.md` 的 Agent 工具**（含部分 OpenCode / 自动化场景）使用。  
> **与 Claude Code 的主约定请以根目录 `CLAUDE.md` 为准**；二者应保持一致，修改时请同步更新。

## 快速对齐

| 主题 | 文件 |
|------|------|
| 产品阶段、栈、竞品与风险 | [`docs/PRODUCT_PLAN.md`](docs/PRODUCT_PLAN.md) |
| Claude Code 会话说明 | 根目录 `CLAUDE.md`（由本目录 `CLAUDE.md` 复制） |
| Cursor IDE 规则（`.mdc`） | 根目录 `.cursor/rules/`（由 `cursor-rules/` 复制） |
| 本地开发与 Docker Postgres | [`docs/DEV.md`](docs/DEV.md) |
| 旧项目路径与链接 | [`docs/LEGACY_REPOS.md`](docs/LEGACY_REPOS.md) |
| 私有设计 / 过程文档 | GitHub **`yclenove/patchbay-doc`**（与公开 **`yclenove/patchbay`** 分仓；当前工作区可能不含该仓库） |

**双仓**：公开仓放代码与已定稿 `docs/`；私有 **`patchbay-doc`** 放脑暴与长篇设计。定稿结论应摘要进 `patchbay` 的 `docs/PRODUCT_PLAN.md` 或 `docs/adr/`。勿在任仓提交生产密钥。

## 综合来源说明

当前仓库规则综合自作者其它项目中的实践：**`telegram-query-bot`**（`.cursor/rules`）、**`opencode-sync`**（`AGENTS.md` + `.cursor/rules`）、**`im-bot-hub`**（`CLAUDE.md`），并裁剪掉 **Java / Spring / MyBatis / OpenCode CLI** 等与 Patchbay 无关的条目，统一为 **Go + Vue + Postgres + TG/Discord** 语境。
