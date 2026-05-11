---
layout: post
title: "GitHub 这周窜得最猛的一个 repo,叫 DeepSeek-TUI——一周涨了 2.2 万颗星,目前 2.47 万星。它是一个跑在终端里的 DeepSeek V4 编码 agent,Rust 写的,定位上跟 Claude Code 是同一个生态位。我看了一圈,值得对着 Claude Code 比一下。"
date: 2026-05-11 18:14:07 +0800
source: https://github.com/Hmbown/DeepSeek-TUI
hero: /assets/deepseek-tui-terminal-agent/2026-05-11_1300_deepseek-tui-terminal-agent-hero.png
topic_tags: [deepseek-v4, deepseek-tui, claude-code, terminal-agent, rust]
---

先讲它能干什么:终端里跟模型对话、流式显示「思考块」、读改本地文件、跑 shell、搜网、管 Git、调子 agent。三种模式可切:Plan(只读规划)、Agent(每步有 approval gate)、YOLO(自动批准)。每一轮自动建一个 Git snapshot,可以一键回滚到任意一回合的状态——而且不动 repo 真实历史,这个细节挺漂亮。

跟 Claude Code 几条轴上对一下。

**模型层**——DeepSeek-TUI 默认走 deepseek-v4-pro 和 v4-flash,有一个 auto 模式根据每一轮的复杂度自动选模型 + 选思考深度。Claude Code 走 Anthropic 自家 Opus / Sonnet / Haiku,模型选择更稳但灵活度低。DeepSeek 一侧的卖点是「便宜 + 长上下文」(1M token,带 prefix-cache 感知 + 成本统计)。

**审批粒度**——DeepSeek-TUI 把模式拆成 Plan / Agent / YOLO 三档,从「只看不动」到「随便跑」全光谱。Claude Code 默认是 Agent 那一档,YOLO 等价于自己加 `--dangerously-skip-permissions`。

**编辑器诊断**——DeepSeek-TUI 内建 LSP,rust-analyzer / pyright / typescript-language-server / gopls / clangd 都在,改完代码自动跑诊断。Claude Code 是独立 CLI,自己直接读写文件,不内建 LSP,有需要走 MCP 接外部工具。前者「即开即诊」,后者「轻装上阵」。

**协议**——两边都支持 MCP,工具生态可以互相借。

**安装**——DeepSeek-TUI 提供 npm / cargo / brew / docker / 预编译二进制五条路径,安装门槛比 Claude Code 还低。

谁该试一下:你已经在用 DeepSeek API 或者跑 Ollama / SGLang / vLLM 本地推理,想要一个比 web UI 更顺手的终端入口——DeepSeek-TUI 是为你做的。你已经在 Claude Code 流程里、对 Anthropic 生态满意——没必要换。值得注意的是这个 repo 写在 README 显眼位置:「与 DeepSeek Inc 没有关联」。换句话说,这是社区项目,DeepSeek 自己没站台。

原文链接放在第一条评论 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#DeepSeek #ClaudeCode #AI #AIagent #AI日报
