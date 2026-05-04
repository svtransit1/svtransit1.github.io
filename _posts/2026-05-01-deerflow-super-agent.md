---
layout: post
title: "字节昨天把 DeerFlow 推到 2.0——这是开源 super agent harness 这条赛道里最值得看的一次更新,五件事最能说明白它要做什么。"
date: 2026-05-01 09:14:27 +0800
source: https://github.com/bytedance/deer-flow
hero: /assets/deerflow-super-agent/2026-05-01_0913_deerflow-super-agent-hero-raw.png
topic_tags: [deerflow, bytedance, super-agent-harness, sub-agents, sandbox, open-source]
---

DeerFlow 这个项目最早是字节的 deep-research 框架,这次 2.0 跟 1.x 完全不共享代码,从零重写,GitHub 现在六万四千颗星,2 月 28 日刚拿过 GitHub Trending 第一。MIT 开源,backend 走 Python 3.12+,前端是 Node 22+。重写这件事在开源项目里不常见——通常是加层、重构、deprecate 旧 API,直接抛弃 v1 代码库的勇气只有 backer 资金充裕的项目敢这么干。下面五个点最能说明 2.0 现在长什么样。

1. 定位换了一档。1.x 是 deep-research,主线是"读完十篇论文给我写报告"。2.0 直接拉到"super agent harness"——做一件需要几分钟到几个小时才能跑完的复杂任务,从研究、写代码到做设计稿都算。底下挂了子 agent、长期记忆、沙盒、技能、工具、消息网关一整套支撑。这个语言层面的转向,跟 OpenAI 这边推 Agents SDK、Anthropic 推 Claude Agent SDK 是一致的方向——大家都在把"agent"从演示品变成生产力载体。

2. Sandbox 不再是可选项。Docker 和 Kubernetes 两种模式都内置好,不用你自己拼。这意味着你可以让 agent 在一个隔离环境里跑 bash、改文件、装包,出问题不污染本地。这条对长任务特别关键——一个跑半小时的 agent,中途装错一个 Python 包就把开发机搞废,这是过去半年最劝退的痛点之一。Kubernetes 模式还能横向扩,你跑十个 sub-agent 并行就是十个隔离 pod,不会互相踩。这条对企业部署很关键——本地 docker 玩玩可以,真要给团队用,一定是上 Kubernetes 的。

3. Coding agent 直连。Claude Code、Codex、Cursor、Windsurf 都能直接对接,README 给了一句一行的接入指令——你把那行话扔给你的 agent,它自己 clone 仓库、跑 docker、把环境装起来,卡住了也会主动告诉你下一步缺什么配置。这种"agent 装 agent"的设计,把 onboarding 时间从一晚压到十分钟。其他几个开源 agent 框架对这一步基本还没做封装,要你自己读 README、跑命令、解依赖。这条说明 DeerFlow 团队自己就是 agent 重度用户——只有真在用,才会想到这层。

4. 模型路线偏中国市场。推荐列表写了 Doubao-Seed-2.0-Code、DeepSeek v3.2、Kimi 2.5,而不是默认 OpenAI/Claude。字节自家的 BytePlus 配了 Coding Plan 算力包,中国大陆开发者还有单独的火山方舟入口。这个细节说明 DeerFlow 不是为美国 dev 写的,主战场是国内加海外华人开发者群体——这跟它的字节出身吻合,也是 OpenHands、CrewAI 这些美国出身的 harness 暂时还没覆盖的市场。同样的 super-harness 设计,模型推荐这一行的偏好就把生态划清了。

5. 部署门槛真的低。`make setup` 跑一个交互向导,选 provider、选 web search、选 sandbox 模式,大概两分钟出 `config.yaml` 和 `.env`。`make doctor` 随时验证环境,给你具体的修复提示——这种"自己会看病"的设计在开源项目里不多见。Docker 是推荐路线,纯本地开发也可以。LangSmith、Langfuse 两套 tracing 都内置接好了,你跑生产链路想看每一步 token 花在哪、哪个 sub-agent 卡住,直接接上就有数据。

开源 agent harness 这条赛道过去半年扎堆——OpenHands、smolagents、CrewAI、AutoGen、LangGraph 都在挤。DeerFlow 的差异化在两点。一是字节砸资源做长链条任务的稳定性:十几个工程师专门盯长跑稳定性,这个投入量在开源 agent 框架里不多见。二是它把"super agent harness"这个语言推到前面,要的不是一个会聊天的 chatbot,是一个能扛半天工作量的执行体——你给它一个项目级目标,它自己拆任务、调子 agent、跑工具、记结果。

谁该看一下这个项目。如果你已经在 Claude Code 上写了一堆 skills,DeerFlow 这套 super-harness 值得花一晚装下来跑一跑——同样的 skills 哲学,但补上了沙盒、子 agent 调度、长期记忆这一整套基础设施。如果你还没用过 Claude Code,先从 Claude Code 上手会更快,DeerFlow 是给那些已经把 agent 当生产工具的人准备的下一档。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ByteDance #开源 #AIagent
