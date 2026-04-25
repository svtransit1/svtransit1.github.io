---
layout: post
title: "写过 agent 的人都知道一个尴尬：写完容易，证明它没翻车很难。各种评测工具拆得很散——一套跑 hallucination，一套跑 tool-use，一套加 guardrail，再一套接监控。每加一层都要写胶水代码。"
date: 2026-04-26 00:14:07 +0800
source: https://github.com/future-agi/future-agi
hero: /assets/future-agi-eval-platform/2026-04-26_0000_future-agi-eval-platform-hero.png
topic_tags: [eval-platform, agent-eval, opentelemetry, prompt-optimization, guardrails, open-source]
---

future-agi 这周开源的同名平台 future-agi 把这五件事装进了一个 docker compose。Apache 2.0、可自托管，凌晨刚上 GitHub trending 周榜。

它把 agent 评测的工作流拆成五个模块：simulate、evaluate、protect、monitor、optimize。每一块单独看都不算新，但放一块的整套已经少见。

simulate 这块给你预置 persona 库，可以批量跑多轮对话，还包括对抗性 persona 和 voice agent 的语音评测——voice 这一项目前是它独有的。evaluate 给了 50+ 内置指标：groundedness、hallucination、PII、tone、tool-use 准确率，混合 LLM-as-judge 和启发式规则两种打分路径。所有打分逻辑可看可改，不是黑盒。

protect 这块塞了 18 个内建 guardrail scanner，加 15 个外部适配器（Lakera、OpenAI Moderation 之类）。monitor 走 OpenTelemetry，覆盖 50+ 框架——LangChain、LangGraph、LlamaIndex、CrewAI、AutoGen、Claude SDK、DSPy 都接好了。

最后还有个 OpenAI 兼容的 gateway，可以路由到 100+ provider；官方贴的吞吐数据是 t3.xlarge 上 29k 请求/秒，开了 guardrail 后 P99 ≤ 21ms。这部分主要是给生产环境的 router 用，跟评测松耦合。

prompt 优化这块塞了 6 种算法（GEPA、PromptWizard、ProTeGi 等）。这一项有点意外——一般评测平台不带 optimizer，但确实是 agent 工作流闭环的最后一环：跑 → 评 → 改。

老实说，对刚开始写 agent 的人这平台过重；但对维护多 agent、多 framework 的团队，把 evaluation + observability + guardrail + gateway 收到一个自托管栈里，比维护四个独立服务划算得多。

仓库 README 自己写着「Nightly release for early testing — expect rough edges」。28 个 commit、347 stars，还在早期。但这个工程方向比再发一篇评测论文实际多了。

来源 · 评论区取 ↓

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #AI工具 #LLM评测 #开源 #AI日报
