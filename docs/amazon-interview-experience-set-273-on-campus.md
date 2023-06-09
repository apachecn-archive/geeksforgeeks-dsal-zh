# 亚马逊面试体验|第 273 集(校内)

> 原文:[https://www . geesforgeks . org/Amazon-面试-体验-设置-273-在校园内/](https://www.geeksforgeeks.org/amazon-interview-experience-set-273-on-campus/)

我想和你的观众分享我的亚马逊面试经历(实习)。

**第一轮(在线编码轮):**
在 Hackerrank 上测试了 90 分钟。它有 20 个 mcq 和 2 个编码问题。mcq 来自时间复杂度、不同排序算法、dbms、os、3-4 谜题和 apti、代码输出等主题。

最低质量分数为 0.50。

中央教育学院、信息技术学院、欧洲经济学院的学生被允许入学，大约有 160 名候选人。

**编码问题:**
1。[查找字符串的第一个非重复字符。](https://practice.geeksforgeeks.org/problems/non-repeating-character/0)

2.T [这里是一个 n 阶的方阵，从 1 到 n^2 在行大调填充。求矩阵螺旋遍历中的 Kth 元素。](https://practice.geeksforgeeks.org/problems/find-nth-element-of-spiral-matrix/1)
例:给定 n=3，K=5。
矩阵:
1 2 3
4 5 6
7 8 9

产出:9

我解决了两个编码问题，尝试了 16 个 MCQs，并获得了下一轮的资格。至少解决一个编码问题才能晋级下一轮，这一点非常重要。

第二轮(个人面试-我):

时间:40-50 分钟。这一轮有 31 名候选人入选。

从跟我说说你自己开始。然后面试官问我的 JEE 等级，以及我知道哪些数据结构。她问了我一些基本的树的问题，比如什么是树，什么是 bst，有多少种旅行方式，以及如何命名。接下来，她给了我这个问题:

1.[给你一个元素数组，找出这个数组是否代表了一个 BST](https://practice.geeksforgeeks.org/problems/preorder-to-postorder/0) 的预序遍历。

我想了几秒钟，给了她 n^2 逻辑。在她让我优化之前，我告诉她我可以试着优化一下。
然后想了几分钟，我告诉她我的 O(n)逻辑。
听了我的做法，她让我编码。我一口气写完了代码，没有任何错误。她在检查我的代码是否没有错误后，问我代码的时间复杂度和空间复杂度。

之后，面试官问了我一些关于 OS 的理论问题，比如什么是临界区、互斥、信号量、虚拟内存、页面故障、防止死锁的方法等等。然后她做了一个简单的表，让我为它写一个 SQL 查询，非常简单。她问我什么是数据库管理系统中的索引，它的类型之间的区别，以及我写的查询是否区分大小写。

接下来面试官问我是否知道[克隆链表问题](https://practice.geeksforgeeks.org/problems/clone-a-linked-list-with-next-and-random-pointer/1)。

我说，是的。所以面试官换了个问题。

2.[给定一个既有负数又有正数的数组，求邻接子数组的最大和。](https://practice.geeksforgeeks.org/problems/kadanes-algorithm/0)
我告诉面试官我的方法(卡丹算法的修改)。她让我写代码。我写的代码没有任何错误。

 **第三轮(个人面试-二):**

时间:80-90 分钟。8 名候选人入围这一轮。

首先面试官看了我的简历，问我最近的项目。然后他问我是否对树木感到舒适。我答应了。他问我:

1.[垂直求和](https://practice.geeksforgeeks.org/problems/vertical-sum/1)
我告诉他方法，他让我写代码。我写代码没有任何错误。

然后他问我理论问题。从虚拟内存概念开始，接下来他写了一段代码，问我有没有错误。然后他基于 malloc/calloc、new 运算符等提出 C/C++问题。一个关于异常处理的棘手问题。还有很多其他的理论问题我不记得了。

2.然后他给了我这个问题:
有 n 个人需要做一些任务。在这 n 个人中，有 x 个人需要一把钥匙来开始他们的工作。有无限个按键，在每一个单位时间里，一个个的扔在人们面前。一个人拿起钥匙所需的时间是一个单位时间。此外，面试官提到了一些条件，比如某个特定的人只能在另一个特定的人完成任务后才能开始。一个人完成任务所需的时间是一个单位。他让我找出所有人完成任务的最短时间。

思考了几分钟后，我告诉面试官我使用图中拓扑排序的方法。然后他让我详细解释拓扑排序。然后他转向另一个问题。

3.你在一片森林里，有许多小路。你需要离开森林。你选择哪条路？
[这是一个寻找图中源节点和目的节点之间最小距离的问题。](https://practice.geeksforgeeks.org/problems/shortest-path-from-1-to-n/0)
我告诉他我的方法，然后他让我解释迪克斯特拉的算法。然后面试官问我 dijkstra 算法和 floyd-warshall 算法的区别。然后他问我 prim 的算法和 kruskal 的算法。

然后他给了我另一个有趣的问题。
4。对于二叉树的每个节点，都给你节点 id 和其子节点 id 之和。找到根的节点 id。

几分钟后，我想到了一个错误的方法。我一告诉面试官这件事，就明白我错了。然后他让我把注意力集中在身份证的总数上。然后不到一分钟，我告诉他另一种方法。他问我为什么这样做，我向他解释，他很满意。

之后面试官问我有没有问题要问他。最后，他又问了我一个使用 Alexa 的项目。

保持冷静会帮助你更快地想出正确的解决方案，如果你有任何疑问，可以向面试官提问，他们非常友好。[练习极客论坛的](https://practice.geeksforgeeks.org/)问题。这对我帮助很大。谢谢你们这些极客。

如果你喜欢极客博客并想投稿，你也可以写一篇文章并把你的文章邮寄到 contribute@geeksforgeeks.org。看到你的文章出现在极客博客主页上，帮助其他极客。

[All Practice Problems for Amazon](https://practice.geeksforgeeks.org/company/Amazon/) !