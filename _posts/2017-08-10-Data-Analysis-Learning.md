---
layout: post
title:  "数据分析学习心得"
description: 
---

Created 170810 
By 游遍星辰

注：本文首发于微信公众号《泰阁志》

### 一 未知，已知

> 我的工作就是发现别人不知道的。
——福尔摩斯 

作为一个推理小说迷，我初中时就把父亲书架上、学校图书馆里的上百本推理小说全部看完。在我看来，推理的迷人之处在于它是一个从已知信息中发现未知的过程。案件发生，当前信息只有犯罪现场的痕迹，若干人的证词，他们每个人都有犯罪动机和作案时间，他们的证词里面有真话、假话，还有他们以为是真话，其实不过是个误解。侦探要做的事情就是辨别真伪，循着线索找到真凶。

只是侦探生活离我们太远，我们只能在文字中领略这个过程。在学习数据分析时，我发现福尔摩斯的这句话同样适用于数据科学家。手机和电脑是我们日常使用最多的工具，无论是社交、购物还是运动，都会留下大量数据，如同有一个无处不在的摄影机，记录下你的每一个动作，存储到数据库中，成为商家下一步营销的依据。《黑客帝国》中的世界越来越接近现实，个体、数据采集设备都成为一个庞大数据中心的终端，不断地输送数据。虚拟世界在不断扩大，把现实世界融入其中，两者边界逐渐模糊。虚拟世界中最重要的元素就是数据。

如何从这些纷繁复杂，浩如烟海的数据中抽丝剥茧，找到其中隐藏的模式，把数字转化为有价值的信息，解决问题。是一个富有挑战性的工作，也是数据分析所做的事情：总结过去，展望未来。

利用信息做出预测，古来有之。古希腊有一位哲学家科学家泰勒斯，凭借着丰富的数学、天文学和农业知识，断定第二年橄榄会丰收，于是他用低价提前租下了附近所有的橄榄榨油器。第二年，橄榄果然大丰收，他于是高价出租榨油器，发了大财。把眼光放回到现代，你是一位投资者，想要判断明年某种作物的收成，要怎么做？夜观天象还是借助科技的力量？

### 二 数据分析过程

