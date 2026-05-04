---
layout: post
title: "Anthropic 把 Claude 插件商店悄悄上线了,Superpowers 是第一批入选的\"完整开发方法论\"。"
date: 2026-04-30 15:18:08 +0800
source: https://github.com/obra/superpowers
hero: /assets/superpowers-methodology/2026-04-30_1500_superpowers-methodology-hero.png
topic_tags: [claude-code, superpowers, plugin-marketplace, methodology, agentic-dev]
---

obra/superpowers 这个 GitHub 仓库 173,647 颗星(没看错,是十七万多),作者 Jesse Vincent。它不是又一个 skill 列表,它是一整套强意见的 AI 编码方法论 — 从你启动 agent 那一刻起,系统就接管全流程。先逼你描述清楚要做什么(spec teasing),然后输出短到能读完的设计稿,等你 sign off 后,生成一份"傻瓜级"的 implementation plan,接下来用 subagent-driven development 自动跑完所有工程任务,Claude 经常能自主跑两个小时不偏离 plan。这种"先停下来想清楚再写"的纪律,跟现在主流 vibes-first 的开发风格是反着来的 — 但效果确实更稳。Jesse 是 Request Tracker(开源工单系统)、K-9 Mail、keyboard.io 这些项目的作者,二十年开源工程经验。他把"项目管理 + 工单流程"那套纪律带进 AI coding 流程里 — 不是空想,是把他做了二十年的工程方法学复用过来。

为什么这件事现在值得讲清楚?因为 AI coding 圈正在快速分化成几个流派,Superpowers 加入 Anthropic 官方插件市场代表"流派之间的标准化竞争已经开始"。你今天选哪个流派,不只是工具偏好,实际上是在投资某种工作风格。半年后这些流派会有明显的产能差距,选错了可能要重学一遍。这种"早期分化期投错"的代价,见过的人都记得 — 当年押 SVN 的人后来切 Git 切了三年才彻底转过去。

跟前几天的 mattpocock/skills 跟 Composio 的 awesome-codex-skills 对比,三套 AI dev 哲学差别很清晰:

Pocock 走的是**模块化 skills 路线**。你写一堆独立的 skill 文件,每个解决一个具体问题(/tdd 治代码不能跑、/grill-with-docs 治理解错需求)。agent 看 description 自己决定什么时候用哪个。优点是灵活、可组合,你想用哪个加哪个,改起来快;缺点是缺乏全局编排,agent 怎么挑 skill 取决于它自己的判断,新手容易翻车。这一派适合个人开发者已经有自己工作流、只想在某些环节让 agent 跑得更稳的人。

Composio 的 awesome-codex-skills 走的是**精选目录路线**。50+ 个 skill 集中在一个仓库里,跟 Anthropic 的 SKILL.md protocol 完全兼容,跨 Claude Code / Codex / Cursor 互通。优点是社区共享 + 一键安装;缺点是没有"哪个先跑哪个后跑"的工作流意见。这一派的本质是把 skill 当 utility,谁好用谁先用,不假设流程。对自由工作流的开发者很合适,对需要"一致性"的团队来说不够。

Superpowers 走的是**强意见方法论路线**。它不只是给你一堆 skill,而是规定了一整套软件开发流程:spec → 短设计稿审查 → implementation plan → subagent-driven dev → red/green TDD → YAGNI / DRY 强制。所有 skill 都是为这套流程服务,触发时机也由 methodology 控制,你不需要"挑 skill",流程会自动调用。优点是新手能直接照流程跑出能 ship 的代码;缺点是流程意见很硬,如果你的项目跟它假设不一致,改起来麻烦。Jesse Vincent 在 README 里直接写了一句很关键的话:"agent 不会跳进来直接写代码,它会先停下来问你到底要做什么"。这种"逼着你想清楚再让 agent 动手"的纪律,对大多数 vibes-first 的工作流来说,是不舒服但有效的矫正。

这三派背后其实是三种不同的工程哲学:Pocock 信"工程师自由 + 工具组合";Composio 信"社区协作 + 兼容标准";Superpowers 信"流程纪律 + 强约束"。哪种更对,没有标准答案,跟你自己的工程习惯、团队规模、项目阶段都有关系。

谁该选哪个?

如果你已经有自己的工作流,只想在某些环节让 agent 跑得更稳,选 Pocock 模块化 skills,挑几个填进自己的项目。学习曲线最低。

