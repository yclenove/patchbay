# 历史项目仓库（对照阅读）

Patchbay 为 **全新主仓**（全 Go + Vue + Postgres）。下列仓库为作者此前相关实现，**仅作行为与边界参考**；不必整体迁移，可按模块借鉴。

## 推荐阅读顺序

1. **[telegram-relay](https://github.com/yclenove/telegram-relay)**（Go）— 中继、转发、与 Telegram 交互的核心思路。  
2. **[telegram-relay-admin](https://github.com/yclenove/telegram-relay-admin)**（Vue）— 管理台页面与交互可参考。  
3. Java 仓库仅当需要查「曾做过哪些命令/接口」时浏览，**新功能不要写在 Java 里**。

## 仓库一览

| 名称 | URL | 语言 | 与 Patchbay 关系 |
|------|-----|------|------------------|
| telegram-relay | https://github.com/yclenove/telegram-relay | Go | **主要参考**中继实现 |
| telegram-relay-admin | https://github.com/yclenove/telegram-relay-admin | Vue | **主要参考**控制台 UI |
| telegram-query-bot | https://github.com/yclenove/telegram-query-bot | Java | 非目标栈；可查 Bot 命令设计 |
| im-bot-hub | https://github.com/yclenove/im-bot-hub | Java | 非目标栈；多 IM 设想曾在此，Patchbay 收敛为 TG/Discord |

## 本地克隆（可选）

```bash
mkdir -p ~/ref && cd ~/ref
git clone https://github.com/yclenove/telegram-relay.git
git clone https://github.com/yclenove/telegram-relay-admin.git
```

在 Claude Code / Cursor 中可同时打开 **本仓库 `H:\aicoding\patchbay`** 与 **`ref/telegram-relay`** 文件夹（多根工作区），便于对照；注意 **不要**把 ref 目录误提交进 Patchbay。

## 本机已检出路径（`H:\aicoding`，Windows）

以下目录在作者当前磁盘上**已存在**（与 GitHub 仓库对应；主开发代码一般在各仓根目录或 `backend/`）。

| GitHub 仓库 | 本机路径 | 备注 |
|-------------|----------|------|
| [telegram-relay](https://github.com/yclenove/telegram-relay) | **`H:\aicoding\telegram-relay`** | **唯一推荐的本地对照路径**；与 `origin/main` 保持 `git pull`。当前 `main` 已含：接入凭证（ingest）、规则预设、部署文档、打包脚本等（见该仓最新提交）。 |
| 同上（可选副本） | **`H:\aicoding\telegram-notification`** | 与上为同一远程仓库的历史目录名；若已 `pull` 到与 `telegram-relay` 相同提交，**二选一即可**，避免两处并行修改；不再需要时可删除或只作备份。 |
| [telegram-relay-admin](https://github.com/yclenove/telegram-relay-admin) | **`H:\aicoding\telegram-relay-admin`** | Vue 管理台；README 写明通过 `/api/v2` 与 relay 通信。 |
| [telegram-query-bot](https://github.com/yclenove/telegram-query-bot) | **`H:\aicoding\telegram-query-bot`** | Java（`backend/pom.xml`）；仓内若有 `.claude/worktrees/`，为本地工作树副本，**以根目录 `backend` 为主**即可。 |
| [im-bot-hub](https://github.com/yclenove/im-bot-hub) | **`H:\aicoding\im-bot-hub`** | Java（`backend/pom.xml`）；同上，注意 `.claude/worktrees/` 仅为工具生成目录。 |

## 与 `docs/PRODUCT_PLAN.md` 的关系

产品阶段、竞品、不做清单以 **`docs/PRODUCT_PLAN.md`** 为准；本文件只解决「旧代码在哪」。
