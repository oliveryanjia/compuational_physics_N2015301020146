## 计算物理期末作业

闫佳 2015301020146 物基二班

### Summary

本文主要结合书上第七章内容，基本沿着书本章节顺序和思路对随机系统做出理论探究并重点于与扩散现象等物理应用内容的结合，之后编写代码对相应的系统做模拟演示，根据演示结果得出相应结论，解决章节问题。

This article mainly combined with the seventh chapter of the book, the basic sequence of the book chapters and ideas to make a theoretical study of random systems and focus on diffusion phenomena and other physical applications combined, and then write code to do the simulation demonstration of the corresponding system, according to Demonstration results come to the conclusion, to solve chapter problems.

### Background

系统的输入输出及干扰有随机因素，或系统本身带有某种不确定性的系统就是随机系统。遇到这类问题我们一般是从量测数据建立系统的数学模型，或用已给出系统的模型结构，根据量测数据来总结规律或估计模型中的未知参数。可相应的微分方程数目庞大，计算繁琐，于是将适当量测数据总结成数字规律或概率问题，之后编写程序用产生的随机数，借助计算机完成重复试验。

System input and output and interference with random factors, or the system itself with some uncertainty of the system is a random system. In the face of such problems, we generally establish the mathematical model of the system from the measured data, or use the model structure of the given system to summarize the law according to the measured data or estimate the unknown parameters in the model. However, the corresponding large number of differential equations, computational complexity, so the appropriate measurement data into a law of numbers or probability problems, then write the program with the generated random number, with the computer to complete the trial.

### Main boby

#### 1. 随机行走问题理论探究（Random Walks）

最简单的随机行走是一维随机行走。考虑数轴上中心处的黑点。

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk01.png)

然后，在每次行走步幅一样的情况下，这个黑点开始迈出一步，向前或向后，做任一选择的概率都是相等的。以后时刻迈出下一步也是一样的，以相等的概率决定向前还是向后。第1步记作a1，第2步记作a2，第3步记a3，以此类推。每个“a”只有两个取值，+1（表示向前走1步）或-1（表示向后退1步），如下图所示，黑点走了5步后停在数轴上-1处。

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk02.png)

假设黑点从0处开始出发，沿着数轴随机行走。首先我们想知道，黑点走了N步后，距离出发点有多远。显然，每次实验得到的结果经常是不一样的。但是我们可以算一下，多次重复实验，黑点最后到出发点距离的平均值。黑点最后到出发点0的距离记作d。这里d可正可负，d>0，表示黑点最后位于0点右边，反之d<0，表示黑点最后位于0点左边。对于任意一次实验，结果为

