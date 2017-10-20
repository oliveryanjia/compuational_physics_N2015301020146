## 题目2.19

Model the effect of backspin on the range of a batted ball. Assume an angular velocity of 2000 rpm.

### Summary

本文结合书中章节2内容，提出题目2.9的解决方案 在未考虑空气阻力以及考虑空气阻力的情况下，之前一次作业已经给出了解决方案，本次问题是在考虑击打之后球体自旋运动对于运行轨迹的影响，本文集中探究解决本问题的方案

### Background

在球类运动中，非常重视对球体的控制，其中包括击出角度的调整，初速度的控制，以及对球体旋转的把握，在足球，网球以及乒乓球等等项目中，对球体旋转的运用能力可以极大程度上影响最终结果

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/table%20tennis.jpg)

### Main boby

- 首先我们需要注意的是球体表面粗糙程度会极大影响空气阻力等因素，所以我现在就阻尼系数的不同先进行探究

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/baseball%20air%20drag.png)

从课本中的图像中三种不同表面的球开始着手分析其运行轨迹（由于曲线方程过于复杂，于是将图中曲线分割为各个阶段构成分段函数曲线，并尽力与原图像相似）

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/smoothorrough.png)

运用上面图形表示的三种球，设计代码得到他们的运动轨迹（此时并未考虑旋转）

[源代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/chapter%2002%EF%BC%882%EF%BC%89picture1)

此时得到的图像为

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter2%20range.png)

- 之后我们加入自旋的影响 
理论表明，马格努斯力的大小与棒球自转的角速度、棒球的半径和棒球在空气中的运动速度有关。以S表示空气对棒球的力的平均效应，可得棒球所受马格努斯力的表达式为

![](http://latex.codecogs.com/gif.latex?\.F_{M}\propto.m\vec{a}\left(v+rw\right)^{2}\left(v-rw\right)^{2}\sim.vrw)

![](http://latex.codecogs.com/gif.latex?\\.F_{M}=S_{0}wv)

在三维空间里建立坐标轴得到棒球运动方程为(B是阻尼系数，S0/m=0.00041)

![](http://latex.codecogs.com/gif.latex?\\frac{d}{dt}x=v_{x})

![](http://latex.codecogs.com/gif.latex?\\frac{d}{dt}y=v_{y})

![](http://latex.codecogs.com/gif.latex?\\frac{d}{dt}z=v_{z})

![](http://latex.codecogs.com/gif.latex?\\frac{d}{dt}v_{x}=-Bvv_{x}+\frac{S_{0}}{m}(w_{y}v_{z}-w_{z}v_{y}))

![](http://latex.codecogs.com/gif.latex?\frac{d}{dt}v_{y}=-Bvv_{y}+\frac{S_{0}}{m}(w_{z}v_{x}-w_{x}v_{z})-g)

![](http://latex.codecogs.com/gif.latex?\\frac{d}{dt}v_{z}=-Bvv_{z}+\frac{S_{0}}{m}(w_{x}v_{y}-w_{y}v_{x}))

取normal ball进行研究（取不同的自旋角速度）

[源代码2](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/chapter%2002%EF%BC%882%EF%BC%89xy)

横坐标为击出方向，纵坐标垂直高度得到其图像

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c2backspinrange.png)

之后我们考虑侧旋带来的影响绘出3D图像观察

[源代码3](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/chapter%2002%203D%20mode)

所得图像

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c2%203d.png)

### Conclusion

- 当自旋旋转速度较小时对运行影响较小
- 加入足够大下旋后球运行轨迹明显更远了，且自旋越快产生的Magnus力越大
- 马格努斯力的大小与棒球自转的角速度、棒球的半径和棒球在空气中的运动速度有关，球在气流中运动时，如果其旋转的方向与气流同向，则会在球体的一侧产生低压，而球体的另一侧则会产生高压。向前运动的球在以顺时针方向旋转时，下侧由于迎着气流运动，受到的空气摩擦力会更大。这就得使球下侧受到的压力比上侧更大，球在压力的作用下便会朝上偏。如果球以逆时针方向旋转，则相反
- 加入侧旋影响后球的运行轨迹更加“捉摸不定”，会产生侧方向的偏移

### Acknowledgement

本文借鉴了“前辈”上官俊怡同学的代码，在此表示感谢；同时参考了百度对3d图像代码设计的介绍以及对马格努斯力性质的阐述，再次对以上同学以及百科送出的助攻表示真诚的谢意