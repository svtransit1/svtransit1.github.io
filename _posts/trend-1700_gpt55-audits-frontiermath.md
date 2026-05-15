---
layout: post
title: "benchmark 自己被 benchmark 它的模型给审计了，这一幕今天在 FrontierMath 身上真发生了。"
date: trend 12:00:00 +0800
hero: /assets/1700_gpt55-audits-frontiermath/trend_2026-05-12_1700_gpt55-audits-frontiermath-hero.png
topic_tags: [gpt-55, frontiermath, benchmark, openai, deepmind, llm-evals]
---

r/singularity 一篇刚冒头的帖子（@skywalkerr0x 在 X 上转得很猛）说：有人拿 GPT-5.5 去过了一遍 FrontierMath 的 Tier 1-4 题库，大约三分之一的题目被这个模型直接标出有 fatal errors——也就是数学层面的实质性错误，不是表述不清，是答案或证明步骤本身站不住。

FrontierMath 是 Epoch AI 出的题库，名义上是衡量"前沿模型在前沿数学题上的能力"——目标受众就是 GPT、Gemini、Claude 这一档。它的 Tier 4 是最难的一档，连前沿模型当前也就 40% 上下：GPT-5.5 Pro 的官方数字是 39.6%，DeepMind 那个新出的多 agent co-mathematician 据说能跑到 48%。

但现在的问题是这样：如果同一档模型已经强到可以反向给题库找 bug，那剩下的那 60% 没做出来的题，到底是模型不够强，还是题本身有问题？这两种解释长得太像了。

这件事对 Chinese AI 圈最值得读的地方有三个：

一是 benchmark 的"权威性"是有 shelf-life 的。我们这一年看 SWE-bench、HumanEval 类指标被快速吃透，背后其实都是同一个故事：题目静态、模型迭代，时间在站模型这一边。一旦交叉过线，benchmark 就从"考试"变成"被考"。

二是 Reddit 这条原帖能不能 1:1 复现还要看后续。Reddit 帖子本身没经第三方审稿——但 "1/3 fatal errors" 这个声量已经传开了，DeepMind 团队、OpenAI 团队、Epoch AI 自己都不会装作没看见，未来一两周大概率会有一份正式回应（或者反驳）。

三是更现实的：如果你做评测、做模型选型，或者你只是个看 leaderboard 决定订阅哪家的人，那这件事会逼你思考一个问题——你在看的那个分数，是模型水平，还是题库的稳定性？

而国内这边其实早就有类似的预演。DeepSeek 这两年放出新版本的时候，社区里反复出现的不是"打分对不对"，是"这道题是不是已经在训练集里"——题库的 contamination 和 staleness 一直是国产模型评分的核心争议点。FrontierMath 这次比那更进一步：不是怀疑模型见过题，而是怀疑题本身有错。

我觉得这一幕是 2026 这一年里很 emblematic 的瞬间：模型已经强到可以质疑用来评价它的工具。不是失败的瞬间，是 inflection point。下一档 benchmark 的设计可能就得换思路——不是出"更难"的题，是出"更可验证"的题，或者干脆放弃静态题库，转向交互式 / 长程任务的评估。

转给那个还在用 benchmark 截图给模型排座次的朋友。

关注 @svtransit1 · 写给真在用 AI 的人

完整链接 · 评论区取 ↓

#AI #LLM #benchmark #FrontierMath
