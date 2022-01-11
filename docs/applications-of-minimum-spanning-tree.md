# 最小生成树问题的应用

> 原文:[https://www . geeksforgeeks . org/最小生成树应用/](https://www.geeksforgeeks.org/applications-of-minimum-spanning-tree/)

最小生成树问题:给定具有正边权重的连通图 G，找到连接所有顶点的最小边权重集。

MST 是具有多种应用的基本问题。

**网络设计。**
*–电话、电气、液压、电视电缆、电脑、道路*
标准应用是针对像电话网络设计这样的问题。你有一个有几个办公室的企业；你想租用电话线把它们连接起来；电话公司收取不同的费用来连接不同的城市。你想要一套线路，以最低的总成本连接你所有的办公室。它应该是一个生成树，因为如果一个网络不是一个树，你总是可以删除一些边缘，节省资金。

**NP 难问题的近似算法。**
*—[旅行推销员问题](http://en.wikipedia.org/wiki/Travelling_salesman_problem)、[斯坦纳树](http://en.wikipedia.org/wiki/Steiner_tree_problem)*
一个不太明显的应用是最小生成树可以用来近似解决旅行推销员问题。定义这个问题的一个方便的正式方法是找到访问每个点至少一次的最短路径。

请注意，如果你有一个路径访问所有的点恰好一次，这是一种特殊的树。例如，在上面的例子中，十六个生成树中的十二个实际上是路径。如果有一条路径多次访问一些顶点，您总是可以删除一些边来得到一棵树。所以总的来说，最小二乘权重小于旅行商权重，因为它是在一个严格更大的集合上的最小化。

另一方面，如果你在最小生成树周围画一条路径跟踪，你跟踪每条边两次，访问所有的点，所以 TSP 权重小于 MST 权重的两倍。因此，这次旅行是最佳的两倍。

**间接应用。**
–最大瓶颈路径
–用于纠错的 LDPC 代码
–与仁义熵的图像配准
–学习实时人脸验证的显著特征
–减少蛋白质中氨基酸测序的数据存储
–湍流流体流中粒子相互作用的模型局部性
–以太网桥接的自动配置协议，以避免网络中的循环

**聚类分析**
k 聚类问题可以看作是找到一个 MST 并删除 k-1 最
昂贵的边。

**来源:**
[http://www . cs . Princeton . edu/courses/archive/SPR 07/cos 226/讲座/MST . pdf](http://www.cs.princeton.edu/courses/archive/spr07/cos226/lectures/mst.pdf)
[http://www.ics.uci.edu/~eppstein/161/960206.html](http://www.ics.uci.edu/~eppstein/161/960206.html)