![](http://latex.codecogs.com/gif.latex?\\·d=a_{1}+a_{2}+...+a_{N})

多次重复实验，得到的d的平均值为：

![](http://latex.codecogs.com/gif.latex?\\·<d>=<a_{1}+a_{2}+...+a_{N}>=<a_{1}>+<a_{2}>+...+<a_{N}>)

因为a1取+1和-1的概率相等,<a1>=0=<aN>

d有正有负，但是d^2 只能是正的,因此平均就不可能是0。那我们就算算⟨d^2⟩，看能得到什么结果：

![](http://latex.codecogs.com/gif.latex?\\·<d^{2}>=<(a_{1}+a_{2}+...+a_{N})^{2}>=<(a_{1}+a_{2}+...+a_{N})(a_{1}+a_{2}+...+a_{N})>=<a_{1}^{2}>+<a_{2}^{2}>+...+<a_{N}^{2}>+2(<a_{1}a_{2}>+<a_{1}a_{3}>+...+<a_{1}a_{N}>+<a_{2}a_{3}>+...+<a_{2}a_{N}>+...))

而在本例中<a1^2>=1是确定的a1a2有1和-1两种几率相等的结果，因此<a1*a2>=0，可得结论：

![](http://latex.codecogs.com/gif.latex?\\·<d^{2}>=N)

√N代表黑点走了N步后到0点的距离（“方均根”距离），我们期望黑点走了N步后，到出发点距离为√N。如果黑点走了25步，黑点净移动步数期望值为5步，不管是什么方向。当然有时候会多于5步，有时候会少于5步，5步是所期望的结果.

现在我们用概要中所提及的方法，也就是编写代码用计算机进行大量实验来验证理论推得的结果。

- ##### 一维随机走动的均方差与均值：

最后停留位置与走动的步数有关，在这里我们观察与统计走动偶数步时停留位置的均方差与均值。
给定走动的步数从2到100，每种步数进行10000次试验，统计最终停留位置的均方差与均值，设计代码以及最后运行结果如下：

[Python源代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final01)

[MATLAB绘图代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final03)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk05.png)
（MATLAB做）

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk04.png)
（MATLAB做）

由于朝两个方向行走的概率是相同的，所以最后停下的时候应该在原点位置附近，图像与理论结果较为相符
- ##### 验证距离的平方期望值和走的步数成正比

由上文的理论推导可知验证距离的平方期望值（即<d^2>）和走的步数成正比，下面设计代码会出图像加以验证：

[Python源代码2](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final01)

[MATLAB绘图代码2](https://github.com/oliveryanjia/compuational_physics_N2015301020146/edit/master/code%20of%20final02)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk03.png)
（MATLAB做）

由图像可知距离的平方期望值（即<d^2>）和走的步数成正比，与以上理论证明的结果一致。

#### 2.趋向概率不同的随机行走

分析的整个过程均与以上相似，但是朝向正方向的几率和朝向负方向的几率不在相等。编辑代码绘出图像，观察现象得到结论：

我们假定朝正方向的概率为0.75，朝负方向的概率为0.25，根据概率平均每步朝正方向行进0.5

[源代码3](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final04)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk06.png)
（Python做）

所得到的图像与理论分析完全相符，平均每步朝正方向走动距离为0.5，距离原点的距离与步数成正比

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk07.png)
（Python做）

距离平方期望与步数成二次方关系，很接近函数1/4(x^2)，这与理论推得到的结果相符的也很好。

#### 3.随机行走及其物理中的应用

- 扩散

扩散是一种常见的随机过程。在扩散现象中，每个粒子的运动都可看作独立的随机行走。因此，随机行走与布朗运动类似，是布朗运动的理想数学状态。尽管在模拟随机行走的过程中，不考虑粒子服从的真实动力学规律，但当模拟的时间足够长、模拟粒子数足够多后，就可以准确的描述真实系统的统计学规律。

先从二维单粒子系统出发，考察粒子的随机行走行为，再模拟多粒子系统，尝试用随机行走描述扩散现象，并得出扩散现象的一些规律。

单个粒子的二维随机行走。粒子每次可朝着上下左右四个方向移动，并且每个方向的几率和移动距离都一样。假设粒子初始时刻位于原点，绘出1000和10000步粒子的行走轨迹为则有：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk08.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk09.png)

从这两幅图中我们可以看出单个粒子在随机行走中逐渐倾向于远离初始点，这既与上文分析结论相一致，又符合“扩散”一词的含义

考虑完单粒子在不同步数之后的表现，我们考虑1000个粒子在不同时间后的分布情况：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk10.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk11.png)

随时间的流逝，粒子远离原点的趋势更加清晰明了，这是随机行走的过程，同时也是重现了“扩散作用”。

如何表现粒子具体分布情况呢，我们设计程序以横轴为距离原点距离x，竖轴为概率作图：

[Python源代码4](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final%2006)

[MATLAB绘图代码4](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final05)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/random%20walk12.png)（MATLAB做）

从这里看出随着与原点距离的增加，粒子数量逐渐减少。

- 针与线的相交问题（蒲丰投针问题）

有一个以平行且等距木纹铺成的地板（如图），现在随意抛一支长度比木纹之间距离小的针，求针和其中一条木纹相交的概率。并以此概率，布丰提出的一种计算圆周率的方法——随机投针法。这就是蒲丰投针问题。

设计代码进行随机投针试验：

[代码5](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20final07)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/needleinline.png)

实验结果与理论概率p=（2l）/（πa）相比，结果相似但也有一定差距，主要因为统计困难而且分辨相交与否有一定主观偏差。其中l为针的长度，a为相邻平行线的距离。

### Conclusion

- 一维随机走动距离的平方期望值（即<d^2>）和走的步数成正比
- 趋向概率不同的随机行走距离原点的距离与步数成正比，而距离平方期望与步数成二次方关系
- 扩散现象中单个粒子在随机行走中逐渐倾向于远离初始点；
- 多粒子系统扩散时，随时间增加空间密度变小，符合“扩散”含义
- 在扩散过程的某一个时刻，随着与原点距离的增加，粒子数量逐渐减少


### Acknowledgement

- 借助在线latex公式编辑器进行公式编写；
- 借鉴百度百科对随机行走、扩散现象、随机投针试验的介绍；
- 参考Nicholas J. Giordano, Hisao Nakanishi, Computational Physics (Second Edition)；
- Random Walks （http://www.mit.edu）和博客园中文版翻译教程

对以上机构或个人表示感谢
