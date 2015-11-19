---
layout: wiki
title: MWbalanced Wiki
---

<div class="jumbotron">
    <p class="lead">这里是喵呜实验室的维基百科。我们提供DIY一个属于你自己两轮自平衡小车的文档，也提供对MWbalanced两轮自平衡小车进行二次开发的指导。 </p>
</div>

<p>MWbalanced是喵呜实验室的两轮自平衡小车的代号。代号MWbalanced的命名遵循“MW+xxx”的方式，MW为大写，是Miaow的缩写，balanced为小写，意为“平衡的”。</p>
* [入手试飞教程](wiki/user-guide.html)
* [组装维修教程](wiki/assemble-guide.html)

<h2 id="rd">开发指南</h2>
* [windows下开发环境搭建—裸机版本](wiki/setup-environment-in-windows-none.html)
* [windows下开发环境搭建—Small RTOS51版本](wiki/setup-environment-in-windows.html)
* [STC-ISP使用及常见问题](wiki/setup-environment-in-linux.html)
* [通过USB烧写固件](wiki/jlink-debug.html)
* [MWbalanced安卓客户端](wiki/crazepony-android-client.html)
* [MWbalanced上位机使用](wiki/flash-firmware.html)

<h2>MWbalanced原理讲解</h2>
* [MWbalanced器件选型总览及说明](wiki/ic-readme.html)
* [MWbalanced硬件原理讲解](wiki/hardware-base.html)
* [MWbalanced软件框架讲解（5.0及以前）](wiki/software-base.html)
* [MWbalanced软件框架讲解](wiki/softmain.html)
* [MWbalanced软件开发经验总结](wiki/software-experience.html)
* [MWbalanced通信协议](wiki/crazepony-communication.html)

<h2 id="exp">开发经验总结</h2>
* [原地直立&原地旋转](wiki/auto-hold.html)
* [动力效率&续航时间](wiki/crazepony-props.html)
* [车体平衡调试](wiki/crazepony-debug.html)
* [超声波和避障](wiki/crazepony-antenna.html)
* [红外巡线](wiki/crazepony-camera.html)
* [摄像头和图传](wiki/remote-controller-bt.html)

<h2 id="quadcopter-dev">两轮自平衡小车算法讲解</h2>
<p>姿态解算是指把陀螺仪、加速度计、罗盘等数据融合在一起，得出飞行器的空中姿态，也叫做姿态融合。姿态解算的过程，涉及到传感器数据读取与滤波，四元数与旋转，姿态解算框架，长期融合/快速融合。</p>
* [姿态解算简介](wiki/attitude-algorithm.html)
* [姿态的数学表示方法](wiki/attitude-math.html)
* [姿态的测量](wiki/attitude-measure.html)
* [姿态解算流程](wiki/attitude-algorithm-flow-graph.html)
* [软件姿态解算](wiki/software-algorithm.html)
* [硬件姿态解算](wiki/hardware-algorithm.html)
* [四元数](wiki/quaternions.html)
* [三轴陀螺仪和三轴加速度计MPU6050](wiki/mpu6050.html)
* [气压计MS5611](wiki/ms5611.html)
* [四轴PID控制算法](wiki/algorithm-pid.html)

<h2 id="crazyflie">Crazyflie</h2>
<p>为了满足各个层次用户的需求和体现出我们的努力，后续会试着移植Small RTOS51实时操作系统内核。Small RTOS51是陈明计先生（就职于周立功公司）编写的一个实时操作系统，适合在小RAM单片机上运行。</p>
* [Small RTOS51简介](wiki/freertos-intro.html)
* [介绍几个常用的宏的作用](wiki/macro-controls.html)
* [固件系统流程框架](wiki/system-flow-graph.html)
* [通信协议](wiki/comm-protocol.html)

<h2 id="other">其他</h2>
* [MWbalanced的机械结构](wiki/crazepony-construct.html)