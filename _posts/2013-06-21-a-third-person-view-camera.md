---
layout: post
category : graphics related
title : "第三人称视角相机"
tagline: "总结一些经验"
tags : [camera, third person view]
---
{% include JB/setup %}

最近在学OpenGL4.0中GLSL，为了观察各种shading的效果又重写了一遍读入OBJ的组件，很是蛋疼。想用以前的代码，发现以前写得代码不堪入目还不如重新写。写着写着自然就涉及到了camera的操作，一直觉得WOW里的左键旋转相机用起来很舒服，于是就打算写一个差不多效果的来做模型的预览。
####问题描述
效果是在以物体中心为球心，观察距离为半径的球面上实现up向量沿着球体经线切线方向的观察相机。
####问题分析
无论是glu提供的OPENGL固定管线lookat函数还是传递给shader的View矩阵，一般的参数接口都是三个。第一个是相机位置中心坐标，第二个是相机指向的目标坐标，第三个是相机头顶方向的up向量。第二个参数由模型矩阵决定，可以看做是已经确定的，第一个参数又鼠标位置确定，首先要解决的问题就是根据这两个参数计算出第三个参数。然后还有个问题涉及到鼠标运动和球面上相机位置之间的关系。
####up向量计算
这里第三个参数的计算是纯数学问题，结果可以以后拿来直接用，就先写在这里。
![image](http://github.com/wunf/Wunf.github.io/raw/master/pictures/p1.jpg)
如图所示
