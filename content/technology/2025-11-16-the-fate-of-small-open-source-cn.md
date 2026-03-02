---
title: "The fate of “small” open source (中文翻译)"
date: 2025-11-16
tags: [technology, web-clip, 中文翻译]
source: https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/
category: technology
lang: zh
translation_source: "2025-11-16-the-fate-of-small-open-source"
translator: "Claude-3-Haiku (via OpenRouter)"
---

> 🌐 **English Version**: [[2025-11-16-the-fate-of-small-open-source|Read original English version]]
# The fate of “small” open source

小型开源软件的命运

标题: 小型开源软件的命运

来源链接: https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/

发布时间: 2025-11-16T19:10:35+00:00

Markdown 内容:

小型开源软件的命运 | 读懂茶叶
===============

[读懂茶叶](https://nolanlawson.com/)软件和其他黑暗艺术, by Nolan Lawson
============================================================================================

![图片 1: 搜索](https://s0.wp.com/wp-content/themes/pub/springloaded/images/search-btn.gif?m=1230136840i)

*   [主页](https://nolanlawson.com/)
*   [应用](https://nolanlawson.com/apps/)
*   [代码](https://nolanlawson.com/code/)
*   [演讲](https://nolanlawson.com/talks/)
*   [关于](https://nolanlawson.com/about/)

« [为什么浏览器会节流 JavaScript 定时器?](https://nolanlawson.com/2025/08/31/why-do-browsers-throttle-javascript-timers/)

[<time>元素应该真正做点什么](https://nolanlawson.com/2025/12/14/the-time-element-should-actually-do-something/) »

11月16日

小型开源软件的命运
-------------------------------

2025年11月16日由 Nolan Lawson 发布在 [软件工程](https://nolanlawson.com/category/software-engineering/). 标签: [LLMs](https://nolanlawson.com/tag/llms/). [9 条评论](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comments)

我写过的 npm 包中,最受欢迎的无疑是 [`blob-util`](https://www.npmjs.com/package/blob-util),它已有10多年历史,每周仍有500万+次下载。

它是一个小型的 JavaScript 工具集,用于处理 [`Blob`](https://developer.mozilla.org/en-US/docs/Web/API/Blob)。我写它是因为发现 PouchDB 用户对如何处理 `Blob`以及如何将它们转换为字符串、`ArrayBuffer`等等感到非常困惑。

鉴于[约80%的开发者](https://survey.stackoverflow.co/2025/ai#sentiment-and-usage)现在在日常工作中使用AI,`blob-util`几乎肯定是大多数开发者会让LLM为他们生成的东西。当然,你 _可以_ 使用 `blob-util`,但这就意味着要引入一个额外的依赖,带来未知的性能、维护和供应链风险。

果然,Claude 在被提示时会很乐意为你生成所需的 `Blob` 工具:

_> 用 TypeScript 编写一个函数,将 Blob 转换为 ArrayBuffer,并返回一个 Promise。_

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19`function``blobToArrayBuffer(blob: Blob): Promise<ArrayBuffer> {`

```return``new``Promise((resolve, reject) => {`

```const reader =``new``FileReader();`

```reader.onload = () => {`

```if``(reader.result``instanceof``ArrayBuffer) {`

```resolve(reader.result);`

```}``else``{`

```reject(``new``Error(``'Failed to read Blob as ArrayBuffer'``));`

```}`

```};`

```reader.onerror = () => {`

```reject(reader.error);`

```};`

```reader.readAsArrayBuffer(blob);`

```});`

`}`

Claude生成的版本与[`blob-util`的版本](https://github.com/nolanlawson/blob-util/blob/99c06472d18329eda1421286692bd875d76d5c9c/src/blob-util.ts#L384-L394)非常相似(这并不奇怪,因为它可能是从那里训练出来的!)。虽然它更冗长,但多余地检查了 `readAsArrayBuffer` 是否真的返回了 `ArrayBuffer`(这确实让TypeScript更开心)。公平地说,它也改进了我的实现,直接用 `reject` 抛出错误,而不是使用更笨拙的 `onerror` 事件。

**注意:** 对于那些想知道的人来说,是的,Claude确实建议使用新的 [`Blob.arrayBuffer()`](https://developer.mozilla.org/en-US/docs/Web/API/Blob/arrayBuffer) 方法,但它也生成了上述代码以支持"旧环境"。

我想有些人会认为这是进步:fewer依赖,更健壮的代码(尽管有些冗长),比起老式的"搜索 npm,找到一个包,读文档,安装它"的方式,更快的交付时间。

我对这个库没有过多的自豪感,也不太关心下载量的增减。但我确实认为AI方式带来了一些损失。当我写 `blob-util` 时,我采取了一种教师的心态:README有一个[可爱而富有想象力的教程](https://www.npmjs.com/package/blob-util#tutorial),里面有粉红色的kirby(那时我喜欢在所有东西里放任天堂角色)。

目标不仅仅是给你一个解决问题的工具(尽管它确实做到了),还要 _教会_ 人们如何有效地使用JavaScript,这样你就能在将来解决其他问题。

我不知道我们正在走向何方(好吧,大约80%的人;对于剩下的坚持者,我向你们致敬并祝你们一路顺风!),但我确实认为这是一个我们更重视即时答案而不是教学和理解的未来。使用像 `blob-util` 这样的东西的需求减少了,这意味着编写它的动力也减少了,因此教育人们了解这个问题领域的动力也减少了。

现在已经有一股趋势,将文档放在一个 [`llms.txt`](https://llmstxt.org/) 文件中,这样你就可以直接让一个代理去读它,而不需要自己费心去理解英语文字。(这还算是文档吗?文档究竟是什么?)

结论
----------

我仍然相信开源,并且仍在继续做下去(虽然断断续续)。但有一点已经很清楚了:像 `blob-util` 这样的小型、低价值的库的时代已经结束了。它们已经因为Node.js和浏览器吸收了越来越多的功能(见 `node:glob`、`structuredClone`等)而走向衰落,而LLMs无疑是最后一颗釘子。

这确实意味着,这些库作为用户教育的跳板的机会减少了(Underscore.js [也有这种理念](https://underscorejs.org/docs/underscore-esm.html)),但也许这没什么不好。如果不需要找一个库来,比如说[对数组中的项进行分组](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/groupBy),那么学习这种库的机制可能就是不必要的。许多软件开发人员会认为,让候选人反转二叉树是毫无意义的,因为这在日常工作中从未出现过,所以也许对于工具库来说也是如此。

我仍在试图弄清楚在这个新时代,哪些类型的开源是值得编写的(提示:那些LLM无法轻易生成的),以及哪里最缺乏教育。我目前的想法是,最有价值的是更大的项目、更有创意的项目,或者涉及LLM训练数据覆盖范围之外的更专门的主题。例如,我回顾自己在 [`fuite`](https://github.com/nolanlawson/fuite) 和各种[内存泄漏追踪博文](https://nolanlawson.com/2022/01/05/memory-leaks-the-forgotten-side-of-web-performance/)方面的工作,我很满意LLM无法复制这些,因为它需要创新的研究和创造性的技术。(尽管谁知道:也许有一天,一个代理会撞击Chrome堆快照,直到找到内存泄漏。我会等着看它实现。)

人们最近一直在为开源在LLM时代的定位而焦虑,但我仍然看到有人在推动边界。例如,许多悲观者认为写一个新的JavaScript框架是没有意义的,因为LLM已经被大量训练过React了,但接着就出现了不屈不挠的[Dominic Gannaway](https://github.com/trueadm)写了[Ripple.js](https://www.ripplejs.com/),又一个JavaScript框架(而且[还有一些新想法](https://podrocket.logrocket.com/ripple-js-dominic-gannaway-logrocket-podrocket))。这就是我喜欢看到的:人类在机器面前大笑,继续他们的人类事业。

所以如果这篇漫无目的的博文(原谅我这个柔软的人类大脑,我没有使用LLM来写这篇文章)有什么结论的话,那就是:是的,LLM已经使某些类型的开源过时了,但仍有大量的开源可以写。我很兴奋看到你们会创造出什么样新颖和意想不到的东西。

### _相关文章_

[浏览器中二进制数据的现状](https://nolanlawson.com/2015/06/30/the-state-of-binary-data-in-the-browser/ "浏览器中二进制数据的现状")2015年6月30日 在 "Webapps"

[介绍Cordova SQLite插件2](https://nolanlawson.com/2016/04/10/introducing-the-cordova-sqlite-plugin-2/ "介绍Cordova SQLite插件2")2016年4月10日 在 "Webapps"

[我在浏览器上报告的bug](https://nolanlawson.com/2024/03/03/bugs-ive-filed-on-browsers/ "我在浏览器上报告的bug")2024年3月3日 在 "Web"

### 9 条对这篇文章的回应

1.   ![图片 2: Ralph Haygood的头像](https://2.gravatar.com/avatar/8835b386e2c474ab19e99505da23750db2fd6a307a418604937ffae4ac8a32c0?s=30&d=https%3A%2F%2F2.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D30&r=G) 由 Ralph Haygood 于 [2025年11月16日 下午1:21](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238069) 发表 "但这就意味着要引入一个额外的依赖,带来未知的性能、维护和供应链风险":那么与其使用一个已经在数百万网站上使用了近10年的小型JavaScript库,不如使用一个巨大、不断变化的统计模型,它有已知的广泛范围的漏洞(提示注入)? 这太荒谬了。我怀疑很少有人会因为担心性能、供应链风险或最不可能的维护问题而使用 klarna coding。我猜他们这样做是因为受到了"新鲜事物综合症"(程序员群体确实很容易受到这种影响)的困扰,他们懒惰得可怕*,或者他们的老板威胁要解雇他们,如果他们不这样做的话。

我称之为 klarna coding 而不是 vibe coding,因为就像 Klarna 一样,它是先买后付,也就是说,如果你做了大量这样的事情,你的代码库中很可能会积累大量的技术债务。你(Lawson)提供了一个小小的例子:正如你指出的,"Claude的版本...要冗长得多",这使得理解它稍微更困难,而不是更容易。除非你在一家计划被收购或破产的初创公司工作,在那里没有人需要担心你拼凑在一起的糟糕代码,否则你应该关心人类能否轻松理解你的代码,因为不管 Anthropic 或 Anysphere 的营销材料如何吹嘘,迟早总会有人(比如你一年后的自己)需要这样做。

哦,好吧。这一切都意味着大量的高利润工作,等待那些愿意清理 klarna coding 造成的混乱的人:

[https://www.404media.co/the-software-engineers-paid-to-fix-vibe-coded-messes/](https://www.404media.co/the-software-engineers-paid-to-fix-vibe-coded-messes/)

另见:

[https://pivot-to-ai.com/2025/09/09/if-ai-coding-is-so-good-where-are-the-little-apps/](https://pivot-to-ai.com/2025/09/09/if-ai-coding-is-so-good-where-are-the-little-apps/)

*我自己也是一个不可否认的懒人,但我不会懒到愿意在糟糕的工作上签名。

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238069#respond)  
2.   ![图片 3: Tim McCormack的

标题：小型开源项目的命运

内容：
Holdout 在这里。:-) 请注意,在大语言模型出现之前,就已经有同样的选择:编写一个实用程序函数,或从一个库中引入它。实用程序函数通常并不太难编写,但仅凭我的记忆,就有一些原因可以避免编写它们,而这些原因与所需的努力无关:

    *   维护、搜索和理解代码库更小。
    *   需要运行的单元测试更少。
    *   该库可能已经消除了大部分主要的错误和边缘情况。
    *   调试时的边界更清晰("可能不需要进入这个函数,因为它来自一个库")。
    *   如果是一个流行的库,那么阅读调用实用程序函数的代码就会更容易;你已经知道那个函数调用的作用。

当然也有缺点,特别是对于真正小型或微不足道的库来说,但你明白我的意思 — 实用程序库当时就有价值,因此现在也有价值。

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238070#respond)

3.   ![Image 4: Jim Shortz's avatar](https://2.gravatar.com/avatar/537a10a4f34d8c6c114594f78641d4d5f521f1cb48c52f5d0e68e72a9302dd32?s=30&d=https%3A%2F%2F2.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D30&r=G) 由 Jim Shortz 于 [2025年11月17日 上午9:05](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238071) 发表 首先,感谢您为社区贡献了有价值的开源项目。但是,我不得不对教学角度表示尊重的不同意见。

我已经不情愿地开始使用AI大语言模型,主要是用于涉及我不常使用的技术栈(如Node.js)的业余项目。当我让它为我编写某些内容时,我并不只是接受它给出的内容。我会仔细阅读,确保我理解每一行都在做什么。如果有我不熟悉的语言结构或库函数,我可以提出后续问题来了解它是什么。

尽管它只是一台机器(有时会给我错误的答案),但我发现"对话"式的风格在帮助我学习新事物方面是一个很大的优势。

最终,我通常不会使用它生成的内容,或者我会把它作为一个起点并大量修改它。

相比之下,我已经依赖了数百个开源库,但除非遇到问题,否则我从未深入研究过它们。

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238071#respond)  
4.   ![Image 5: Manuel Jasso's avatar](https://graph.facebook.com/v6.0/10162958391802442/picture?type=large) 由 Manuel Jasso 于 [2025年11月17日 下午12:28](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238072) 发表 Nolan,首先:我很想你。

我已经编写代码大约40年了,尽管这波AI浪潮令人印象深刻,但我已经见过足够多的令人印象深刻的技术浪潮,可以说最终只有时间才能告诉我们这一波会落在哪里。我们今天说的一切只是猜测。

我对这波AI浪潮有一个担忧,就是你提到的学习和理解与代码生产的问题。

我担心年轻的程序员会过度依赖一些本质上不可靠的东西,因为我认为信任是一种人与人之间的现象。是的,这是我的观点,它不对也不错,只是我的信念。没有人能证明我是对是错,只有时间才能告诉我们。

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238072#respond)  
    *   ![Image 6: Nolan Lawson's avatar](https://1.gravatar.com/avatar/4ef0fd7e6ff4540febaf58f7a093ee4a4f285dcba7fb1543ebcc17670d8b03e8?s=30&d=https%3A%2F%2F1.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D30&r=G) 由 [Nolan Lawson](http://nolanlawson.com/) 于 [2025年11月18日 下午1:13](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238075) 发表 我也很想你,Manuel!是的,我确实有这种担忧。不过,我还是试着保持乐观态度 — 也许我们只是在增加"不需要知道的底层细节"的列表。

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238075#respond)  

5.   ![Image 7: Unknown's avatar](https://hrbrmstrsdailydrop.files.wordpress.com/2023/12/site-logo.png?w=30) 由 [Drop #732 (2025-11-17): Reliable Sources – hrbrmstr's Daily Drop](https://dailydrop.hrbrmstr.dev/2025/11/17/drop-732-2025-11-17-reliable-sources/) 于 [2025年11月17日 下午12:32](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238073) 发表 […] 所引用的文章质疑了在AI驱动的开发世界中,像blob-util这样的小型npm包的未来,引用了Nolan Lawson关于小型开源项目的帖子([https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/)) […]

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238073#respond)  
6.   ![Image 8: Tim's avatar](https://0.gravatar.com/avatar/37102125b390509c367181cf5df2791502ea1cbfb484db8234d1392031c9a12b?s=30&d=https%3A%2F%2F0.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D30&r=G) 由 Tim 于 [2025年11月17日 下午3:47](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238074) 发表 既然这是互联网,我要抓住你说的一个偶然的评论,然后跑到一个疯狂的切题上。

"80%的开发者现在在日常工作中使用AI"

80%_的StackOverflow用户_。我想这并不太令人惊讶,因为人们去那里寻找答案来解决小型、自包含的问题,这正是大语言模型擅长的。这也绝对不能代表所有的开发者。

我在的每一个非网络开发领域(航空航天、嵌入式系统、主要开源关系型和文档型数据库之外的数据库、游戏、工业等)在StackOverflow上都代表不足或根本没有代表。例如,"playstation4"标签只有4个问题,而且还没有"playstation5"标签。难道真的有人相信整个全球PlayStation开发者社区在5年内没有一个问题吗!

还有许多语言/库已经有了很好的在线社区,从未觉得有必要搬到那里。例如,StackOverflow上的平均Lisp问题都很基础(有大量关于"hello world"和设置编辑器的问题),而认真的Lisp程序员仍然在其他地方聚会。很明显,那些只是为了好玩而试图弄清楚新语言基本语法的人会大大过度代表LLM的使用。

我认为你的观察中更有趣的是:编写你汽车信息娱乐系统的人(例如)会使用LLM来内联所有的库,而不是采用实际的依赖关系吗?如果是这样,他们将如何在以后调试它,因为他们不理解代码,也无法使用依赖管理器进行升级?如果他们用这种方式编写ECU的代码会怎样?

我们已经认为公司蛇吞象地利用志愿者维护者是一件坏事了(XKCD: 2347)。情况只会变得更糟,因为现在他们不仅要利用我们的源代码,而且还不需要遵守许可条款,甚至在发现问题时也不需要提交错误报告。

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238074#respond)  
7.    由 [Open Source Now for Rich Peeps : Stephen E. Arnold @ Beyond Search](https://www.arnoldit.com/wordpress/2025/12/03/open-source-now-for-rich-peeps/) 于 [2025年12月3日 凌晨2:07](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238093) 发表 […] 曾经,开源只属于一个小众市场的初创公司。Nolan Lawson在他的博客"Read The Tea Leaves"上写了一篇名为"小型开源项目的命运"的文章。他解释说,越来越多的开发者在工作中使用AI […]

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238093#respond)  
8.    由 [Dödar AI öppen källkod? | Computer Sweden](https://computersweden.se/article/4130775/dodar-ai-oppen-kallkod.html) 于 [2026年2月12日 晚上9:00](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#comment-238255) 发表 […] 源项目最受影响。Nolan Lawson最近在一篇题为"小型开源项目的命运"的文章中探讨了这个问题。Lawson是blob-util库的作者,这个库有数百万次下载 […]

[回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/?replytocom=238255#respond)  

### 发表评论 [取消回复](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/#respond)

Δ

该网站使用Akismet来减少垃圾评论。[了解您的评论数据是如何处理的。](https://akismet.com/privacy/)

### 最新文章

*   [你有一个故事](https://nolanlawson.com/2026/02/18/you-had-a-story/)
*   [奇迹与奇迹的日子](https://nolanlawson.com/2026/02/15/days-of-miracle-and-wonder/)
*   [我们悼念我们的技艺](https://nolanlawson.com/2026/02/07/we-mourn-our-craft/)
*   [15年博客生涯](https://nolanlawson.com/2026/02/01/15-years-of-blogging/)
*   [一次性构建浏览器API](https://nolanlawson.com/2026/01/31/building-a-browser-api-in-one-shot/)

### 关于我

![Image 9: Photo of Nolan Lawson, headshot](https://nolanlawson.com/wp-content/uploads/2023/01/profile_17.jpg?w=300)
我是来自西雅图的程序员Nolan,在Socket工作。所有观点都是我自己的。照片由Cătălin Mariș拍摄。

### 归档

标题："小型"开源项目的命运

内容：
*   [2026年2月](https://nolanlawson.com/2026/02/)(4)
*   [2026年1月](https://nolanlawson.com/2026/01/)(2)
*   [2025年12月](https://nolanlawson.com/2025/12/)(4)
*   [2025年11月](https://nolanlawson.com/2025/11/)(1)
*   [2025年8月](https://nolanlawson.com/2025/08/)(1)
*   [2025年6月](https://nolanlawson.com/2025/06/)(1)
*   [2025年4月](https://nolanlawson.com/2025/04/)(1)
*   [2025年1月](https://nolanlawson.com/2025/01/)(1)
*   [2024年12月](https://nolanlawson.com/2024/12/)(2)
*   [2024年10月](https://nolanlawson.com/2024/10/)(2)
*   [2024年9月](https://nolanlawson.com/2024/09/)(3)
*   [2024年8月](https://nolanlawson.com/2024/08/)(1)
*   [2024年7月](https://nolanlawson.com/2024/07/)(1)
*   [2024年3月](https://nolanlawson.com/2024/03/)(1)
*   [2024年1月](https://nolanlawson.com/2024/01/)(1)
*   [2023年12月](https://nolanlawson.com/2023/12/)(4)
*   [2023年8月](https://nolanlawson.com/2023/08/)(2)
*   [2023年1月](https://nolanlawson.com/2023/01/)(2)
*   [2022年12月](https://nolanlawson.com/2022/12/)(1)
*   [2022年11月](https://nolanlawson.com/2022/11/)(2)
*   [2022年10月](https://nolanlawson.com/2022/10/)(2)
*   [2022年6月](https://nolanlawson.com/2022/06/)(4)
*   [2022年5月](https://nolanlawson.com/2022/05/)(3)
*   [2022年4月](https://nolanlawson.com/2022/04/)(1)
*   [2022年2月](https://nolanlawson.com/2022/02/)(1)
*   [2022年1月](https://nolanlawson.com/2022/01/)(1)
*   [2021年12月](https://nolanlawson.com/2021/12/)(3)
*   [2021年9月](https://nolanlawson.com/2021/09/)(1)
*   [2021年8月](https://nolanlawson.com/2021/08/)(6)
*   [2021年2月](https://nolanlawson.com/2021/02/)(2)
*   [2021年1月](https://nolanlawson.com/2021/01/)(2)
*   [2020年12月](https://nolanlawson.com/2020/12/)(1)
*   [2020年7月](https://nolanlawson.com/2020/07/)(1)
*   [2020年6月](https://nolanlawson.com/2020/06/)(1)
*   [2020年5月](https://nolanlawson.com/2020/05/)(2)
*   [2020年2月](https://nolanlawson.com/2020/02/)(1)
*   [2019年12月](https://nolanlawson.com/2019/12/)(1)
*   [2019年11月](https://nolanlawson.com/2019/11/)(1)
*   [2019年9月](https://nolanlawson.com/2019/09/)(1)
*   [2019年8月](https://nolanlawson.com/2019/08/)(2)
*   [2019年6月](https://nolanlawson.com/2019/06/)(4)
*   [2019年5月](https://nolanlawson.com/2019/05/)(3)
*   [2019年2月](https://nolanlawson.com/2019/02/)(2)
*   [2019年1月](https://nolanlawson.com/2019/01/)(1)
*   [2018年11月](https://nolanlawson.com/2018/11/)(1)
*   [2018年9月](https://nolanlawson.com/2018/09/)(5)
*   [2018年8月](https://nolanlawson.com/2018/08/)(1)
*   [2018年5月](https://nolanlawson.com/2018/05/)(1)
*   [2018年4月](https://nolanlawson.com/2018/04/)(1)
*   [2018年3月](https://nolanlawson.com/2018/03/)(1)
*   [2018年1月](https://nolanlawson.com/2018/01/)(1)
*   [2017年12月](https://nolanlawson.com/2017/12/)(1)
*   [2017年11月](https://nolanlawson.com/2017/11/)(2)
*   [2017年10月](https://nolanlawson.com/2017/10/)(1)
*   [2017年8月](https://nolanlawson.com/2017/08/)(1)
*   [2017年5月](https://nolanlawson.com/2017/05/)(1)
*   [2017年3月](https://nolanlawson.com/2017/03/)(1)
*   [2017年1月](https://nolanlawson.com/2017/01/)(1)
*   [2016年10月](https://nolanlawson.com/2016/10/)(1)
*   [2016年8月](https://nolanlawson.com/2016/08/)(1)
*   [2016年6月](https://nolanlawson.com/2016/06/)(1)
*   [2016年4月](https://nolanlawson.com/2016/04/)(1)
*   [2016年2月](https://nolanlawson.com/2016/02/)(2)
*   [2015年12月](https://nolanlawson.com/2015/12/)(1)
*   [2015年10月](https://nolanlawson.com/2015/10/)(1)
*   [2015年9月](https://nolanlawson.com/2015/09/)(1)
*   [2015年7月](https://nolanlawson.com/2015/07/)(1)
*   [2015年6月](https://nolanlawson.com/2015/06/)(2)
*   [2014年10月](https://nolanlawson.com/2014/10/)(1)
*   [2014年9月](https://nolanlawson.com/2014/09/)(1)
*   [2014年4月](https://nolanlawson.com/2014/04/)(1)
*   [2014年3月](https://nolanlawson.com/2014/03/)(1)
*   [2013年12月](https://nolanlawson.com/2013/12/)(2)
*   [2013年11月](https://nolanlawson.com/2013/11/)(3)
*   [2013年8月](https://nolanlawson.com/2013/08/)(1)
*   [2013年5月](https://nolanlawson.com/2013/05/)(3)
*   [2013年1月](https://nolanlawson.com/2013/01/)(1)
*   [2012年12月](https://nolanlawson.com/2012/12/)(1)
*   [2012年11月](https://nolanlawson.com/2012/11/)(1)
*   [2012年10月](https://nolanlawson.com/2012/10/)(1)
*   [2012年9月](https://nolanlawson.com/2012/09/)(3)
*   [2012年6月](https://nolanlawson.com/2012/06/)(2)
*   [2012年3月](https://nolanlawson.com/2012/03/)(3)
*   [2012年2月](https://nolanlawson.com/2012/02/)(1)
*   [2012年1月](https://nolanlawson.com/2012/01/)(1)
*   [2011年11月](https://nolanlawson.com/2011/11/)(1)
*   [2011年8月](https://nolanlawson.com/2011/08/)(1)
*   [2011年7月](https://nolanlawson.com/2011/07/)(1)
*   [2011年6月](https://nolanlawson.com/2011/06/)(3)
*   [2011年5月](https://nolanlawson.com/2011/05/)(2)
*   [2011年4月](https://nolanlawson.com/2011/04/)(4)
*   [2011年3月](https://nolanlawson.com/2011/03/)(1)

### 标签

[可访问性](https://nolanlawson.com/tag/accessibility/)[AI](https://nolanlawson.com/tag/ai/)[alogcat](https://nolanlawson.com/tag/alogcat/)[Android](https://nolanlawson.com/tag/android-2/)[Android Market](https://nolanlawson.com/tag/android-market/)[Apple](https://nolanlawson.com/tag/apple/)[App Tracker](https://nolanlawson.com/tag/app-tracker/)[基准测试](https://nolanlawson.com/tag/benchmarking/)[Boost](https://nolanlawson.com/tag/boost/)[Bootstrap](https://nolanlawson.com/tag/bootstrap/)[浏览器](https://nolanlawson.com/tag/browsers/)[Bug 报告](https://nolanlawson.com/tag/bug-reports/)[catlog](https://nolanlawson.com/tag/catlog/)[和弦阅读器](https://nolanlawson.com/tag/chord-reader/)[代码](https://nolanlawson.com/tag/code/)[联系人](https://nolanlawson.com/tag/contacts/)[持续集成](https://nolanlawson.com/tag/continuous-integration/)[版权](https://nolanlawson.com/tag/copyright/)[Couch Apps](https://nolanlawson.com/tag/couch-apps/)[CouchDB](https://nolanlawson.com/tag/couchdb/)[CouchDroid](https://nolanlawson.com/tag/couchdroid/)[开发者](https://nolanlawson.com/tag/developers/)[开发](https://nolanlawson.com/tag/development/)[表情符号](https://nolanlawson.com/tag/emoji/)[Grails](https://nolanlawson.com/tag/grails/)[HTML5](https://nolanlawson.com/tag/html5/)[IndexedDB](https://nolanlawson.com/tag/indexeddb/)[信息检索](https://nolanlawson.com/tag/information-retrieval/)[日语名称转换器](https://nolanlawson.com/tag/japanese-name-converter/)[JavaScript](https://nolanlawson.com/tag/javascript/)[Jenkins](https://nolanlawson.com/tag/jenkins/)[KeepScore](https://nolanlawson.com/tag/keepscore/)[ListView](https://nolanlawson.com/tag/listview/)[Logcat](https://nolanlawson.com/tag/logcat/)[LogViewer](https://nolanlawson.com/tag/logviewer/)[Lucene](https://nolanlawson.com/tag/lucene/)[Nginx](https://nolanlawson.com/tag/nginx/)[NLP](https://nolanlawson.com/tag/nlp/)[Node](https://nolanlawson.com/tag/node/)[Node.js](https://nolanlawson.com/tag/nodejs/)[npm](https://nolanlawson.com/tag/npm/)[离线优先](https://nolanlawson.com/tag/offline-first/)[开源](https://nolanlawson.com/tag/open-source/)[密码](https://nolanlawson.com/tag/passwords/)[性能](https://nolanlawson.com/tag/performance/)[Pinafore](https://nolanlawson.com/tag/pinafore/)[PokeDroid](https://nolanlawson.com/tag/pokedroid/)[PouchDB](https://nolanlawson.com/tag/pouchdb/)[PouchDroid](https://nolanlawson.com/tag/pouchdroid/)[查询扩展](https://nolanlawson.com/tag/query-expansion/)[相关性计算器](https://nolanlawson.com/tag/relatedness-calculator/)[相关性系数](https://nolanlawson.com/tag/relatedness-coefficient/)[S3](https://nolanlawson.com/tag/s3/)[Safari](https://nolanlawson.com/tag/safari/)[讽刺](https://nolanlawson.com/tag/satire/)[分段ListView](https://nolanlawson.com/tag/sectioned-listview/)[安全](https://nolanlawson.com/tag/security/)[语义版本](https://nolanlawson.com/tag/semver/)[Shadow DOM](https://nolanlawson.com/tag/shadow-dom/)[社交媒体](https://nolanlawson.com/tag/social-media/)[Socket.IO](https://nolanlawson.com/tag/socket-io/)[软件开发](https://nolanlawson.com/tag/software-development/)[Solr](https://nolanlawson.com/tag/solr/)[单页应用](https://nolanlawson.com/tag/spas/)[SuperSaiyanScrollView](https://nolanlawson.com/tag/supersaiyanscrollview/)[同义词](https://nolanlawson.com/tag/synonyms/)[Twitter](https://nolanlawson.com/tag/twitter/)[UI 设计](https://nolanlawson.com/tag/ui-design/)[终极填字游戏](https://nolanlawson.com/tag/ultimate-crossword/)[W3C](https://nolanlawson.com/tag/w3c/)[Web 应用](https://nolanlawson.com/tag/webapp/)[Web 应用程序](https://nolanlawson.com/tag/webapps-2/)[Web 平台](https://nolanlawson.com/tag/
---
## 📝 翻译说明

本文由 **AI 自动翻译**，可能存在翻译不当之处。

| 项目 | 信息 |
|------|------|
| **原文链接** | [点击查看](https://nolanlawson.com/2025/11/16/the-fate-of-small-open-source/) |
| **翻译模型** | Claude-3-Haiku (via OpenRouter) |
| **翻译来源** | OpenRouter API |
| **翻译时间** | 2025-11-16 |
| **校对状态** | 待人工校对 |

> 💬 如发现翻译问题，欢迎在评论区指正，帮助改进翻译质量。
