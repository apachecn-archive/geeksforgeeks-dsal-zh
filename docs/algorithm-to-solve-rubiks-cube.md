# 解魔方的算法

> 原文:[https://www . geeksforgeeks . org/算法求解魔方/](https://www.geeksforgeeks.org/algorithm-to-solve-rubiks-cube/)

A **魔方**是由‘Erno Rubik’发明的一个有趣的谜题，它有 4300 万种可能的配置。但是通过使用某些算法，这个问题很容易解决。如今魔方有很多变体，但最基本的是 **3x3x3 魔方。**

一个 3x3x3 魔方由 21 块拼接而成:1 块三轴原理块，8 块三色调角块(角立体造型)，12 块二色调边块(边 3D 方块)。

![3x3x3 rubik's cube](img/6b3ad9d0918bd68a1dde97e52f98b4db.png)

**注意-**
中心件总是只在原来的位置。

**魔方的基本旋转:**

*   **R:** 顺时针旋转右侧图层。
*   **R:**逆时针旋转右侧图层。
*   **L:** 顺时针旋转左侧图层。
*   **L':** 逆时针旋转左侧图层。
*   **U:** 顺时针旋转顶层。
*   **U:**逆时针旋转顶层。
*   **F:** 顺时针旋转前层。
*   **F:**逆时针旋转前层。

**初学者方法:**
解魔方的简单方法是按照先解底层，再解中间层，最后解顶层的方法。

![Layer's RUbik's cube](img/7ef1b435406b813654c31466ee538e6c.png)

以下是解魔方的步骤-
**第一步:**首先选择任意颜色的中心(比如白色)，然后通过将所有四个相邻的边缘块放在白色中心来制作*白色十字架*。

![Step 1](img/a290e29b3a00c404ccd6a75cb4ebacc9.png)

**第二步:**将侧面所有四个中心件的颜色与底层的边缘一一匹配，并将匹配的对以相反的方向发送，然后再次将它们带到一起，制成白色的十字。

![Step 2](img/aa316cd7bf9257681ca0a293ea842fd2.png)

匹配所有层后，立方体看起来像这样-

![Matching colors](img/3b6d91745a09443d73ae191219b982dc.png)

**步骤 3:** 通过首先匹配与其所需颜色相匹配的正确角来设置底层的角。然后应用***【R U R ' U】***算法，重复同样的算法，直到底角块设置在正确的位置，如下图所示****

****![Apply RUR'U'](img/bdefdbcc17a065a55fdc9e74e5d0550e.png)****

****在设置了所有的角之后，立方体会看起来像这样-****

****![Setting all the corners](img/ce287e8ce624ac25eb6274b54853f918.png)****

******步骤 4:** 通过匹配侧面的所有四条边来制作第二层。首先，将顶层边缘的颜色与其中心层匹配，并观察该片的其他部分，即顶面颜色。****

*   ******情况 1:** 如果另一个零件颜色与右侧的中心件匹配，则应用算法*U R U R' U' F' U' F.*****
*   ******情况 2:** 如果另一个零件颜色与左侧的中心件匹配，则应用算法***U ' L U ' L ' U ' F U F '。*******

******![Step 4](img/ad1a59ba37dd51a94a57a083edaf2cf5.png)******

******把这个应用到所有其他部分后，立方体看起来像这样-******

******![Result after step4](img/600fc9e6124bb36a68b3ec2283a2e7e8.png)******

********第五步:**应用简单算法***F R U R ' U ' F '**1-3 次*在顶层做黄色十字，如下图。********

******![Apply FRUR'U'F'](img/5a49f39cc064ad811bd649ed3edb8940.png)******

********第六步:**现在将顶层的任意一条边与中间层的中心点进行匹配，然后应用 *F R U R' U' F'* 算法，直到所有边都匹配。******

****![Step 6](img/5e8e67e6c741f1ac536a54c5cb8dc1f8.png)****

******第七步:**现在要匹配顶层的所有角块，首先看到已经被匹配的角，并将其保持为正面(在这种情况下是绿黄橙的组合)，然后应用算法 *U R U L U R' U' L。*****

****![Apply URU'LUR'U'L'](img/d1987a05275393227aede5695ea72119.png)****

****在应用这个算法 1-3 次后，立方体看起来像-****

****![After Step 7](img/5e8e67e6c741f1ac536a54c5cb8dc1f8.png)****

******第 8 步**:最后一步保持黄色为正面，从任意一个角开始应用 *U R' U' R* 算法，直到角排列正确，然后旋转顶层，在右上角带来另一个混乱的角，再次重复*U R' U' R* 算法进行排列，以此类推。排列完所有的角块后，如果需要完全解决你的立方体，只需移动黄色饰面层 *1-2 次*。****

****![Rubik's cube solved](img/c307c068cabb0e1032feb91071efd5af.png)****

****有了这最后一步，魔方终于解开了。****