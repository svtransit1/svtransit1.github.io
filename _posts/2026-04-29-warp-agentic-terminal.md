---
layout: post
title: "Warp 一夜 11,955 颗星 — 终端正在变成 agent 的主战场。"
date: 2026-04-29 21:14:38 +0800
source: https://github.com/warpdotdev/warp
hero: /assets/warp-agentic-terminal/2026-04-29_2100_warp-agentic-terminal-hero.png
topic_tags: [warp, terminal, agentic, claude-code, codex, gemini-cli]
---

之前 Warp 只是个"漂亮的 terminal",这次正式开源 AGPL v3 之后定位完全变了:不是 GUI 终端,是一个"agent 在 shell 里跑"的 IDE。Claude Code、Codex、Gemini CLI 三个主流 coding agent 全部 native 集成,文件读写跟 agent orchestration 挂在自带的 Drive 文件系统上。OpenAI 是 founding sponsor — 这条线说明大厂已经认定 terminal 是下一战场。过去两年大家把 AI coding 想成"chat 界面 + IDE 插件",但 terminal 才是工程师真正长时间停留的工作面,Cursor / VSCode 这类编辑器被 AI 重新发明的同时,terminal 也在被重新发明 — 而 Warp 跑在前面。Rust 构建、本地优先、macOS + Linux,开源出来之后社区改造成本接近零。半年后这条线可能跟 Claude Code 这类 client 形成竞争关系而不是补充。多 agent 协作稳定性、长 session context 管理这些细节都还在早期,但值得 clone 一份当玩具看看 agentic terminal 是什么体验 — Drive 文件系统里 agent 跨 session 共享 state 这一块如果跑得通,本地工作流可以彻底重排,不用每次开 session 重新交代项目背景。Cursor、Claude Code、VSCode + Copilot 这一代 IDE-first 玩家半年内会被迫做出回应。值得提的是 Warp 不是孤立选择走 terminal 这条路 — Codex CLI、Gemini CLI、Claude Code 这些主流 agent 本身就是 CLI-first,Warp 只是把它们整合到一个统一终端壳子里,降低工程师切换成本。中文圈独立开发者特别值得早试,因为 terminal-native AI 工作流对网络延迟、上下文管理、跨工具集成的要求,跟国内多云、多账号、多 backend 的复杂场景天然贴合 — 比 Cursor 那种"一个 IDE 锁一家 backend"的模型更适合本地真实工程环境。开源仓库一夜窜到 11,955 stars 不是社区跟风,是工程师在用脚投票:我们已经习惯 terminal,不需要再被新 IDE 教育一次。

转给那个还在用 iTerm 跑 Claude Code 的同事 ↓

源链接在评论区 👇

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Warp #Terminal #ClaudeCode #AI日报
