---
layout: post
title: "让 Claude Code 自己写 n8n workflow，不用再翻 1650 个 node 的文档。这个 MCP 一天涨了 500 颗星，总数到 1.9 万。"
date: trend 11:11:00 +0800
source: https://github.com/czlonkowski/n8n-mcp
hero: /assets/1100_n8n-mcp/trend_2026-05-05_1100_n8n-mcp-hero.png
topic_tags: [mcp, n8n, claude-code, automation, workflow]
---

n8n-MCP 这个项目，czlonkowski 写的，直接把 n8n 那 1650 个 node API 全部包成 MCP tool 喂给 Claude Code、Cursor、Windsurf 之类的 IDE。你跟 Claude 说一句"做一条 Slack 收到关键词触发就推到 Notion 顺便发邮件提醒"，它能自己去查 node 怎么配、validate 字段、把整条 workflow YAML 吐出来部署上去。

这么干的人多了，问题始终卡在前两步：node 发现 + 字段配置。n8n 一个 node 平均七八个字段、二三十个可选参数，写错一个就跑不通；翻文档慢、试错也慢，新手第一次跑通一条 5-step workflow 平均要烧两小时。MCP 这一层把 node schema 拉成 tool definition，Claude 看到的不是文档而是结构化能力 —— "这是个 Slack node，能 send-message / read-channel / search-history / react，每个动作要这些 input、返这些 output"。模型挑哪个 node、填哪些字段、怎么连线，一次过的概率高得多。作者说 1650 节点全覆盖，self-host 也行，云端 dashboard.n8n-mcp.com 有 100 次/天的免费额度，足够个人玩家试。

安装也轻：MCP server 一行 npx 就起，IDE 那边在 settings.json 里加一段就接通了。我自己没跑，但能预判一个边界 —— 复杂 conditional branching 和 loop 这类高阶逻辑，模型还是容易写出"看起来对但跑起来死循环"的 workflow，前期人工 review 不能省。

这条路本质上是把 SaaS 产品的 UI 那层 bypass 掉。n8n 之前最贵的部分是它的可视化编辑器和 node 库 —— 编辑器降低小白门槛、node 库收摄使用频率。MCP 接进来之后，编辑器变成可选项 —— 你想用就用，不用就直接让 Claude 帮你拼，跑通了再去 UI 里检查参数。Zapier、Make、Airflow、Pipedream、Workato 这些 workflow 工具下半年都会面对同一个问题：当 IDE 里的 AI 能直接生成 workflow 配置，他们的 UI 价值还剩多少？答案是：还剩"非工程师友好的 UX"和"已有的客户合同"。但增量市场会被 IDE-driven 的玩法侵蚀。

举个具体场景。假设你想做一条这样的自动化：每天扫一下你 Gmail 里所有未读 newsletter，提取核心要点，写到 Notion 数据库里，每周一早上 9 点把这周积累的发到 Slack 频道顺便 @相关同事。手搓 n8n 你要找：Gmail node、IMAP 配置、AI summarization node、Notion API 鉴权、Slack webhook、cron 触发器、conditional 路由 —— 6-7 个 node，每个 node 字段都要查文档。新手两小时起步。用 n8n-MCP，跟 Claude 描述上面这一段话，它直接吐 workflow JSON，再让你自己在 n8n UI 里打开微调，10 分钟跑通。这种"从思路到能跑的自动化"的距离被压短得很狠。

更大的信号是 MCP 这条协议正在快速吃掉"应用层和 agent 之间"的中间层。前两天 Browserbase Skills 把浏览器自动化做成 MCP-compatible 的 SDK，今天 n8n-MCP 把 workflow 编排做成 MCP，下半年还会看到数据库 client、ETL 工具、CMS 后台、内部系统逐个接入。每接进来一个，agent 的工具栈就深一层、人手写胶水代码的需求就少一段。再过半年到一年，"接 API 写胶水代码"会从工程日常变成稀缺活。

价格视角顺手算。Zapier Professional 最低档 $19.99/月、Make Standard 起价 $9/月、n8n cloud Starter 也要 $20/月。n8n self-host 加上 n8n-MCP cloud 免费 100 次/天的额度，对个人开发者和小团队来说接近零成本。月预算敏感的玩家这条路算下来比上面三个都便宜。

谁该试？已经在用 n8n 跑自动化、刚开始用 Claude Code 或 Cursor 做工程的人 —— MCP 装一下就能省掉大量复制粘贴。谁先别动？还没想清楚业务流的人 —— 工具再快也救不了流程没设计好；Zapier 重度玩家、合同已经签下来的、对 self-host DevOps 不感冒的，也先别折腾。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #MCP #n8n #自动化
