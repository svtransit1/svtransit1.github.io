---
layout: post
title: "「AI 编程,哪个模型最省钱?」——你要是拿「每百万 token 多少钱」去比,大概率会挑错。"
date: 2026-07-09 18:17:00 +0800
source: https://databricks.com/blog/benchmarking-coding-agents-databricks-multi-million-line-codebase
hero: /assets/databricks-cost-per-task-not-token/2026-07-09_1730_databricks-cost-per-task-not-token-hero.png
topic_tags: [databricks, coding-agents, cost-per-task, llm-eval, harness]
---

Databricks 刚在自己几百万行、十多种语言的真实代码库上,认真测了一轮编程 agent。方法挺硬:拿真实合并过的 PR、跑测试套件来判分(不是让另一个 LLM 当裁判),每个样本还人工过一遍,跑的时候把 git 历史封起来,防模型偷看答案。结论一句话:token 单价,根本预测不了你端到端跑一个任务的真实花费。

最扎心的例子是 Sonnet 5。它每 token 比 Opus 便宜差不多 1.7 倍,听着划算。可真放到任务上,它每个任务反而更贵——2.09 美元,比 Opus 的 1.94 还高;分还低了 6 个点(81 对 87)。原因很简单:它为了做完,干得更久、读得更多,总共多烧了 1.9 倍的 token。便宜的单价,换来更贵的活。

更狠的是 harness 这一条。同一个模型、同样的思考强度,只是换了个外壳(Claude Code/Codex 换成 Databricks 自己的 Pi),每任务成本能差出 2 倍以上,质量还一样。差在哪?Pi 每一轮发的上下文少了约 3 倍。也就是说,你怎么喂上下文,可能比你选哪个模型还影响账单。

(顺带,这轮里 GLM 5.2 挺抢眼:每任务 1.28 美元,质量跟 Opus 统计上打平——又便宜又不输。)

所以问题该换个问法:别问「哪个模型 token 最便宜」,问「在你自己的 harness、你自己的任务上,每完成一个任务花多少」。最便宜的 token 可能是最贵的活;换个更省上下文的壳,省下的没准比换模型还多。

当然,有几点得说在前头:这是 Databricks 一家的代码库和任务分布,数字别照搬——恰恰因为这样,重点是去量你自己的那份,别照抄它的排名;这里的「质量」是过它自己测试套件的通过率,不算通用跑分;而且是某个时间点的快照,模型和 harness 都在迭代,过阵子数字可能就变。还有,Pi 就是 Databricks 自己做的,「harness 很重要」这条它有利益相关,你读的时候留个心。我没自己跑这套 benchmark,以上都照它博客讲的。

转给那个还在按 token 单价挑模型的同事。

关注 @svtransit1 · 写给真在用 AI 的人

原文链接放在第一条评论 ↓

#AI #ClaudeCode #AI编程 #AIagent
