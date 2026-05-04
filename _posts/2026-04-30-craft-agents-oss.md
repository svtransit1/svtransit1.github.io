---
layout: post
title: "craft.do 团队从今年开始做自家产品已经不开 VSCode 了——他们只用一个东西:自家做的 agent 客户端 Craft Agents,昨天 Apache 2.0 开源。"
date: 2026-04-30 21:13:30 +0800
source: https://github.com/lukilabs/craft-agents-oss
hero: /assets/craft-agents-oss/2026-04-30_2014_craft-agents-oss-hero-raw.png
topic_tags: [craft-agents, agent-native, claude-agent-sdk, open-source, vscode]
---

背景是这样。过去一两年市面上 agent 工具大致分两条路:一条把 agent 塞进 IDE 旁边的 chat 框,代表是 Cursor 和 Copilot Chat;另一条做 CLI 形态的 agent runner,代表是 Claude Code 和 Codex CLI。craft.do 自己内部用了一段时间,觉得这两条都是把 agent 当二等公民——主体还是文件树或者终端窗口,agent 是在边上协助。他们想反过来,UI 不再围着代码长,而是围着 agent 重新长一遍。所以 Craft Agents 不是"加了 AI 的 IDE",是干脆没有 IDE 这块。整个 app 启动起来,你看到的是一个 inbox 和一个对话面板,文档为中心,代码只是其中一种内容形态。

举个具体场景。你刚开了一个新的 workspace,想把今天的工作接进去。在 VSCode 那条路你打开 Linear 的 settings 找 personal API token、在 .vscode/mcp.json 里加 server config、然后问 chat 这个 token 怎么传——大概要跑七八步,中间还要切到几个外部页面。在 Craft Agents 这边你打字"接 Linear",剩下的事 agent 自己跑;它需要你授权的时候,弹一个 OAuth 窗口,你点同意,完事。同样接 Slack 和 Gmail 的过程也是这种节奏——把你过去要做的"机械配置工作"全部下沉到 agent 那一层。

这套设计跟主流路线最大的差别,可以拆成三个轴来看。

第一个轴是接 service 的方式。走 VSCode 那条路你要装插件、配 MCP server、贴 API key、跑 OAuth 流程,一个 service 接上来通常要十几分钟。Craft Agents 这边直接打字告诉 agent"帮我接 Linear",它去找 Linear 的公开 API 文档和 MCP server,自己读完,自己把 credential 流程跑完,自己把工具配置写好。Slack、Gmail、Postgres 都是这一套,你把已有的 OpenAPI spec 粘进去也行,把 endpoint 截图扔进去也行。没有配置文件,没有设置向导,没有"先打开开发者后台、生成 token、回来粘贴"的那一长串。它把"接服务"这件事从人的工作变成 agent 的工作。

第二个轴是 session 的形态。chat-bot 思路天然是单线程——你打开窗口、提问、等回复、继续问。问题是当你同时想跑五件事,这个形态会让人盯着窗口干等。Craft Agents 把 session 做成 inbox,多个任务并发跑,每个 session 有独立的工作流状态(Todo / In Progress / Needs Review / Done),可以加 flag,可以归档,可以暂时搁着不管。这一步把人从"守在 chat 窗口前"解放出来,变成"任务面板里挑哪些已经跑完、哪些等审"。这个形态贴近真实工作流——你本来就不会盯着每个后台任务,你查 inbox。

第三个轴是 skill 和 MCP 的迁移成本。这条特别戳那些已经在 Claude Code 里写了一堆 skills 的人——换平台不用从零再教一遍。一句"把我 Claude Code 里的 skills 都导进来",它把整套迁移自动做完。下面接的是 Anthropic 的 Claude Agent SDK + craft.do 自家的 Pi SDK 双层结构,provider 可以挂 Anthropic、Google AI Studio、ChatGPT Plus 的 Codex OAuth、GitHub Copilot OAuth,每个 workspace 可以设默认。多家 provider 不绑死在一家——你的 Anthropic 额度耗了,这个 workspace 切到 Google AI Studio,session 自己继续跑。32 个内置 Craft 工具,文档块、collection、search、tasks 都能直接调,不需要你再写胶水代码。还有一个看起来朴素但实际很有用的功能:Multi-File Diff,VSCode 风格的窗口,一次看完一轮 turn 里 agent 改了哪些文件——这是过去最容易让人不放心 agent 的地方,Craft Agents 把这个 surface 做得跟 IDE 一样仔细。

这三条加起来背后的逻辑是:agent 的能力已经强到可以承担"配置和路由"这一类工作,人不再需要为它做基础设施。把环境搭好这件事过去十几年都是工程师的活,现在 agent 接得上 API 文档、读得懂 OpenAPI、能跑 OAuth,它就该接过去。craft.do 这个团队的大胆之处是把这一步做得很早——别人还在 IDE 旁边加 chat 的时候,他们直接做了一个"chat 不是边栏,chat 是主体"的 app。

谁该看这个项目,谁可以先放放。如果你写代码主战场仍然是 IDE,agent 在你的工作流里只占一小角,Cursor 加 Copilot 已经够用,这个换不上来。但如果过去半年你的 agent session 数已经超过普通编辑会话,你已经在 Claude Code 里写到第二位数的 skills,你已经习惯把任务丢出去再回来收,Craft Agents 大概率是你下一站要看的方向。

跑起来的成本不高,curl 一行装,或者 git clone 后 bun install + bun run electron:start。Electron + TypeScript,代码可读。开源是最直接的"这是不是真能用"测试——能用不能用,你装了就知道。再看一眼 craft.do 自己的状态:他们说现在内部所有的开发都用 Craft Agents 完成,不再开任何代码编辑器。这句话本身就是最猛的一条 testimonial。如果一个团队愿意把自家产品的开发寄托在自家 agent 客户端上,那这个客户端至少在他们自己眼里是真的能跑生产级别的活。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #开源 #AIagent
