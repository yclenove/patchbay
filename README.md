# Patchbay

**English:** [README.en.md](README.en.md)

自托管的 **Telegram（主）/ Discord（次）** 消息中继与规则引擎：在群、频道与 Webhook 之间做可控路由，配套 **Web 控制台** 与出站事件。默认面向 **防循环、可控广播、可观测** 的生产习惯，而不是「协议越多越好」。

---

## 解决什么问题

- **社群与项目方**：多群/多频道公告、只读镜像、关键词与路由规则，少踩「误双向、刷爆群、找不到哪条没同步」的坑。  
- **小团队**：TG 与 Discord 之间受控互通，配置与状态集中在控制台，方便审计与排障。  
- **开发者**：统一事件形态对接自建服务、告警或自动化（详见产品规划中的 Webhook/扩展章节）。

---

## 能力概览

| 能力 | 说明 |
|------|------|
| 中继与规则 | 按路由与策略在 TG/Discord 与 Webhook 之间转发；强调默认安全与环路意识 |
| 控制台 | Vue 3 管理界面；配置、健康与关键指标可见（随 Phase 0/1 逐步落地） |
| 自托管 | Go 单二进制 + PostgreSQL，Docker Compose 交付；数据与控制面在你侧 |

更细的模块划分、事件模型与阶段路线图见 **[docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)**。

---

## 适合谁

技术社群、开源维护者、跨境小团队、以 Telegram 为主阵地的运营者——需要 **窄协议、轻运维、硬默认**，而不是 Matterbridge 式全协议桥或完整客服 SaaS。

---

## 与常见路线相比（摘要）

| 维度 | Matterbridge 等 | **Patchbay** |
|------|------------------|--------------|
| 心智 | 多协议桥 | **TG 深、Discord 次 + 规则 + 控制台** |
| 上手 | 偏配置驱动 | **Compose + 向导式默认（目标）** |
| 防事故 | 高度依赖经验 | **产品级默认单向与环路意识（目标）** |

完整对比见 [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) 第 4 节。

---

## 明确不做（v1.x 范围）

- 个人微信机器人、非官方 WhatsApp 个人号等灰区协议。  
- 替代企业 IM 的 SSO/审批流全家桶。  
- 承诺各平台 100% 语义一致（能力差异客观存在）。

实验能力与边界以 **[docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)** 附录为准。

---

## 技术栈与许可

| 项目 | 内容 |
|------|------|
| 运行时 | Go（中继 + API + Bot 网关） |
| 控制台 | Vue 3 / TypeScript / Vite |
| 数据 | PostgreSQL |
| 许可 | [MIT](LICENSE) · Copyright (c) 2026 yclenove |

使用 Telegram、Discord 及其他集成时，请遵守各平台服务条款与适用法律法规；你对群内容与部署环境负责。

---

## 当前进度

**Phase 0**：Compose、最小 API、控制台骨架与开发文档持续完善中。欢迎 Issue 与 PR。

---

## 快速开始

```bash
git clone https://github.com/yclenove/patchbay.git
cd patchbay
# 全栈 Compose 就绪后见 docs/DEV.md
```

仅启动 **PostgreSQL** 做本地开发：见 **[docs/DEV.md](docs/DEV.md)**。

---

## 文档与贡献

| 文档 | 说明 |
|------|------|
| [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) | 产品与技术规划（主事实来源） |
| [docs/DEV.md](docs/DEV.md) | 本地开发、Docker、数据库 |
| [docs/LEGACY_REPOS.md](docs/LEGACY_REPOS.md) | 相关历史仓库 |
| [docs/DOCUMENTATION.md](docs/DOCUMENTATION.md) | 仓库文档结构说明 |
| [CONTRIBUTING.md](CONTRIBUTING.md) | 贡献方式；**提交说明请使用中文** |
| [SECURITY.md](SECURITY.md) | 漏洞报告 |
| [docs/adr/](docs/adr/) | 架构决策记录 |
