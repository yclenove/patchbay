# Claude Code — Patchbay 项目说明

> **使用方式**：本文件为模板。请**复制到仓库根目录**并命名为 `CLAUDE.md`（该文件已列入 `.gitignore`，**不会**提交到远端）。Claude Code 默认读取根目录 `CLAUDE.md`。

本文件在每次会话开始会被读取。请优先遵守本文与 `docs/PRODUCT_PLAN.md`。  
**Cursor IDE** 补充规则：将同目录下 **`cursor-rules/*.mdc`** 复制到仓库根 **`.cursor/rules/`**（该目录默认不提交远端）。若有冲突以本文 + `docs/PRODUCT_PLAN.md` 为准。  
另在根目录放置从本目录复制的 **`AGENTS.md`**（供读 `AGENTS.md` 的工具使用）。

## 项目是什么

**Patchbay**：自托管的 Telegram（主）/ Discord（次）消息中继与规则引擎，带 Web 控制台与 Webhook 扩展；默认强调 **防循环、防炸群、可观测**。官方仓库：https://github.com/yclenove/patchbay

## 文档语言（综合 opencode-sync / 旧项目习惯）

- **用户可读文档**（README、`docs/*.md`）：以 **中文** 为主，或 **中英对照**；命令名、配置键、包名、环境变量、URL **保持英文原文**。
- **提交信息**：**请使用中文**，简短、一事一提交（与 `CONTRIBUTING.md` 一致）。

## 对外契约

- 仅依赖 **Telegram Bot API、Discord Bot API** 的公开能力；平台行为变更时适配层需重新验证。
- **配置、路由表、Webhook URL** 等属于对外契约，变更时同步文档与 `CHANGELOG.md`（有用户可见变化时）。

## 已定技术栈（不要擅自改栈）

| 层级 | 选型 |
|------|------|
| 后端 | **Go 1.22+**，单二进制 **`patchbay`**（子命令如 `serve`、`migrate`；可选 `worker`） |
| 前端 | **Vue 3 + TypeScript + Vite**（控制台） |
| 数据库 | **PostgreSQL 15+**（不用 SQLite 作主库） |
| 部署 | **Docker Compose**：`patchbay` + `postgres` + 可选 `nginx`（托管前端 `dist`） |
| IM | 仅 **Telegram Bot API、Discord Bot API**；不要引入 JVM/Node 作为核心运行时 |

建议目录：`cmd/patchbay`、`internal/relay`（或 `internal/core`）、`internal/bot`、`internal/api`、`internal/store`、`web/`（Vue）。

## 产品规划与阶段（必读）

完整规划见 **`docs/PRODUCT_PLAN.md`**（路线图、Phase 0–4、NFR、风险、竞品对比）。

当前优先级：**Phase 0**（README、Compose、Postgres、最小控制台登录）→ **Phase 1**（TG 单向广播 MVP）。不要跳过 Phase 0 直接堆功能。

## 工程质量（综合 opencode-sync / im-bot-hub）

- **小步可构建**：优先小而正确的改动；大改动前用 **Plan mode** 出方案。
- **不吞异常**：错误要带上下文返回或记录；用户可见输出简洁，避免直接堆栈。
- **文档同步**：命令、Compose、API、阶段边界变化时更新 `README.md` / `docs/DEV.md` / `docs/PRODUCT_PLAN.md` 等相关文档。
- **测试门槛**：Go 默认 **`go test ./...`**；`web/` 落地后加上前端 build（及后续测试命令）。

## 历史代码在哪里看（只读参考，不复制进本仓也可）

旧实现用于 **理解业务与边界**，**Patchbay 目标栈是全 Go + Vue**，Java 老项目不要继续扩展。

| 仓库 | 链接 | 说明 |
|------|------|------|
| telegram-relay | https://github.com/yclenove/telegram-relay | Go 中继逻辑参考 |
| telegram-relay-admin | https://github.com/yclenove/telegram-relay-admin | Vue 管理端参考 |
| telegram-query-bot | https://github.com/yclenove/telegram-query-bot | Java，**非目标栈** |
| im-bot-hub | https://github.com/yclenove/im-bot-hub | Java，**非目标栈** |

更细的链接、克隆说明与 **本机 `H:\aicoding` 下已检出路径**见 **`docs/LEGACY_REPOS.md`**。对照 Go 中继请用 **`H:\aicoding\telegram-relay`** 并与 `origin/main` 同步；勿依赖未 pull 的旧副本目录。

## 开发约束

1. **不要**提交真实 Bot Token、`.env` 密钥；使用 `.env.example` 占位。  
2. **不要**实现个人微信非官方协议、赌资/抽水相关能力。  
3. 默认路由：**单向**优先；双向必须带环路检测与显式确认（见规划文档）。  
4. 日志：结构化；默认避免持久化消息全文（隐私）。  
5. 小步提交、保持 `main` 可构建。

## 常用命令（占位，随仓库填充后更新）

```bash
# Go
go build -o patchbay ./cmd/patchbay
go test ./...

# 前端（待 web/ 创建后）
# cd web && npm ci && npm run build

# 数据库迁移（待引入 migrate 工具后补充）
```

## 文档索引

| 文件 | 用途 |
|------|------|
| `docs/PRODUCT_PLAN.md` | 产品与技术规划全文 |
| `docs/LEGACY_REPOS.md` | 旧仓库列表与本机路径 |
| `docs/DEV.md` | 本地开发（含 Docker Postgres） |
| `docs/adr/` | 架构决策（ADR），一事一文 |
| `.cursor/rules/*.mdc`（本地） | 从 `docs/templates/ai-local/cursor-rules/` 复制 |
| `AGENTS.md`（本地） | 从本目录复制到根目录 |
| `CONTRIBUTING.md` | 贡献与 PR 约定 |
| `SECURITY.md` | 漏洞报告 |
| `README.md` | 对外简介与快速开始 |
