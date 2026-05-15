---
layout: post
title: "tmux 该退休了，Claude Code 自己把多 session 装进一个面板。"
date: trend 12:00:00 +0800
hero: /assets/1100_claude-code-agent-view/trend_2026-05-12_1100_claude-code-agent-view-hero.png
topic_tags: [claude-code, anthropic, agent-view, tmux, multi-session]
---

Anthropic 今天把 Agent View 放进了 Claude Code，目前是 Research Preview，所有付费方案直接可用。

以前要并行跑两三个 session，你得开三个终端 tab，或者上 tmux 来分屏切窗口。现在一条命令 `claude agents` 打开面板，所有正在跑的、正在等你回话的、跑完的 session 全列在一栏里。

它的核心动作就三个：

看一眼就知道哪个 session 卡住等你输入；不用切窗口直接 inline 回一句话让它继续；任意时候跳进某个 session 接着干，不会丢上下文。

配套两个新命令也挺好用——`/bg` 把当前会话扔到后台，`claude --bg "任务描述"` 直接开一个后台 session 自己跑。

这一步其实把 Claude Code 从「单 agent CLI 工具」推到了「多 agent 调度台」。一个开发者同时盯 3-4 个 agent 干活的工作流，第一次有了像样的原生界面。

那些每天开六七个 terminal tab 的人，今天可以清掉桌面了。

链接放在第一条留言。

#ClaudeCode #Anthropic #AI开发
