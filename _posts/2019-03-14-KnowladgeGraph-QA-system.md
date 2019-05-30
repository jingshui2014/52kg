---
layout: post
title: 医疗知识图谱问答系统探究（一）
date: 2019-03-14 22:34:00 +0800
categories: Works
tags: [知识图谱,问答系统,医疗诊断,项目实战]
excerpt: 从无到有搭建一个以疾病为中心的一定规模医药领域知识图谱，以该知识图谱完成自动问答与分析服务。该项目立足医药领域，以垂直型医药网站为数据来源，以疾病为核心，构建起一个包含7类规模为4.4万的知识实体，11类规模约30万实体关系的知识图谱。
---

![Caption](https://www.bobinsun.cn/assets/images/logo-top.jpg)

### **1、项目背景**

为通过项目实战增加对知识图谱的认识，几乎找了所有网上的开源项目及视频实战教程。

果然，功夫不负有心人，找到了中科院软件所刘焕勇老师在github上的开源项目，基于知识图谱的医药领域问答项目QABasedOnMedicaKnowledgeGraph。


> 项目地址：https://github.com/liuhuanyong/QASystemOnMedicalKG

**用了两个晚上搭建了两套，Mac版与Windows版，哈哈，运行成功！！！**

从无到有搭建一个以疾病为中心的一定规模医药领域知识图谱，以该知识图谱完成自动问答与分析服务。该项目立足医药领域，以垂直型医药网站为数据来源，以疾病为核心，构建起一个包含7类规模为4.4万的知识实体，11类规模约30万实体关系的知识图谱。 本项目将包括以下两部分的内容：

基于垂直网站数据的医药知识图谱构建
基于医药知识图谱的自动问答

### **2、项目环境**
####  **2.1 windows系统**

搭建中间有很多坑，且行且注意。

**配置要求：**要求配置neo4j数据库及相应的python依赖包。neo4j数据库用户名密码记住，并修改相应文件。

**安装neo4j，neo4j 依赖java jdk 1.8版本以上：**

> jdk安装方法可参考：windows系统下安装JDK8，下载地址：[https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-windows-x64.exe][1]

> 安装neo4j可参考博文：windows安装neo4j，下载地址：[https://go.neo4j.com/download-thanks.html?edition=community&release=3.4.1&flavour=winzip][2]

> 安装python可参考：Windows环境下安装python2.7

根据neo4j 安装时的端口、账户、密码配置设置设置项目配置文件：answer_search.py &  build_medicalgraph.py (github下载项目时根据个人需要也可使用git)

**数据导入：**
python build_medicalgraph.py，导入的数据较多，估计需要几个小时。

python build_medicalgraph.py导入数据之前，需要在该文件main函数中加入：

![Caption](https://www.bobinsun.cn/assets/images/001.jpg)
![Caption](https://www.bobinsun.cn/assets/images/002.jpg)


**启动问答**：python chat_graph.py

### **2.2 Mac系统**
mac本身自带python、java jdk环境，可直接安装neo4j图数据库，项目运行步骤与windows基本一样。

**问题解答：**

> **安装过程中如遇问题可联系Wechat: dandan-sbb。**

### **2.3 Neo4j数据库展示**

![Caption](https://www.bobinsun.cn/assets/images/003.jpg)

### **2.4 问答系统运行效果**

![Caption](https://www.bobinsun.cn/assets/images/004.jpg)

## **3、项目介绍**
该项目的数据来自垂直类医疗网站寻医问药，使用爬虫脚本data_spider.py，以结构化数据为主，构建了以疾病为中心的医疗知识图谱，实体规模4.4万，实体关系规模30万。schema的设计根据所采集的结构化数据生成，对网页的结构化数据进行xpath解析。

项目的数据存储采用Neo4j图数据库，问答系统采用了规则匹配方式完成，数据操作采用neo4j声明的cypher。

项目的不足之处在于疾病的引发原因、预防等以大段文字返回，这块可引入事件抽取，可将原因结构化表示出来。

![Caption](https://www.bobinsun.cn/assets/images/005.jpg)


### **3.1 项目目录**
```python
.
├── README.md
├── __pycache__      编译结果保存目录
│   ├── answer_search.cpython-36.pyc
│   ├── question_classifier.cpython-36.pyc
│   └── question_parser.cpython-36.pyc
├── answer_search.py
├── answer_search.pyc
├── build_medicalgraph.py    知识图谱数据入库脚本
├── chatbot_graph.py    问答程序脚本
├── data
│   └── medicaln.json  本项目的全部数据，通过build_medicalgraph.py导neo4j
├── dict
│   ├── check.txt    诊断检查项目实体库
│   ├── deny.txt      否定词库
│   ├── department.txt  医疗科目实体库
│   ├── disease.txt    疾病实体库
│   ├── drug.txt      药品实体库
│   ├── food.txt      食物实体库
│   ├── producer.txt    在售药品库
│   └── symptom.txt    疾病症状实体库
├── document
│   ├── chat1.png    系统运行问答截图01
│   ├── chat2.png      系统运行问答截图01
│   ├── kg_route.png    知识图谱构建框架
│   ├── qa_route.png    问答系统框架图
├── img    README.md中的所用图片
│   ├── chat1.png
│   ├── chat2.png
│   ├── graph_summary.png
│   ├── kg_route.png
│   └── qa_route.png
├── prepare_data
│   ├── build_data.py    数据库操作脚本
│   ├── data_spider.py    网络资讯采集脚本
│   └── max_cut.py      基于词典的最大向前/向后脚本
├── question_classifier.py    问句类型分类脚本
├── question_classifier.pyc    
├── question_parser.py    问句解析脚本
├── question_parser.pyc
```

### **3.2 知识图谱的实体类型**

| 实体类型 | 中文含义 | 实体数量 |举例 |
| :--- | :---: | :---: | :--- |
| Check | 诊断检查项目 | 3,353| 支气管造影;关节镜检查|
| Department | 医疗科目 | 54 |  整形美容科;烧伤科|
| Disease | 疾病 | 8,807 |  血栓闭塞性脉管炎;胸降主动脉动脉瘤|
| Drug | 药品 | 3,828 |  京万红痔疮膏;布林佐胺滴眼液|
| Food | 食物 | 4,870 |  番茄冲菜牛肉丸汤;竹笋炖羊肉|
| Producer | 在售药品 | 17,201 |  通药制药青霉素V钾片;青阳醋酸地塞米松片|
| Symptom | 疾病症状 | 5,998 |  乳腺组织肥厚;脑实质深部出血|
| Total | 总计 | 44,111 | 约4.4万实体量级|

### **3.3 知识图谱的实体关系类型**

| 实体关系类型 | 中文含义 | 关系数量 | 举例|
| :--- | :---: | :---: | :--- |
| belongs_to | 属于 | 8,844| <妇科,属于,妇产科>|
| common_drug | 疾病常用药品 | 14,649 | <阳强,常用,甲磺酸酚妥拉明分散片>|
| do_eat |疾病宜吃食物 | 22,238| <胸椎骨折,宜吃,黑鱼>|
| drugs_of |  药品在售药品 | 17,315| <青霉素V钾片,在售,通药制药青霉素V钾片>|
| need_check | 疾病所需检查 | 39,422| <单侧肺气肿,所需检查,支气管造影>|
| no_eat | 疾病忌吃食物 | 22,247| <唇病,忌吃,杏仁>|
| recommand_drug | 疾病推荐药品 | 59,467 | <混合痔,推荐用药,京万红痔疮膏>|
| recommand_eat | 疾病推荐食谱 | 40,221 | <鞘膜积液,推荐食谱,番茄冲菜牛肉丸汤>|
| has_symptom | 疾病症状 | 5,998 |  <早期乳腺癌,疾病症状,乳腺组织肥厚>|
| acompany_with | 疾病并发疾病 | 12,029 | <下肢交通静脉瓣膜关闭不全,并发疾病,血栓闭塞性脉管炎>|
| Total | 总计 | 294,149 | 约30万关系量级|

### **3.4 知识图谱的属性类型**

| 属性类型 | 中文含义 | 举例 |
| :--- | :---: | :---: |
| name | 疾病名称 | 喘息样支气管炎 |
| desc | 疾病简介 | 又称哮喘性支气管炎... |
| cause | 疾病病因 | 常见的有合胞病毒等...|
| prevent | 预防措施 | 注意家族与患儿自身过敏史... |
| cure_lasttime | 治疗周期 | 6-12个月 |
| cure_way | 治疗方式 | "药物治疗","支持性治疗" |
| cured_prob | 治愈概率 | 95% |
| easy_get | 疾病易感人群 | 无特定的人群 |

### **3.5 问答项目实现原理**

![Caption](https://www.bobinsun.cn/assets/images/006.jpg)

本项目的问答系统完全基于规则匹配实现，通过关键词匹配，对问句进行分类，医疗问题本身属于封闭域类场景，对领域问题进行穷举并分类，然后使用cypher的match去匹配查找neo4j，根据返回数据组装问句回答，最后返回结果。

> **问句中的关键词匹配：**

![Caption](https://www.bobinsun.cn/assets/images/007.jpg)

> **根据匹配到的关键词分类问句**

![Caption](https://www.bobinsun.cn/assets/images/008.jpg)

> **问句解析**

![Caption](https://www.bobinsun.cn/assets/images/009.jpg)

> **查找相关数据**

![Caption](https://www.bobinsun.cn/assets/images/010.jpg)

> **根据返回的数据组装回答**

![Caption](https://www.bobinsun.cn/assets/images/011.jpg)

### **3.6 问答系统支持的问答类型**

| 问句类型 | 中文含义 | 问句举例 |
| :--- | :---: | :---: |
| disease_symptom | 疾病症状| 乳腺癌的症状有哪些？ |
| symptom_disease | 已知症状找可能疾病 | 最近老流鼻涕怎么办？ |
| disease_cause | 疾病病因 | 为什么有的人会失眠？|
| disease_acompany | 疾病的并发症 | 失眠有哪些并发症？ |
| disease_not_food | 疾病需要忌口的食物 | 失眠的人不要吃啥？ |
| disease_do_food | 疾病建议吃什么食物 | 耳鸣了吃点啥？ |
| food_not_disease | 什么病最好不要吃某事物 | 哪些人最好不好吃蜂蜜？ |
| food_do_disease | 食物对什么病有好处| 鹅肉有什么好处？ |
| disease_drug | 啥病要吃啥药 | 肝病要吃啥药？ |
| drug_disease | 药品能治啥病 | 板蓝根颗粒能治啥病？ |
| disease_check | 疾病需要做什么检查 | 脑膜炎怎么才能查出来？|
| check_disease |　检查能查什么病 | 全血细胞计数能查出啥来？ |
| disease_prevent | 预防措施| 怎样才能预防肾虚？ |
| disease_lasttime | 治疗周期 | 感冒要多久才能好？ |
| disease_cureway | 治疗方式 | 高血压要怎么治？ |
| disease_cureprob | 治愈概率 | 白血病能治好吗？ |
| disease_easyget | 疾病易感人群 | 什么人容易得高血压？ |
| disease_desc | 疾病描述 | 糖尿病 |

## **4、项目总结**
基于规则的问答系统没有复杂的算法，一般采用模板匹配的方式寻找匹配度最高的答案，回答结果依赖于问句类型、模板语料库的覆盖全面性，面对已知的问题，可以给出合适的答案，对于模板匹配不到的问题或问句类型，经常遇到的有三种回答方式：

* 给出一个无厘头的答案；
* 婉转的回答不知道，提示用户换种方式去问；
* 转移话题，回避问题；

> 例如，本项目中采用了婉转的方式回答不知道：

![Caption](https://www.bobinsun.cn/assets/images/012.jpg)

基于知识图谱的问答系统的主要特征是知识图谱，系统依赖一个或多个领域的实体，并基于图谱进行推理或演绎，深度回答用户的问题，基于知识图谱的问答系统更擅长回答知识性问题，与基于模板的聊天机器人有所不同的是它更直接、直观的给用户答案。对于不能回答、或不知道的问题，一般直接返回失败，而不是转移话题避免尴尬。

整个问答系统的优劣依赖于知识图谱中知识的数量与质量。也算是利弊共存吧！知识图谱图谱具有良好的可扩展性，扩展了知识图谱也就是扩展了问答系统的知识库。如果问句在射程范围内，可轻松回答，但如果不幸脱靶，则体验大打折扣。

从知识图谱的角度分析，大多数知识图谱规模不足，主要原因还是数据来源以及技术上知识的抽取与推理困难。

![Caption](https://www.bobinsun.cn/assets/images/logo-bottom.png)
