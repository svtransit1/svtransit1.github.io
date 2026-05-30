---
layout: post
title: "Claude Code 现在会一边帮你写代码，一边盯着你有没有写出漏洞了。🛡️"
date: trend 17:14:10 +0800
source: https://www.helpnetsecurity.com/2026/05/27/anthropic-claude-code-security-guidance-plugin/
hero: /assets/1700_claude-code-security-plugin/trend_2026-05-29_1700_claude-code-security-plugin-hero.png
topic_tags: [claude-code, security, vulnerability, anthropic, plugin]
---

Anthropic 上周给 Claude Code 上了一个官方的「安全审查」插件，免费、所有套餐都能用，终端里一句 /plugins 就装上。这两天在 X 上刷了快两百万阅读——值得说道说道它到底干了什么。

「它是每次都喊一个大模型来审吗？那不得慢死？」

不是。它分三层，越往后越深：

第一层，每次你改文件，先跑一遍纯规则匹配，不调模型、几乎零延迟，专抓那些一眼就危险的写法——eval()、os.system()、child_process.exec()、pickle 反序列化，还有前端那个臭名昭著的 dangerouslySetInnerHTML 和 .innerHTML=。

第二层，等这一轮改完，Claude 会把整段 git diff 拉出来通读一遍，找那些规则匹配漏掉的、需要理解上下文才能看出来的问题。

第三层最狠：当 Claude 真要 commit 或 push 的时候，它会连周边文件、相关的 sanitizer、调用链一起翻一遍，确认这个漏洞是不是真的，顺手把误报压下去。

「那它到底能抓哪些洞？」

靠正则覆盖了大概 25 类高危漏洞：SQL 注入、命令注入、XSS、硬编码的密钥和 API key、不安全的反序列化、输入没校验……基本是 OWASP 那一挂常客。

效果上，Anthropic 自己内部跑下来，用了这插件的 PR，安全相关的评审意见少了三到四成。

我觉得这东西真正的意义，不是「AI 又能干一件事」，而是它把安全审查从「上线前那道单独的关卡」往前挪到了「你敲代码的当下」。漏洞最便宜的修复时机，本来就是它刚被写出来的那一秒。

你写代码的时候，是有人在旁边盯着安全，还是全等 code review 那一刀？

🛡️ Anthropic 官方安全插件公告 + 三层审查细节 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #ClaudeCode #代码安全 #AIagent
