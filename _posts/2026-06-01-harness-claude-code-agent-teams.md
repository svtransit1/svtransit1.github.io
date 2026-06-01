---
layout: post
title: "给 Claude Code 配个「团队」,质量能涨多少?有个插件给的答案是六成——但先把丑话说前头:这数字的样本只有 15 次。😬"
date: 2026-06-01 09:35:49 +0800
source: https://github.com/revfactory/harness
hero: /assets/harness-claude-code-agent-teams/2026-06-01_0900_harness-claude-code-agent-teams-hero-6-raw.png
topic_tags: [harness, claude-code, multi-agent, agent-orchestration, ai-agent]
---

GitHub 上这个叫 Harness 的项目(4.6k star,Apache 协议),作者管它叫「给 Claude Code 的团队架构工厂」:别再让一个 agent 从头干到尾,它按现成的六种组队方式,帮你自动搭出一个多 agent 团队。

六种架构,各对一类活:

① Pipeline 流水线 — 任务一棒接一棒,适合有明确先后的流程:读需求 → 写代码 → 写测试。

② Fan-out / Fan-in 分发汇总 — 大任务拆成小份并行跑,最后有人收回来拼好,适合能并行的批量活。

③ Expert Pool 专家池 — 一群各有专长的 agent 待命,来活按领域派给最合适的那个。

④ Producer-Reviewer 写审分离 — 一个写、一个专挑错,通常比一个 agent 自己写自己改要稳。

⑤ Supervisor 主管 — 一个 agent 当头,拆活派活盯进度,其它的干执行。

⑥ Hierarchical 层级委派 — 主管底下还能再带主管,适合特别大、得分层管的任务。

装好插件,直接说一句「给这个项目搭个 harness」,它就照着生成。作者放的数据:组队后平均质量分 49.5 → 79.3(涨约六成),15 场对比里团队全胜,输出波动也小了三成。

⚠ 把话讲全:这组数字,作者自己每次引用旁边都标着「n=15、本人做的 A/B、第三方还没复现」。方向挺诱人,但别当成定论——能不能在你项目上复刻,还得自己跑一遍。🧐

真要上手,大多数项目从「写审分离」或者「主管」这两种起步就够了,效果最容易看出来;流程固定的活配「流水线」;至于「层级委派」,一般是任务大到一个主管都盯不过来才用得上。反过来,也别为了组队而组队——一个 agent 利索就能搞定的事,硬塞几个进去,只会多一层互相协调的开销,有时候反而更慢。

单个 agent 上下文一拉长就容易跑偏,自己写的 bug 自己也常看不出;拆成有人写、有人审、有人统筹,本来就是人类团队磨了很多年的分工。手里的 agent 越来越多,怎么把它们编排好,可能比单个模型再聪明几分更值得花心思。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AIagent #多智能体 #Claude
