# 参与贡献

Patchbay 尚在 **Phase 0**，欢迎 Issue 与小步 PR。开发前请先阅读：

- [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)（路线图与不做清单）
- [docs/DEV.md](docs/DEV.md)（本地环境、数据库）
- [docs/DOCUMENTATION.md](docs/DOCUMENTATION.md)（仓库文档结构说明；含可选本地编辑器补充文件）

## 基本原则

1. **对齐规划**：大功能先对照 `docs/PRODUCT_PLAN.md` 当前 Phase；明显超出范围的改动请在 Issue 里先讨论。  
2. **小步提交**：一个 PR 聚焦一类变更，便于 review。  
3. **不要**在仓库中提交密钥、真实 Bot Token、生产数据库转储。  
4. **提交信息**：**请使用中文**，简短清晰、一事一条；避免无意义占位符或与改动无关的套话。  
5. **Issue / PR 描述**：中文或英文均可，以能把问题说清楚为准。

## PR 前自检（代码落地后逐步启用）

- `go test ./...`（Go）  
- `go fmt` / 项目选用的 linter  
- `web/` 下 `npm run build`（前端就绪后）

## 行为准则

保持尊重、就事论事；骚扰与歧视性内容不予接受。
