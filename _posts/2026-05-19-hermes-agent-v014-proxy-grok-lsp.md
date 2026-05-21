---
layout: post
title: "NousResearch 这周把 hermes-agent 推到 v0.14.0,代号 \"The Foundation Release\"。808 个 commits、633 个 PR、165K 行 insertion、215 个社区贡献者。我挑五件 AI 编程者今天就该装的事。"
date: 2026-05-19 23:02:17 +0800
source: https://www.blocktempo.com/nousresearch-hermes-agent-proxy-claude-chatgpt-supergrok-lsp-diagnostics-xai/
hero: /assets/hermes-agent-v014-proxy-grok-lsp/2026-05-19_0900_hermes-agent-v014-proxy-grok-lsp-hero.png
topic_tags: [hermes, nousresearch, agent, proxy, claude-pro, chatgpt-pro, supergrok, lsp, ai-tools]
---

1. `hermes proxy` —— Pro 订阅当 API key

跑 `hermes proxy`,本地起一个 OpenAI 兼容端点,后面接的是你 Claude Pro / ChatGPT Pro / SuperGrok 的 OAuth 登录态。然后 Codex CLI、Aider、Cline、Continue 全部不用申请 API key 就能用。一份订阅,所有工具复用 —— 这件事真正解决了 "我有 Pro 但工具要 API" 的痛。

2. grok-4.3 · 1M context via SuperGrok OAuth

xAI 这次进来得很狠。SuperGrok 订阅者 OAuth 登入就能用 Grok,不要单独 API key、不要单独账单。顺手把 grok-4.3 的 context 拉到 100 万 token,整个 codebase / research corpus 灌进去就是一个 prompt。

3. LSP semantic diagnostics on every write

每次 agent 跑 `write_file` 或 `patch`,Hermes 自动跑一遍 Language Server,把类型错误、未定义符号、缺失 import 当场返给 agent。LLM "我已经改好了" 但其实没动文件,或者动了但代码炸 —— 这两个常见骗局,这一版终于堵了。

4. `pip install hermes-agent` —— 直接上 PyPI

不用 clone 仓库、不用 shell installer。一行 pip 完事。Wheel 自带 Ink TUI 和 shell launcher,装完直接 `hermes` 起。同时把 22 个 messaging adapter 拆成 lazy-install,首次用到才装,默认安装变得很瘦。

5. 冷启动砍掉 19 秒 + browser_console 180×

冷启动用 skill cache、lazy import、disk-first model catalog 一起优化,`hermes tools` 的 All Platforms 屏从 14 秒掉到 1.5 秒以下。browser_console 现在复用一条 CDP WebSocket,以前几秒的浏览器内 eval 变成毫秒级。

收一句话:Hermes 这版的逻辑不是 "再加功能",是 "把已经买过的订阅榨干"。如果你已经在用 Claude Pro / ChatGPT Pro / SuperGrok,这一版至少值得 demo 一下 proxy 看看 token 账单怎么走。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#Hermes #NousResearch #ClaudePro #ChatGPTPro #AI工具
