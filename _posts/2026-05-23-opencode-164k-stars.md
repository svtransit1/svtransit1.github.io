---
layout: post
title: "「现在开源里最像 Claude Code 的东西是什么?」"
date: 2026-05-23 18:10:34 +0800
source: https://github.com/anomalyco/opencode
hero: /assets/opencode-164k-stars/2026-05-23_1801_opencode-164k-stars-hero-raw.png
topic_tags: [opencode, ai-coding-agent, open-source, claude-code, terminal, anomaly]
---

答案是 OpenCode。今天(5 月 23 日)它发了 v1.15.10——一个非常普通的小版本号——但摆出几个数字一起看,这个项目其实已经不普通了。

OpenCode 是 Anomaly(也就是做 terminal.shop 那家)在搞的一个开源 AI coding agent。GitHub 上现在 16.4 万颗星,19400 个 fork,13334 个 commit,MIT 许可证。对比一下:Claude Code 的开源相关仓库大概在 7.1 万星这个量级。OpenCode 在 star 数上是它的两倍多。

它和 Claude Code 最根本的区别,在 model provider 这一头。Claude Code 锁定 Anthropic 的模型,Cursor / Copilot 各自绑定自家选择。OpenCode 走的是反过来的路:75+ provider,Anthropic、OpenAI、Google Gemini、本地 Ollama 全都能接。你想换模型,就是改个配置;不用换工具,也不用换工作流。

实际用上来,它内置两个 agent:build agent 做写代码,plan agent 是 read-only 的分析。装法也多:npm、Homebrew、Windows/Linux 包管理器都能装,还出了一个 beta 的桌面 app——意思是它不再只是个终端 CLI,正在往更通用的方向走。

那要不要从 Claude Code 换过来?如果你重度用 Anthropic 一家的模型、并且觉得 Claude Code 现成的 hook、skill 这套生态够用,留着没问题。如果你的工作流里要在多家模型之间切——白天用 Claude、晚上跑本地 Ollama 实验,或者团队里有人坚持 GPT——OpenCode 几乎是现在唯一一个把多 provider 当一等公民来做的开源选项。这就是它两个月内冲到 16 万星的真实原因。

原文链接放在第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #OpenCode #ClaudeCode #开源 #AI编程