如果你想从零开始让 Claude Code / Codex / Cursor 都能用,选 Composio awesome-codex-skills,clone 进项目当 starter pack。跨 ecosystem 互通是最大优势。

如果你是新手,或者团队想标准化"agent 怎么写代码",选 Superpowers。它替你做了所有"流程上的判断",代价是你接受这套 opinionated 的方式。Jesse Vincent 是 Request Tracker、K-9 Mail、keyboard.io 这些项目的作者,二十年开源工程经验,这套流程的纪律性是他多年工程方法的浓缩 — 不是空想。具体一点:他强调 spec → 设计稿 → 实施计划 → subagent dev 这条线,每一环都不能省;Red/Green TDD 是硬约束不是建议;subagent 跑长链条任务时主 agent 要做 review,这跟普通 Claude Code 直接让 agent 一路写到底完全两种风格。新手按这个流程跑会觉得"麻烦"但产出稳定,老手按这个跑会觉得"被绑手"但 bug 率会下降。

我自己的判断:Anthropic 上线官方插件商店这件事,信号比单个仓库重要得多。VS Code 当年把"editor + 第三方 extension"做成行业标准,IDE 从此分化成两个梯队:能装扩展的、和不能装的。Anthropic 这次走同一条路 — Claude Code 从"模型 + 单 agent"变成"模型 + 插件生态",Superpowers / Pocock / Composio 这些都是早期典型,半年后会有数百个。这个生态跑起来之后,Claude Code 跟 Cursor 的差距会被拉开 — 不在模型本身,而在"能不能跑别人的流程"。

更深一层看,这件事重新定义了"AI coding 工具"的护城河。早些时候厂商比的是模型(Sonnet 比 GPT-4 多几个百分点 SWE-Bench)、然后比的是客户端(Cursor UI 比 Claude Code 漂亮)、再后来比的是 agent 能力(谁的 agent 能跑长链条)。现在比的是"插件生态的丰富度跟可组合度"。你的工作流跑在 Claude Code 上,装了 Superpowers + 自己的几个 skill,这套组合是别人复制不了的资产。Cursor 的优势随之被稀释 — 它的"全在 IDE 里"理念在插件时代反而变成约束,因为插件机制要求开放接口跟可拔插。

中文圈独立开发者特别值得关注的点:Anthropic 的官方插件商店(claude.com/plugins/)目前还在早期,中文社区贡献者寥寥。这意味着前几个月你写的中文场景插件 — 翻译跨境工作流、本地化 deploy 流程、跟国内云厂商集成 — 都有早期 mover 优势。等到生态饱和才进场,跟现在 VS Code marketplace 一样,top 10 已经被瓜分。这种"早期生态红利"机会,在过去十年的 npm、VS Code marketplace、Cursor extensions 都出现过 — 早期贡献者后来都拿到了不成比例的可见度。

实操建议:三个都试一次,各 1 小时。一个真实小项目,先用 Superpowers 走一遍完整流程感受 opinionated 方法论;然后切 Composio 当 starter pack 自由组合;最后用 Pocock 几个 skill 替换某些环节。这样你能用脚投票,知道哪种工作流跟自己的脑回路最契合。我估计大部分人会落在 Pocock + Composio 的混合区间 — 既要灵活又要 starter pack;少数追求极致流程纪律的会切到 Superpowers,完全交出工作流主导权给 methodology。但试过三种你才能确定自己是哪种。

最后一个值得一提的工程信号:Superpowers 用的"subagent-driven development"概念,跟 Anthropic 自己的 Sub-agents API 在过去一年的演进路径完全合拍。这条线说明 Anthropic 内部对 agent 的工作模式已经从"单 agent 长 context"转向"主 agent 编排 + 多 sub-agent 并行执行"。Cursor 跟 Copilot 还在死磕 single-agent IDE 体验,Anthropic 这边在悄悄往 agent orchestration 推进。半年后 agent 协作的标准实践如果是 sub-agent driven,Cursor 这一代 IDE 要么跟,要么被边缘化。如果你在用 Cursor 跑生产工作流,这件事值得近期盯一下。

转给那个还在每次手动跟 agent 解释项目流程的同事 ↓

源链接在评论区 👇

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Superpowers #AIagent #AI日报
