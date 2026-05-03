# 文档分层说明（给人看的）

Patchbay 把文档分成两类，避免把 **给 AI 的长篇操作说明** 和 **给人看的交付文档** 混在同一套远端可见文件里。

## 1. 随仓库发布（远端可见，给人 + 协作者）

| 路径 | 用途 |
|------|------|
| `README.md` | 项目入口、链接、快速开始 |
| `docs/PRODUCT_PLAN.md` | 产品与技术规划 |
| `docs/DEV.md` | 本地环境、Docker Postgres |
| `docs/LEGACY_REPOS.md` | 旧项目对照 |
| `docs/adr/` | 架构决策 |
| `CONTRIBUTING.md` / `SECURITY.md` / `LICENSE` | 贡献、安全、许可 |
| **`docs/templates/ai-local/`** | **仅模板**：供每人复制出本地 AI 配置，模板本身可审查、可演进 |

## 2. 仅本机（默认不提交远端，给 AI）

| 路径 | 工具 | 说明 |
|------|------|------|
| `/CLAUDE.md`（根目录） | Claude Code | 从 `docs/templates/ai-local/CLAUDE.md` 复制 |
| `/AGENTS.md`（根目录） | 读 AGENTS 的 Agent | 从模板复制 |
| `.cursor/rules/*.mdc` | Cursor | 从 `docs/templates/ai-local/cursor-rules/` 复制 |

以上三项已写入 **`.gitignore`**。新克隆仓库后需要 **按 `docs/templates/ai-local/README.md` 做一次复制**，本地 AI 才有完整上下文。

## 3. 还可选的 Cursor 规则（未建模板时的心智清单）

若你希望继续加强 IDE 约束，可在**本地** `.cursor/rules/` 增加 `.mdc` 例如：

- **API 破坏性变更**：`/api/v1` 弃用策略、响应错误码表。  
- **数据库迁移**：命名、回滚策略、禁止在生产自动 `down`。  
- **发布与版本**：SemVer、`CHANGELOG` 与 tag 对齐。  
- **国际化**：控制台中英文案与 key 命名约定。  

这些是否放进远端模板由你决定；当前策略是 **模板在 `docs/templates/ai-local/`，是否 push 扩展模板 = 仍属「给人看的可审查文本」**。
