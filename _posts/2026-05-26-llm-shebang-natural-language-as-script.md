---
layout: post
title: "很多人开始用 Claude Code、Codex、Gemini CLI 这一类 agent 工具时,第一反应通常是「我怎么把 prompt 写得更像咒语」。但 Simon Willison 5 月 11 号在他 TIL 上贴的那条小笔记,指了另一条更值得想的路:"
date: 2026-05-26 12:00:00 +0800
hero: /assets/llm-shebang-natural-language-as-script/2026-05-26_0900_llm-shebang-natural-language-as-script-hero.png
---

#把自然语言当成可执行脚本

也就是说:把 prompt 不再当成你「跟模型聊天的话」,而是当成一个可以放在 `#!/usr/bin/env -S llm -f` shebang 行下面、`chmod +x` 之后直接 `./run.sh` 跑起来的、第一类公民的可执行文件。

#shebang是操作系统给文件的一张身份证

回想 shebang 的本意——`#!/bin/bash`、`#!/usr/bin/env python` 这一行写在文件最顶,操作系统就知道「这文件该交给哪个解释器去跑」。Bash 文件交给 bash,Python 文件交给 python。

Simon 这个观察的意义是:`#!/usr/bin/env -S llm -f` 等于新签了一份合约——「这个文件,交给 LLM 当解释器」。文件正文是什么?是自然语言。

#最小可跑的样子

Simon 自己贴的最小例子,两行:

```

#!/usr/bin/env -S llm -f

Generate an SVG of a pelican riding a bicycle

```

存成 `pelican.sh`、`chmod +x pelican.sh`、`./pelican.sh`——直接产出一只骑自行车的鹈鹕 SVG。没有 Python 中间层、没有 API client 库、没有 main 函数。

#四个 escalating 用法

第一档:`-f` 把 prompt 当 fragment 拼进对话。

第二档:`-T tool_name` 把外部工具(比如 `llm_time` 拿到系统时间)插进 LLM 推理链。

第三档:`-t template.yaml` 把整个脚本结构化——`model`、`system`、`functions` 这些字段写在 YAML 里,prompt 部分变成模板调用。

第四档:`--td` 调试整个 prompt-template 渲染过程,看 LLM 真正收到的最终 prompt 长什么样。

每一档都是「把 shell 工程师 30 年来熟悉的 composable 武器(管道、参数、debug flag)直接套到 LLM 上」。

#不会写脚本怎么办

如果你从没写过 shell 也别躲——这正是 Simon 这条 pattern 最妙的地方:`.sh` 文件的内容就是自然语言,你直接打:

「找出当前目录所有 .png,按文件大小排序」

「读 README.md,给我提取所有 install 步骤」

「检查这段 Python 代码有没有 SQL injection 风险」

存成 `task.sh`,`chmod +x`,跑。出错不知道为啥?加 `--td` 看渲染。要换模型?改 YAML 里的 `model: gpt-5.5`。要给它工具权限?加 `-T tool_name`。

整套学习曲线对一个非工程师,大概一晚上。

#这件事在大叙事里的位置

过去 50 年,「把指令变成可重复执行的文件」一直是 shell 工程师生产力的核心——shell scripts、Makefile、Dockerfile 都是这个 motif 的版本。Simon 这条 pattern 的位置很清楚:`#!llm` 是这条 motif 的下一个版本。自然语言成了可以 `chmod +x` 的第一类公民。

下一步大概率是:VS Code 这样的编辑器直接把 `#!llm` 文件当 native 文件类型对待;package manager 出现「LLM 脚本仓库」;团队把日常运维的小活儿全部以 `.sh` + 自然语言写成可 review 的 PR。

shell 是 PC 时代的电,自然语言是 AI 时代的电。Simon 这条 pattern 是给后者第一次画上插座。

原文 · 👇 第一条评论

#AI #LLM #ClaudeCode #DevTools #SimonWillison #硅谷中转站
