# AI_summer_camp

> 基于论文摘要的文本分类与关键词抽取挑战赛


> 本教程会带领大家项目制学习，由浅入深，逐渐进阶。从跑通最简的Baseline，精读Baseline，到底层算法原理与进阶实践技巧的学习，千里之行，始于足下，从这里，开启你的 AI 学习之旅吧
—— Datawhale贡献者团队
教程链接地址：https://linklearner.com/learn/detail/123?detail=703&index=1


## 基于论文摘要的文本分类与关键词抽取挑战赛
[https://​challenge​.xfyun​.cn​/topic​/info​?type​=​abstract​-of​-the​-paper​&​ch​=​ymfk4uU]{https://​challenge​.xfyun​.cn​/topic​/info​?type​=​abstract​-of​-the​-paper​&​ch​=​ymfk4uU}


> 赛题背景:
医学领域的文献库中蕴含了丰富的疾病诊断和治疗信息，如何高效地从海量文献中提取关键信息，进行疾病诊断和治疗推荐，对于临床医生和研究人员具有重要意义。

> 赛事任务:
机器通过对论文摘要等信息的理解，判断该论文是否属于医学领域的文献。

- 任务示例：
'''

输入：

论文信息，格式如下：

Inflammatory Breast Cancer: What to Know About This Unique, Aggressive Breast Cancer.，

[Arjun Menta, Tamer M Fouad, Anthony Lucci, Huong Le-Petross, Michael C Stauder, Wendy A Woodward, Naoto T Ueno, Bora Lim]，

Inflammatory breast cancer (IBC) is a rare form of breast cancer that accounts for only 2% to 4% of all breast cancer cases. Despite its low incidence, IBC contributes to 7% to 10% of breast cancer caused mortality. Despite ongoing international efforts to formulate better diagnosis, treatment, and research, the survival of patients with IBC has not been significantly improved, and there are no therapeutic agents that specifically target IBC to date. The authors present a comprehensive overview that aims to assess the present and new management strategies of IBC.，

Breast changes; Clinical trials; Inflammatory breast cancer; Trimodality care.

输出：

是(1)

'''

> 赛题数据集
训练集与测试集数据为CSV格式文件，各字段分别是标题、作者、摘要、关键词。

> 评价指标
本次竞赛的评价标准采用F1_score，分数越高，效果越好。

> 解题思路
 文献领域分类
 
 针对文本分类任务，可以提供两种实践思路，一种是使用传统的特征提取方法（如TF-IDF/BOW）结合机器学习模型，另一种是使用预训练的BERT模型进行建模。
 
 ## 使用特征提取 + 机器学习的思路步骤如下：
 
 - 数据预处理：首先，对文本数据进行预处理，包括文本清洗（如去除特殊字符、标点符号）、分词等操作。可以使用常见的NLP工具包（如NLTK或spaCy）来辅助进行预处理。
 - 特征提取：使用TF-IDF（词频-逆文档频率）或BOW（词袋模型）方法将文本转换为向量表示。TF-IDF可以计算文本中词语的重要性，而BOW则简单地统计每个词语在文本中的出现次数。可以使用scikit-learn库的TfidfVectorizer或CountVectorizer来实现特征提取。
 - 构建训练集和测试集：将预处理后的文本数据分割为训练集和测试集，确保数据集的样本分布均匀。
 - 选择机器学习模型：根据实际情况选择适合的机器学习模型，如朴素贝叶斯、支持向量机（SVM）、随机森林等。这些模型在文本分类任务中表现良好。可以使用scikit-learn库中相应的分类器进行模型训练和评估。
 - 模型训练和评估：使用训练集对选定的机器学习模型进行训练，然后使用测试集进行评估。评估指标可以选择准确率、精确率、召回率、F1值等。
 - 调参优化：如果模型效果不理想，可以尝试调整特征提取的参数（如词频阈值、词袋大小等）或机器学习模型的参数，以获得更好的性能。