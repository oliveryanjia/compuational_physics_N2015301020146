## 题目1.4
### Summary
本文结合第一章内容，提出题目1.4的解决方案，通过两种核子的衰变模型，探究t(A)与t(B)不同比值下的衰变规律
### Background
对于连续进行衰变的元素，如由A衰变为B，再由B衰变为C，每一个过程如果独立考虑，则与课文中所讨论的类型相似，不过在本题中，元素B不只考虑衰变为C，同时它也是元素A衰变后的产物，因此，在消耗B衰变为C的过程中，B也在由A的衰变所生成

![](http://latex.codecogs.com/gif.latex?\frac{d}{dx}N_{A}=)![](http://latex.codecogs.com/gif.latex?\frac{-N_{A}}{t_{A}})

![](http://latex.codecogs.com/gif.latex?\frac{d}{dx}N_{B}=\frac{N_{A}}{t_{A}}-\frac{N_{B}}{t_{B}})

这是与书中原例题有所差别的地方，也是拓展的地方
### Main boby
类似书中从（1.1）到（1.2）处理办法，我们先写出AB两者的解析解之后取近似且t(A)远大于t(B)，我们有

![](http://latex.codecogs.com/gif.latex?\.N_{A})![](http://latex.codecogs.com/gif.latex?\=N_{A}(0)\*e^{-T/t})

![](http://latex.codecogs.com/gif.latex?\.N_{B})![](http://latex.codecogs.com/gif.latex?\=N_{A}(0)\*e^{-T/t})![](http://latex.codecogs.com/gif.latex?\frac{t_{B}}{t_{A}-t_{B}})
 
 
 有欧拉法及书上（1.3）~（1.6）可有t+dt时刻N与t时刻N的关系如下

![](http://latex.codecogs.com/gif.latex?\.N_{A}(T+dT))![](http://latex.codecogs.com/gif.latex?\=N_{A}-N_{A}/t_{A}*dT)

![](http://latex.codecogs.com/gif.latex?\.N_{B}(T+dT))![](http://latex.codecogs.com/gif.latex?\=N_{B}-(N_{A}/t_{A}-N_{B}/t_{B})*dT)
 

此即为欧拉法解题中心思想，由前一组取值用公式计算出趋势，取一定步长，估计出经历一定步长之后的值,此时我们确定A与B的初始值，步长h=dT，t(A)与t(B)比值，设计出程序以实现目的源代码，由图像可得其变化特点，以及t(A)与t(B)不同比值下的衰变规律
### [源代码](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter01-1.4.py)
