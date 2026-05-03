# Patchbay

**简体中文（主文档）：** [README.md](README.md)

Self-hosted **Telegram-first / Discord-second** relay and rules: route messages across groups, channels, and webhooks with a **web console** and outbound events. Defaults emphasize **loop prevention**, **safe fan-out**, and **observability**—not “every protocol under one roof.”

---

## What problem it solves

- **Communities & maintainers**: announcements across groups/channels, read-only mirrors, keywords and routing—with fewer foot-guns like accidental bidirectional sync or runaway spam.  
- **Small teams**: controlled TG ↔ Discord paths, config and status in one console for audit and troubleshooting.  
- **Developers**: a unified event shape for hooks, alerts, or automation (see **PRODUCT_PLAN** for Webhook/extension details).

---

## Capabilities at a glance

| Area | Notes |
|------|--------|
| Relay & rules | Route between TG/Discord and webhooks by policy; safety and loop awareness by design |
| Console | Vue 3 admin UI; config, health, and key metrics (rolling out with Phase 0/1) |
| Self-host | Go binary + PostgreSQL, Docker Compose; data and control plane stay on your side |

Architecture, event model, and phased roadmap: **[docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)** (Chinese; product source of truth).

---

## Who it’s for

Technical communities, open-source maintainers, cross-border teams, and operators who live on **Telegram** and want a **narrow protocol surface, light ops, and strong defaults**—not a Matterbridge-style mega-bridge or a full customer-support SaaS.

---

## Compared to common options (summary)

| Aspect | Tools like Matterbridge | **Patchbay** |
|--------|-------------------------|--------------|
| Focus | Many-protocol bridge | **Deep TG + secondary Discord + rules + console** |
| Onboarding | Config-heavy | **Compose + guided defaults (goal)** |
| Safety | Often operator-dependent | **Product defaults for one-way & loop awareness (goal)** |

Full comparison: [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) §4.

---

## Explicitly out of scope (v1.x)

- Personal WeChat bots, unofficial WhatsApp personal APIs, and similar grey areas.  
- Enterprise IM SSO / approval “full stack” replacements.  
- A promise of 100% semantic parity across platforms (APIs differ).

Experimental features and boundaries: **[docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md)** appendix.

---

## Stack & license

| Item | Detail |
|------|--------|
| Runtime | Go (relay + API + bot gateway) |
| Console | Vue 3 / TypeScript / Vite |
| Data | PostgreSQL |
| License | [MIT](LICENSE) · Copyright (c) 2026 yclenove |

You must comply with Telegram, Discord, and other platforms’ terms and applicable law; you are responsible for group content and your deployment.

---

## Status

**Phase 0** in progress: Compose, minimal API, console skeleton, and dev docs. Issues and PRs welcome.

---

## Quick start

```bash
git clone https://github.com/yclenove/patchbay.git
cd patchbay
# Full-stack Compose: see docs/DEV.md when documented
```

**PostgreSQL-only** dev instance: **[docs/DEV.md](docs/DEV.md)**.

---

## Docs & contributing

| Doc | Purpose |
|-----|---------|
| [docs/PRODUCT_PLAN.md](docs/PRODUCT_PLAN.md) | Product & technical plan (authoritative) |
| [docs/DEV.md](docs/DEV.md) | Local dev, Docker, database |
| [docs/LEGACY_REPOS.md](docs/LEGACY_REPOS.md) | Related legacy repos |
| [docs/DOCUMENTATION.md](docs/DOCUMENTATION.md) | How repo docs are organized |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute; **commit messages in Chinese** |
| [SECURITY.md](SECURITY.md) | Vulnerability reporting |
| [docs/adr/](docs/adr/) | Architecture decision records |
