---
layout: post
title: "「用 `claude -p` 起多 agent fleet，会不会哪天被 Anthropic 封？」——这问题在 Claude Code 圈里飘了几个月，今天 OpenClaw 官方给了答案。"
date: 2026-04-22 00:08:25 +0800
source: https://docs.openclaw.ai/providers/anthropic
hero: /assets/openclaw-claude-cli-ok/2026-04-22_0005_openclaw-claude-cli-ok-hero.png
topic_tags: [claude-code, openclaw, anthropic, policy]
---

文档更新写得直白：Anthropic 的人告诉他们，「OpenClaw 风格的 Claude CLI 使用方式重新被允许」。之前这条路灰了一阵，不少把 Claude Code 当后端工作单元的人心里一直悬着。openclaw、cowork、managed agents、昨天聊过的 claude-mem，全都靠这条路能跑。

留的退路是「除非 Anthropic 发布新政策推翻」——现在明确 OK，但没写成正式条款，还是 vibe 授权。

两处要注意：生产级 always-on gateway 还是推荐走 API key，稳定性和合规线更清晰；`context-1m-*` 这个 1M 上下文 beta header 用老的 OAuth token（`sk-ant-oat-*`）会被拒，只能走 API key。

HN 上这条讨论 12 小时冲到 363 分，评论区明显松了一口气。

原帖：docs.openclaw.ai/providers/anthropic

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #ClaudeCode #openclaw #Anthropic
