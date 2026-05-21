---
name: open-design-navigator
description: Use Open Design from nexu-io/open-design as the first design workflow when the user asks for UI, web pages, HTML reports, dashboards, posters, decks, visual systems, design critique, or says "利用这个设计".
version: 1.0.0
triggers:
  - "利用这个设计"
  - "接入设计 skill"
  - "open-design"
  - "nexu-io/open-design"
  - "设计稿"
  - "页面设计"
  - "网页原型"
  - "HTML 报告"
  - "可视化报告"
  - "海报"
  - "PPT 设计"
  - "仪表盘"
  - "UI/UX"
metadata:
  source: "https://github.com/nexu-io/open-design"
  local_repo: "/Users/xiemiaoyang/Documents/New project/open-design"
  category: design
---

# Open Design Navigator

Use this skill as the design entrypoint for the current workspace.

Open Design is a design-focused skill and template catalogue. Prefer it when a task asks for a concrete visual output: website, app screen, HTML report, presentation, poster, social card, dashboard, design system, motion artifact, or design critique.

## Source And Local Runtime

- GitHub: `https://github.com/nexu-io/open-design`
- Existing local repo: `/Users/xiemiaoyang/Documents/New project/open-design`
- Runtime requirement: Node `~24`, pnpm `10.33.2`
- Main command family: `pnpm tools-dev`

Useful runtime commands from the Open Design repo:

```bash
source "$HOME/.nvm/nvm.sh" && nvm use 24
corepack pnpm --version
pnpm tools-dev status
pnpm tools-dev check
pnpm tools-dev start web
pnpm tools-dev start desktop
pnpm tools-dev stop
```

Daemon health check:

```bash
curl http://127.0.0.1:59126/api/health
```

Expected healthy shape:

```json
{"ok":true,"version":"0.5.0"}
```

If the daemon binary is missing, build it first:

```bash
pnpm --filter @open-design/daemon build
pnpm install
```

## How To Route User Requests

Before designing, choose the closest Open Design skill or template and read its `SKILL.md` plus any referenced `assets/`, `references/`, `templates/`, or example files.

Common routing:

| User need | Prefer these Open Design skills/templates |
| --- | --- |
| Web page, product page, landing page, prototype | `web-prototype`, `web-artifacts-builder`, `web-design-guidelines`, `saas-landing`, `pricing-page`, `waitlist-page` |
| HTML report, business dashboard, visualized analysis | `data-report`, `finance-report`, `flowai-live-dashboard-template`, `trading-analysis-dashboard-template`, `social-media-dashboard` |
| Slides, HTML PPT, management presentation | `html-ppt`, `guizang-ppt`, `deck-open-slide-canvas`, `deck-guizang-editorial`, `kami-deck` |
| Poster, social image, Xiaohongshu-style card | `image-poster`, `magazine-poster`, `social-carousel`, `card-xiaohongshu`, `card-twitter` |
| Mobile UI | `mobile-app`, `mobile-onboarding`, `swiftui-design` |
| Design system, UI audit, critique | `web-design-guidelines`, `brand-guidelines`, `taste-skill`, `critique`, `ui-skills` |
| Animation, video, motion frames | `motion-frames`, `video-hyperframes`, `sprite-animation`, `vfx-text-cursor` |
| 3D or shader work | `threejs`, `algorithmic-art` |

If the local repo appears stale or a listed folder is missing, check the live upstream directory:

```text
https://github.com/nexu-io/open-design/tree/main/skills
```

## Working Rules

1. Treat "利用这个设计" as an instruction to consult Open Design first.
2. Do not stop at a recommendation when the user asks for an artifact; create the artifact and verify it.
3. Use the chosen Open Design skill's example or template when available instead of recreating structure from scratch.
4. For HTML outputs, verify locally in a browser or via an HTTP status check before finishing.
5. For visual deliverables, check layout density, text overflow, spacing, hierarchy, and mobile fit.
6. If Open Design cannot be used directly, continue with the closest local design workflow and state the limitation briefly.

## Install Or Refresh Notes

If the repo needs to be installed again in a new workspace:

```bash
git clone --depth 1 https://github.com/nexu-io/open-design.git open-design
cd open-design
source "$HOME/.nvm/nvm.sh" && nvm install 24 && nvm use 24
corepack enable
pnpm install
pnpm --filter @open-design/daemon build
pnpm install
pnpm tools-dev check
```

Plain `git clone` may fail on slow GitHub HTTP/2 connections; use the shallow clone form above first.
