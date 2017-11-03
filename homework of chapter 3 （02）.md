## 题目3.21

Investigate the bifurcation diagrams found for the pendulum with other values of the drive frequency and damping parameter. Warning:This can easily become an ambitious project.

### Summary

本文依据第三章内容，以及题目3.12 3.16的思路顺序。使用Euler-Cromer方法，解决一定条件下物理摆的混沌现象，并借此解答了作业第21题

### Background

混沌（chaos）是指确定性动力学系统因对初值敏感而表现出的不可预测的、类似随机性的运动。系统既是确定性的又是不可预测的。也就是说，一个系统服从一定的物理定律，但运动不可准确预测。在本实验中物理摆有很多独特性质，最重要的可能就是混沌现象。

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/%E6%B7%B7%E6%B2%8C%E7%8E%B0%E8%B1%A1.jpg)

### Main boby

由上一次作业分析方法又考虑到驱动力，具有振幅 F 和角频率 Ω 可有

![](http://latex.codecogs.com/gif.latex?\frac{d^{2}\theta}{dt^{2}}=-\frac{g}{l}\theta-q\frac{d\theta}{dt}+F_{D}sin(\Omega_{D}t))   （#）

记（#）式右面为f（θ,w,t）由 Euler-Cromer方法得

![](http://latex.codecogs.com/gif.latex?\omega_{i+1}=\omega_{i}+f\Delta·t)

![](http://latex.codecogs.com/gif.latex?\theta_{i+1}=\theta_{i}+\omega\Delta·t)

![](http://latex.codecogs.com/gif.latex?\·t_{i+1}=t_{i}+\Delta·t)

类似书中59页处理办法（参数也类似），编写代码得到运动图像，此时有结论：在低驱动力下，钟摆发生简谐振荡； 但在大驱动下时，动作混乱。

[源代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c3%20T-21%20code%2001)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3T21fig1.png)

探究混沌摆的角度与角速度的关系，设计程序得到图像

[源代码2](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c3%20T21%20code2)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3T21fig2.png)

F=1.2时Poincare图

[源代码3](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c3%20T21%20code3)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3T21fig3.png)

类似书中66 67页思路，我们考虑混沌现象发生过程，如书中一样，我们分别取F为1.35 1.44 1.465，可有：

[源代码4](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c3%20T21%20code%204)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3t21figF1.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3t21figF2.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3t21figF3.png)

之后我们绘出bifurcation图
- 改变外力的频率，令f=2/3,2/3+0.00001,2/3+0.00002,可得

[源代码5](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c3%20T21%20code5)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3t21fig%20different%20f.png)

### Conclusion
- 第一张图可知单摆在开始阶段将初始条件决定的运动通过阻力消耗后，在之后的运动中做与外力同频率的简谐振动。F=1.2时可以看到，单摆的运动是没有周期性的，这就是混沌的特征。
- 从不同的F三张图中可知：第一张图的周期与外界驱动力的相同，第二张图的周期是外力周期两倍，第三张图是外力周期四倍。随着外力在这个范围内的增加，单摆的周期变为外力周期的两倍、四倍、八倍等等，最终进入混沌状态。
- 从最后一张图可以看出：当外力的频率增大时，图像的结构没有发生变化，只是图形整体下移，且上面的点有所增加。

### Acknowledgement

本文借鉴了“前辈”上官俊怡同学的代码，在此表示感谢；同时参考了百度上对图像代码设计的介绍以及对混沌现象的介绍，再次对以上同学以及百科送出的帮助表示真诚的谢意 
