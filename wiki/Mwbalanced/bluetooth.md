---
layout: wiki
title: 蓝牙通讯实验
---

# {{ page.title }}

> 作者：Songyimiao

在这里，蓝牙模块只是作为信息中转设备，它自身并不产生信息，只对主/从设备的信息进行搬运。

蓝牙通讯实验，跟上一章节的串口通信类似，MWbalanced控制板的蓝牙模块连接了单片机的串口2。

![](/img/wiki/bluetooth-001.png)

![](/img/wiki/bluetooth-002.png)

所以，我们只需要初始化串口2，然后其他跟串口通讯实验类似，我们可以用MWbalanced连接带有蓝牙的笔记本或者手机，用自收自发检验功能是否正常。

（蓝牙）无线通讯实验代码传送门：（这几天整理下就上传）

