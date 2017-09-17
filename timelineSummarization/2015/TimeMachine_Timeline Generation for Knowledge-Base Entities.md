# TimeMachine: Timeline Generation for Knowledge-Base Entities

author：Tim Althoff*, Xin Luna Dong†, Kevin Murphy†, Safa Alai†, Van Dang†, Wei Zhang†

*Computer Science Department, Stanford University, Stanford, CA 94305
†Google, 1600 Amphitheatre Parkway, Mountain View, CA 94043
*althoff@cs.stanford.edu †{lunadong, kpmurphy, safa, vandang, weizh}@google.com

**摘要：**本文提出一个叫做TIMEMACHINE的方法来对时间和知识库中的实体关系生成一个时间轴。

​           一个理想的时间轴应该满足三个质量标准：（1）它显示了与实体相关的事件。（2）它显示了不同时间的事件，因此他们沿着时间轴点分布。（3）它显示了内容多样的事件，因此他们包含了很多种事件（例如，对于一个演员来说，它应该显示电影、婚姻和奖项，而不仅仅是电影）。

​          本文提出一个算法对给定的时间段和尺寸来生成时间轴，该方法基于子模最大化（submodular optimization）和Web共生统计（Web-co-occurrence statistics）。

**介绍：** TIME-MACHINE----1 相关性：展示最“interesting”和“relevance”事件。2 时态多样性：沿时间轴均匀分布事件，以避免视觉拥挤，并允许与所描述的事件轻松交互。3 内容多样性：展示一个事件的多样性集合。

方法步骤：1 给定一个感兴趣实体的话题，通过在给定的知识库中来搜索带时间戳的周边实体生成竟可能的候选事件。2 对所有线下可能的有兴趣的目标生成候选事件，然后，在给定一集候选集和感兴趣的时间点后，对最相关的事件线上选择丰富的子集。

## 事件候选集生成

本文方法是生成一个大集合的事件，然后过滤掉不相关事件。































































