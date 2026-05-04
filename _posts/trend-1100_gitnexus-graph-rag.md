---
layout: post
title: "\"我让 Claude Code 改一个文件,改完它把另外三个引用这个函数的地方全漏掉了——为什么?\"
date: trend 11:13:41 +0800
source: https://github.com/abhigyanpatwari/GitNexus
hero: /assets/1100_gitnexus-graph-rag/trend_2026-05-01_1100_gitnexus-graph-rag-hero.png
topic_tags: [gitnexus, code-knowledge-graph, mcp, claude-code, agentic-coding, polyform]
---

短答案是 agent 没看到调用关系。它读到了那个文件、改对了那一行,但它从来不知道还有谁在调你。这事跟模型聪不聪明关系不大,跟它"看到的代码视野"关系大。LLM 拿到的上下文是一段一段拼出来的文本块,没有调用图、没有依赖关系、没有谁导入谁的连线——你让它做局部修改它能干,你让它做需要全局视野的修改,它就开始遗漏。这是过去半年 Claude Code、Cursor、Codex 在中型 repo 上反复出现的同一类失误,不是某个模型的问题,是整套上下文供给的方式还停留在文本拼接这一层。

具体怎么补这个洞,GitNexus 这个项目今天给了一个干净的答案,GitHub Trending 第一,昨天到今天一天涨了七百多颗星,累计三万三千多。它做的事情不复杂:把整个 repo 索引成一张知识图谱——每一条依赖、每一个 call chain、每一处执行流——然后把这张图通过 MCP 暴露给 agent。Claude Code、Cursor、Codex、Windsurf 都接得上,一句 `npx gitnexus analyze` 跑完整套——索引代码、装上 agent skills、给 Claude Code 注册 hooks、自动写好 `AGENTS.md` 和 `CLAUDE.md` 上下文文件。本地起一个 MCP server,你的 agent 改东西之前先问图谱"这个函数还有谁在调",再做决定。这一步把"假设没人在用"变成了"先看了再说"。换句话说,过去靠"agent 自己读文件 + 凭记忆"判断影响范围,现在变成"agent 查图谱+得到完整调用链",前者是猜后者是问。这两种工作方式对中大型 repo 的差距,基本就是改一个函数翻车与否的差别。

实现层面值得提的几点。一是底下用 Tree-sitter 解析 + LadybugDB 存图,CLI 版是本地持久化、增量更新,WebUI 版完全跑在浏览器里(WASM,不上传任何代码),适合临时看一个陌生 repo。二是 README 里那条对比很贴:DeepWiki 帮你理解代码,GitNexus 让你分析代码——一个是描述,一个是关系。三是企业版加了 PR review 的 blast-radius 分析、自动 reindex、多 repo 联合视图,定位是给团队级 agent 工作流当上下文层用——这条对那种"agent 写完 PR、人审"的团队特别有意义,你能先看一眼这个 PR 到底牵动了多少下游代码再决定要不要 merge。许可证是 PolyForm Noncommercial,商用走 akonlabs.com 的企业渠道。

这件事最大的信号其实不在 GitNexus 这一个项目身上,而是整个 agentic-coding 圈子开始集体承认:光给 agent 一个聪明的脑子是不够的,必须给它一张地图,否则在中大型 repo 里再聪明的脑子也会绕迷路。过去半年大家堆模型参数、堆 reasoning chain,2026 年的方向开始往"上下文工程"挪——怎么把代码、依赖、调用关系、变更历史这些信号塞进 agent 的视野里,让它做决定的时候有根据。GitNexus 是这条路最直白的一刀。

如果你已经在 Claude Code 上反复踩"改了 A 没改 B"的坑,这套是值得花一晚装下来跑一跑的方向。同样的 agent,加上一张完整的代码图,看到的视野不一样——它不会更聪明,但它不会再瞎改。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #AIagent #开源
