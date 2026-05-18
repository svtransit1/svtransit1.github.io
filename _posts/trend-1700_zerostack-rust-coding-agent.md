---
layout: post
title: "本周 HN 前排的一件事:有人用 Rust 把\"coding agent\"重新做了一遍——8.9 MB 二进制,~10 MB 内存,跟 opencode / Claude Code 的 JS 实现比小了 30 倍。"
date: trend 17:12 +0800
source: https://github.com/gi-dellav/zerostack
hero: /assets/1700_zerostack-rust-coding-agent/trend_2026-05-17_1700_zerostack-rust-coding-agent-hero.png
topic_tags: [rust, coding-agent, mcp, opencode, claude-code, zerostack]
---

背景说清楚——过去一年 coding agent 圈基本是 TypeScript / Node 主场。Anthropic 的 Claude Code、Codex CLI、Cursor 的 background-agent、Continue、opencode 这一堆,后端不一致但 CLI 那一层基本都是 Node。Node 启动慢 + 内存大,装满 npm 依赖之后一个简单 agent 进程动辄占 300 MB,跑在边缘机器、容器、CI runner 里就很别扭。

`gi-dellav/zerostack` 这周冲到 HN 第二条,378 分 151 评论,283 star。作者把整个 coding agent 重写成 Rust,完整功能用了 ~7K LOC,编译出来的二进制 8.9 MB。

三条对得起对比的轴:

体积——zerostack 8.9 MB 二进制 vs opencode/Continue 一类的 Node 安装包动辄 100MB+(还要 Node runtime),差距数十倍。

内存——zerostack 空 session ~8 MB,工作时 ~12 MB(README 原话)vs JS-based agent 一般 ~300 MB。这个差距是 30 倍以上,可以在低端 VPS 或者一个 Docker container 里同时跑十几个 zerostack 实例。

provider 不锁死——OpenRouter / OpenAI / Anthropic / Gemini / Ollama / 自定义 provider 全支持。MCP 也是编译选项,需要时打开。

谁该用?

CI runner 跑 agent 测试、edge box 上跑 自动化 workflow、想在自己机器一次跑多个 agent 实例的人——zerostack 的轻量直接对上痛点。

如果你已经在 Claude Code 里 deep workflow + Cursor IDE 集成,zerostack 暂时还替代不了——它定位是 CLI agent 不是 IDE 插件,功能集相比 Claude Code 也少。

GPL-3.0 license。受 pi 和 opencode 启发(README 原话)。

更深的信号——Rust 在 LLM 工具链里的份额在涨。前两年是 Python / Node 一统天下,这两个月 Rust-based agent / MCP server / inference runtime 开始爆发(orthrus、zerostack、各种 MCP server)。原因是 LLM 工作负载本质 IO-bound + 长期运行,Rust 的内存安全 + 启动速度刚好对症。

转给那个还在用 npm install 装 coding agent 的朋友——这边的 binary 比你的 node_modules 小一千倍。

关注 @svtransit1 · 写给真在用 AI 的人

完整链接 · 评论区取 ↓

#AI #Rust #ClaudeCode #CodingAgent #MCP
