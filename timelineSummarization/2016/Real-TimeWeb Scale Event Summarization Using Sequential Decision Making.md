# Real-TimeWeb Scale Event Summarization Using Sequential Decision Making #

author：Chris Kedzie， Fernando Diaz， Kathleen McKeown

**摘要：**本文为线上多文档流摘要提出一个基于序贯决策（sequential decision）的系统。

给定一个感兴趣的事件（如：Boston marathon bombing），本文的系统可以获取到相关联的文本流然后产生一系列的短文本。

本文方法可以联合建模相关性、综合性、新颖性和时效性。

本文是针对实时事件来生成摘要，采用的方法为序贯决策。利用序贯决策的动态性来对实时web事件进行摘要，该方法仍旧为抽取式摘要，方法为有监督方法。

由于采用的是序贯决策，因此该任务被定义为基于句子的属性特征和该句之前的句子的属性特征来确定当前状态，即决策的当前状态就是联合属性（也称为特征表示--有静态特征和动态特征），用oracle policy来决定是选择该句还是跳过该句，模型采用局部最优搜索来学习。

## 数据 ##

TREC Temporal Summarization Track data（http://www.trec-ts.org/）
数据采用的为公开的TREC Temporal Summarization Track data。数据包含三个部分，corpus：从web上爬取的从2011年10月到2013年二月的12亿个时间戳文件。queries：44个事件。
relevance judgments: 人工标准匹配。比较的baseline为TREC2015时事摘要的两个最好的系统Cos和APSAL，以及本文的模型Ls和LsCos。结果显示本文模型比Cos和APSAL大部分都要好些，Ls和LsCos各有千秋。本文还从错误率上进行了对比，更加验证了该问模型的有效性。

## 阅读体会： ##
1本文大致上是通过序贯决策这个算法来得到一个实时的摘要，
这个方法用了很多特征信息来确定当前状态，然后用oracle policy选择句子。
2 该论文陈述的是一个实时摘要系统，是针对一个query生成的一个摘要，同时该摘要生成的时段不是固定的，是通过前面的状态来影响下一阶段的抽取抉择，是一种新的想法。
3 本文没有明确的说明摘要的覆盖性和时间连贯性上是如何考虑的，这可以进行补充。



