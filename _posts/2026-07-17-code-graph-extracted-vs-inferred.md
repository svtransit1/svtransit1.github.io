---
layout: post
title: "🗺️ 给 AI 读你的代码库,现在流行的做法是塞进向量库、靠相似度模糊搜——快,但它是个黑盒,你并不知道它凭什么把两段代码扯到一起。"
date: 2026-07-17 18:16:03 +0800
source: https://github.com/Graphify-Labs/graphify
hero: /assets/code-graph-extracted-vs-inferred/2026-07-17_1800_code-graph-extracted-vs-inferred-hero.png
topic_tags: [code-search, knowledge-graph, claude-code, rag, agent-tooling]
---

Graphify 走了条相反的路:用 tree-sitter 把代码解析成一张确定的图,不用 embedding,也不出本机。更要紧的一点:它给每一条连线都打了标签——EXTRACTED(源码里明写的)还是 INFERRED(它自己推出来的)。哪条是事实、哪条是猜测,你一眼分得清。

模糊搜索真正的坑,是把"猜的"和"真的"一起端给你,你还看不出来。一张会区分事实和推断的图,至少让你知道:哪里可以直接信,哪里得回去核一核。它现在能挂进 Claude Code、Cursor、Codex、Gemini CLI 二十多个工具,一条 /graphify 就调起来。

它选了条更老实的路:一张能解释、能追溯的图——可解释,有时候比"更聪明"更管用。🧭

你更信一个说不清理由的相似度,还是一张标明了哪条是事实、哪条是猜测的图?

转给那个在陌生代码库里让 agent 乱翻的同事。

完整链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #代码搜索 #知识图谱 #AI编程
