## 题目3.26 3.29 3.31

Study the behavior for other types of tables. One interesting possibility is a square table with a circular interior wall locate either in the center, or slightly off-center. Another possibility is an elliptical table.

### Summary

本文结合第三章内容解决题目3.26 3.29和3.31。 在解题过程中，参考书上过程我们使用欧拉 克罗默方法研究洛伦兹模型。
并为洛伦茨问题构建相空间图。
编写代码设计程序用以实现这个任务。

### Background

洛伦兹研究流体力学时候提及的基本方程，就是所谓的纳维 - 斯托克斯方程，它被认为是适合流体形式而写成的牛顿定律，足以感受到其重要性。他考虑的具体情况是Rayleigh-Benard问题，涉及容器中的顶部和底部表面保持在不同温度的流体。然后在大大地简化了问题之后获得了洛伦兹方程。

### Main boby

洛伦兹将Navier-Stokes方程简化有书中（3.29）式：

![](http://latex.codecogs.com/gif.latex?\frac{dx}{dt}=\sigma(y-x))

![](http://latex.codecogs.com/gif.latex?\frac{dy}{dt}=-xz+rx-y)

![](http://latex.codecogs.com/gif.latex?\frac{dz}{dt}=xy-bz)

所以得到下列式组：

![](http://latex.codecogs.com/gif.latex?\·x_{i+1}=x_{i}+\sigma(-x_{i}+y_{i})dt)

![](http://latex.codecogs.com/gif.latex?\·y_{i+1}=y_{i}+(-x_{i}z_{i}+rx_{i}-y_{i})dt)

![](http://latex.codecogs.com/gif.latex?\·z_{i+1}=z_{i}+(x_{i}y_{i}-bz_{i})dt)

和书中取值一样，取![](http://latex.codecogs.com/gif.latex?\sigma)=10，b=8/3.

设计代码运行程序，得到Lorenz模型变量y和z随时间变化的变化：

[源代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%203.26%20(01))

得到图像为

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2001.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2002.png)

为绘制相空间图，设计如下程序：

[源代码2](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20chapter%203.26%EF%BC%8802%EF%BC%89)

得到图像为

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2003.png)

之后就像书中79、80页给出x = 0时yOz的相空间图的及y = 0时的xOz的相空间图的思路一样，我也设计程序实现这两个图像首先取r=60

[源代码3](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20chapter%203.26%EF%BC%8803%EF%BC%89)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2004.png)
![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2005.png)

之后改变r值到120，得到图像有：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2006.png)
![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter%203.26%2007.png)

### Conclusion

- 洛伦兹模型具有混沌特性；
- 在洛仑兹原始的工作中，x表示的是对流的翻动速率，y正比于上流与下流液体温差，z是垂直方向的温度梯度。式中三个参数![](http://latex.codecogs.com/gif.latex?\sigma)（Prandtl数）、b和r（Rayleigh数）可任取大于0的数值。常用的组合是就是文中所取的10和8/3；
- 在r较小（如取1）的情况下，系统是稳定的，演化到两个吸引点中的一个。随着r的增加，系统趋于复杂，r=28在时达到混沌状态。r大一些的情况是所谓的圆环结；
- 混沌理论也不一定要求系统形式上的复杂性，比如描述洛伦兹吸引子的方程组就很简单。关键是，在简单的表象后面莫测的复杂。

### Acknowledgement

借助在线latex公式编辑器进行公式编写；借用前辈刘洋的部分代码进行绘图，借助百度百科及部分学术文章对[洛伦兹模型](https://wenku.baidu.com/view/4ca33a8216fc700aba68fc1f.html)问题的介绍理解问题及解答方法，对以上机构或个人表示感谢