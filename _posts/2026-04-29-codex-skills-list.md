---
layout: post
title: "awesome-codex-skills 这个 GitHub 仓库一夜涨 953 颗星,内容比标题朴素得多 — Composio 团队把 50 多个 Codex skill 文件列了一份精选清单。但意义不在清单本身。意义在于:Anthropic 在 Claude Code 里发明的 skills 机制,正在变成 AI 编码 agent 的行业标准,OpenAI 阵营这周开始跟。"
date: 2026-04-29 18:18:31 +0800
source: https://github.com/ComposioHQ/awesome-codex-skills
hero: /assets/codex-skills-list/2026-04-29_1800_codex-skills-list-hero-raw.png
topic_tags: [codex, claude-code, skills, openai, anthropic, agent-protocols]
---

什么是 skill 机制,先快速回顾一下。一个文件夹一个 SKILL.md,带 YAML frontmatter(name + description),agent 在启动时读 description,决定要不要在某个任务上触发这个 skill,只在触发后才加载完整的 instructions body。这套设计是 Anthropic 早些时候在 Claude Code 里推出来的,核心解决的是"agent 上下文太长就糊"和"开发者重复对齐 prompt"两个老问题。

现在 OpenAI Codex 完全抄了这套结构。awesome-codex-skills 仓库的 README 写得明明白白:`$CODEX_HOME/skills` 目录、SKILL.md 文件、name + description frontmatter、progressive disclosure(references/ 子文件夹按需加载)。换字段名都没改 — 这不是平行设计,是直接 fork 了 Anthropic 的 protocol 抄回来。Composio 这个仓库就是把 OpenAI 阵营的早期 skill 实现汇总,方便开发者直接 install。

仓库里有几个看起来真有用的 skill:`brooks-lint` — 用六本经典工程书的角度做代码 review,带衰减风险诊断和书目引用;`codebase-recon` — 不读代码,只读 git history 找 hotspot、bug magnet、bus factor;`codebase-migrate` — 大型迁移分批走,带 CI 验证和回滚;`mcp-builder` — 写 MCP server 的脚手架带 evaluation harness;`unslop` — 从输出里清掉 AI 写作的 tricolon、em-dash 滥用、hedging stack(讽刺的是这个 skill 同时支持 Codex / Claude Code / Gemini / Cursor 四端)。每个 skill 大概 50-150 行 markdown,跟 Claude Code 那一套完全可以互相 port。

为什么 skill 这个机制特别值钱?跟普通的 prompt template 比,它解决了三个 prompt 不能解决的问题。一是触发条件被结构化:description frontmatter 告诉 agent "什么时候用",不是让 agent 每次都判断完整 prompt;二是 progressive disclosure — agent 第一遍只读 metadata,触发后才加载完整 body,context 浪费降低 80% 以上;三是版本可控,skill 是文件不是 prompt 历史,你 git diff 能看到改了什么,跟 prompt 工作流"靠记忆"完全两回事。这三件事叠在一起,把"AI 协作"从口语化交流推进到了工程化 protocol。

这件事的真正信号有三个层次。

最浅的一层是开发者得到一个新的 starter pack。如果你在用 Codex 而且没花时间自己写 skill,直接 clone awesome-codex-skills 进 `~/.codex/skills/`,选 3-5 个常用的留下,半小时搭起一个比裸用 Codex 强不少的工作流。

中间一层是行业标准化。skills 这个机制能从 Anthropic 一家扩散到 OpenAI 阵营,意味着以后再扩散到 Gemini、Mistral、本地模型,只是时间问题。awesome-codex-skills 已经有 cross-tool 的 skill(unslop 同时支持四端)。再过半年,跨 agent 互相借用 skill 文件可能成默认操作 — 一个 SKILL.md 文件,Claude Code 跑得动,Codex 跑得动,Gemini 跑得动。

最深的一层是 client 跟 model 之间的边界正在被重画。早些时候厂商靠"客户端独占"锁定用户(Cursor 锁 OpenAI、Claude Code 锁 Anthropic)。skill 机制开源出来之后,客户端独占价值降低,因为同一份 skill 在不同客户端跑出来差不多的效果。下一个被解构的就是模型独占 — 这条线我们昨天已经看到苗头(free-claude-code 把 Claude Code 的客户端跟 Anthropic 模型解耦)。一旦客户端跟模型双方都被解构,留给厂商的护城河就剩"基础模型本身的能力差异"和"商业生态服务质量"两条。这个状态对开发者是巨大解放,对厂商是利润空间被压缩。

