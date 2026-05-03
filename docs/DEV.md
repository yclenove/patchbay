# 本地开发说明

> **状态**：主代码（`cmd/patchbay`、`web/` 等）尚未落地；本文随 Phase 0 进展更新。

## 环境要求（目标）

| 组件 | 版本（建议） |
|------|----------------|
| Go | 1.22+ |
| Node.js | 20 LTS（前端就绪后） |
| PostgreSQL | 15+ |
| Docker | 用于 Compose 一键环境 |

## 在 WSL 里用 Docker 跑 PostgreSQL（推荐）

不一定要在 WSL 里 `apt install postgresql`；用 **Docker** 即可，版本与生产更接近（本仓库示例为 **Postgres 17**）。

**前提**：WSL 里已安装 Docker（Docker Desktop 开启 WSL 集成，或在 WSL 内安装 `docker.io` + 配好 `docker` 组）。

在 **WSL 终端** 中（先 `cd` 到本仓库根目录，或把 `-f` 换成该文件的绝对路径）：

```bash
cd ~/path/to/patchbay   # 或 Windows 挂载路径如 /mnt/h/aicoding/patchbay

docker compose -f deploy/docker-compose.postgres-dev.yaml up -d
docker compose -f deploy/docker-compose.postgres-dev.yaml ps
```

默认连接（**仅开发**，密码请自行改掉再提交环境文件）：

```text
postgres://patchbay:patchbay_dev_change_me@127.0.0.1:5432/patchbay?sslmode=disable
```

从 Windows 上的 Go/IDE 连 WSL 里的容器时：若 Docker 端口映射在 WSL 的 `5432`，一般仍用 **`127.0.0.1:5432`**（Docker Desktop 会转发）；若连不上，再试 **`localhost`** 或查 Docker Desktop 文档中的 WSL2 端口转发说明。

停止并删除数据卷：

```bash
docker compose -f deploy/docker-compose.postgres-dev.yaml down -v
```

## 克隆与文档

```bash
git clone https://github.com/yclenove/patchbay.git
cd patchbay
```

- 产品规划：[PRODUCT_PLAN.md](PRODUCT_PLAN.md)  
- 对照旧实现：[LEGACY_REPOS.md](LEGACY_REPOS.md)  
- 文档分层（人 / AI）：[DOCUMENTATION.md](DOCUMENTATION.md)  
- AI 规则模板（复制到根目录后使用）：[templates/ai-local/README.md](templates/ai-local/README.md)

## 待补充（代码就绪后填写）

- [ ] 复制 `.env.example` → `.env` 并填写说明  
- [x] 仅 Postgres 开发实例：`deploy/docker-compose.postgres-dev.yaml`  
- [ ] 全栈 `docker compose up`（`postgres` + `patchbay`）待主程序落地  
- [ ] 数据库迁移命令（如 `patchbay migrate`）  
- [ ] 前端 `cd web && npm ci && npm run dev` 与 API 代理配置  

## 与旧仓库并行开发

若本机同时打开 [telegram-relay](https://github.com/yclenove/telegram-relay) 对照，路径见 [LEGACY_REPOS.md](LEGACY_REPOS.md)；**勿**将旧仓路径或 `node_modules` 提交进 Patchbay。
