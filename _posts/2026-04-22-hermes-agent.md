---
layout: post
title: "「有没有一个 agent 框架不被 Claude / OpenAI 绑死，还能跨会话记住上次学到的东西？」——这个问题今年问得越来越多，答案上周冲到 GitHub 109K 星。"
date: 2026-04-22 12:14:28 +0800
source: https://github.com/NousResearch/hermes-agent
hero: /assets/hermes-agent/2026-04-22_1205_hermes-agent-hero-raw.png
topic_tags: [nousresearch, agent-framework, open-source, skill-learning]
---

多数人第一反应是找 Claude Code 或 Cursor。但那一类本质上是包装好的厂商客户端——模型绑死、UI 绑死、工具链绑死，换家就是整个迁移项目；上下文也存在厂商服务器，换客户端就从零开始。想要真正的 agent 基础设施，得跳出客户端层。

叫 Hermes Agent，NousResearch 开的源，MIT 协议。做的事比听上去厚：一套自我改进的 agent 框架，从使用里自动创建 skill、随用随改进，对话历史持久化到跨会话建立用户模型——每次开 agent 它都记得上次的项目背景、风格偏好、踩过的坑。

模型那头直接放飞：官方宣称支持 200+ providers，Nous Portal / OpenRouter / NVIDIA NIM / Xiaomi MiMo / OpenAI / Hugging Face / Kimi / MiniMax 全都能接。切换不改代码，一句 `hermes model` 命令搞定。Claude Code 和 Cursor 这类官方客户端做不到这个自由度。

部署面也铺得宽——六种后端：本地、Docker、SSH、Daytona、Singularity、Modal；$5 的 VPS 能跑，GPU 集群也能扩，serverless 路径「闲置时几乎不花钱」。TUI 完整（多行编辑、斜杠命令、流式输出），cron 调度内置，还把 Telegram、Discord、Slack、WhatsApp、Signal 全做成可选入口。并行执行会开隔离子 agent，RPC 脚本层让外部系统直接驱动。

装法一行：

    curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash

Linux / macOS / WSL2 / Termux 都能跑。547 位贡献者、15.7K fork——维护强度是认真的。

和 Claude Code 是两条路：Claude Code 是成品，你买的是 Anthropic 的整条工具链；Hermes 是积木，重一点，但选模型、选后端、选入口的权力都在你手上。

仓库：github.com/NousResearch/hermes-agent

关注 @svtransit1 · 每天都有有用的 AI 资讯

#AI #AIagent #开源 #NousResearch #AI工具
