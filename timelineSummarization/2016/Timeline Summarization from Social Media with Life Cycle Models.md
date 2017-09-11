# Timeline Summarization from Social Media with Life Cycle Models #

author：Yi Chang, Jiliang Tang, Dawei Yin, Makoto Yamada, and Yan Liu

**摘要：**对社交媒体数据关于实体的时间轴摘要面临两个挑战：1 关于实体的关键时间轴情节通常在现有的社交媒体服务中不可用。 2 由于社交媒体的剪短、噪音多以及非正式的自然因素，仅仅基于内容的摘要是不充足的。本文提出了一个新的框架Timeline-Sumy，该框架包含情节检测和摘要排序。情节检测部分：由于时间总呈现sudden-rise-and-heavy-tail的形式，因此使用life cycle model来检测时间情节。在摘要排序部分：通过learning-to-rank的方法来排序每个情节中的社交媒体文本。

**本文主要贡献：** 1）通过life cycle model为时间序列的sudden-spike-and-heavy-tail建模。 2）为了对情节进行检测，使用一个新的贝叶斯非参模型来同时获取内容和时态信息。 3）提出的Timeline-Sumy框架可以灵活的融合社交媒体数据中的各种类型信号。


**内容：**  关键是联合时态信息和内容信息。
              
              未完待续、、、、、、


## 数据集 ##
手动标记了4个社交媒体数据集作为评估数据(2012年6月22日~8月7日)：

684.9k----Andy Murray

20.8k----David Ferrer

72.9k----Maria Sharapova

336.9k----Roger Federer 

无标签数据：检测本文提出模型是如何帮助用户回答相应问题。

601.9k----Jennifer Lopez(2014年六月1日到7月31日）

## 实验 ##
**实验对比模型：**

**非监督模型：**

1 LexRank：图模型

2 ETS：新闻语料的时间轴摘要--是一个基于全局优化和局部优化的图。

3 TPM:基于tweet数据的时间轴摘要算法，通过兴趣和主题来推断动态概率分布。

**监督模型：几个不同的情节检测方法 + LTR（learning to rank）**

4 K-Means + LTR：使用K-Means方法来检测基于内容信息的情节，但忽略了时态信息。

5 Hiscovery + LTR：使用Hiscovery来检测情节（该模型包括使用多项式分布为内容建模 + 使用混合高斯模型获取的时间信息）。

6 DTM + LTR：采用动态主题模型（DTM）来检测情节，DTM是一个很先进的模拟全时间段内的主题演化模型，因此使用DTM来通过将每个主题看作时间轴情节来检测情节。

经过K-Means、Hiscovery和DTM检测到情节后，再通过交叉验证来训练Learning to rank模型。


## 相关工作 ##
**新闻时间轴摘要：**

1 Po Hu, Minlie Huang, Peng Xu, Weichang
Li, Adam K. Usadi, and Xiaoyan Zhu. Generating breakpoint-based timeline overview for news topic retrospection. In Preceedings of ICDM, 2011.

2 R. Yan, X. Wan, J. Otterbacher, L. Kong,
X. Li, and Y. Zhang. Evolutionary timeline summarization: a balanced optimization framework via iterative substitution. In Preceedings of SIGIR, 2011.

**社交媒体摘要：**

1 Zhaochun Ren, Shangsong Liang, Edgar Meij, and Maarten de Rijke. Personalized time-aware tweets summarization. In Preceedings of SIGIR, 2013.

等等。。。。。。

**简要内容：**

1 该文章通过对每个聚簇使用一个Dirichlet-Hawkes过程来获得时态信息和内容信息，然而该文假设事件之间的间隔是预先知道的，而这不适合本文的场景。----Nan Du, Mehrdad Farajtabar, Amr Ahmed, Alexander Smola, and Le Song. Dirichlet-hawkes processes with applications to clustering continuous-time document streams. In Preceedings of KDD, 2015.

2 通过联合优化时间约束和事件约束来构造时间轴。----Quang Xuan Do, Wei Lu, and Dan Roth. Joint inference for event timeline construction. In Preceedings of EMNLP-CoNLL, 2012.

3 通过一个狄力克雷过程模型来挖掘个性时间轴。----Jiwei Li and Claire Cardie. Timeline generation: Tracking individuals on twitter. In Preceedings of WWW, 2014.

4 时间感知的层次贝叶斯模型（a time-aware hierarchical Bayesian model）结合learning-to-rank模型来生成时间轴。----T. Ge, W. Pei, H. Ji, S. Li, B. Chang, and Z. Sui. Bring you to the past: Automatic generation of topically relevant event chronicles. In Preceedings of ACL, 2015.

以上的模型都没有模拟时间轴事件的时态模式（temporal patterns）。

**模拟时态模式的几个方法：**

1 Hawkes过程----Yasuko Matsubara, Yasushi Sakurai,B. Aditya Prakash, Lei Li, and Christos Faloutsos.Rise and fall patterns of information diffusion: Model and implications. In Proceedings of KDD, 2012.

2 幂定律分布函数（power law distribution functions）----Riley Crane and Didier Sornette. Robust dynamic classes revealed by measuring the response function of a social system. Proceedings of the National Academy of Sciences, 2008.

3 无限状态自动机（infinite-state automation approach）----Jon Kleinberg. Bursty and hierarchical structure in streams. Data Mining and Knowledge Discovery, 7(4):373–397, 2003.

4 Life Cycle model----Y. Chang, M. Yamada, A. Ortega, and Y. Liu. Ups and downs in buzzes: Life cycle modeling for temporal pattern discovery. In Preceedings of ICDM, 2014.

还有一些年代久远~~~~~~~~~~~~~~


# 总结 #

1 本文的时间信息和内容信息是单独分开获得，是否可以时间信息和内容信息联合强化。

2 人类生成时间轴摘要都是根据上个时间段信息来生成下个时间段信息，两个时间之间有一个演化过程。

**由2可以想到，分段时间，然后将上一时间段的信息抽取关键信息融合到下一时间段信息的生成。可用生成式（关键主题信息生成式模型），用生成式模型就可以将每个时间段的内容作为一个样本。**
