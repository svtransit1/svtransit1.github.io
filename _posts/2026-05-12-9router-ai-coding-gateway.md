---
layout: post
title: "订了 Claude Code、Cursor、Codex 三家，月底还是被限流踢出来——这是不少人现在的日常。"
date: 2026-05-12 12:00:00 +0800
hero: /assets/9router-ai-coding-gateway/2026-05-12_1115_9router-ai-coding-gateway-hero.png
topic_tags: [9router, ai-coding-gateway, claude-code, cursor, token-compression, fallback]
---

9router 这两天冲到 GitHub trending 前几位，单日 941 star，目前总 star 8.5k。它想做的事很直接：装一个本地 CLI gateway，所有 AI 编码工具都从这一个口子出去，自动在多家供应商之间切换，省钱顺便兜底。

前端兼容的工具列了一长串：Claude Code、Cursor、Codex、Cline、Continue、Copilot、OpenCode、Kiro、Droid、Antigravity、Roo、Kilo Code——12 个名字几乎覆盖了主流 IDE 里的 AI 编码插件。后端聚合了 40 多个 model provider，从 Anthropic、OpenAI 到 DeepSeek、GLM、Vertex 都在里面。

省 token 的部分是它最具体的一块。叫 RTK Token Saver，专门压缩工具调用的回包——README 给的例子是一次原本要发 47K token 给 LLM 的请求，压完只发了 28K，省 40%。另外有个更狠的 Caveman Mode，号称输出 token 最多砍掉 65%。这两个数字都是项目自己测的，没经第三方验证，但思路是真的——agent 工作流里 tool output 重复度极高，能压。

更有意思的是它给的「白嫖配方」。Kiro AI 免费档（含 Claude 4.5 + GLM-5 + MiniMax 不限量）+ OpenCode 免费层 + Google Vertex 新户 300 美金信用，三层叠起来号称月成本可以做到 0。当然你得自己承担"哪家明天倒闭"的风险，但作为一个先把路由跑通再说的临时配置，思路挺现实。

安装一行 `npm install -g 9router && 9router`，然后浏览器打开 localhost:20128 看 dashboard，30 秒内能看到所有 provider 状态、token 用量、自动切换记录。

读完一圈我觉得它最值得装的不是省 token，是 fallback——你在 Cursor 里写到一半 Claude 报 429，gateway 直接切到 DeepSeek 接着把这次请求跑完，IDE 那头完全无感。这个体验对每天都靠 AI 写代码的人，比省 30% token 实用得多。

唯一要警惕的：把多家 API key 放进一个本地中间件，等于多了一个攻击面。如果你在公司机器上跑，先去 issue 区看看有没有 key 泄漏或者明文存储的报告，再下手。

转给那个还在为 quota 限流抓狂的同事——他大概率会想跑一遍。

关注 @svtransit1 · 写给真在用 AI 的人

来源 · 评论区取 ↓

#AI #ClaudeCode #AI编码 #开发者工具
