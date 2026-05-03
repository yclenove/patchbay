# 文档结构说明

仓库文档分两类：**随 Git 发布的正式文档**，与 **仅本机的本地补充文件**（默认不进入远端，避免个人工作流与公共仓库混杂）。

## 1. 随仓库发布（远端可见）

| 路径 | 用途 |
|------|------|
| `README.md` | 项目入口（**中文为主**）、产品摘要、快速开始 |
| `README.en.md` | 英文版入口（与中文版互链） |
| `docs/PRODUCT_PLAN.md` | 产品与技术规划 |
| `docs/DEV.md` | 本地环境、Docker Postgres |
| `docs/LEGACY_REPOS.md` | 旧项目对照 |
| `docs/adr/` | 架构决策 |
| `CONTRIBUTING.md` / `SECURITY.md` / `LICENSE` | 贡献、安全、许可 |
| `docs/templates/ai-local/` | 可选：本地编辑器/辅助工具用的**模板**，按需复制到仓库根（见该目录 `README.md`） |

## 2. 仅本机（已 `.gitignore`）

| 路径 | 说明 |
|------|------|
| `/CLAUDE.md` | 从 `docs/templates/ai-local/CLAUDE.md` 复制到根目录后使用 |
| `/AGENTS.md` | 从模板复制 |
| `.cursor/rules/*.mdc` | 从 `docs/templates/ai-local/cursor-rules/` 复制 |

克隆后若使用上述工具，可按 **`docs/templates/ai-local/README.md`** 一次性复制；不复制不影响阅读正式文档与构建（待代码落地后）。

## 3. 可选：在本地 `.cursor/rules/` 追加的约定

若需加强 IDE 约束，可在**本地** `.cursor/rules/` 增加 `.mdc`，例如：

- **API 破坏性变更**：`/api/v1` 弃用策略、响应错误码表。  
- **数据库迁移**：命名、回滚策略、禁止在生产自动 `down`。  
- **发布与版本**：SemVer、`CHANGELOG` 与 tag 对齐。  
- **国际化**：控制台中英文案与 key 命名约定。  

需要团队共享的补充约定时，可经 PR 更新 **`docs/templates/ai-local/`** 下的模板；与产品无关的纯个人习惯请留在本机、勿提交。
