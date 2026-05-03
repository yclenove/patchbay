# Patchbay

自托管 **Telegram（主） / Discord（次）** 消息中继与规则引擎，带 Web 控制台与 Webhook 扩展；强调 **防循环、防炸群、可观测**。

- **仓库**：https://github.com/yclenove/patchbay  
- **技术栈**：Go（`patchbay` 单二进制）+ Vue 3 + PostgreSQL + Docker Compose  
- **产品规划**：[docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)  
- **历史代码索引**（对照用）：[docs/LEGACY_REPOS.md](docs/LEGACY_REPOS.md)  
- **Claude Code** 请先读根目录 [CLAUDE.md](CLAUDE.md)

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

待定（规划建议 MIT 或 Apache-2.0）。
