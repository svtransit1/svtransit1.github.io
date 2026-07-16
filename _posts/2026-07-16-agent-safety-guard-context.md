---
layout: post
title: "🛡️ 给 AI coding agent 装一道\"防手滑\"的护栏,听起来很简单:看见 rm -rf、git reset --hard、DROP TABLE 就拦下来。但真动手做过的人都清楚,识别危险命令是简单那一半,难的那一半是——别误伤。"
date: 2026-07-16 12:17:48 +0800
source: https://github.com/Dicklesworthstone/destructive_command_guard
hero: /assets/agent-safety-guard-context/2026-07-16_1100_agent-safety-guard-context-hero.png
topic_tags: [agent-safety, claude-code, coding-agents, guardrails, tooling]
---

⚠️ 一个只会正则匹配的护栏,会把你写在注释里、写在文档 heredoc 里、写在字符串里的那句 rm -rf 也一并拦掉。误报几次,开发者嫌烦,顺手就把它关了。护栏做得再严,被关掉就等于零。

这几天在 GitHub 冲起来的 dcg(destructive command guard,4.8k star)正是冲着这道坎去的。Rust 写的,三层结构:先用正则快筛,再从 heredoc、内联脚本里把真正要执行的内容抽出来,最后按语言做一遍 AST 匹配——只拦真要跑的那条,注释和字符串里的照样放过。它还特意做成 fail-open:遇到超时、分析不了的情况,宁可放行也不卡你的活,200 毫秒是硬上限。

拦得住,还不惹人烦——这才是一道安全护栏能被长期留在系统里的真正前提。🧯

你给 agent 设的那些限制,是真在用,还是早被你自己关掉了?

转给那个给 agent 开了满权限的同事。

来源 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AI安全 #AIagent #编程工具
