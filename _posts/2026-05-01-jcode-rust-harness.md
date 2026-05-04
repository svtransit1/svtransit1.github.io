---
layout: post
title: "一张图看懂 jcode 跟主流 coding agent 的性能差。重点我用橙色标了。"
date: 2026-05-01 12:14:21 +0800
source: https://github.com/1jehuang/jcode
hero: /assets/jcode-rust-harness/2026-05-01_1213_jcode-rust-harness-hero-raw.png
topic_tags: [jcode, rust, coding-agent-harness, benchmark, claude-code-comparison]
---

jcode 是 Rust 写的 coding agent harness,昨天发的 v0.11.6,目前累计接近两千颗星,一天涨了六百七十多颗,GitHub Trending 上来了。下面这张图来自 jcode 官方 README 的自测数据(同一台 Linux 机器,十次 PTY 启动平均),作者挑了三组对比:启动延迟、十路并行内存、扩展开销。对照对象是 Claude Code、Cursor Agent、Codex CLI、GitHub Copilot CLI、OpenCode、pi。

启动延迟看 time-to-first-frame。jcode 十四毫秒到第一帧,Claude Code 三千四百三十七毫秒——慢两百四十五倍。意思是你的同事开 jcode 已经看到回复了,你这边 Claude Code 还在渲染 banner。Cursor Agent 一千九百五十毫秒,慢一百三十九倍;Codex CLI 八百八十三毫秒,慢六十三倍。

并行扛压看十个 session 同时跑。jcode 内存占用一百一十七兆,Claude Code 两千三百兆(十九点七倍),OpenCode 三千二百三十七兆(二十七点七倍)。每多开一个 session,jcode 多吃九点九兆,Claude Code 多吃两百一十三兆,扩展开销差二十一倍。这一档跑长任务、开多个 background agent 的开发者最在意——风扇起飞跟没事一样的差别。

memory 系统也是 jcode 在 README 里强调的卖点之一——每一轮对话嵌入成向量,自动从图谱里 cosine 检索相关历史,不再靠 memory tool call 烧 token。这种"自动语义召回"跟过去靠人写 prompt 标关键信息再塞回去的做法是两套路径。

数据是开发者自家测的,不是第三方验证,看的时候按官方自测看待。但即便打个折,Rust 写的 coding agent harness 跟 Node/Python 写的差距,这次被一组对照表压实了——这一两年开发工具往 Rust 迁的趋势,又被一组数字拍实。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Rust #开源
