---
layout: post
title: "问：能不能让一个普通文本文件，加一行 shebang 就变成可执行的 LLM 脚本？"
date: 2026-05-12 12:00:00 +0800
hero: /assets/llm-shebang-script/2026-05-12_1725_llm-shebang-script-hero.png
topic_tags: [llm-cli, simon-willison, shebang, shell, tool-calls, automation]
---

答：Simon Willison 这周写了一篇博客告诉你怎么做，写法极简。

最小版本就一行 shebang + 一行 prompt：

```

#!/usr/bin/env -S llm -f

Generate an SVG of a pelican riding a bicycle

```

把它存成 `pelican.sh`，`chmod +x`，然后 `./pelican.sh`。下面那行 prompt 会直接被送进 LLM CLI 执行，输出就是模型的回应。整个文件本身就是 prompt——没有解释器层，没有调用代码，shebang 把 LLM 当成了 interpreter。

`env -S` 这个 flag 是关键。Linux 的 shebang 默认只接一个参数，`-S` 允许把后面整串当作 multi-arg 传给 interpreter，所以 `llm -f`、`llm -T llm_time -f`、`llm -t` 这些组合都能塞进去。`-f` 是 read-from-file，让 llm CLI 把脚本文件本身当 prompt 读。

问：那要带 tool call 怎么办？

答：再加一个 `-T <tool_name>`：

```

#!/usr/bin/env -S llm -T llm_time -f

写一首带当前时间戳的俳句

```

这里 `llm_time` 是一个你预先在 llm CLI 注册过的 Python 函数 tool。模型在执行时会自己调这个工具，把当前时间塞进 prompt context，然后写俳句。脚本里不用写任何 glue code。

问：debug 怎么看？

答：跑的时候加 `--td` flag（tools debug），LLM CLI 会把每一次 tool call 打印出来，类似 `Tool call: multiply({'a': 2344, 'b': 5252})` 加返回值。逐步追踪很方便。

问：这有什么实际价值？

答：你可以把一类小任务彻底脚本化——日报、commit message、code review prompt、错误日志摘要——每个任务一个 shebang 文件，扔进 `~/bin/` 就能像普通命令一样调用，不用每次开 chat。配合 cron 也行：`0 9 * * * ~/bin/daily-summary.sh`，每天九点生成一份。

整件事的 vibe 是：LLM 不再是一个你要专门打开的 app，它就是 shell 工具链里一环。

转给那个还在浏览器里复制粘贴 prompt 的同事——他会想试一遍。

关注 @svtransit1 · 写给真在用 AI 的人

链接 · 👇 第一条评论

#AI #LLM #Claude #Shell
