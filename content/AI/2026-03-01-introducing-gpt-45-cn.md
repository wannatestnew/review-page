---
title: "Introducing GPT-4.5 (中文翻译)"
date: 2026-03-01
tags: [ai, web-clip, 中文翻译]
source: https://openai.com/index/introducing-gpt-4-5/
category: AI
lang: zh
translation_source: "2026-03-01-introducing-gpt-45"
translator: "GLM-5 (NVIDIA NIM)"
---

> 🌐 **English Version**: [[2026-03-01-introducing-gpt-45|Read original English version]]
# Introducing GPT-4.5

标题：介绍 GPT-4.5

内容：

标题：介绍 GPT-4.5

来源链接：https://openai.com/index/introducing-gpt-4-5/

Markdown 内容：

介绍 GPT-4.5 | OpenAI
===============

[](https://openai.com/)

*   [研究](https://openai.com/research/index/)
*   产品
*   [商业](https://openai.com/business/)
*   [开发者](https://openai.com/api/)
*   [公司](https://openai.com/about/)
*   [基金会](https://openai.com/foundation/)

登录[试用 ChatGPT(在新窗口打开)](https://chatgpt.com/)

*   研究
*   产品
*   商业
*   开发者
*   公司
*   [基金会](https://openai.com/foundation/)

[试用 ChatGPT(在新窗口打开)](https://chatgpt.com/)登录

OpenAI

目录

*   [扩展无监督学习](https://openai.com/index/introducing-gpt-4-5/#scaling-unsupervised-learning)
*   [针对人类协作的训练](https://openai.com/index/introducing-gpt-4-5/#training-for-human-collaboration)
*   [更强大的推理能力在路上](https://openai.com/index/introducing-gpt-4-5/#stronger-reasoning-on-the-horizon)
*   [安全性](https://openai.com/index/introducing-gpt-4-5/#safety)
*   [如何在 ChatGPT 中使用 GPT-4.5](https://openai.com/index/introducing-gpt-4-5/#how-to-use-gpt-45-in-chatgpt)
*   [如何在 API 中使用 GPT-4.5](https://openai.com/index/introducing-gpt-4-5/#how-to-use-gpt-45-in-the-api)
*   [结论](https://openai.com/index/introducing-gpt-4-5/#conclusion)
*   [附录](https://openai.com/index/introducing-gpt-4-5/#appendix)

2025 年 2 月 27 日

[发布](https://openai.com/research/index/release/)[产品](https://openai.com/news/product-releases/)

介绍 GPT‑4.5
===================

我们最强大的 GPT 模型的研究预览版。面向全球 Pro 用户和开发者。

[在 ChatGPT 中试用(在新窗口打开)](https://chatgpt.com/)

加载中...

分享

我们发布了 GPT‑4.5 的研究预览版 - 这是我们迄今为止最大和最好的聊天模型。GPT‑4.5 是在扩展预训练和后训练方面的一个进步。通过扩展无监督学习,GPT‑4.5 提高了其识别模式、建立联系和产生创造性洞见而无需推理的能力。

早期测试显示,与 GPT‑4.5 交互感觉更自然。它更广泛的知识库、更好的跟随用户意图的能力以及更高的"情商"使它在改善写作、编程和解决实际问题等任务中很有用。我们也预计它会产生更少的幻觉。

我们将 GPT‑4.5 作为一个研究预览版发布,以更好地了解它的优势和局限性。我们仍在探索它的能力,并期待看到人们以我们可能没有预料到的方式使用它。

扩展无监督学习
-----------------------------

我们通过扩展两个互补的范式来推进 AI 能力:无监督学习和推理。这代表了两个智力维度。

1.   无监督学习增加了世界模型的准确性和直觉。像 GPT‑3.5、GPT‑4 和 GPT‑4.5 这样的模型推进了这一范式。
2.   [扩展推理⁠](https://openai.com/index/learning-to-reason-with-llms/)，另一方面,教会模型在做出响应之前进行思考和产生思维链,使它们能够解决复杂的 STEM 或逻辑问题。像 OpenAI o1 和 OpenAI o3‑mini 这样的模型推进了这一范式。

GPT‑4.5 是通过扩展计算能力和数据,以及架构和优化创新来扩展无监督学习的一个例子。GPT‑4.5 是在微软 Azure AI 超级计算机上训练的。结果是一个拥有更广泛知识和对世界有更深入理解的模型,从而减少了幻觉并在各种主题上更可靠。

#### 扩展 GPT 范式

GPT-4.5 (2025)
--------------

第一种语言是什么?

我们不知道第一种语言究竟是什么,科学家认为我们可能永远也无法确定,因为口语语言出现在书面记录之前很长一段时间。

以下是我们所知道的:

*   **没有单一的"第一语言":** 语言可能是在不同的人类群体中逐步发展起来的,时间可以追溯到数万年甚至数十万年前。
*   **起源于非洲:** 大多数科学家认为,口语语言可能最早出现在非洲,大约在 10 万年前。
*   **原始语言:** 与其说是单一语言,不如说人类最初可能是从简单的交流开始,逐步发展成更复杂的语言。最早的语言形式可能包括手势、声音和信号,用于表达基本的想法和情感。
*   **失落在历史中:** 由于语音没有留下直接的化石记录,而且书写出现得相对较晚(大约在 5000 年前),我们无法知道最早的语言到底是什么样子的。

今天,语言学家研究现有的语言,以了解它们在数千年间是如何演化的,但人类最初的语言到底是什么,这个谜团可能永远也无法解开。

#### 更深入的世界知识

##### SimpleQA 准确率(越高越好)

##### SimpleQA 幻觉率(越低越好)

_SimpleQA 衡量大型语言模型在简单但具有挑战性的知识问题上的事实性。_

针对人类协作的训练
--------------------------------

随着我们的模型不断扩展,并解决越来越复杂的问题,教会它们更好地理解人类需求和意图变得越来越重要。对于 GPT‑4.5,我们开发了新的可扩展技术,使我们能够利用从较小模型获得的数据来训练更大、更强大的模型。这些技术提高了 GPT‑4.5 的可控性、对微妙之处的理解以及自然对话能力。

##### 与人类测试者的比较评估

_人类偏好度量了测试者更喜欢 GPT‑4.5 而不是 GPT‑4o 的查询百分比。_

将对世界的深入理解与改善的协作能力相结合,产生了一个能够自然融合想法、更温暖、更直观的模型,它更能适应人类协作。GPT‑4.5 更好地理解人类的意思,并以更细腻和"情商"的方式解读微妙的暗示或隐含的期望。GPT‑4.5 还展现出更强的美学直觉和创造力。它在写作和设计方面表现出色。

#### 使用案例

度过艰难时期 识别一幅画 探索太空

GPT-4.5
-------

我刚刚考试失败,现在很沮丧

哦,我真的很抱歉听到这个。考试失败确实会让人感到很沮丧和泄气,但请记住,这只是一个时刻 - 并不代表你的本质或能力。你想谈谈发生了什么吗,还是你只需要转移注意力?无论如何,我都在这里支持你。

GPT-4o
------

我刚刚考试失败,现在很沮丧

我很抱歉听到你现在正经历困难时期。以下是一些你可能考虑的事项:

1. **反思和理解**: 试着分析可能出了什么问题。是准备不足、考试时间管理不善,还是可能对课程内容理解有误?找出根源原因有助于你在未来解决问题。

2. **寻求支持**: 与你信任的人 - 朋友、家人或学校辅导员 - 谈谈。他们可以提供不同的视角,有时仅仅倾诉自己的感受就能缓解。

3. **与老师或教授交流**: 他们可以就你可能出错的地方提供见解,并就如何改进提供建议。他们也可能提供补考或加分的机会。

4. **制定学习计划**: 根据你的反思,制定一个提高学习习惯的计划。这可能包括设定固定的学习时间、将材料分解成可管理的部分,或找到更适合你的新学习方法。

5. **保持积极乐观,宽恕自己**: 错误和挫折是生活的一部分。对自己要友善,认识到失败只是通往成功的垫脚石。

6. **关注大局**: 请记住,一次考试只是你学习历程的一部分。未来还有很多机会去表现出色。

如果你需要进一步的支持或资源,可以考虑联系你所在机构的教育支持服务,或者如果你感到特别沮丧,可以寻求心理健康资源。你并不孤单,通过时间和努力,事情一定会好起来的。

GPT‑4.5 展现出更高的"情商",知道何时邀请进一步交流,何时向用户提供更多信息。

更强大的推理能力在路上
---------------------------------

GPT‑4.5 在做出响应时并不会先思考,这使它的优势与 OpenAI o1 等推理模型有所不同。与 OpenAI o1 和 OpenAI o3‑mini 相比,GPT‑4.5 是一个更通用、天生更聪明的模型。我们相信推理将成为未来模型的一项核心能力,而预训练和推理这两种扩展方法将相互补充。随着像 GPT‑4.5 这样的模型通过预训练变得更聪明、更有知识,它们将为推理和工具使用代理提供更强大的基础。

安全性
------

每一次模型能力的提升,也是提高模型安全性的机会。GPT‑4.5 是使用新的监督技术训练的,这些技术与传统的监督微调(SFT)和基于人类反馈的强化学习(RLHF)方法(如 GPT‑4o 中使用的)相结合。我们希望这项工作将为对齐未来更强大的模型奠定基础。

为了压力测试我们的改进,我们在部署前进行了一系列安全测试,这是根据我们的[准备框架⁠(在新窗口打开)](https://cdn.openai.com/openai-preparedness-framework-beta.pdf)进行的。我们发现,扩展 GPT 范式有助于提高我们评估中的各项能力。我们将在附带的[系统卡⁠](https://openai.com/index/gpt-4-5-system-card/)中发布这些评估的详细结果。

如何在 ChatGPT 中使用 GPT-4.5
-----------------------------

从今天开始,ChatGPT Pro 用户将能够在网页、移动和桌面版本上的模型选择器中选择 GPT‑4.5。我们将在下周开始向 Plus 和 Team 用户推出,然后在下一周推出给 Enterprise 和 Edu 用户。

GPT‑4.5 可以访问最新的更新信息并进行搜索,支持文件和图像上传,并可以使用画布进行写作和编码。但是,GPT‑4.5 目前不支持 ChatGPT 中的多模态功能,如语音模式、视频和屏幕共享。未来,我们将努力简化用户体验,让 AI"为你而生"。

如何在 API 中使用 GPT-4.5
-----------------------------

我们也在[所有付费使用等级⁠(在新窗口打开)](https://platform.openai.com/docs/guides/rate-limits#usage-tiers)的开发者中预览 GPT‑4.5 的聊天完成 API、助手 API 和批处理 API。该模型支持函数调用、结构化输出、流式传输和系统消息等关键功能。它还支持通过图像输入的视觉能力。

根据早期测试,开发者可能会发现 GPT‑4.5 特别适用于需要其更高情商和创造力的应用程序 - 如写作帮助、沟通、学习、辅导和头脑风暴。它在代理规划和执行方面也表现出色,包括多步骤的编码工作流和复杂任务自动化。

标题: 介绍 GPT-4.5

内容:

GPT‑4.5 是一个非常大型和计算密集的模型,使其比 GPT‑4o 更[昂贵⁠](https://openai.com/api/pricing/)且不是其替代品。因此,我们正在评估是否继续长期在 API 中提供它,同时平衡支持当前功能和构建未来模型。我们期待了解更多关于它在实际应用中的优势、能力和潜在用途。如果 GPT‑4.5 为您的用例提供独特的价值,您的[反馈⁠(在新窗口中打开)](https://community.openai.com/t/gpt-4-5-is-live-in-the-api/1131571)将在指导我们的决策中发挥重要作用。

结论
----------

随着计算能力每增加一个数量级,就会出现新的能力。GPT‑4.5 是在无监督学习前沿的一个模型。我们继续被社区发现新能力和意想不到的用例的创造力所惊讶。通过 GPT‑4.5,我们邀请您探索无监督学习的前沿,与我们一起发现新的能力。

附录
--------

下面,我们提供了 GPT‑4.5 在标准学术基准测试上的结果,以说明它在传统上与推理相关的任务上的当前性能。即使通过简单地扩大无监督学习,GPT‑4.5 也显示出比之前的模型(如 GPT‑4o)有意义的改进。不过,我们期待通过这次发布获得更全面的 GPT‑4.5 能力图景,因为我们认识到学术基准测试并不总是反映实际应用的有用性。

#### 模型评估分数

**GPT-4.5****GPT-4o****OpenAI o3-mini (high)**
GPQA (科学)71.4%53.6%79.7%
AIME '24 (数学)36.7%9.3%87.3%
MMMLU (多语言)85.1%81.5%81.1%
MMMU (多模态)74.4%69.1%-
SWE-Lancer Diamond (编码)*32.6%

$186,125 23.3%

$138,750 10.8%

$89,625
SWE-Bench Verified (编码)*38.0%30.7%61.0%

*显示的数字代表内部最佳性能。

作者
-------

[OpenAI](https://openai.com/news/?author=openai#results)

基础贡献者
-------------------------

Adam Goucher, Alex Paino, Ali Kamali, Amin Tootoonchian, Andrew Tulloch, Ben Sokolowsky, Clemens Winter, Colin Wei, Daniel Kappler, Daniel Levy, Felipe Petroski Such, Geoff Salmon, Ian O'Connell, Jason Teplitz, Kai Chen, Nik Tezak, Prafulla Dhariwal, Rapha Gontijo Lopes, Sam Schoenholz, Youlong Cheng, Yujia Jin, Yunxing Dai

研究
--------

**核心贡献者**

Aiden Low, Alec Radford, Alex Carney, Alex Nichol, Alexis Conneau, Ananya Kumar, Ben Wang, Charlotte Cole , Elizabeth Yang, Gabriel Goh, Hadi Salman, Haitang Hu, Heewoo Jun, Ian Sohl, Ishaan Gulrajani, Jacob Coxon, James Betker, Jamie Kiros, Jessica Landon, Kyle Luther, Lia Guy, Lukas Kondraciuk, Lyric Doshi, Mikhail Pavlov, Qiming Yuan, Reimar Leike, Rowan Zellers, Sean Metzger, Shengjia Zhao, Spencer Papay, Tao Wang

**贡献者**

Adam Lerer, Adrien Ecoffet, Aidan McLaughlin, Alexander Prokofiev, Alexandra Barr, Allan Jabri, Andrew Gibiansky, Andrew Schmidt, Casey Chu, Chak Li, Chelsea Voss, Chris Hallacy, Chris Koch, Christine McLeavey, David Mely, Dimitris Tsipras, Eric Sigler, Erin Kavanaugh, Farzad Khorasani, Huiwen Chang, Ilya Kostrikov, Ishaan Singal, Ji Lin, Jiahui Yu, Jing Yu Zhang, John Rizzo, Jong Wook Kim, Joyce Lee, Juntang Zhuang, Leo Liu, Li Jing, Long Ouyang, Louis Feuvrier, Mo Bavarian, Nick Stathas, Nitish Keskar, Oleg Murk, Preston Bowman, Scottie Yan, SQ Mah, Tao Xu, Taylor Gordon, Valerie Qi, Wenda Zhou, Yu Zhang

扩展
-------

**核心贡献者**

Alex Chow, Alex Renzin, Aleksandra Spyra, Avi Nayak, Ben Leimberger, Christopher Hesse, Duc Phong Nguyen, Dinghua Li, Eric Peterson, Francis Zhang, Gene Oden, Kai Fricke, Kai Hayashi, Larry Lv, Leqi Zou, Lin Yang, Madeleine Thompson, Michael Petrov, Miguel Castro, Natalia Gimelshein, Phil Tillet, Reza Zamani, Ryan Cheu Stanley Hsieh, Steve Lee, Stewart Hall, Thomas Raoux, Tianhao Zheng, Vishal Kuo, Yongjik Kim, Yuchen Zhang, Zhuoran Liu

**贡献者**

Alvin Wan, Andrew Cann, Andrew Codispoti, Antoine Pelisse, Anuj Kalia, Aaron Hurst, Avital Oliver, Brad Barnes, Brian Hsu, Chen Ding, Chen Shen, Cheng Chang, Christian Gibson, Christopher Berner, Duncan Findlay, Fan Wang, Fangyuan Li, Gianluca Borello, Heather Schmidt, Henrique Ponde de Oliveira Pinto, Ikai Lan, Jiayi Weng, James Crooks, Jos Kraaijeveld, Junru Shao, Kenny Hsu, Kenny Nguyen, Kevin King, Leah Burkhardt, Leo Chen, Linden Li, Lu Zhang, Mahmoud Eariby, Marat Dukhan, Mateusz Litwin, Miki Habryn, Natan LaFontaine, Pavel Belov, Peng Su, Prasad Chakka, Rachel Lim, Rajkumar Samuel, Renaud Gaubert, Rory Carmichael, Sarah Dong, Shantanu Jain, Shuaiqi Xia, Stephen Logsdon, Todd Underwood, Tony Zhao, Weixing Zhang, Will Sheu, Weiyi Zheng, Yinghai Lu, Yunqiao Zhang

安全系统
--------------

Andrea Vallone, Andy Applebaum, Cameron Raymond, Chong Zhang, Dan Mossing, Elizabeth Proehl, Eric Wallace, Evan Mays, Grace Zhao, Ian Kivlichan, Irina Kofman, Joel Parish, Kevin Liu, Keren Gu-Lemberg, Kristen Ying, Lama Ahmad, Lilian Weng, Leon Maksin, Leyton Ho, Meghan Shah, Michael Lampe, Michele Wang, Miles Wang, Olivia Watkins, Phillip Guo, Samuel Miserendino, Sam Toizer, Sandhini Agarwal, Tejal Patwardhan, Tom Dupré la Tour, Tong Mu, Tyna Eloundou, Yunyun Wang

部署
----------

Adam Brandon, Adam Perelman, Adele Li, Akshay Nathan, Alan Hayes, Alfred Xue, Alison Ben, Alec Gorge, Alex Guziel, Alex Iftimie, Ally Bennett, Andrew Chen, Andy Wang, Andy Wood, Angad Singh, Anoop Kotha, Antonia Woodford, Anuj Saharan, Ashley Tyra, Atty Eleti, Ben Schneider, Bessie Ji, Beth Hoover, Bill Chen, Blake Samic, Britney Smith, Brian Yu, Caleb Wang, Cary Bassin, Cary Hudson, Charlie Jatt, Chengdu Huang, Chris Beaumont, Christina Huang, Cristina Scheau, Dana Palmie, Daniel Levine, Daryl Neubieser, Dave Cummings, David Sasaki, Dibya Bhattacharjee, Dylan Hunn, Edwin Arbus, Elaine Ya Le, Enis Sert, Eric Kramer, Fred von Lohmann, Freddie Sulit, Gaby Janatpour, Garrett McGrath, Garrett Ollinger, Gary Yang, Hao Sheng, Harold Hotelling, Janardhanan Vembunarayanan, Jeff Harris, Jeffrey Sabin Matsumoto, Jennifer Robinson, Jessica Liang, Jessica Shieh, Jiacheng Yang, Joel Morris, Joseph Florencio, Josh Kaplan, Kan Wu, Karan Sharma, Karen Li, Katie Pypes, Kendal Simon, Kendra Rimbach, Kevin Park, Kevin Rao, Laurance Fauconnet, Lauren Workman, Leher Pathak, Liang Wu, Liang Xiong, Lien Mamitsuka, Lindsay McCallum, Lukas Gross, Manoli Liodakis, Matt Nichols, Michelle Fradin, Minal Khan, Mingxuan Wang, Nacho Soto, Natalie Staudacher, Nikunj Handa, Niko Felix, Ning Liu, Olivier Godement, Oona Gleeson, Philip Pronin, Raymond Li, Reah Miyara, Robert Xiong, Rohan Nuttall, R.J. Marsan, Sara Culver, Scott Ethersmith, Sean Fitzgerald, Shamez Hemani, Sherwin Wu, Shiao Lee, Shuyang Cheng, Siyuan Fu, Spug Golden, Steve Coffey, Steven Heidel, Sundeep Tirumalareddy, Tabarak Khan, Thomas Degry, Thomas Dimson, Tom Stasi, Tomo Hiratsuka, Trevor Creech, Uzair Navid Iftikhar, Victoria Chernova, Victoria Spiegel, Wanning Jiang, Wenlei Xie, Yaming Lin, Yara Khakbaz, Yilei Qian, Yilong Qin, Yo Shavit, Zhi Bie

执行领导层
--------------------

Aidan Clark, Bob McGrew, David Farhi, Greg Brockman, Hannah Wong, Jakub Pachocki, Johannes Heidecke, Joanne Jang, Kate Rouch, Kevin Weil, Lauren Itow, Liam Fedus, Mark Chen, Mia Glaese, Mira Murati, Nick Ryder, Sam Altman, Srinivas Narayanan, Tal Broda

我们的研究
*   [研究索引](https://openai.com/research/index/)
*   [研究概述](https://openai.com/research/)
*   [研究驻留](https://openai.com/residency/)
*   [OpenAI for Science](https://openai.com/science/)
*   [经济研究](https://openai.com/signals/)

最新进展
*   [GPT-5](https://openai.com/gpt-5/)
*   [Codex](https://openai.com/index/introducing-gpt-5-3-codex/)
*   [OpenAI o3](https://openai.com/index/introducing-o3-and-o4-mini/)
*   [OpenAI o4-mini](https://openai.com/index/introducing-o3-and-o4-mini/)
*   [GPT-4o](https://openai.com/index/gpt-4o-system-card/)
*   [GPT-4o mini](https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/)
*   [Sora](https://openai.com/index/sora-system-card/)

安全
*   [安全方法](https://openai.com/safety/)
*   [安全和隐私](https://openai.com/security-and-privacy/)
*   [信任和透明度](https://openai.com/trust-and-transparency/)

ChatGPT
*   [探索 ChatGPT(在新窗口中打开)](https://chatgpt.com/overview)
*   [商业](https://chatgpt.com/business/business-plan)
*   [企业](https://chatgpt.com/business/enterprise)
*   [教育](https://chatgpt.com/business/education)
*   [定价(在新窗口中打开)](https://chatgpt.com/pricing)
*   [下载(在新窗口中打开)](https://chatgpt.com/download)

Sora
*   [Sora 概述](https://openai.com/sora/)
*   [功能](https://openai.com/sora/#features)
*   [定价](https://openai.com/sora/#pricing)
*   [Sora 登录(在新窗口中打开)](https://sora.com/)

API 平台
*   [平台概述](https://openai.com/api/)
*   [定价](https://openai.com/api/pricing/)
*   [API 登录(在新窗口中打开)](https://platform.openai.com/login)
*   [文档(在新窗口中打开)](https://developers.openai.com/api/docs)
*   [开发者论坛(在新窗口中打开)](https://community.openai.com/)

面向企业
*   [企业概述](https://openai.com/business/)
*   [解决方案](https://openai.com/solutions/)
*   [联系销售](https://openai.com/contact-sales/)

公司
*   [关于我们](https://openai.com/about/)
*   [我们的宪章](https://openai.com/charter/)
*   [基金会](https://openai.com/foundation/)
*   [职业](https://openai.com/careers/)
*   [品牌](https://openai.com/brand/)

支持
*   [帮助中心(在新窗口中打开)](https://help.openai.com/)

更多
*   [新闻](https://openai.com/news/)
*   [故事](https://openai.com/stories/)
*   [直播](https://openai.com/live/)
*   [播客](https://openai.com/podcast/)
*   [RSS](https://openai.com/news/rss.xml)

条款和政策
*   [使用条款](https://openai.com/policies/terms-of-use/)
*   [隐私政策](https://openai.com/policies/privacy-policy/)
*   [其他政策](https://openai.com/policies/)

[(在新窗口中打开)](https://x.com/OpenAI)[(在新窗口中打开)](https://www.youtube.com/OpenAI)[(在新窗口
---
## 📝 翻译说明

本文由 **AI 自动翻译**，可能存在翻译不当之处。

| 项目 | 信息 |
|------|------|
| **原文链接** | [点击查看](https://openai.com/index/introducing-gpt-4-5/) |
| **翻译模型** | GLM-5 (NVIDIA NIM) |
| **翻译来源** | NVIDIA NIM API |
| **翻译时间** | 2026-03-01 |
| **校对状态** | 待人工校对 |

> 💬 如发现翻译问题，欢迎在评论区指正，帮助改进翻译质量。
