# 高通访谈|第二集

> 原文:[https://www.geeksforgeeks.org/qualcomm-interview-set-2/](https://www.geeksforgeeks.org/qualcomm-interview-set-2/)

在高通接受采访是一次非常好的经历。

我参加了嵌入式软件应用程序开发人员职位的面试，我的经验和专长是电信领域的 C/RTOS/数据结构。

**流程:** 1 次电话会议，5 次技术会议，1 小时一轮(每次 40 分钟至 1 小时)。

所有的回合都没有那么艰难，面试官都很友好。

**电话:**

*   关于你的简历
*   关于项目和它实际上是如何工作的许多问题
*   操作系统概念和真实示例
*   死锁情况(检测、预防)
*   Sw 看门狗定时器
*   操作系统调度程序和算法
*   系统中的错误处理、核心转储等
*   内存管理概念
*   IPC 通信
*   互斥体/临界区/信号量

注:所有问题都被问得很深，需要告诉他，直到他用答案说服。

两天后，我接到一个电话，要我到 Qcom 办公室参加下一轮面试。那一天很长..！！

**第一轮:**

*   C 编程基础
*   程序、存储类及其映射的内存映射
*   如果我们声明的变量数量超过了处理器上可用的寄存器数量？它们将被存放在哪里。
*   IPC(信号，正如我在本文中编码的)它实际上是如何传输内存的
    一组用于调试的 C 代码片段…识别其中的问题并告诉输出

还有其他问题..比如为什么？

**第二轮:**

*   基础 C 题
*   编写一个程序来删除一个节点，只给一个指向循环链表中节点的指针
*   从被调用函数中返回数据后如何访问该函数中的数据(这里的要点是，被调用后不能访问函数中的自动变量)
*   编写一个程序从函数中返回字节流
*   很多关于函数指针的问题，如何，用法，例子

 **第三轮:**

*   关于他们正在做的项目、市场价值如何、什么产品即将到来的一般性问题
*   SIM 卡/嵌入式应用中的内存处理
*   操作系统程序的优先级、进程和线程差异
*   如何处理泛型函数，比如空指针

**第 4 轮:**

*   为 strstr 函数编写自己的程序，优化方式
*   编写一个程序，将一个给定的链表转换成 BST
*   软件开发是如何发生的，如果给你一个开发的产品，你会怎么做
*   项目问题
*   一年后你想怎么看自己，你的意图，志向

**第 5 轮:**

*   大端和小端–定义、表示、写下来、交换等等
*   很多记忆相关的问题
*   [自己写一个实现 memcpy()的程序](https://www.geeksforgeeks.org/write-memcpy/)–
*   需要评估许多其他条件，如重叠情况等。,
*   库调用和系统调用的区别
*   RTOS 中的优先级反转及其解决方案

**第 6 轮(HR):**

*   高通的抱负、文化和你未来的样子，我们对采访的反馈，没什么，只是随便聊聊。

注意:所有回合，你需要清楚地解释你的项目，他们可以从项目中问一些非常好的问题。明确你的项目和简历。
所有的面试官都会解释你申请的职位，如果你多问一些关于他们到底是做什么的，以及如何工作的问题，那就好了。

*我把这些采访做得很好，但不幸的是，在这之后我没有进入高通。但他们考虑了另一个职位，不到一个月，我又接到了一个电话，又是 3 轮技术面试，如下所示:*

**工艺:** 3 技术

**第一轮:**

*   网络流量测量
*   Udp 与 tcp 比较
*   操作系统调度程序
*   定时器模块代码//您需要为定时器模块编写代码，该模块实际上处理所有客户端的超时功能，并在超时时执行客户端的处理程序。(他们寻找的是如何设计给定的问题、回调函数、函数指针等)
*   关于回叫功能的问题
*   关于函数指针的问题
*   [反向单个链表的程序](https://practice.geeksforgeeks.org/problems/reverse-a-linked-list/1)
*   [检测单个链表中循环的程序](https://practice.geeksforgeeks.org/problems/detect-loop-in-linked-list/1)
*   检测

    ```
    int main(void)
    {
        char *p;
        while(i<50)
           p++;
        return p;
    } 
    ```

    以下 pgm 中的错误

**第二轮:**

*   深入了解项目细节
*   Ipc，os 调度程序
*   优先化流程，加权循环
*   sw wdog
*   内存管理
*   Mem 泄漏和相应的工具
*   缓冲区溢出以及由此产生的影响/问题
*   死锁、避免、防止的方法等
*   信号量、互斥量、忙等待
*   memcpy 和问题的代码，涵盖所有错误场景。

**第三轮:**

*   堆栈损坏
*   通过堆栈粉碎进行黑客攻击
*   程序调试
*   优先级反转，例如
*   比赛条件，例如
*   信号量，互斥量，例如
*   Strcmp，pgm，ff 结束
*   仲裁链表
*   Memcpy pgm，重叠内存地址复制等可能性。
*   小将军 DI 拼图
*   指示字减法

在这之后，我实际上进入了我的梦想公司和快乐..！！

我真诚地感谢 GeeksforGeeks 对我的准备非常有帮助，并希望这对其他有抱负的人有所帮助。

多多多多恭喜作者。如果你喜欢极客博客并想投稿，你也可以写一篇文章并把你的文章邮寄到 contribute@geeksforgeeks.org。看到你的文章出现在极客博客主页上，帮助其他极客。

[All Practice Problems for Qualcomm](https://practice.geeksforgeeks.org/company/Qualcomm/) !