![](http://oa01ru7zq.bkt.clouddn.com/image/jpg/pie.jpg)



数据分析流程图(维基百科)

直接讲理论或许过于抽象，这里以我学习数据分析时做的第一个项目作为例子，来简单介绍数据分析的过程。

1.结合现实，定义问题和目标      

数据分析的目的是解决问题。例如推测明年橄榄的产量，就是一个明确的目的。公司有两种方案基于对用户进行广告营销，哪一种方案更好？销售量下滑，是价格提高还是质量问题引起的？也要通过数据分析来验证。这里的示例是对豆瓣阅读上的电子书进行分析。属于探索性数据分析，在实际的应用中更多的是目标明确的。

2.收集数据

确定目标后，首先要收集数据。有时数据是现成的，比如公司的业务数据库，存放了多年的系统数据。有时要利用各种方法获取数据，包括填写调查问卷，从网站上下载（例如国家统计局网站），自己写爬虫程序来抓取。数据的存储形式多种多样，包括数据库，文本文件，Excel文件等。我所需要的数据，只能利用爬虫从网页上抓取，包括每本书的作者、出版社、评分以及目录等信息。

3.清洗数据和处理数据

就像做菜之前要先备好原料，在分析之前也要进行一定的准备工作。如果数据是错误的，得到的模型再精确也不具备参考价值，甚至可能会导致错误决策。 很多数据源都有一些这样或者那样的问题，例如：重复值，异常值，空值，以及多余的空格等问题。

豆瓣阅读的页面是按类别显示的。我的做法是按顺序抓取每一类别下的图书，而一本书有可能在不同的类别下都出现，例如采铜老师的《 精进：如何成为一个很厉害的人》，既属于心理学，又属于管理，所以抓到的数据肯定是有重复的。所以要把重复记录删除；豆瓣的评分是0-10分，假如出现了这个范围之外的数字，就是异常值；有的书是没有评分的，就会出现空值。结合业务实际，选择抛弃这些记录或者对异常值和空值进行填充，比如用平均数、中位数、出现最频繁的数。

同时，要把数据处理成我们需要的形式，便于后面的分析。例如，图书有个类别属性，只有两个值：虚构和非虚构。可以给数据增加一个新的列，0代表虚构，1代表非虚构。假如你要处理的数据中存在一个身份证号的字段，我们可以增加两个列，出生年月和年龄，分别从身份证号中提取出来。

4.数据探索是数据探索

数据探索是对数据进行概括性的描述，能帮助我们认识数据的全局。通常采用可视化方法，即利用图形如饼图、柱形图、折线图、散点图对数据进行对比、排序，可以更直观的展现数据特征，读者也更易于接受。假如我告诉你今年已经过了83天，恐怕你不会有很深的感受，但是当你看到这张图，心里会不会就有一种紧迫感？

![image](http://upload-images.jianshu.io/upload_images/2510946-5c5647dcf2d963e1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这里我们可以看到所有图书分数的分布，接近于正态分布。

![image](http://upload-images.jianshu.io/upload_images/2510946-85fd7e8a67106861.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

也可以求出一些有代表性的数字比如平均值，中位数等等。

思考一个问题：如何衡量某个出版社的在某一个主题比如心理学方面的水平？可以把所有心理学类书籍提取出来，计算每个出版社平均分。有的出版社只有一本心理学书籍，有的则出了几十本，用平均分来衡量并不准确。用箱线图来查看每个出版社的评分分布。

![image](http://upload-images.jianshu.io/upload_images/2510946-7c8755f19a105e3b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

x轴为出版社名字和图书数目，y轴则是分数的分布。比如中信出版社，有34本心理学书籍，中位数大约是7.5，也就是说有17本书的评分在7.5以上。

假如给图书数目和评分赋予不同的权重，就可以得到一个计算模型，用以衡量出版社的水平。就像把一位篮球队员的场均得分、得分总数、投篮命中率等等若干个参数综合起来，转换成特定的公式，就可以生成球员的评价模型。

![image](http://upload-images.jianshu.io/upload_images/2510946-20fb8376f3be3b47.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5.数据建模
模型是对现实问题的抽象，发现数据的特征和内在联系。
评论人数较多的书，也就是热门书籍，评论人数和分数之间有没有相关性？引入一个线性模型来分析，结果显示相关度非常低，也就是说大家热衷于评论的书籍未必就是高分书籍。再如，假设我们手头有豆瓣阅读用户的购买数据，就可以对用户分类，并针对不同类别用户推荐不同的书籍。

6.数据分析报告结论
结合前面的分析结果，对数据进行解读，提出建议和解决方案。

### 三、元认知学习法

阳志平老师的《工作谈》中提到元认知学习法。当我们学习一个新领域知识时，时时对照，用来指导自己的学习过程。怎样进入数据分析这个新的领域，我们也可以分为三个阶段：

- 主题学习

广度优先搜索。我把课程给出的、网上推荐的参考书找来，对比之下，可以发现，数据科学是一个融合了统计学，计算机技术和特定领域知识的交叉学科。

工欲善其事，必先利其器。前面所说的数据分析每一个流程，都离不开工具的帮助，如python、R语言等工具包。无论多先进的算法都需要通过代码来实现，才能真正生成数据分析产品；数学、统计学则是数据科学的基础，在相关模型和理论的辅助下，我们才能从海量数据里提取有用的知识，个人在学习过程中最为吃力的也是这一部分。并不是要求你成为统计学专家，但是常用的统计概念和数据挖掘算法是必须掌握的；结合业务去理解数据，才能发挥数据的价值。假如你是出版从业者，透彻理解一本书的出版，流通，销售过程以及每一环节中的关键因素，又掌握数据分析技术，便可以用数据验证你的猜测，支撑你的观点，发现未知模式，从一个新的角度解决问题。

- 深度学习

前面给大家介绍的数据分析的实例，只是一个很简单的，浅层次的应用，其中的知识也都属于“司机知识”。深度学习才是接下来的重点。我目前也在这个平台期挣扎。比如前面说的数据挖掘常用算法，要理解各种算法的适用情况和优缺点，找一些公开数据集来进行测试，才能真正掌握算法的使用。

- 行动学习

学习课程期间，难免有各种原因，客观如工作忙，主观如自己犯懒，导致进度跟不上。这时就要记住“最小行动”。实在做不出来，就参考他人的代码，从中学习。
在写第一个数据分析项目时，我虽然有编程的经验，但是没有写过python程序，语法等具体知识也没有大量实践过。如果先按照书本，写一个个小程序来学习，必定是来不及的。就在网上找了一位同学的爬虫代码，于是先看明白他的代码，再进行修改，遇到问题直接谷歌。在这个过程中，也相当于是进行python的入门，理解了基本的语法和相关代码包的使用。  

### 四 生活中的统计学


本科时也有概率论与统计学这一门课程，但在工作中从未应用过。数据分析课程让我重新学习相关理论，并且思考，在现实世界中，有哪些事情和统计学有着千丝万缕的联系。

- 做大概率事件，不把希望寄托在小概率事件上。

我相信每个人都在心里幻想过，如果我中了彩票大奖，会做些什么事情，会过什么样的生活。报纸上也常常报道，某个人一直守一个号码多少年，终于中奖。但是如果你了解统计学，就会明白，其实每一次开奖，都是一个独立事件，概率是固定的，不管买同一个号码多少年，都不会提高概率。

人人都期待中奖，人人看到闪电袭来都会躲开，但是这两件事情的概率相比，哪一个更高呢？美国PowerBall的头奖概率约为3亿分之一，国内的双色球概率是1/17721088，。美联邦应急管理局估计当前美国人平均遭雷击的概率为60万分之一。我国的气象部门在2010年统计，雷击事件有759起，如果按照人口总数来计算，遭雷击的概率是180万分之一。不管是用哪一组数字来对比，都会发现中奖的概率的确低到可以忽略。只要具体一点统计学的基本知识，就能做出这样一个结论：彩票不是不能买，而是完全不值得花费任何的精力和时间在上面。所以，彩票行业里真正提高收入的是开彩票站的人，如同19世纪淘金热中致富者寥寥，为淘金者们发明牛仔裤的李维·施特劳斯，所创Levis品牌至今屹立不倒。

- 莫把局部当总体

“现在找工作都是靠关系，某某家的孩子，那学校名字都没听过，家里不也给安排了个工作，工资高又清闲！”
“是啊，你看有些名校出来的还找不到工作呢，读这么多念书也没用。”

这是偶然听到的一段对话，相信你也不会感到陌生。这种案例时不时出现，比如引发热烈讨论的[父亲反对女儿上大学，称捡垃圾比读书强](http://xian.qq.com/a/20130902/004673.htm)。父亲的理由是：读大学花8万，不读挣8万；读大学是“肯定失败的投资”。好像也有一点道理？等等，如果你也这么想，那就掉进了一个无处不在的大坑——把少量样本当总体。

是否上过大学，对工作收入有怎样的影响？国内的统计数据没有找到，美国旧金山联储2014年发表的报告[Does College Matter?](http://www.sffed-education.org/annualreport2014/files/2014%20Annual%20Report%20Essays.pdf)表明： 在过去四十年里，相比没读过大学的人，拥有大学学位的人每年平均收入多出了约20300美元。大学学位带来的经济回报是终生的，其回报超过了42万美元。

大学教育的水平如何，那是另一个话题。如果仅仅是按照这位父亲的逻辑，有的人不读书一样能挣钱，有的人读了书也还在家里蹲，就做出不让女儿读大学的决定，那只能说是太武断了。

- 人生的正态分布

统计学中有一个重要的正态分布，又称为钟形曲线。 比如，人类的智商、身高、胆固醇含量等。

>什么是[标准九]（Stanine）？它是将正态分布曲线划分为九个部分，平均值为5，标准差为2，除了标准一与标准九两级之外，各个分数的范围全部都是半个标准差。如下图所示：
![image](http://upload-images.jianshu.io/upload_images/2510946-7cd195a3fe5f321a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


标准3到标准7这五个区间，一共占据了78%，大多数人都是在这个区间里面，两端的标准九和标准一都是极少数。当你清楚这一点，如同一棵树知道自己在森林中的哪个位置。前景黯淡时，不必妄自菲薄，我们都是芸芸众生中的一员，你并不孤独；花团锦簇时也不会被冲昏头脑，咱离最高那4%还远着呢。每一个区间都有上限和下限，到不了最高区间，但也可以尽自己所能，往前一步，再往前一步，这就是心理学中的成长型思维。

从以上角度来说，真心认为，基础统计学应该作为一门通识课程普及给所有人，无论是文科生还是理科生。或许，你压根儿不打算学编程，或许你的工作不需要和数字打交道，但是在统计学的帮助下，你可以尝试换一个视角看世界。

注：文中提及的豆瓣阅读分析项目地址-https://github.com/blueseach/book_analyze，但是豆瓣阅读后来改版了，所以爬虫代码应该是不能直接用了，仅供参考。

### 参考
[人生标准九](http://www.yangzhiping.com/psy/Stanine.html)

[数据科学-wiki](https://en.wikipedia.org/wiki/Exploratory_data_analysis)

[气候数据可提前预警作物歉收](http://www.ccchina.gov.cn/Detail.aspx?newsId=40876&TId=58)

[通过数据分析预测葡萄酒的品质](http://www.readingtimes.com.tw/ReadingTimes/ProductPage.aspx?gp=productdetail&cid=rtbe(SellItems)&id=BE0158&p=excerpt&exid=39006)

[遭遇雷击的概率有多高](http://www.cma.gov.cn/kppd/kppdsytj/201606/t20160620_314488.html)

