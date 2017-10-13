## 题目2.9

Calculate the trajectory of our cannon shell including both air drag and the reduced air density at high altitudes so that you can reproduce the results in Figure 2.5. Perform your calculation for different firing angles and determine the value of the angle that gives the maximum range

### Summary

本文结合书中章节2.1，2.2，2.3内容，提出题目2.9的解决方案，既考虑空气阻力和不同海拔空气密度的情况下，探究加农炮开火角度的最优解（借用题目2.5的方法）

### Background

不论是体育竞赛中的投掷类比赛，还是加农炮发射炮弹，都需要依靠此问题的解答从而选择最合适的出手或发射角度，容易知道的是，在发射点和落地点同一海拔高度，又不需考虑空气阻力的情况下，45度是最优解，然而考虑空气阻力和不同高度空气密度也不同带来的影响时，我们需要考虑更多因素带来的影响
 
### Main boby

首先我们从简单情况考虑起，其由第一章内容和自由抛体运动规律可知

![](http://latex.codecogs.com/gif.latex?\frac{d^2x}{dt^2}=0)

![](http://latex.codecogs.com/gif.latex?\frac{d^2y}{dt^2}=-g)

为了实现欧拉法，我们将二阶导式子拆成两个一阶导式子，同时引入v(x)与v(y)，此时我们有

![](http://latex.codecogs.com/gif.latex?\frac{dx}{dt}=v_{x})

![](http://latex.codecogs.com/gif.latex?\frac{dv_{x}}{dt}=0)

![](http://latex.codecogs.com/gif.latex?\frac{dy}{dt}=v_{y})

![](http://latex.codecogs.com/gif.latex?\frac{dv_{y}}{dt}=-g)

之后表达为不同的形式

![](http://latex.codecogs.com/gif.latex?\.x_{i+1}=x_{i}+v_{x,i}*\Delta{t})

![](http://latex.codecogs.com/gif.latex?\.y_{i+1}=y_{i}+v_{y,i}*\Delta{t})

![](http://latex.codecogs.com/gif.latex?\.v_{x,i+1}=v_{x,i})

![](http://latex.codecogs.com/gif.latex?\.v_{y,i+1}=v_{y,i}-g\Delta{t})

此事我们将空气阻力空气密度等因素考虑在内，结合书中式（2.20）将上面四式表达为

![](http://latex.codecogs.com/gif.latex?\.x_{i+1}=x_{i}+v_{x,i}*\Delta{t})

![](http://latex.codecogs.com/gif.latex?\.y_{i+1}=y_{i}+v_{y,i}*\Delta{t})

![](http://latex.codecogs.com/gif.latex?\\.v_{x,i+1}=v_{x,i}-B_{2}vv_{x,i}/m*\Delta{t}*(1-ay_{i}/T_{0})^{\alpha})

![](http://latex.codecogs.com/gif.latex?\\.v_{y,i+1}=v_{y,i}-g\Delta{t}-B_{2}vv_{y,i}/m*\Delta{t}*(1-ay_{i}/T_{0})^{\alpha})

对于题目2.5，设计程序得到适当图像，以横坐标表示炮弹攻击距离，以纵坐标表示高度，于是每一条曲线均为炮弹运行轨道，设定合适的初始速度即可得到一条轨道曲线，注意结合实际问题当图像曲线达到y=0时，实际情况为炮弹落地，于是曲线应在此停止，由上述可得：

#### [源代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/chapter%2002%20code%201)

运行程序绘制图像

- 取v=500m/s时可得图像

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c2%20v%3D500.png)

- 取v=800m/s时可得图像

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c2%20v%3D800.png)

这种图像便于直观感受炮弹运行轨迹，但却不能充分表达射程和发射角度的具体关系，于是设计程序绘出纵轴为射程，横轴为发射角度的图像，可得：

#### [源代码2](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/chapter%2002%20code%202)

- 取v=300m/s时可得图像

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c2%20range1.png)

- 取v=500m/s时可得图像

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c2%20range2.png)

### Conclusion

- 在不考虑空气阻力及密度情况的情况下，出射角度为45度时发射距离最远
- 在考虑空气阻力以及空气密度的情况下，射程最远时出射角度略小于45度（v=500m/s时，最远射程为15843米，此时角度为42.96度；当v=700m/s时，最远射程为24732米，此时角度为43.87度）
具体求解射程和角度的精确值的源代码：
#### [源代码3](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/chapter%2003%20code%203)

- 只考虑空气阻力而没有考虑空气密度随高度变化而变化的情况下，发射高度及距离均不及考虑空气密度问题情况下的结果，这是因为在考虑空气密度之后，炮弹运行到高空时空气阻力会变小，因此会打到更高更远的地方

### Acknowledgement

本文借鉴了“前辈”吴雨桥同学的代码，在此表示感谢；同时参考了百度对函数代码的介绍，使本文结论有了图像证明之后变得更加可完整，再次对以上同学以及大神送出的助攻表示真诚的谢意
 
### 注
- 用 pygame上的抛物线模拟器模仿两次出射角度不同时的曲线

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/parabola1.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/parabola2.png)
 
- 此外pygame里有一个Mario游戏，他有两种攻击模式，一个扔得远，一个扔得近（即初速大【蓝色球】和初速小【红色球】）

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/Mario.gif)