仓库里几个值得单独看的有意思设计:`Bernstein` 这个多 agent 编排器,通过 Codex CLI adapter 在隔离的 git worktree 里并行跑多个 Codex agent,带 quality gate;`Vibe-Skills` 这个 skill harness 把 340+ skills 路由进"需求冻结 → 计划批准 → 执行 → 验证证据 → 跨会话记忆"的 staged 流程。这两个项目本质上是把 skill 机制从"单 skill 单任务"扩展成了"多 skill 多 agent 编排平台",方向已经超出了 Anthropic 当初的设计意图,是社区在替厂商往前推一步。

对中文圈独立开发者最直接的影响:你写的 skill 文件是真正属于你的资产,不是属于厂商的。Cursor 的 rules、Continue 的 config、Claude Code 的 skills,过去三年这条护城河在每个开发者本地的工具配置里慢慢叠厚。从 dotfiles 开始,到 vim/emacs 配置,到 IDE settings,现在轮到 AI agent skills。这条路径还有一个好处:中国大陆开发者不需要等 Anthropic / OpenAI 开放官方文档站,GitHub 上的开源 skill 集就是事实标准的索引。你写的 skill 跟硅谷工程师写的没有差别,都能被任何兼容的 client 跑起来。

写好 skill 也不是凭感觉,从 Pocock、Composio、Anthropic 三方的实践看下来,有几条共通的 best practice。description 字段写得越具体越好,模糊的描述 agent 读了不会照做,例如"帮你优化代码"远不如"在 PR 提交前自动检查类型错误、运行 linter、并修正 import 顺序"。skill 之间不要 overlap,否则 agent 在多个 skill 之间打架;触发条件最好互斥。skill body 用"必须"和"不要"这种命令式语言,避免"建议"和"可以考虑"这种弱语气 — agent 对硬约束的执行率明显高于软建议。最后,skill 越短越好,50-150 行 markdown 是甜点位,超过 300 行 agent 在执行末段会丢规则。

Anthropic 的反应也值得看 — 它发明了 skills,现在被 OpenAI 抄,会不会主动开放 SKILL.md 这个格式作为 industry standard?如果开放,Anthropic 拿到的是行业领头人的叙事;如果不开放,被 OpenAI / Composio 这种第三方接手定义,叙事就变成了"开源社区在替 Anthropic 推标准"。这是接下来六个月值得盯的局。Anthropic 之前在 MCP 这件事上选了开放路线 — Model Context Protocol 一开始就是开源标准,现在 Cursor、Cline、Continue 都支持。skill 这条线如果走同样路径,中长期对生态健康是好事;如果选封闭,反而可能被 OpenAI 抢走主导权。

往前再看半年,这场标准化还可能延伸到第三层:skill marketplace。当 skill 文件足够标准化、跨平台之后,会出现专门的 skill 商店 — 类似 VSCode extensions 的形态。开发者卖 skill,公司订阅 skill 包,有人专门做 skill 评测和质量认证。Composio 这次的 awesome-codex-skills 已经隐隐有 marketplace 雏形(installer 脚本可以一键安装第三方 skill)。这条产业链一旦形成,中国独立开发者有机会抢早期红利 — 写中文场景、本地化集成、跨境工作流这种 niche skill,海外厂商不会做但有真实市场。

实操建议:这周抽 1 小时把 awesome-codex-skills 的目录过一遍,挑 3-5 个跟你工作流匹配的 skill,clone 到本地,改改适配自己项目。即便你只用 Claude Code 不用 Codex,这些 skill 的 markdown 文件本身也可以直接复制到 ~/.claude/skills/,大部分能直接跑。互通性是这次最大的礼物 — 你的工作流不再被绑死在某一家厂商的客户端上,而是变成可以跨 agent 复用、跨团队共享、跨年迭代的资产。这就是 skill 机制的真正长期价值。一份你写过两年的 skills 文件夹,比你今天的任何具体技术栈都更接近你这个工程师的"个人资产"。框架会过时、模型会换代、IDE 会被取代,但你跟 agent 反复磨合出来的那套规矩,会一直跟着你走。这是 AI 时代独立开发者真正稀缺的护城河。今天开始写,五年后回看这绝对是最划算的投资之一。每写一个新 skill 都是把自己的工程经验沉淀成可执行格式。

转给那个还在每次手动跟 agent 解释项目规矩的同事 ↓

源链接在评论区 👇

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Codex #AIagent #AI日报
