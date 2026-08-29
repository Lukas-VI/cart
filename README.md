# neko cart 无人车

本项目用于记录制作无人小车的全过程，用于学习ROS2和SLAM，包括程序实现与硬件选型，所记录的文档资料等。

想要以极致的性价比组装小车，捡垃圾的技巧和精神是必不可少的。

## 当前进度

2026年8月29日

组装了一半, 雷达焊好接头测试了点云, 安全下车

![点云](docs\picture\daily\dotmap.jpg)
![电机](docs\picture\daily\半成品.jpg)

## 部件选型

| 项目 | 图示 | 注释 | 参考价格 |
|--|--|--|--|
|轮毂电机| ![电机](docs\picture\motor.jpg) | 闲鱼上大量流通的二手平衡车拆机无刷轮毂电机，配合驱动板使用。选择它是因为使用该动力的人很多，方案成熟。 | 190元/4个 |
|驱动板|![驱动板](docs\picture\DriveBoard.jpg)| 同样为拆车件的驱动板，STM或GD32F103可以刷固件进行自定义控制 |40|
|Pandar 40p 激光雷达|![雷达](docs\picture\LiDar.jpg)| 虽然VLP-16更为流行，资料多，但是同等价位下选择这个就能拿到40线的，但是必须要解决它的Lemo接口问题：网上几乎不卖数据盒，因此需要单买母口并自行焊接线材。|本体450 + 接口 70|
|主控 RK3576-miniEVM 评估板|![主控](docs\picture\Mainboard.jpg)| 放在今天价格优势不明显，但是仍然能在成本、功耗和算力上得到较好的平衡。| - |
|G354 六轴惯导模块|| 百元价位无敌的性能，但是封装刁钻，需要自己焊转接板| 80 |

# 软件栈

处于各层的软件将作为各个模块进行分发, 没有链接就是WIP

### 操作系统：

- Ubuntu22.04 ROS2 humble

### 硬件驱动：

- [Hverboard FOC](https://github.com/Lukas-VI/hoverboard-firmware-FOC)

- [ROS2 相机驱动](https://github.com/Lukas-VI/hikvision_ros2)

- 惯导驱动

### SLAM：

- Fasht-LIO2 前端

- Cartographer 位姿估计

- 卡尔曼滤波

### 路径规划/决策：

- Nav2

### 交互：

- RK NPU 目标检测

- 骁龙 ELite NPU 检测

- 云台控制: 联动瞄准与火控

- 4G 远控

- 适用于高斯泼溅的街景数据采集

- UWB 跟随组件
