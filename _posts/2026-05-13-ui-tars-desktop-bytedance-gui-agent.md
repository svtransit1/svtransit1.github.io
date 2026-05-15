---
layout: post
title: "\"我的 agent 到底会不会真的去点屏幕上的按钮?\"
date: 2026-05-13 12:00:00 +0800
hero: /assets/ui-tars-desktop-bytedance-gui-agent/2026-05-13_2100_ui-tars-desktop-bytedance-gui-agent-hero.png
---

过去一年所有 agent 产品都在比谁的工具调用更聪明、谁的记忆更便宜、谁的 router 更小。但有一件最朴素的事一直被绕开——这玩意儿真的会操作 UI 吗?答案大多数时候是"不会"。它能调 API,能写代码,能查数据库,但你要它打开 VS Code 把 autosave 选项找出来勾上,它就跳过了。这一周 ByteDance 把这一块补上了:UI-TARS-Desktop 开源,33.6K 星,这周新增 3.8K,在 GitHub 上爬得很凶。

它跟 LangChain、Claude Code 那类抽象编排层不在一个层。UI-TARS 押的是最底层的"看 + 点":模型(ByteDance 自己的 UI-TARS 视觉语言模型)直接看你的屏幕截图、识别 UI 元素、规划鼠标轨迹、按键。换句话说,它把"agent 怎么变成一双手"这件事单独抽出来做了。这条路 OpenAI Operator 和 Anthropic Computer Use 也在走,但 UI-TARS 是开源的——连模型权重一起开,可以本地跑。

具体怎么用:两种模式。Local Operator 把模型跑在你这台电脑上,vision-loop 完全不出机器,适合企业内部数据的场景。Remote Operator 在云端虚拟桌面上跑,适合"我想让它帮我连续干几个小时,但不占我本地屏幕"的场景。跨 Windows、macOS、加浏览器内三个平台。

repo 里 demo 的工作流挺接地气:"帮我把 VS Code 的 autosave 打开"、"去 GitHub 看一下我们仓库还有几个 open issue"、"把 Excel 里这一列数字加起来"——这些之前你得自己写个 Python 脚本去做的小活,现在自然语言一句就过。当然 vision-language agent 还是会偶尔点错按钮,但这种"能错"的实物级别工具,比一万个"我会写 prompt"的 wrapper 都值钱。

下一波 agent 进步可能不在模型大小或编排框架,在屏幕这一层——谁先让它准确点按钮,谁就赢了"computer use"这条赛道。

关注 @svtransit1 · 写给真在用 AI 的人

链接 · 👇 第一条评论

#AI #AIagent #开源工具 #ComputerUse
