title: render
date: 2017-08-03 16:21:12
tags: 
---

# 软件渲染
在不使用图形Api(例如 OpenGL DirectX)的情况下, 使用图形学的方法渲染出模型.

渲染图形到屏幕上

![](/uploads/15017503698011.jpg)


假设截面1 是屏幕 ,E是摄像机 , 被渲染的物体在截面1 和 截面2 之间, 渲染的过程就是将物体映射到截面1上.


## 向量与矩阵的理解

先从一片空白中随便选取一点作为原点,以此为原点做两个正交的单位向量(先考虑二维的情况)

![](/uploads/15017527644716.png)

平面上的一个点就可以这样表示:

![](/uploads/15017528682613.png)

把这个简化一下就是向量的形式 (2,1), 是以原点为起点 指向(2,1)的向量.这里先看成是一个点 坐标是(2,1).

![](/uploads/15017530980806.png)

整个二维平面上的点都可以通过 ![](/uploads/15017531703985.jpg)
的方式表示
同事这也是i,j的线性空间

把整个线性空间画出来
![](/uploads/15017536059550.png)

如果 i,j不是正交的长度也不是1,并且i,j不在一条直线上就可以张成一个二维空间

![](/uploads/15017537260555.png)

![](/uploads/15017537608678.png)


有一个二维的向量 x (2,1)
还有一个旋转矩阵 
![](/uploads/15017541376178.jpg)

Ax的效果就是让向量旋转到目的地
![v2-342d39e9f3eb7d964ca3ddfeedf3dfa4](/uploads/v2-342d39e9f3eb7d964ca3ddfeedf3dfa4_r.jpg))


![](/uploads/15017544383403.png)


[理解矩阵 一](http://blog.csdn.net/myan/article/details/647511)
[理解矩阵 二](http://blog.csdn.net/myan/article/details/649018)
[理解矩阵 三](http://blog.csdn.net/myan/article/details/1865397)
## 齐次坐标

有向量v可以找到一组坐标 （v1，v2, v3)

![](/uploads/15017678144223.gif)

v = v1a + v2b + v3c    (1)

有一个点p， 可以找到（p1, p2, p3)使得
p - o = p1a + p2b + p3c (2)
我们把点的位置看作是对这个基的原点o所进行的一个位移，即一个向量 p – o
所以 p = o + p1a + p2b + p3c (3)
这样我们可以看出点与向量的不同表达一个点要比表达一个向量多一个额外的信息
可以把（1）（3） 写成矩阵的形式
![](/uploads/15017682243004.gif)
（a, b, c, o)是基矩阵， 列向量分别代表了在基矩阵下的坐标，向量和点在同一个基矩阵下有不同的表达方式，向量的第四个代数分量是0， 点的第四个代数分量是1.

通过齐次坐标区分向量和点，对于平移变换只有对于点才有意义，向量只有大小和方向

![](/uploads/15017688563938.gif)

对于普通的坐标 p(p1, p2, p3) 对应的有一组齐次坐标（wp1, wp2, wp3, w)
齐次坐标坐标相当于 （wp1/w, wp2/w, wp3/w, w/w)

可以用二维齐次坐标是三维在z = 1 的平面上的坐标
## lookat矩阵
function lookAtLH(eye:Vector3D, at:Vector3D, up:Vector3D)
三个参数分别是： 摄像机位置，目标位置，摄像机上下方

lookat矩阵的作用是将目标的坐标变换到摄像机的空间内。

![28115843-c9df8ad58696491b88808ec4cc19b694](/uploads/28115843-c9df8ad58696491b88808ec4cc19b694.png)

摄像机起点到目标点的点位向量是摄像机空间的z’轴
up * z‘ 得到摄像机空间的x‘轴
z’ * x‘ 得道摄像机空间的y’轴
x‘ y’ z‘ 分别为
z' = cameraZ = Normalize(at - eye)
x' = cameraX = Normalize(Cross(up, cameraZ))
y' = cameraY = Cross(cameraZ, cameraX) 

这样就可以得到从世界空间线性变换到摄像机空间的线性矩阵的线性变换

$$
\left[
\begin{matrix}
cameraX.x & cameraY.x & cameraZ.x \\
cameraX.y & cameraY.y & cameraZ.y \\
cameraX.z & cameraY.z & cameraZ.y
\end{matrix}
\right]
$$

还有从世界空间到摄像机空间的位移

$$
\left[
\begin{matrix}
1 & 0 & 0 & eye.x \\
0 & 1 & 0 & eye.y \\
0 & 0 & 1 & eye.z \\
0 & 0 & 0 & 1
\end{matrix}
\right]
$$

可以得到以下公式

![](/uploads/15017709376880.jpg)




## 透视矩阵

规范立方体



