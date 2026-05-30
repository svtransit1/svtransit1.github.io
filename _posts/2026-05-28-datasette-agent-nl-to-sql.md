---
layout: post
title: "【原来......很多人都不知道你可以让 AI 直接问你的 SQLite 数据库?】📊⚡"
date: 2026-05-28 12:00:00 +0800
hero: /assets/datasette-agent-nl-to-sql/2026-05-28_2100_datasette-agent-nl-to-sql-hero-2-raw.png
---

很多 dev 团队的数据还躺在 SQLite 里, 想做点分析就得手写 SQL。Simon Willison 5 天前发的 Datasette Agent 把这事翻过来 — 你在对话框里用自然语言问问题, agent 自动写 SQL 跑给你看, 还能直接出图表、生成图、跑代码。

它实际能做什么:

① 数据查询场景

- NL → SQL 自动翻译, 你直接问「上个月哪些客户 churn 了」

- agent 跑完查询, 把结果展示成表格 / 图表

- 想再深一层, 接着问就好, agent 保留 session 上下文

- 全程不用你写 SQL, 不用记 schema, 不用切换工具

② 数据分析场景

- datasette-agent-charts 插件用 Observable Plot 画图

- datasette-agent-openai-imagegen 插件直接调 ChatGPT Images 2.0 给你生成图

- datasette-agent-sprites 插件提供 Fly Sprites 沙盒, agent 可以跑代码 (不止 SQL)

- 三个插件拼一起 = 完整 AI 数据工作台

⚙ 5 步本地跑通:

1 · 装 uv: `curl -LsSf https://astral.sh/uv/install.sh | sh` (mac/Linux)

2 · 装 LM Studio + 下个本地模型 (推荐 gemma-4-26b-a4b)

3 · 一行命令起 Datasette + Agent:

    `uvx --prerelease=allow --with datasette-agent --with llm-lmstudio datasette --internal internal.db --root -s plugins.datasette-llm.default_model lmstudio/google/gemma-4-26b-a4b data.db`

4 · 浏览器打开 http://localhost:8001, 找到 Agent 入口

5 · 用自然语言问你的数据库

它提的核心抽象很直接: 把数据库当一个可以对话的 datastore, agent 替你做翻译 + 视化 + 解释这三件事。

两个典型 Workflow 你可以建:

— Workflow A · 「客户数据日常巡检」

agent 每天问数据库: 新增用户数、活跃度变化、付费转化, 自动出图, 发给团队的 Slack 频道。SQL 你一行都不用写。

— Workflow B · 「ad-hoc 分析」

临时需求来了, 你直接打字: 「过去 30 天里, 哪些 product feature 的使用频率上涨最快?」 agent 跑 SQL + 出图 + 解释趋势, 3 分钟搞定。

这事的份量在: BI 工具 (Tableau / Looker / Metabase) 那套「先建 dashboard, 再点点点」的范式, 正在被 agent + 数据库这种「问就完了」的范式吃掉。BI 这条赛道接下来一年会被 AI 重新洗一遍。

P.S. 默认模型用的是 Gemini 3.1 Flash-Lite (云端), 也可以全本地跑 (LM Studio + 开源模型)。需要 reliable tool calls, 太小的模型跑不动, gemma-4-26b-a4b 算门槛。Live demo 在 agent.datasette.io。

转给那个还在手写 SQL 给老板做月报的同事 👇

关注 @svtransit1 · 写给真在用 AI 的人

📊 Simon Willison 原文 + 官方 live demo + datasette-agent GitHub · 评论区取 ↓

#Datasette #SimonWillison #AIagent #NLtoSQL #本地LLM
