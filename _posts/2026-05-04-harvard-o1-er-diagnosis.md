---
layout: post
title: "\"我去急诊看病,AI 真的比急诊医生诊断更准吗?\"
date: 2026-05-04 09:13:34 +0800
source: https://techcrunch.com/2026/05/03/in-harvard-study-ai-offered-more-accurate-diagnoses-than-emergency-room-doctors/
hero: /assets/harvard-o1-er-diagnosis/2026-05-04_0700_harvard-o1-er-diagnosis-hero-raw.png
topic_tags: [openai, o1, harvard, beth-israel, medical-ai, er-diagnosis, science-journal]
---

短答案:在哈佛医学院刚发表的一项 Science 研究里,在 ER 初次分诊这个最紧张、信息最少的环节,OpenAI 的 o1 模型确实比两位主治医生答得更准——o1 在 67% 的病例里给出"完全正确或非常接近"的诊断,两位主治医生分别是 55% 跟 50%。但研究者自己第一时间提醒:这远不是"AI 可以独立看病"的信号,法律、责任、临床流程的事一件都还没解决。

具体怎么测的。研究团队来自 Harvard Medical School 跟 Beth Israel Deaconess Medical Center,用 76 个真实进 ER 的病人案例做对照。流程是这样:每个案例的初始电子病历(EMR 文本)同时给两位内科主治医生跟 OpenAI 的 o1 跟 4o 模型,让他们各自给出诊断,然后另外两位主治医生在不知道哪份诊断来自人哪份来自 AI 的盲评条件下给打分。这就是医学评估里的"双盲评分",意思是评分医生不会被"这是 AI 写的"或"这是同事写的"影响。

数字最关键的差距在第一诊断节点(initial ER triage),也就是病人刚进急诊、信息最少、决策最赶的那一刻。这一刻 o1 67%、医生甲 55%、医生乙 50%。研究指出这个差距在信息越少、时间越紧的场景里越大——一旦做完更多检查、拿到更多影像跟实验室数据,人跟 AI 的差距就开始收窄。换句话说,AI 在"你只有一段主诉文字就要给鉴别诊断"这种 cold-start 情境下表现尤其好。研究主作者之一 Arjun Manrai(哈佛 AI lab 负责人)的原话是:"我们把这个 AI 模型对着几乎所有基准都测了一遍,它压过了之前的模型,也压过了我们的医生 baseline。"

但同一篇研究的另一位主作者 Adam Rodman(Beth Israel 内科医生)在接受 Guardian 采访时立刻泼冷水:"AI 诊断现在没有任何正式的问责框架,病人还是希望由医生来主导诊疗决定。"换句话说,准不等于能用。临床部署需要 prospective trial(前瞻性试验)、需要监管框架、需要责任分配机制——这些没一个跟着诊断准确率自动到位。

谁该读一下这篇。如果你是医生,这是一个可以直接放进自己工作流的工具方向——把初始 EMR 喂给 o1,看它的鉴别诊断列表跟你自己的有没有出入,把这当 second opinion 用,看几个案例就能感觉到它的强项跟盲区在哪。如果你只是普通病人,这条信号不是"下次去医院前先问 ChatGPT"——AI 在缺关键检查数据的情境下表现好,反而意味着病人提供更完整的症状描述、最近用药史、检查结果给医生(或医院的辅助系统),整个诊断质量都会跟着提升。这条研究最有价值的副产品是它把"AI 在初诊比人准"这件事从论文猜测变成了 Science 级别的实证,接下来一两年的临床研究、监管讨论、医院 pilot 都会以这个数字为基线往前推,这个 baseline 一旦立住,讨论的语境就不一样了。

链接 · 评论区取 ↓

关注 @svtransit1 · 写给真在用 AI 的人

#AI #医疗 #OpenAI #o1
