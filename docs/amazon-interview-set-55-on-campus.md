# 亚马逊采访|第 55 集(校内)

> 原文:[https://www . geesforgeks . org/Amazon-interview-set-55-on-campus/](https://www.geeksforgeeks.org/amazon-interview-set-55-on-campus/)

**interview street 线上测试:**
18 道 MCQs(普通 C 循环题、网络、dbms、os、解析)
2 道编码题
1。检查无向图是否是树。
2。[给定一个整数数组，打印绝对差最小的 2 个元素。](https://practice.geeksforgeeks.org/problems/minimum-difference-pair/0)

**面试回合:-**
**第一回合:**
说说你自己。
1。[给定一个矩阵(不一定是正方形)，其中一行和一列中的元素被排序。在矩阵中找出一个给定的整数。](https://practice.geeksforgeeks.org/problems/search-in-a-matrix/0)
告知进场。然后编码。
2。给定一个位置，骑士被放在 nXn 棋盘上。找到棋盘上可以放置的最大骑士数量，这样就不会有 2 个骑士互相攻击。
记住你只需要给出骑士的数量，而不是他们所有的位置。我首先可以安排 ceil(n*n/3)骑士。然后他让我找一个更好的解决办法。最后我到了天花板(n*n/2)。然后他让我编码。然后他让我去掉上限条件(分别检查偶数和奇数)。
他问我有没有问题要问他。我问——亚马逊努力成为地球上最以客户为中心的公司。作为一名程序员/开发人员，你做了什么来实现这一点，因为一般来说，客户的问题是高层管理者和计划者的问题。

**第二轮:**
从我的实习生项目的一些问题开始。
1。[给定一棵二叉树，用其所有后代节点的数据之和替换每个节点的数据。](https://practice.geeksforgeeks.org/problems/transform-to-sum-tree/1)(叶节点将有 0)
2。给定一个正整数排序数组，找到最少缺失的正整数。首先我给出了一个 O(n)解。然后他让我优化一下。最后我给出了一个 O(log n)的解。
3。给定一串数字，从中找出 k 个随机数。我向他解释了油藏取样方法。他问为什么这种方法有效。每个数字被选中的概率是多少？如果流中的数字少于 k 个(它的值为 1)，那么任何数字被选中的概率是多少。
他问我有没有问题。我说我有一个，但我已经问过以前的面试官了。他问我是否得到了满意的答案。我说答案非常令人满意。

**第 3 轮(CS 轮):**
他问我写 SQL 查询舒服吗。我宁愿不要。
1。什么是接口？为什么要用？举个例子。什么是抽象类？为什么要用？举个例子。为什么接口和抽象类有两个不同的概念？
2。你知道单例类吗？这是什么？实现一个简单的单例类。我在使属性静态等方面犯了一些错误。他指导我，最后我纠正了所有的错误。
3。给定一个二叉树，其中每个节点都有一个额外的下一个指针。填充下一个指针，使每个节点的下一个指针指向其下一个兄弟节点。首先，我给出了一个解决方案，其中我需要一个映射，其中每个映射键将是一个级别号，值将指向该级别的最后一个当前访问的节点。然后他让我在没有空间的情况下做。最后我给了他一个没有空间的解决方案。我给出了一个非递归的方法，他让我编码。

**第 4 轮(西雅图办公室的高三 SDE):**
他给我讲了他自己、他的团队、他的工作和他团队的工作。
1。说说你的一个具有挑战性的项目/实习/课堂作业。
2。给出一个你生活中得到负面反馈的情况，以及你是如何处理这种情况的。
3。向我解释了一个缓存的情况，其中，键将在缓存中，每个键将指向一个字符串。这是 LRU 缓存条件，我必须实现 LRU 缓存。然后编写一个函数，从这个缓存中检索一个给定关键字的字符串。retrieval 应该是 O(1)(如果你给 O(n)retrieval，他会让你做成 O(1))。

终于拿到 offer 了！！🙂 🙂

当你回答一个问题时，澄清你想到的任何疑问。不要自己做任何假设。
继续说出你的想法。如果可能的话，继续说，即使是在你写代码的时候。他们想测试你是否真的知道方法，而不仅仅是复制代码。所有回合都是技术和淘汰。最后一轮在他们的程序中权重最高。写干净的代码，如果你想的话，争取一些时间。

非常感谢 GeeksForGeeks 团队对面试准备的帮助！🙂

许多许多祝贺作者。如果你喜欢极客博客并想投稿，你也可以写一篇文章并把你的文章邮寄到 contribute@geeksforgeeks.org。看到你的文章出现在极客博客主页上，帮助其他极客。

[**亚马逊所有练习题**](https://practice.geeksforgeeks.org/company/Amazon/) **！**

Related Practice Problems[Save Knights](https://practice.geeksforgeeks.org/problems/save-knights/0)