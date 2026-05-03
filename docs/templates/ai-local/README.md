# 本地编辑器辅助规则（模板，不提交远端）

本目录**随仓库提交**，供需要的人在克隆后复制到仓库根；复制后的 **`CLAUDE.md`、`AGENTS.md`、`.cursor/rules/`** 已在根 `.gitignore` 中排除，**不会**进入远端。

## 一次性设置（Linux / WSL / macOS）

在**仓库根目录**执行：

```bash
cp docs/templates/ai-local/CLAUDE.md ./CLAUDE.md
cp docs/templates/ai-local/AGENTS.md ./AGENTS.md
mkdir -p .cursor/rules
cp docs/templates/ai-local/cursor-rules/*.mdc .cursor/rules/
```

## PowerShell（Windows）

在仓库根目录：

```powershell
Copy-Item docs\templates\ai-local\CLAUDE.md .\CLAUDE.md -Force
Copy-Item docs\templates\ai-local\AGENTS.md .\AGENTS.md -Force
New-Item -ItemType Directory -Force -Path .cursor\rules | Out-Null
Copy-Item docs\templates\ai-local\cursor-rules\*.mdc .cursor\rules\ -Force
```

## 更新模板后

若远端更新了 `docs/templates/ai-local/`，可再执行上述复制覆盖本地文件（注意备份你对本地的个性化修改）。
