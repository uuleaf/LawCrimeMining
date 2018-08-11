# LawCrimeMining
Law Crime Mining Based on Corpus build and content analysis by NLP methods. 基于领域语料库构建与NLP方法的裁判文书与犯罪案例文本挖掘项目
# 项目介绍
正邪不两立，法律与犯罪水火不容，随着我国法制建设不断健全，法规日趋完善，人们的法律意识也越来越强．当前，随着越来越多的法律文本公开，为犯罪案件审理这个方面的挖掘积累了大量的文本内容．因此，通过收集法律与犯罪领域文本，构建起司法领域语料库，并使用自然语言处理技术进行挖掘，具有重要意义，我们将其称为法律智能，引用smp2018司法论坛的发言来说，法律智能包括以下几个应用点:  
1) 面向案例文书的判决预测：根据案件的案情描述，预测最终的判决结果。  
2) 拓扑结构预测的判决预测：通过法官的判案逻辑找到子任务之间的依赖关系。  
3) 引入区分性属性的罪名预测，包括低频罪名、混淆罪名的相应预测：通过引入显式的属性，能对低频罪名进行基于属性的判断，对混淆罪名进行区分；此外还能采用多任务学习及注意力机制训练基于属性的罪名预测模型。  
4) 基于层次结构的案由预测：通过刑事案由（罪名）和民事案由的层次结构，结合案由本身的文本信息，采用序列预测及基于案由名称的注意力机制，训练相应模型。  
5) 基于法律阅读理解的判决预测：由于在民事案件中判决结果需要结合原告的具体诉求，可以建立基于阅读理解机制，模仿「人带着问题找答案」的阅读理解行为进行案件判决的预测。  

# 项目结构
本项目由两个部分组成：  
１）司法领域语料库的构建，这个部分细分为两个子库，一个是法律裁判文书，另一个是犯罪案例  
２）基于司法领域语料库的挖掘, 尝试进行以下实验:  
a) 刑事与民事案件分类  
b) 案件语义区域识别  
c) 犯罪事实与量刑结果二元抽取  
d) 基于犯罪案例的判决预测  

# 脚本结构
1)script_spider:  
anliwang_spider.py:案例馆语料采集，案例馆中主要有各种案例，用于构建犯罪案例语料库  
sifafwang_spider.py:司法考试网语料采集，该网站中有各类案例，用于构建犯罪案例语料库  
courtlaw_spider.py:最高人民法院裁判文书采集，用于构建裁判文书语料库  
lawlib_spider.py: 法律图书馆网站裁判文书采集，用于构建裁判文书语料库  
2) corpus_lawsuit:  
裁判文书语料库的1000个文本样例，执行采集脚本后，可得到108545，量级为十万的裁判文书  
3) corpus_crime:  
犯罪案例语料库的1000个文本样例，指定采集脚本后，可得到63451, 量级为6万的犯罪案例  

# 基于刑法的因果字典抽取
根据中国人民刑法，对其进行因果处理，形成crime_nanme, cause, crime三个字段的抽取，形成量刑的基础,示例如下：

    {'crime_name': ['故意伤害罪', '组织出卖人体器官罪'],
    'cause': ['故意伤害他人身体的'],
    'crime': '三年以下有期徒刑、拘役或者管制'}
    {'crime_name': ['故意伤害罪', '组织出卖人体器官罪'], 
    'cause': ['致人死亡或者以特别残忍手段致人重伤造成严重残疾的'], 
    'crime': '十年以上有期徒刑、无期徒刑或者死刑'}
    {'crime_name': ['过失致人重伤罪'],
    'cause': ['过失伤害他人致人重伤的'],
    'crime': '三年以下有期徒刑或者拘役'}
    {'crime_name': ['强奸罪'], 
    'cause': ['以暴力、胁迫或者其他手段强奸妇女的'],
    'crime': '三年以上十年以下有期徒刑'}
    {'crime_name': ['强奸罪'], 
    'cause': ['中国刑事辩护网提供致使被害人重伤、死亡或者造成其他严重后果的'],
    'crime': '中国刑事辩护网提供致使被害人重伤、死亡或者造成其他严重后果的'}
    {'crime_name': ['强制猥亵、侮辱罪、猥亵儿童罪'],
    'cause': ['以暴力、胁迫或者其他方法强制猥亵他人或者侮辱妇女的'], 
    'crime': '五年以下有期徒刑或者拘役'}
    {'crime_name': ['非法拘禁罪'], 
    'cause': ['非法拘禁他人或者以其他方法非法剥夺他人人身自由的'], 
    'crime': '三年以下有期徒刑、拘役、管制或者剥夺政治权利'}
    {'crime_name': ['非法拘禁罪'], 
    'cause': ['具有殴打、侮辱情节的', '从重处罚'], 
    'crime': '具有殴打、侮辱情节的，从重处罚'}
    {'crime_name': ['非法拘禁罪'], 
    'cause': ['致人死亡的'], 
    'crime': '十年以上有期徒刑'}
  
# to be continued...
