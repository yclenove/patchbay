# Claude Code — Patchbay 项目说明

本文件在每次会话开始会被读取。请优先遵守本文与 `docs/PRODUCT_PLAN.md`。

## 项目是什么

**Patchbay**：自托管的 Telegram（主）/ Discord（次）消息中继与规则引擎，带 Web 控制台与 Webhook 扩展；默认强调 **防循环、防炸群、可观测**。官方仓库：https://github.com/yclenove/patchbay

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
5. 大改动前用 **Plan mode** 出方案；小步提交、保持 `main` 可构建。

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
| `docs/DEV.md` | 本地开发（占位，随 Phase 0 填命令） |
| `docs/adr/` | 架构决策（ADR），一事一文 |
| `CONTRIBUTING.md` | 贡献与 PR 约定 |
| `SECURITY.md` | 漏洞报告 |
| `README.md` | 对外简介与快速开始 |
