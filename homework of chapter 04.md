## 题目4.16

Carry out a true three-body simulation in which the motions of Earth, Jupiter, and the Sun are all calculated. Since all three bodies are now in motion, it is useful to take the center of mass of the three-body system as the origin, rather than the position of Sun. It is also recommendable to give the Sun an initial velocity to make the total momentum of the system exactly zero (so that the center of mass will remain fixed). Study the motion of Earth with different initial conditions. Also, try increasing the mass of Jupiter to 10, 100, 1000 times of its true mass.

### Summary

本文结合书中章节4.4内容，提出题目4.16的解决方案，本节内容主要在于探究三体问题，以及木星对地球运动的影响（本节题目）。因此本文从太阳，地球和木星构成的三体系统研究由地球和木星之间的引力以及其对地球运动的影响。

### Background

三体问题是天体力学中的基本力学模型。它是指三个质量、初始位置和初始速度都是任意的可视为质点的天体，在相互之间万有引力的作用下的运动规律问题。分析理论更加复杂。由于木星是太阳系中最大的行星，在本题目中我们考虑由太阳，地球和木星组成的三体问题。

可以查得：
![](http://latex.codecogs.com/gif.latex?m_S%3D2.0%5Ctimes10%5E%7B30%7Dkg%2Cm_E%3D6.0%5Ctimes10%5E%7B24%7Dkg%2Cm_J%3D1.9%5Ctimes10%5E%7B27%7Dkg)  
![](http://latex.codecogs.com/gif.latex?x_S%3D0%2Cx_E%3D1AU%2Cm_J%3D5.2AU) 

### Main boby

类似书上过程进行分析。两个星体引力表示为（书上114页）：
 
![](http://latex.codecogs.com/gif.latex?F_%7Bij%7D%3D%5Cfrac%7BGm_im_j%7D%7B%28x_i-x_j%29%5E2&plus;%28y_i-y_j%29%5E2%7D)  

以i星体为主体进行表示（将i视为地球，则考虑j为太阳和木星）：  
![](http://latex.codecogs.com/gif.latex?%5Coverrightarrow%7BF_i%7D%3D%5Csum_%7Bj%7D%5E%7Bj%5Cneq%20i%7D%5Cfrac%7BGm_im_j%7D%7B%5Cleft%20%7C%20%5Coverrightarrow%7Br_j%7D-%5Coverrightarrow%7Br_i%7D%20%5Cright%20%7C%5E2%7D%5Ccdot%20%5Cfrac%7B%5Coverrightarrow%7Br_j%7D-%5Coverrightarrow%7Br_i%7D%7D%7B%5Cleft%20%7C%20%5Coverrightarrow%7Br_j%7D-%5Coverrightarrow%7Br_i%7D%20%5Cright%20%7C%7D)  

我们将地球和太阳距离用一个天文单位AU来表示：![](http://latex.codecogs.com/gif.latex?d_%7BS%2CE%7D%3D1AU)，因此可有 ![](http://latex.codecogs.com/gif.latex?Gm_S%3D4%5Cpi%5E2AU%5E3/yr%5E2) 

[设计程序会出图像{可点击}](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%204.26)

当取Mass of Jupiter=原质量，即n=1时，可得运动轨迹为：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter4.26%2001.png)

当n=15时

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter4.26%2002.png)

n=100时

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter4.26%2003.png)

n=200时

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter4.26%2004.png)

### Conclusion

- 当木星质量为常态时，地球和木星运行均为周期性近圆形轨道，太阳在图中坐标系下相对静止
- 当木星质量扩大为15倍时，已明显影响地球轨道，而太阳运行受影响较小
- 当木星质量扩大为百倍以上时，太阳和地球运行轨道收到明显影响，变得杂乱起来

### Acknowledgement

本文代码由学长王世兴代码改变而得，在此表示感谢；同时参考了百度对三体运动的分析，对此表示真诚的谢意
