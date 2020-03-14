# 地面站
c#上位机

版本 v0.01

## 协议
协议说明:

SUM等于从该数据帧第一字节开始，也就是帧头开始，至该帧数据的最后一字节所有字节的异或。

协议中长度字节表示该数据帧内包含数据的字节总长度，不包括帧头、功能字、长度字节和最后的校验位，只是数据的字节长度和。比如该帧数据内容为3个int16型数据，那么LEN等于6。


|飞控->地面站
|-|-|-|-|-|-|
|帧头|功能字|长度|数据|校验|备注|
|-|-|-|-|-|-|
|3E|01|-|-|-|飞机状态信息,锁定/姿态异常/电压值|
|-|-|-|-|-|-|
|3E|02|06|DATA|SUM|3个int16型数据,roll/pitch/yaw数据各乘100|
|-|-|-|-|-|-|
|3E|03|0C|DATA|SUM|6个int16型数据,分别为陀螺仪和加速度计原始数据|
|-|-|-|-|-|-|
|3E|04|08|DATA|SUM|4个int16型数据,分别为4个电机的油门大小|
|-|-|-|-|-|-|
|地面站->飞控
|-|-|-|-|-|-|
|3C|02|08|DATA|SUM|4个int16型数据,roll/pitch/yaw/throttle控制数据|

## BUG
