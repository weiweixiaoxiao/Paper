# A Low-Rank Approximation Approach to Learning Joint Embeddings of News Stories and Images for Timeline Summarization #

author：William Yang Wang, Yashar Mehdad, Dragomir R. Radev, Amanda Stent

**摘要：**

1 先前的工作都集中在fully-observable ranking models或者用手动抽取特征的clustering models上。2 大多数摘要语料只有文档。

为了解决上述两个问题，1 本文利用推荐系统中的矩阵因式分解技术，以及使用一个表示学习的方法，将该问题变为一个句子推荐任务。2 为了丰富只有文本的语料，对每个新闻文章候选句子，通过从Web上搜索出排名第一的图片，然后利用CNN嵌入该图片。3 最后，提出一个可利用的low-rank approximation approach来学习联合嵌入的新闻和图片。


## 数据集 ##

17 timeline dataset----9 topics（CNN, BBC and NBC News），包括4650个新闻文档。

## 比较模型 ##

1 Random：摘要句子是通语料中随机选择。

2 MEAD:多文档摘要。

3 Chieu et al.: 使用TFIDF分数来表示句子的重要性的多文档摘要。

4 ETS:最先进的非监督时间轴摘要系统

5 Tran et al.:基于learn-to-rank技术的先进时间轴摘要系统。

6 Regression:将句子抽取的任务作为一个监督式回归问题。

