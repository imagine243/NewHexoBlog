title: arkit_note
date: 2017-11-15 16:34:40
tags: arkit
---

# ARKit 总结

### ARkit对现实世界的理解


##### TrueDepth Camera (iPhone x前置)
iPhone X 和 ARKit 可以实时对面部进行检测, 检测到结构化的表达方式.利用这些特性可以将面部的表情映射到3D的模型上.

##### Camera && Core Motion (VIO)
ARKit 可以使用摄像头, 动作感应数据来检测到周围的环境. 比如现在的位置,朝向高度等.

##### 场景理解和光照计算
ARKit 首先可以分析出摄像机的画面中水平的平面, 其次可以感知到场景中光的总量来调整虚拟物体上的关照.

##### 硬件支持和开发环境
ARKit 现在只能运行在6s之后的iPhone和 2017年之后的iPad上. 操作系统要求是iOS11. 可以使用苹果的Metal,SceneKit 和 第三方的 Unity 或者Unreal 来开发AR应用.

### iOS平台接口

![](/uploads/15111728620339.jpg)


##### ARSession 

ARSession 管理着ARkit需要的大部分的功能. 包括动作传感器读取的数据, 相机中读取到的数据,以及根据这一系列数据的分析. 然后 ARSession分析得到的现实世界和虚拟世界融合.

ARSession 被包含在ARSCNView和 ARSKView 中,  如果想创建一个AR的应用,可以使用前面的两个View, 或者创建一个View,在其中包含一个ARSession的对象.

![](/uploads/15111738618236.jpg)


##### ARConfiguration

ARConfiguration 是抽象类, 运行ARSession需要ARConfiguration的子类.
游戏中最最主要使用的是 ARWorldTrackingConfiguration类.
ARWorldTrackingConfiguration 后置相机, 同时追踪了手机的位置,旋转. 可以使用 plane detection 和 hit testing.

AROrientationTrackingConfiguration 只提供了简单的AR功能, 使用了后置相机和手机的旋转.

ARFaceTrackingConfiguration 使用前置相机 可以追踪用户的脸部数据. (仅限iPhone x)

##### ARFrame

ARSession会捕捉相机中的每一帧的画面,ARFrame同时存储了每一帧的画面,还有这一帧时相机的位置,光照情况,以及ARKit分析出的场景中的数据等.

##### ARAnchor

ARAnchor 是在真实世界中的位置和旋转等信息,通过这个数据我们可以将物体放在AR的场景中.

ARPlaneAnchor 代表AR分析出的平面信息.

##### ARCamera

包含了相机的信息, 相机在世界坐标中的transform(位置,旋转), 相机的状态, 相机的projectionMatrix viewMatrix等数据,可以使用在绘制虚拟的世界.



### Unity ARKit

##### 相机的配置
ARCameraManager.cs
UnityARVideo.cs
UnityARCameraNearFar.cs

##### 场景中的对象
GeneratePlanes.cs
PointCloudParticleExample.cs

##### 环境光的配置
UnityARAmbient.cs

shadowPlanePrefab

unity中一个点位代表真实世界的1米


