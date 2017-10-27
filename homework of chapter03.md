## 题目3.9

Study the effects of damping by starting the pendulum with some initial angular displacement, say θ=0.5 radians, and study how the motion decays with time. Use q=0.1 and estimate the time constant for the decay. Compare your result with approximate analytic estametes for the decay time.

### Summary

本文结合第三章内容3.1 3.2 3.3节,提出题目3.9的解决方案, 在这份报告中，一个简单的摆锤开始于某个角度，在一定阻尼条件下开始运动，随时间变化的运动情况是研究焦点 考虑有驱动力和非线性影响，可能发展为混沌系统

### Background

钟摆问题经常在生活中遇到，振荡现象的例子在物理学中更是数不胜数，通常我们在研究理想情况下摆动问题时，忽略阻尼带来的影响，摆动角度被认为是很小的 . 然而在实际问题中，我们不仅要考虑到阻尼问题，由外力驱动的摆在摆动开始角度也要认为的大一些

### Main boby

##### 理论探究

和以前探究问题方法一样，我们从最简单的情况开始探究
在理想情况下的简单谐波运动，我们容易有

![](http://latex.codecogs.com/gif.latex?\frac{d^{2}\theta}{dt^{2}}=-\frac{g}{l}\theta)

![](http://latex.codecogs.com/gif.latex?\theta=\theta_{0}sin(\Omega*t+\phi))

之后我们开始考虑阻尼带来的影响，考虑线性影响下的情况，可有摩擦力形式为![](http://latex.codecogs.com/gif.latex?\frac{qd\theta}{dt}) 摆的速度可以表示为![](http://latex.codecogs.com/gif.latex?\frac{ld\theta}{dt})

再之后考虑到驱动力，假设驱动力随时间的变化呈正弦曲线，具有振幅 F 和角频率 Ω 可有

![](http://latex.codecogs.com/gif.latex?\frac{d^{2}\theta}{dt^{2}}=-\frac{g}{l}\theta-q\frac{d\theta}{dt}+F_{D}sin(\Omega_{D}t))   （#）

有书上式（3.15）和式（3.16）可有

![](http://latex.codecogs.com/gif.latex?\theta(t)=\theta_{0}sin(\Omega_{D}t+\phi))

![](http://latex.codecogs.com/gif.latex?\theta_{0}=\frac{F_{D}}{\sqrt{(\Omega^{2}-\Omega_{D}^{2})+(q\Omega_{D})^{2}}})

当摆动角度不能视为很小的时候上面θ需写为原来的形式sinθ

记#式右面为f（θ,dθ/dt,t）由 Euler-Cromer方法得

![](http://latex.codecogs.com/gif.latex?\omega_{i+1}=\omega_{i}+f\Delta·t)

![](http://latex.codecogs.com/gif.latex?\theta_{i+1}=\theta_{i}+\omega\Delta·t)

![](http://latex.codecogs.com/gif.latex?\·t_{i+1}=t_{i}+\Delta·t)

二阶Runge-Kutta方法可有

![](http://latex.codecogs.com/gif.latex?\omega'=\omega_{i}+\frac{1}{2}f\Delta·t)

![](http://latex.codecogs.com/gif.latex?\theta'=\theta_{i}+\frac{1}{2}\omega\Delta·t)

![](http://latex.codecogs.com/gif.latex?\·t'=t_{i}+\frac{1}{2}\Delta·t)

![](http://latex.codecogs.com/gif.latex?\omega_{i+1}=\omega_{i}+f(')\Delta·t)

![](http://latex.codecogs.com/gif.latex?\theta_{i+1}=\theta_{i}+\omega'\Delta·t)

![](http://latex.codecogs.com/gif.latex?\·t_{i+1}=t_{i}+\Delta·t)

##### 代码和图像

无驱动力的时候不同阻尼对摆运动的影响

[源代码1](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c%203-9%20code1/)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3-9%20fig1.png)

有驱动力和阻力的时候在各自初始条件下，逐步趋近于稳定状态的过程

[源代码2](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/c%203-9%20code2)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/c3-9%20fig2.png)

### Conclusion

- 从无驱动图里可知在阻尼系数较小的时候，摆经过多次振荡趋近于停滞，且阻尼系数越小，持续时间越长。而当阻尼系数较大时，摆并不会振荡，而是直接停在平衡处，此时阻尼系数越大，摆下降得越慢，到达最低点平衡处经历时间越长。这和我们生活事实经验符合得很好。
-  从第二张图可以看出，在有驱动力的情况下，最开始并没有形成规则地摆动，而是施加的频率将与摆锤的固有频率竞争，经过一定时间后，才趋近稳定的摆动，Ω越大稳定后周期越小，F（D）越大稳定后振幅越大

### Acknowledgement

借助在线latex公式编辑器进行公式编写；借用前辈吴雨桥的部分代码进行绘图，借助百度百科及部分学术文章对摆动问题的介绍理解问题及解答方法，对以上机构或个人表示感谢
