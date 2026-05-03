# 本地开发说明

> **状态**：主代码（`cmd/patchbay`、`web/` 等）尚未落地；本文随 Phase 0 进展更新。

## 环境要求（目标）

| 组件 | 版本（建议） |
|------|----------------|
| Go | 1.22+ |
| Node.js | 20 LTS（前端就绪后） |
| PostgreSQL | 15+ |
| Docker | 用于 Compose 一键环境 |

## 克隆与文档

```bash
git clone https://github.com/yclenove/patchbay.git
cd patchbay
```

- 产品规划：[PRODUCT_PLAN.md](PRODUCT_PLAN.md)  
- 对照旧实现：[LEGACY_REPOS.md](LEGACY_REPOS.md)  

## 待补充（代码就绪后填写）

- [ ] 复制 `.env.example` → `.env` 并填写说明  
- [ ] `docker compose up` 或分步启动 `postgres` + `patchbay`  
- [ ] 数据库迁移命令（如 `patchbay migrate`）  
- [ ] 前端 `cd web && npm ci && npm run dev` 与 API 代理配置  

## 与旧仓库并行开发

若本机同时打开 [telegram-relay](https://github.com/yclenove/telegram-relay) 对照，路径见 [LEGACY_REPOS.md](LEGACY_REPOS.md)；**勿**将旧仓路径或 `node_modules` 提交进 Patchbay。
