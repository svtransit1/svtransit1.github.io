---
layout: post
title: "\"代码便宜了之后该做什么\"——David Breunig 这篇 5/4 写的 10 条 agentic coding 心得，HN 上一小时窜上来，说出了很多 Claude Code 重度玩家半年来想说没说完的话。"
date: trend 17:11:17 +0800
source: https://www.dbreunig.com/2026/05/04/10-lessons-for-agentic-coding.html
hero: /assets/1700_10-lessons-agentic-coding/trend_2026-05-05_1700_10-lessons-agentic-coding-hero.png
topic_tags: [agentic-coding, claude-code, dev-philosophy, david-breunig]
---

把整篇精华按我自己跑下来的体感重排了一下，10 条留给你：

1️⃣ 写代码是为了学习。不是计划清楚再写，是写过一轮才知道当初没看见的边界条件、隐藏依赖、不合理的假设。先让 agent 写一遍跑通，再回头改 spec —— 这样的迭代节奏比"先想三天再敲键盘"快得多。

2️⃣ 重写比改 bug 更值。代码便宜了，experiment 的成本接近零。整块功能不顺手就砍掉重来一次，比对着 patch 改 50 行更省时间，结果也更干净。这条对老工程师反直觉 —— 我们被训练成"修改胜于重写"，因为以前手写代码贵；现在反过来。

3️⃣ 投资 end-to-end 测试，别堆 unit test。测的是行为契约，不是实现细节。重写第三遍的时候，单测要改 200 个，e2e 测试一个不动 —— 因为它只关心"用户输入 X 系统返 Y"。这一条直接决定你能不能放心让 agent 重构。

4️⃣ 把"为什么"留在文档里，不是"是什么"。Claude 能复现你的代码、看出你怎么做的，但复现不了你当时为什么排除了 A 方案、为什么选 B、为什么没用看似更优雅的 C —— 那些 trade-off 思考是 codebase 真正的资产。intent 比 code 更值钱，因为 code 可以重新生成。

5️⃣ Spec 是活文档不是冻结资产。每跑一轮 agent，spec 里会冒新约束、新边界、新前提。把它们写回去 —— spec 文档版本号每周往上走，下一轮 prompt 才更准。冻结的 spec 等于过期的地图。

6️⃣ 主动找硬活。直觉性的 UX 设计、性能调优、安全审计、架构权衡 —— 这些 agent 一时半会还接不住，因为它们要的是"对的判断"而不是"能跑的代码"。容易的活让 agent 干，难的活留给自己，差异化和价值就在这里出来。

7️⃣ 简单事情全自动化。skill 系统、子 agent、复用工作流、cron 调度 —— 把所有"我每周都要做一遍"的活变成一次性配置。但 Breunig 提了一个坑：小心陷在"持续优化工具"这个泥潭里出不来 —— 我也踩过，三天没产出业务代码全在调 agent 工具链。

8️⃣ 培养品味。当外部验证慢于 agent 输出速度时，你自己的判断力就是质量天花板。domain knowledge 和用户理解 —— 这两个你不练，agent 也救不了你。下半年值钱的工程师不是写得最快的，是看得最准的。

9️⃣ Agent 放大经验。同样一句"做一个登录系统"，工程老手能写出"用 PKCE flow 配 JWT，refresh token 走 Redis，rate limit 在 nginx 那一层，认证失败要 timing-attack-safe"—— agent 能落地。新手只能写"做个登录系统"—— agent 给你一个能跑但全是坑的 demo。经验让 prompt 输出质量翻倍，prompt 写得越具体差距越大。

🔟 隐性成本还在。代码便宜，但维护、支持、安全、合规、可观测性这些没变便宜。跑得快需要相应的运维纪律 —— 不然 6 个月后 codebase 烂在手里，agent 自己都看不懂。Breunig 这一条提醒得很实在：写得快不等于活得久。

我自己的总结：核心信号是 agent 把"实现"这一步压到接近零成本，但"判断"和"长期维护"这两端的成本结构没变。把工程时间从打字挪到思考、写规范、做端到端测试 —— 这三件事下半年会区分谁的 codebase 在长高、谁的在塌方。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AI编程 #agent #编程心得
