---
layout: post
title: "Chrome 148 默认在你硬盘上安一个 4GB 的 AI 模型，不问你。HN 5 小时 430 分、413 条评论，骂声占大头。"
date: 2026-05-05 21:10:44 +0800
source: https://www.thatprivacyguy.com/blog/chrome-silent-nano-install/
hero: /assets/chrome-silent-gemma-nano/2026-05-05_1730_chrome-silent-gemma-nano-hero-raw.png
topic_tags: [chrome, gemma, privacy, on-device-llm, google]
---

事情是这样：Chrome 147 还藏在两个 flag 后面 —— `#optimization-guide-on-device-model` 和 `#prompt-api-for-gemini-nano`。148 这两个 flag 一律默认开。结果是：你装 Chrome 升级，浏览器后台静默拉一份 Gemma Nano 模型 —— CPU 版 2.7GB、GPU 版 4.0GB，加上下载过程要 22GB 磁盘空间 + 两倍模型大小的临时空间。一句弹窗都没有。

Google 的逻辑：Prompt API 是 web 平台未来标配，每个网站都能调用本地 Gemini Nano，不用 token 不联网。听起来是在给开发者发福利、给用户省流量。问题是：用户没同意。一个浏览器升级悄悄占 4GB 硬盘 + 拉一个能识图能分析输入的模型 —— 在隐私语境下是越权动作。

更深一层是开发者 agency 的问题。Chrome 是 70%+ 桌面浏览器份额，Google 一旦把"on-device LLM"做成 web 标准默认项，所有 web app 都默认能用。Firefox / Safari 要不跟、要不抗 —— 跟的话浏览器互不兼容多一截，不跟的话用户体验落后。Anthropic 的 Claude.ai、OpenAI 的 ChatGPT web 端都得重新评估自己的 web 端策略。

这事儿在国内尤其敏感。Edge / Chromium 内核国产浏览器（QQ 浏览器、夸克、360）一旦默认 sync Chrome 148 这一段，就是"国产浏览器悄悄装 Google 模型"的合规问题。下半年要么有人提工信部投诉，要么有国产替代版本上线。

我自己的判断：默认 ON 这个决定 Google 撑不到一年。要么改成首次访问 Prompt API 的网站时弹窗、要么改成可选下载。3 周内会有更新。

升级前想保留 disk 的人，先去 chrome://flags 把那两个 flag 关掉，再点升级。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #Chrome #隐私 #Gemma #本地AI
