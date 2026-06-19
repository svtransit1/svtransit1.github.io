---
layout: post
title: "【原来…… VS Code 早就能在里面用任何大模型,很多人还在被 Copilot 绑着】🧐"
date: 2026-06-19 12:00:00 +0800
hero: /assets/vscode-byok/2026-06-19_1800_vscode-byok-hero.png
---

一直以来,VS Code 里的 Chat 只能用 Copilot 内置的那几个模型。但它其实已经支持"自带钥匙"(BYOK)——你塞进自己的 API key,就能在编辑器里把模型换成任何一家的。

为什么值得开?两类人最受益:

🔹 想省钱 / 用自家供应商的:接 Anthropic、OpenAI、Gemini、OpenRouter,用公司已有的账号和额度,不用再单独为 Copilot 的模型买单;

🔹 要隐私 / 想离线的:用 Ollama 或 Foundry Local 跑本地模型,代码不出本机,断网也能照聊。

⚙ 怎么开,五步:

1. Chat 面板 → Manage Language Models

2. 选 Add Models

3. 挑供应商(Azure / Anthropic / Hugging Face / Gemini / OpenAI / OpenRouter / Ollama / Foundry Local)

4. 填上 key 和配置

5. 回 Chat 的模型选择器,直接选你刚加的那个

但有个大多数标题不会告诉你的限制 ⚠️:BYOK 只管"Chat 这一侧"(聊天和辅助任务),不管你打字时的那个自动补全——补全用的还是 Copilot 自己的模型。而且别误会:这是在 Copilot Chat 里面换模型,不是把 Copilot 绕开了,它还得装着、登着。

所以这不是"彻底甩开 Copilot",而是"把编辑器和聊天模型解绑":编辑器正在从"绑死一家模型的客户端",变成"你自己挑模型的容器"。

原文 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #VSCode #ClaudeCode #赶快分享给还在被Copilot绑着的同事
