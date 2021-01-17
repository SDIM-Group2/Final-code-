# 概述
总体上包含电机控制代码、吸盘控制代码、电子秤代码以及舵机测试仪代码，大体上使用了树莓派、Arduino、STM32三种控制工具

## 电机控制
### 编译环境：基于Arduino的IDE，简化版的C语法
### 基本描述：主要是针对舵机和步进电机，基本的控制形式相同——串口传输（通过PC端口，USB线）、红外控制（红外发射器+红外接收器）、WIFI控制、蓝牙控制
WIFI——通过搭载ESP8266-12F芯片的NodeMCU开发板实现接收信号，使用手机上的app——Blinker(物联网)发射信号，从而实现具体的控制
 蓝牙——通过HC-05蓝牙模块接受信号，使用手机上的app——Roboremo发射信号，从而实现具体的控制
对于两种电机的具体代码来说——导入的库不同，所以核心代码不同；但是总体上的流程一致
最终项目中采用了蓝牙去控制步进电机，而且没有使用Arduino中自带的库，自己去编写了核心的控制代码

## 吸盘控制
### 编译环境：基于树莓派的IDE，python语法
### 基本描述：使用电磁继电器去实现气泵的开关，从而去控制吸盘的吸取与放置


## 电子秤
### 编译环境：基于Arduino的IDE，简化版的C语法；基于树莓派的IDE，python语法
### 基本描述：通过HX711芯片和具体的计算代码去测量物体的重量
包含setup部分、主体的测量部分与减少误差的相关计算，可以实现持续的输出，同时更新测量到的数据

## 舵机测试仪
### 编译环境：MDK-ARM V5
### 基本描述：使用STM32F103C8T6蓝色开发板、电位器、OLED屏幕等，当转动电位器时舵机进行旋转，同时屏幕显示高电平时间
核心代码：main.c文件-包含程序说明、主函数
         config.c文件-包含TIM/ GPIO/ ADC等初始化函数
         config.h-包含函数预定义和全局变量预定义
         oled.c-包含各种显示函数和IIC初始化
         oled.h-包含函数预定义和OLED显示所需的宏定义 
