---
layout: post
title: "让 Claude 自己去爬 Cloudflare 后面的网站。Browserbase 这个礼拜把 9 个 skill 一起开源了，2000 多颗星。"
date: 2026-05-05 09:11:17 +0800
source: https://github.com/browserbase/skills
hero: /assets/browserbase-skills/2026-05-05_0600_browserbase-skills-hero-raw.png
topic_tags: [claude, agent-sdk, browserbase, browser-automation, captcha]
---

Claude Agent SDK 出门以前只能用文字工具：搜索、读文件、写代码。一旦下游网站要登录、要 CAPTCHA、要 anti-bot 反爬，agent 就当场卡住。Browserbase 把云端浏览器、住宅代理、CAPTCHA 解决器、cookie 同步、stealth 反指纹这一整摞工程，打成一个 skill 包丢给 Claude 直接调用。

跟手搓的方案放一起比一下，三条路各有各的偏好。

▍Browserbase Skills — 9 件套 SaaS

云端 Chrome session、residential proxy 切 IP、CAPTCHA 自动解、cookie 从本地同步上去、stealth 反 fingerprint、表单填充、文件上传、PDF 抓取、serverless 部署。每一项之前都要自己接 puppeteer + 反爬绕过，工程经验不薄的小团队也得花几天甚至一周。强项是 day-1 就能跑、运营托管、IP 池就绪、cookie 从本地浏览器一键同步上去（这点对要登录态做事的 RPA 特别值钱）、CAPTCHA 跳过率作者声称很高（自报数字未经第三方复测）。弱项也明显：按用量付费、Chrome session 要过他们的服务器、住宅代理流量按 GB 计费容易超预算、数据合规要看你目标行业。

▍Anthropic computer use — 本地路线

Claude 直接看屏幕、移鼠标、敲键盘，跑在你自己机器上。强项是数据不出门、不依赖第三方、最像"真人在用电脑"的姿态、合规上最稳。弱项是没有 IP 池、没有住宅代理、没有 CAPTCHA solver，碰到反爬重地需要自己拼一层；速度也比无头浏览器慢，因为要走视觉理解。

▍puppeteer / playwright + 自家反爬层 — 手搓

灵活度最高、单次成本最低、但工程时间最贵。维护反爬层是钉子户成本，每一次目标网站调整 anti-bot 规则、推 Cloudflare Turnstile 新版本，团队就要追着改。适合已经有团队在做爬虫多年、目标网站有限且稳定、对单条任务成本极度敏感的场景。新团队冷启动这条路至少烧两个月。

谁该上 Browserbase Skills？需要快速跑 RPA、价格监控、QA 自动化、招聘自动投递、电商竞品爬取、SEO 数据收集这类场景，团队没有反爬经验、不想自己养 IP 池、按月预算可控的人 —— 直接调 SDK，一周内就能进生产。谁先别动？数据敏感型业务（金融、医疗、合规、内部系统爬取）先评估数据流向；目标网站里有 ToS 明令禁止爬虫的也先看法律；单条任务超大量、长期重度使用的场景算一算月成本可能超过自家工程团队 —— 按用量计费在量大时反而吃亏。中间地带的小团队和 PoC 阶段的产品 —— 用 Browserbase 上线、跑通流程、跑出数据再决定要不要自建。

更大的信号是 agent 工具栈正在被分层托管。模型那一截商品化（最近 deepclaude / DeepSeek V4 这条路在切 Anthropic 的 API 利润），数据检索那一截开源化（前两天的 LearningCircuit / local-deep-research 把 OpenAI Deep Research 那条产品形态拆出来），现在浏览器自动化这一截被云端 SaaS 化。三个层都在同一个方向走 —— 单点工具能力的护城河越来越薄、专业基建变成订阅业务。

下半年还会看到更多"agent 周边基建"被打包成订阅服务：长期记忆 / 用户画像存储 / 邮件协作 / 日历调度 / 视频生成 / 语音克隆。剩下值钱的，是分发渠道、工作流调度的产品判断、长期工程经验、合规壁垒、行业 Know-how。这些慢、贵、难复制的部分才是新一波 AI 创业的真正护城河 —— 拿现成 SDK 拼出来的"AI agent for X"，下半年会看到大批死亡。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #Agent #Browserbase #AI工具
