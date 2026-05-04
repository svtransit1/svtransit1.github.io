---
layout: post
title: "一份私人 dotfiles 24 小时被 5,645 个工程师抄作业。Matt Pocock 把自己用 Claude Code 的踩坑经验,写成 10 几个 skill 文件丢在 GitHub,现在 mattpocock/skills 已经 34,400 stars。"
date: 2026-04-28 21:17:51 +0800
source: https://github.com/mattpocock/skills
hero: /assets/pocock-skills/2026-04-28_2110_pocock-skills-hero.png
topic_tags: [claude-code, agent-skills, pocock, tdd, agent-protocols]
---

为什么这种朴素的东西突然爆款?因为它把 Claude Code agent 实际跑起来反复出现的 4 个坑,各自配了一条对应的 skill。下面是每条 skill 解决的具体问题。

第一个坑是 misalignment — agent 跑出来的方向跟你想要的差一截。表面上看是它"理解错了",但根因往往是它把模糊的指令脑补成了它自己的版本。Pocock 的 `/grill-with-docs` 强制 agent 在动手之前,先把它"以为自己理解的需求"用文档原文核对一遍。一个对齐 step,效果比反复 retry 强得多。

第二个是 verbosity。agent 喜欢写"我帮你做了 X、然后做了 Y、最后还做了 Z"那种汇报。Pocock 的 skill 直接禁了这种语气,要求只输出"做了什么 + 哪行变了",不要复述意图。读 diff 就够了,不需要 agent 替你写小作文。看起来是小问题,但减少 token 浪费、降低噪音对长 session 影响很大。

第三个是 non-functional code。agent 经常生成"语法对、跑不通"的代码 — 类型勉强对,但函数签名假设错了,或者依赖一个不存在的 API。`/tdd` 这个 skill 强制 agent 先写测试再写实现,而且要求测试必须能 fail 一次再 pass — 没有 red→green 的循环就 reject。这个流程比"加点 typing 提示"管用一个量级。

第四个是 architecture drift。一个 agent 跑十几次,慢慢把代码风格改得四不像 — 这周改一个文件用 class,下周改另一个文件用 functional,半年后整个 codebase 像不同人写的。`/diagnose` 让 agent 在动手前先列出"我理解的现有架构是这样,这个改动会触碰哪几个边界",触发自我审查。等于把"先停一下想清楚"写成默认动作,不是依赖运气。

其他几个 skill 也有意思:`/spike` 让 agent 不写产线代码先做最小可跑方案验证想法;`/refactor` 强调"只动一种东西",一次重构只改命名或只改结构;`/explain` 要求先把代码用纯英文讲一遍再决定要不要改。每个 skill 50-150 行 markdown,没有魔法,就是一段写给 agent 的工作守则。

整个仓库的 insight 不是"我发明了 N 种 prompt 模板",而是"我把每次跟 agent 工作时反复要解释的规矩,写成 skill 让它自己读"。下次开新对话,agent 进入工作目录就自动读到这套规矩,不需要每次重新对齐。模型本身一直在升,但你跟模型协作的"流程层"才是你自己的护城河。

README 里还总结了"skill 怎么写才好用"几条经验:写得越具体越好,模糊的 skill agent 读了不会照做;skill 之间别 overlap,否则 agent 不知道该听哪个;skill 不要写"鼓励"式语言,直接说"必须"和"不要"。

最实用的用法:克隆仓库扔进自己项目当 starter pack,逐个 skill 过一遍,留下用得上的、改掉不顺手的、删掉用不到的。第一周先只启用 `/tdd` 和 `/grill-with-docs` 两个 — 一个治"代码不能跑",一个治"理解错了需求",这两条最先节省时间。其余的等具体问题反复出现再加。一开始就上 10 个 skill 反而让 agent 在不同规则之间打架,效率反而下降。

跟其他几个流行 skill 集对比一下:Anthropic 官方的 example skills 偏教科书,演示功能但真实项目场景假设少;awesome-claude-code 类社区列表大杂烩,什么都收但没筛选。Pocock 这个的纯度在于"我每天都用、能 reproduce 我的工作流",这才是别人能直接抄走的版本。

一句话挑出值得抄的:agent 协作流程的最佳实践,正在从厂商文档迁移到独立开发者的真实工程实践 — 这才是值得跟进的信号。Pocock 这套基于 Claude Code + TypeScript 调出来,Cursor 或 Python 项目要改改语言假设,直接复制不能完美跑通是正常的。

转给那个还在每次手动跟 agent 对齐需求的同事 ↓

原始出处 · 第一条评论拿

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AIagent #AI工具 #AI日报
