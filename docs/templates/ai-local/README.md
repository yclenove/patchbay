# AI 本地配置模板（不提交远端）

本目录文件**随 Git 提交**，供协作者复制到仓库根使用；复制后的 **`CLAUDE.md`、 `AGENTS.md`、 `.cursor/rules/`** 已在根目录 `.gitignore` 中排除，**不会 push 到 GitHub**。

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

若远端更新了 `docs/templates/ai-local/`，可再执行上述复制覆盖本地 AI 文件（注意备份你对本地的个性化修改）。
