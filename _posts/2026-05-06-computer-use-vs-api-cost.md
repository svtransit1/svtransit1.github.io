---
layout: post
title: "让 agent 看屏幕点鼠标，比让它直接调 API 贵 45 倍 —— Reflex 这个礼拜跑完 benchmark，把数字摆在桌上：53 步 / 55 万 token vs 8 次调用 / 1.2 万 token。"
date: 2026-05-06 09:10:54 +0800
source: https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/
hero: /assets/computer-use-vs-api-cost/2026-05-06_0630_computer-use-vs-api-cost-hero.png
topic_tags: [computer-use, claude, agent-cost, reflex, benchmark]
---

任务很普通：管理一个有 900 客户、600 订单、324 评价的后台 admin 面板，做点筛选、分页、关联查询。两条路都用 Claude Sonnet：一条是让 Claude 截屏、看图、点界面（computer use），一条是让 Claude 直接调内部 API。结果差距大得有点夸张。

先看 token。computer use 走完任务花 55.1 万 token，比 1.2 万 token 的 API 路线多 45 倍。按 Claude Sonnet 当前定价（input \$3 / output \$15 每百万 token）换算，单次任务大约 \$1.65 vs \$0.04。一万次自动化跑下来 \$16500 vs \$400，差三个零的尾巴。

延迟更夸张。vision agent 平均 1003 秒、标准差 254 秒 —— 基本上跑一次接近 17 分钟，运气不好半小时。Sonnet 的 API 路线 19.7 秒、Haiku 的 API 路线 7.7 秒。从用户体感看，前者是"开了任务去喝咖啡"，后者是"按下回车就出结果"。

成功率这一块更值得记一下。最初没有详细 prompt 时，vision agent 直接失败。作者补了一份 14 步详细 walkthrough 提示之后才能跑通 —— 等于把工程师写的产品手册塞进每次调用，那"自动化"两个字就有点尴尬。API 那条路 100% 成功，重复跑 N 次结果一致。

为什么 vision 路线这么贵？三层叠加：第一，每一帧截屏都是几万 token 的图像输入，53 步意味着至少 50 张截图轮流喂给模型，光图像 token 就压死成本；第二，agent 推理"看到什么、点哪里"需要长 chain-of-thought，每一步都在 thinking 里写"我看到一个蓝色按钮，标题是 Submit，鼠标坐标 ..."，输出 token 也跟着膨胀；第三，一旦中间一步识别错（按钮被遮挡、弹窗没等出现、表格列宽变了导致点错位），retry 让整条链翻倍消耗 —— 这个是非线性的，越长的任务 retry 风险叠加越凶。

工程意义上还有第四层：调试体验差很多。API 调用错了立刻报 schema 错误，看一眼就知道；vision agent 跑错了你要回去翻 53 张截图找哪一步认错了元素，调试一次的人力成本比一次任务的 token 成本还高。这个隐性成本论文里没算。

那 computer use 还有用武之地吗？有，但是边界很窄。三种场景值得用：第一，第三方 SaaS 没开放 API —— 比如某些 CRM、ERP、政府系统、银行老旧后台，没接口、不会有接口；第二，内部系统但没人维护接口文档 —— 公司内部那种"传说中的"管理后台，找不到能写出 schema 的工程师；第三，跨多个不相关产品做端到端流程 —— 比如自动从 Salesforce 拉客户数据、登录某个第三方报税平台填表、再回写到 Notion 文档。这种链路上 API 那条路根本拼不出来，vision agent 是唯一选择。Anthropic 当初推 computer use 的姿态本来也是"作为 fallback 而不是 default"，作者文章里特意点了这一点。

对自己做内部工具的人，作者的建议很直接："数学算出来已经指向另一边"。要做自动化，先看看你能不能花一个小时给后台加几条结构化 API。一万次跑下来省下来的钱够你雇半个工程师。

Anthropic 上礼拜搞合资公司外包企业落地、deepclaude 切走 Claude Code 的模型层、Browserbase 把浏览器自动化打包成 SDK，再加上今天这条 benchmark —— agent 工具栈的成本结构正在被一项一项重新算账。模型那一截商品化、工具栈那一截 SaaS 化、computer use 那一截被 ROI 数字打回去当 fallback 用。下半年值钱的是工作流编排和 ROI 判断，不是会用最炫的工具。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Claude #computeruse #agent #成本
