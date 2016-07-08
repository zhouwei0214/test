---
layout: wiki
title: MWbalanced硬件原理讲解
---

# {{ page.title }}

> 作者：Songyimiao

## 原理图设计

MWbalanced硬件组成：

* 控制芯片：IAP15W4K61S4
* 姿态传感器：MPU6050（3轴加速度传感器+3轴陀螺仪）
* 无线通信协议：蓝牙2.1/蓝牙4.0双模透传（预留NRF24L01+接口) 
* 有线通信协议：CP2102
* 电机驱动：MC33186
* 外部接口：Mirco-USB接口
* 电机：GB37减速电机（DC12V，减速比30，转速365RPM）
* 车轮：65mm
* 电池：1300mAh 25c锂电池

# MWbalanced原理图设计简介

## 单片机最小系统

单片机选择宏晶公司IAP15W4K61S4，它体积小（LQFP48），工作电压宽（2.5V-5.5V
），具有丰富的外设模块，适合制作两轮自平衡小车。

它的主要外设包括：

1. PWM ：6路15位硬件PWM+2路CCP的16位；
2. UART：4组；
3. ADC：8路10位高速ADC；
3. 定时器：共7个定时器，5个16位可重装载定时器/计数器,2路CCP还可再实现2个定时器；
5. IO口：最多提供62个GPIO；
6. 内部存储器资源包括： 61k程序Flash，4kSRAM。

此外，IAP15W4K61S4内部还集成了时钟电路、内部高可靠复位电路以及看门狗电路等。下图显示该单片机的内部资源情况。

![](/img/wiki/hardware-basic-01.png)

由于该单片机内已经包含了时钟和复位电路，所以单片机的最小系统电路非常简洁。

![](/img/wiki/hardware-basic-02.png)


## 系统电源

系统采用的动力源是航模锂电池，电池组充满电压达12.6V。而系统的部分芯片需要5V供电，部分芯片需要3.3V供电，所以需要电源转换电路。MWbalanced采用的是芯片LM2596-5.0和ASM1117-3.3。

![power](/img/wiki/hardware-basic-03.png) 


## 姿态传感器

MWbalanced采用的是当下很火的的MPU6050陀螺仪加速度计一体芯片，成本不超过15元，对两轮自平衡小车来说，它的精度和性能绰绰有余了，MPU6050在这个价位里面几乎是占有绝对的性价比优势。首先，它将陀螺仪和加速计封装在一起，通过IIC总线给出六个维度的ADC值；其次，芯片本身提供一个IIC从接口，供用户接第三方的IIC器件，一般选择是接一个电子罗盘，如HMC5883L，构成一个9轴的输出的姿态模组。现在MPU9150已经丧心病狂的把电子罗盘功能也整合在片上了，但是要买60+元。最后，这颗芯片内部集成了一个DMP（Digital Motion Processor）处理器，能直接硬件解算四元数，这让姿态解算不再是难事，跳过这个障碍后就连大妈都能做两轮自平衡小车了。

![](/img/wiki/hardware-basic-04.png) 

## 电机驱动电路

由于车体需要两组电机，因此也需要两组H桥驱动电路。系统选用两片飞思卡尔公司专用电机驱动芯片 MC33186 组成了电机驱动电路。

![](/img/wiki/hardware-basic-07.png) 

每一路电机为了能够实现正反转，都需要两个PWM信号。两个电机总共需要4路PWM信号。


## USB-Serial协议转换
因为考虑到不是每个同学手上都有USB-TTL下载模块的，而且市面上的USB-TTL模块质量参差不齐,质量差的还会导致电脑蓝屏，于是，MWbalancd板载USB-TTL下载电路，通过一根安卓手机标配的MicroUSB线，就可以轻易简单地进行固件更新和调试参数。如此简单的操作步骤，想来随便从大街拉个路人过来应该都可以完成。

![](/img/wiki/hardware-basic-05.png) 

# 蓝牙透传模块

为了让小车能跟上智能机泛滥的步伐，同时也是为了增加它的适应性和降低成本的考虑，我们在原来的基础上增加了蓝牙透传模块，硬件焊盘上兼容蓝牙2.1和蓝牙4.0 BLE技术。就是说，同样一块裸PCB板，可以选择焊接蓝牙2.1和蓝牙BLE的模块。

![](/img/wiki/hardware-basic-06.png) 

蓝牙协议是很复杂的，要想去接触并试图一步一步的写出来，在我现有的时间下，几乎不太可能了。而将蓝牙透明传输成串口，这就很好的将小车与安卓设备对接了，可以直接在安卓设备上面开发遥控app或者上位机。这想想也有点小激动呢，于是，我们真的这么干了，也成功了。