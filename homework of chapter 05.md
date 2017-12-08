## 题目3.9

Use the symmetry of the capacitor problem to write a program that obtain the results by calculating the potential in only one quadrant of the x-y plane.

### Summary

本文结合书上5.1的内容研究了电容器的问题，并由对称性来编写程序，通过计算x-y平面的一个象限中的电势来获得结果。


### Background

在书中使用的方法是relaxation method，这种方法可以用来数值求解以拉普拉斯方程为代表的一类所谓的“椭圆偏微分方程”.这种方法也是有不同的版本，最简单的一种是Jacobi方法。经过改进有Gauss-Seidel方法
与给定初始条件的微分方程不同，可以用欧拉方法或龙格 - 库塔方法来求解拉普拉斯方程，而边界条件常常引入拉普拉斯方程，这些边界条件指定了空间中某个表面上的值。 或者，边界条件可以用与电势的梯度成比例的电场来给出。
因此，引入松弛方法来解决这个项目。 处理称为椭圆方程的偏微分方程组是很方便的，其中拉普拉斯方程就是一个例子。

### Main boby

![image](https://github.com/JunyiShangguan/computationalphysics_N2013301020076/blob/master/ex13/1.png)

由对称性表示只需要一个象限来计算，所以选择第一象限

![image](https://github.com/JunyiShangguan/computationalphysics_N2013301020076/blob/master/ex13/2.png)

电势满足拉普拉斯方程书上（5.1）式：

![](http://latex.codecogs.com/gif.latex?%5Cfrac%7B%5Cpartial%5E2%20V%7D%7B%5Cpartial%20x%5E2%7D&plus;%5Cfrac%7B%5Cpartial%5E2%20V%7D%7B%5Cpartial%20y%5E2%7D&plus;%5Cfrac%7B%5Cpartial%5E2%20V%7D%7B%5Cpartial%20z%5E2%7D%3D0) 

![image](https://camo.githubusercontent.com/f35958018ca64d59388081376393e3a8d1302abd/687474703a2f2f6c617465782e636f6465636f67732e636f6d2f6769662e6c617465783f782533446925354344656c746125323078253243792533446a25354344656c7461253230792532437a2533446b25354344656c74612532307a)可有![image](https://camo.githubusercontent.com/fb2cea965b88fa229cf6e2de1e1cc1f0be77e1e6/687474703a2f2f6c617465782e636f6465636f67732e636f6d2f6769662e6c617465783f56253238692532436a2532436b2532392535436571756976253230562532386925354344656c7461253230782532436a25354344656c7461253230792532436b25354344656c74612532307a253239)

我们有书上（5.2）式：

![](http://latex.codecogs.com/gif.latex?%5Cfrac%7B%5Cpartial%20V%7D%7B%5Cpartial%20x%7D%5Capprox%20%5Cfrac%7BV%28i&plus;1%2Cj%2Ck%29-V%28i%2Cj%2Ck%29%7D%7B%5CDelta%20x%7D)

由此我们可得书上（5.5）（5.6）（5.7）式：

![](http://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20%5Cfrac%7B%5Cpartial%5E2%20V%7D%7B%5Cpartial%20x%5E2%7D%20%26%5Capprox%20%5Cfrac%7B1%7D%7B%5CDelta%20x%7D%5B%5Cfrac%7B%5Cpartial%20V%7D%7B%5Cpartial%20x%7D%28i&plus;%5Cfrac%7B1%7D%7B2%7D%29-%5Cfrac%7B%5Cpartial%20V%7D%7B%5Cpartial%20x%7D%28i-%5Cfrac%7B1%7D%7B2%7D%29%5D%20%5C%5C%20%26%5Capprox%5Cfrac%7B1%7D%7B%5CDelta%20x%7D%5B%5Cfrac%7BV%28i&plus;1%2Cj%2Ck%29-V%28i%2Cj%2Ck%29%7D%7B%5CDelta%20x%7D-%5Cfrac%7BV%28i%2Cj%2Ck%29-V%28i-1%2Cj%2Ck%29%7D%7B%5CDelta%20x%7D%5D%20%5C%5C%20%26%5Capprox%20%5Cfrac%7BV%28i&plus;1%2Cj%2Ck%29&plus;V%28i-1%2Cj%2Ck%29-2V%28i%2Cj%2Ck%29%7D%7B%28%5CDelta%20x%29%5E2%7D%20%5Cend%7Balign*%7D) 

则V（i，j，k）得出（5.8）式

![](http://latex.codecogs.com/gif.latex?%5Cbegin%7Balign*%7D%20V%28i%2Cj%2Ck%29%20%3D%26%5Cfrac%7B1%7D%7B6%7D%5BV%28i&plus;1%2Cj%2Ck%29&plus;V%28i-1%2Cj%2Ck%29&plus;V%28i%2Cj&plus;1%2Ck%29%5C%5C%20%26&plus;V%28i%2Cj-1%2Ck%29&plus;V%28i%2Cj%2Ck&plus;1%29&plus;V%28i%2Cj%2Ck-1%29%5D%20%5Cend%7Balign*%7D)  

接下来设计程序会出图像

[源代码一](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%205.1)

得到图像：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter5.1.png)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter5.1-01.png)

可知电场分布

[源代码二](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/code%20of%205.1%EF%BC%8802%EF%BC%89)

得到图像有：

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/chapter5.1-02.png)

### Conclusion

- 由文中的方法得到的图像和结果与电磁学分析电势情况结果一致
- 电场线主要从左侧板流向右侧板，板间的电场是近乎均匀的
- relaxation method这种方法可以用来数值求解以拉普拉斯方程为代表的一类所谓的“椭圆偏微分方程”

### Acknowledgement

本文借鉴了上官俊怡同学的代码，在此表示感谢