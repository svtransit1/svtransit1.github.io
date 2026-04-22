---
layout: post
title: "一个通用 agent 框架,3000 行代码,arXiv 论文刚挂,5.9k star。GenericAgent · 五件值得看的事(和一件值得怀疑的)。"
date: 2026-04-23 06:15:00 +0800
source: https://github.com/lsdefine/GenericAgent
hero: /assets/generic-agent/2026-04-23_0330_generic-agent-hero-raw.png
topic_tags: [ai-agent, generic-agent, skill-crystallization, l0-l4-memory, arxiv, open-source]
---

1. **核心就 100 行。** 整个 agent loop 压在 100 行里,骨架极薄。外围 3K 行分在 9 个原子工具和记忆管理上,加起来才到框架总量。

2. **9 个原子工具。** code_run、file_read、file_write、file_patch、web_scan、web_execute_js、ask_user、update_working_checkpoint、start_long_term_update。没有 agent 圈常见的 20+ tool 大礼包——设计上赌"少即是多",靠代码+文件+网页的基本能力去组合出一切。

3. **L0-L4 分层记忆。** L0 元规则、L1 索引、L2 稳定知识、L3 任务 SOP、L4 会话归档。跑完一个任务,它自动提取执行路径存成 L3 的"技能 skill",下次遇到相似任务直接调用,不是重跑推理。

4. **Demo 的路数有点野。** 外卖自动点单、EXPMA 金叉量化选股、网页自主探索边跑边总结、Alipay 账单 ADB 抓取记账。全是实用日常操作,不是 benchmark 跑分。

5. **MIT + arXiv 双轨。** 代码 MIT 协议,技术报告挂在 arXiv 2604.17091(两天前),作者看起来要把这事做成标准框架,不是一次性项目。

**值得怀疑的那件:** README 标题写"6x less token consumption",但正文没给任何对比数据或 benchmark 方法论——属于营销话术。框架值得跑,"6 倍省 token"这个数字暂时不要当真,跑一轮自己测。

安装四步:git clone + pip install streamlit pywebview + cp mykey_template.py mykey.py + python launch.pyw。

关注 @svtransit1 · 每天都有有用的 AI 资讯

https://github.com/lsdefine/GenericAgent

#AI #AIagent #开源 #LLM
