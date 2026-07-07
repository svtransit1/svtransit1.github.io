---
layout: post
title: "【原来……很多人还不知道:AI agent 现在能直接「看」懂 Word / Excel / PPT 了】"
date: 2026-07-07 21:22:00 +0800
source: https://github.com/iOfficeAI/OfficeCLI
hero: /assets/officecli-office-for-agents/2026-07-07_2100_officecli-office-for-agents-hero.png
topic_tags: [claude-code, mcp, agents, office-automation, tooling]
---

大多数人以为让 agent 处理 Office 文件,就是让它去解析 .docx 背后那一坨 OOXML——又长又乱,改个格子都容易翻车。有个刚冒头的开源工具 OfficeCLI(GitHub 9.3k star、C# 单个二进制、连 Office 都不用装)换了个招:给 agent 装「眼睛」。

它能干的活,大致两类:

文档类(Word / PPT)——按批注改稿、核对页眉页脚、把某页标题缩到不溢出、统一全篇字号配色、重排版式、生成一页汇报;每个元素都有条固定路径(像 /slide[1]/shape[2]),想动第几页第几个形状,直接指过去,不用在一堆标签里数括号。

表格数据类(Excel)——写进去的公式当场就算,内置 350 多个函数,动态数组、财务、统计分布都覆盖到了,一条命令生成 pivot,批量核数不用你手搓。

⚙ 怎么接上你的 agent:

1. 下 OfficeCLI 单个二进制(不用装 Office)

2. 跑 officecli mcp,起一个 MCP server

3. 它会自动认出你在用的工具(Claude Code / Cursor / VS Code Copilot / LM Studio)并装好 skill 文件

4. 让 agent 用 view screenshot 出每页截图、view html 出网页,或 watch 开实时预览,把文档「看」成图

5. 用路径定位到具体元素,改完再渲染回看,不对就再来一轮

带回家一个概念——「render → look → fix」循环:别让 agent 盲改 XML,先把文档渲染成图让它看见,改完再渲染回来确认,像人一样闭环。两个例子:

· 修 PPT:agent 看截图发现第 3 页标题溢出 → 按路径把那个标题缩字 → 再截图确认没出血

· 核 Excel:写进一条公式当场算出结果 → 生成 pivot → 渲染出来核对数字对不对

往大了看,这类工具在把「agent 能干的活」从纯代码、纯文本,挪到普通人每天在用的办公文档上——agent 的地盘,正从 IDE 往办公桌上爬。最先吃到红利的,大概率是天天跟 Excel、PPT 死磕的运营、财务和销售,程序员反倒排在后面。

P.S. 泼盆冷水:README 里「第一个、也是最好的」是作者自己讲的,别当真;9.3k star 说明还早、圈子还小;所有本事都是作者自述,没第三方验证;复杂排版渲染准不准,也还没人系统测过。想上手先拿不重要的文件试。

链接 · 👇 第一条评论

关注 @svtransit1 · 写给真在用 AI 的人

#AI #AIagent #ClaudeCode #转给天天和Excel搏斗的同事
