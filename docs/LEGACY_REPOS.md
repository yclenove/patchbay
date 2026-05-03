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

## 与 `docs/PRODUCT_PLAN.md` 的关系

产品阶段、竞品、不做清单以 **`docs/PRODUCT_PLAN.md`** 为准；本文件只解决「旧代码在哪」。
