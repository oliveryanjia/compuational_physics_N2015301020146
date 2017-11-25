## Mid-term Assignment

### Summary

本文主要介绍使用pygame制作的一款小游戏的过程极其最后运行结果（会有具体代码和游玩动图）

### Background

贪吃蛇游戏是一款经典的益智游戏，有PC和手机等多平台版本。既简单又耐玩。该游戏通过控制蛇头方向吃食物，从而使得蛇变得越来越长，现在贪吃蛇已经有了很多新颖的玩法（如下图贪吃蛇大作战，由多个玩家控制进行对抗），在这里实现了最质朴的游戏方式

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/%E8%B4%AA%E5%90%83%E8%9B%87%E5%A4%A7%E4%BD%9C%E6%88%98.jpg)

### Main boby

最开始导入pygame，sys，time和random模块即import pygame, sys, time, random，这里参考：

[对time和random模块的介绍](http://blog.csdn.net/hguan07/article/details/77884921)

检测是否有初始化错误，命名，设定各种物体的颜色（包括蛇本身，背景，分数等）

用Pygame.time.Clock()控制帧速率，并不是向每个循环凌驾一个延迟，Pygame.time.Clock()会控制每个循环多长时间运行一次

[此时学习这里的介绍](https://www.cnblogs.com/xiaowuyi/archive/2012/06/11/2545350.html)

对于变量的设定以及定义gameOver函数和score函数参考

[这里的教程](https://www.cnblogs.com/yxcyxc/p/7840391.html)

对于主函数的设定主要就是初始化变量，定义按键控制方向（键盘事件）以及判断是否吃掉食物以增加长度并重新生成食物

[对于主函数设定借用这里代码【可点击】](https://stackoverflow.com/questions/26959562/pygame-restart-function)


最后得到的[游戏程序代码](https://raw.githubusercontent.com/oliveryanjia/compuational_physics_N2015301020146/master/core%20of%20Mid-term%20Assignment)

![image](https://github.com/oliveryanjia/compuational_physics_N2015301020146/blob/master/snack02.gif)

### Conclusion

本文实现了最基础的贪吃蛇游戏设计，对pygame的使用有了不少的了解，也对游戏设计的思路有了一定的反思，简单的吃食物加分的游戏设定，在设计中曾出现忘记写吃掉后再次随机生成食物的代码，也出现过忘记设计触及身体会触发死亡的代码，等等问题。对于代码编写规则有了很多新的了解

### Acknowledgement

对于mainbody中许多网上教程以及代码、模块介绍表示诚挚的感谢；此外，编写过程中也麻烦了计院的同学，感谢同学马绍一提供的支持
