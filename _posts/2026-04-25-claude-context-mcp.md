---
layout: post
title: "Anthropic API 这周还在排队限流。这边有人开了一道侧门——让 Claude Code 干同样的事，token 用量砍掉将近一半。"
date: 2026-04-25 18:13:28 +0800
source: https://github.com/zilliztech/claude-context
hero: /assets/claude-context-mcp/2026-04-25_1800_claude-context-mcp-hero.png
topic_tags: [claude-code, mcp, code-search, token-optimization, infra]
---

Zilliz 这周开源的 Claude Context MCP 是冲着大代码库来的。

它做的事其实很朴素：给 Claude Code 加一层语义代码搜索。底层是 Milvus 向量库，配 BM25 + 向量混合检索，整个仓库先被索引成可查的语义库。Claude 要读哪段代码，由检索环节先决定，而不是把整个目录倒进上下文。

官方仓库给的数字——保持检索质量等价的前提下，token 用量减少 40% 左右。同一段任务，原本要烧的 token 砍掉将近一半。

要算清的细节也直白：向量库用 Zilliz Cloud 或本地 Milvus；embedding 默认走 OpenAI API，也支持 VoyageAI、Gemini、Ollama——后者意味着可以做成完全本地。Node.js 必须 20.x 或 22.x，24 不兼容。

支持的客户端范围很广：Claude Code、Cursor、Windsurf、VSCode、Codex CLI、Qwen Code、Gemini CLI 都列在文档里——任何接 MCP 协议的工具理论上都能用。

权衡也写在标签上：你需要一个向量库实例 + 一个 embedding 提供方。省下的 Claude API 钱，一部分会变成 Zilliz / OpenAI embedding 那一侧的支出。小项目不一定划算，几十万行的仓库差距很明显。

语义代码搜索不是新概念。但把它做成开箱即用的 MCP 插件、且专门为 Claude Code 优化，这是第一次有完整的开源实现。Anthropic API 配额持续紧张的这周，这个工具的价值可能比平时高得多。

GitHub 仓库 · 👇 第一条评论

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #ClaudeCode #MCP #AI工具 #开源
