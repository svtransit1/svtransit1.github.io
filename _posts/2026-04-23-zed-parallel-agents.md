---
layout: post
title: "想象一下:一个 agent 在改前端、一个改后端、一个跑测试,全在同一个 Zed 窗口里同时干活,互不打架。Zed 最新版把 parallel agents 做进去了。"
date: 2026-04-23 09:14:00 +0800
source: https://zed.dev/blog/parallel-agents
hero: /assets/zed-parallel-agents/2026-04-23_0630_zed-parallel-agents-hero.png
topic_tags: [zed, parallel-agents, dev-tools, ide, multi-agent, ai-coding, claude-code, cursor]
---

跑过 Claude Code、Cursor 的都知道痛点在哪——单线程。一个 agent 起来占住整个项目,你只能等它跑完。想让第二个 agent 干别的活?开新窗口、切项目、把上下文重新喂一遍。用久了发现大半时间花在"等 agent 和管 agent"上,不是写代码。这套工作流在做 hotfix、临时 exploration、日常小任务的时候特别拖节奏——一件事堵住,什么都停了。

Zed 的做法是把 thread 当一等公民。左侧 Threads Sidebar 管所有 agent 线程——每个线程自选模型(任意 provider,OpenAI、Anthropic、Google、本地 Ollama 都行)、自选 worktree、自选能访问的文件夹和 repo。做前后端协作的任务,起两个 thread,一个绑前端目录、一个绑后端,它们看到的就是各自的世界,不会互相踩。Thread A 跑 API 重构的时候,Thread B 同步在 React 这头加组件,主线程你自己手写 glue code,三条线并行往前推。

跨项目也行。作者博客的原话是 "work across projects, with one agent thread reading and writing across repos"——一个 thread 可以横跨多个 repo,适合做 monorepo 重构或者服务间 migration 工作。权限这一侧明确给了隔离钩子:"control exactly which folders and repositories agents can access"。敏感目录不想让 agent 看,直接关掉;只允许它碰测试目录,单独开权限。比一股脑把整个 repo 喂给 agent 要安全得多。

还有一条值得提。编辑器这端没掉帧。Zed 一直押的是 GPU 渲染、Rust 内核的 120fps 路线,这次把多 agent 并发扔进去,UI 侧宣称没掉到下限。实际效果要等社区跑多了才有数,但光这个设计目标就跟 Electron 系编辑器拉开代际差——Cursor / VS Code 系要做同样的事,架构上就吃亏。多个 agent 同时写文件、同时触发 diff 预览、同时跑 lint,Electron 架构下每一步都是潜在的卡顿点。

哲学层面作者写了一句话:"combining human craftsmanship with AI tools to build better software"。不是押完全自动化,也不回避 AI——中间那条人机协作线。这个定位跟 Claude Code 的 cowork 调调很像,不是"点一下跑整晚"那种 SaaS 宣传片路数。你不是在雇 agent 替你写代码,是在跟多个 agent 同时做手艺活。

操作上,option-cmd-j(Mac)/ ctrl-option-j(Linux、Windows)就能拉起 Threads Sidebar,默认在左边,Agent Panel 旁边,Project Panel 和 Git Panel 移到右边。新 thread 起步、归档、切换,键盘快捷键全覆盖。

最新版 Zed 直接升级就有,免费。想认真跑 agent 工作流的、做 monorepo 的、或者平时 hotfix 和探索性任务比较多的人,值得把 Zed 当主力 IDE 试一下——至少把"多 agent 并发"从愿望清单里划掉了。

转给做前端 / 后端 / data 的朋友——他们会想跑一遍。

关注 @svtransit1 · 每天都有有用的 AI 资讯

https://zed.dev/blog/parallel-agents

#AI #ClaudeCode #AIagent #Zed
