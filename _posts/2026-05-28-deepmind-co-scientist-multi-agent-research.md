---
layout: post
title: "DeepMind 9 天前在 Nature 发了一篇论文, 配了一个正在 rolling out 的产品: Co-Scientist。它不是又一个 chatbot, 它是一个由 7 个角色 agent 拼装出来的「AI 科研搭档」。🧬⚡"
date: 2026-05-28 12:00:00 +0800
hero: /assets/deepmind-co-scientist-multi-agent-research/2026-05-28_1800_deepmind-co-scientist-multi-agent-research-hero-3-raw.png
---

它做的事很具体: 你给它一个研究问题, 7 个 agent 接力跑一整轮假设生成、互相辩论、Elo 排名、迭代演化、最后给你一份可执行的研究方案。已经在抗药菌、植物免疫、肝纤维化、ALS、细胞衰老、药物再利用这些方向上跑出真实结果, 而且 100 多家研究机构在跟着验证。

7 个 agent 是怎么拼的:

① Generation agent — 从文献里捞 initial focus + 提出新假设

② Proximity agent — 把假设聚类, 保证探索多样性

③ Reflection agent — 当 virtual peer reviewer 评审每个假设

④ Ranking agent — 跑 Elo 锦标赛 pairwise 比较

⑤ Evolution agent — 把高分假设合并、迭代

⑥ Meta-review agent — 综合所有 round, 给最终方案

⑦ Supervisor agent — 总调度, 决定哪些 agent 并行跑、跑多深

中间最有意思的是 Elo 排名机制。它把假设当作棋手, 让 agent 两两对比, 算出 Elo 分。不是单一打分, 是相对排名 — 这点跟人类同行评议的实际逻辑更像。

为什么这件事份量重?

过去两年 multi-agent 系统大多停在「客服 + 工作流」级别 — 一个 agent 接 ticket、另一个 agent 调 API、最后总结。Co-Scientist 把同样的拼装方式往「严肃科研」推: 这 7 个 agent 加起来在做的是「假设生成→辩论→演化→收敛」这一整套科研动作, 让 LLM 集合体本身长出一种「研究流程」的形状。

实际产出已经能看到:

— 抗药菌 (antimicrobial resistance) 新机制候选

— 肝纤维化治疗思路

— ALS 治疗方向

— 老药再利用 (drug repurposing)

— 细胞衰老逆转线索

合作伙伴名单也扎实: Daiichi Sankyo、Bayer Crop Science、美国国家实验室。这种规模的企业先跟上, 说明 internal validation 已经走过 demo 阶段, 有可量化的 throughput。

集成层: ChEMBL、UniProt、AlphaFold (限合作伙伴)、Google Cloud 企业版。基本把「文献检索 → 蛋白结构 → 分子库 → 算力」整条链路接通了。

接入方式: 现在在 labs.google/science 开了 Hypothesis Generation 候补, 个人研究者可以申请。企业版要走合作伙伴渠道。

更大的信号: 2026 下半年「agent 拼装做严肃工作」会成为主线。从 Marco 的视角看, Claude Code 之于代码、Co-Scientist 之于实验室 — 都是同一种范式: 单 agent 不够, 多 agent 角色分工 + 互相评议才逼近真正的智能产出。

下一年, 看这套架构能不能从生命科学迁移到材料、化学、经济学。一旦能, AI 真正进入「研究合伙人」的位置。

转给那个还在科研第一线的朋友 👇

关注 @svtransit1 · 写给真在用 AI 的人

🧬 DeepMind Co-Scientist 官方页 + Nature 论文 + labs.google/science 候补 · 评论区取 ↓

#DeepMind #CoScientist #多智能体 #AI科研 #Nature
