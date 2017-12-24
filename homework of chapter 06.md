## 题目6.12

2015301020146 物基二班 闫佳

### Summary

本文结合第六章内容,提出题目6.6和题目6.12的解决方案，研究波的叠加原理，6.6题考虑横波两列波相遇时，振幅叠加，不发生相互作用，分离后保持原有的形状、速度。  开始时，介绍并开发了一个理想情况下的波动方程的解决方案，此外在频谱分析中应用傅立叶分析来分析弦上的波的形状。

### Background

忽略介质损耗则有波动方程（考虑一维情况）：

![]( http://latex.codecogs.com/gif.latex?%5Cfrac%7B%5Cpartial%5E2%20y%7D%7B%5Cpartial%20t%5E2%7D%3Dc%5E2%5Cfrac%7B%5Cpartial%5E2%20y%7D%7B%5Cpartial%20x%5E2%7D)

适用于横波或纵波。式中c为波速，t为时间，y代表弦上各点相对于其平衡位置的位移，x代表各点在弦上的坐标。叠加原理不受各波初始条件的影响，因此我们可以改变波的形状表现波的叠加和分离

### Main boby

为了求解时间相关的解，波动方程应该采用与拉普拉斯方程中所用的方法。根据书上分析问题思路，表示几个量：

![]( http://latex.codecogs.com/gif.latex?x%3Di%5CDelta%20x%2Ct%3Dn%5CDelta%20t). ![]( http://latex.codecogs.com/gif.latex?y%28i%2Cn%29%5Cequiv%20y%28x%3Di%5CDelta%20x%2Ct%3Dn%5CDelta%20t%29)

得到式子（6.5）：

![]( http://latex.codecogs.com/gif.latex?%5Cfrac%7By%28i%2Cn&plus;1%29&plus;y%28i%2Cn-1%29-2y%28i%2Cn%29%7D%7B%28%5CDelta%20t%29%5E2%7D%5Capprox%20c%5E2%5B%5Cfrac%7By%28i&plus;1%2Cn%29&plus;y%28i-1%2Cn%29-2y%28i%2Cn%29%7D%7B%28%5CDelta%20x%29%5E2%7D%5D)  

表示为式子（6.6）形式：

![]( http://latex.codecogs.com/gif.latex?y%28i%2Cn&plus;1%29%3D2%281-r%5E2%29y%28i%2Cn%29-y%28i%2Cn-1%29&plus;r%5E2%5By%28i&plus;1%2Cn%29&plus;y%28i-1%2Cn%29%5D)

在弦上施加的干扰表示为：

![](http://latex.codecogs.com/gif.latex?\·y_{0}(x)=exp[-k(x-x_{0})^{2}])

设置两个波包，弦长为1；两个高斯型扰动重要参数：k0,x0=1000,0.3；k1,x1=300,0.7；波速为300m/s

则设计程序并绘出图像：

[代码一](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20chapter6.12(01))

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter06waves01.png)

在弦的中心位置加上高斯型的扰动后，位置为0.05的点振动大小随时间的变化情况有（书上图figure6.6）：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter06waves02.png)

功率谱：

[代码二](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20chapter6.12%EF%BC%8802%EF%BC%89)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter06waves03.png)

初始波形为三角波时，其功率谱为：

[代码三](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%20chapter%206.12%EF%BC%8803%EF%BC%89)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter06waves04.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter06waves05.png)

### Conclusion

- 横波两列波相遇时，振幅叠加，不发生相互作用，分离后保持原有的形状和速度，由此可知，这几个波作为弦的运动的解，是相互独立的
- 在主题文章的情况下由频谱可知频率为150Hz的奇数倍时有峰值
- 初始波形为三角波时功率谱上有几个峰，随着频率的增大峰值在减小

### Acknowledgement

借助在线latex公式编辑器进行公式编写；借用前辈吴威鹏的部分代码进行绘图；借助Computational Physics, Nicholas J. Giordano & Hisao Nakanishi部分内容，对此表示诚挚的谢意
