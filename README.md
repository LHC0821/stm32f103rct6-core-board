# STM32F103RCT6 Multi-Interface Control Board

**基于 STM32F103RCT6 的多接口集成式嵌入式控制开发板**

<p align="center">
  <img src="https://img.shields.io/badge/MCU-STM32F103RCT6-blue" />
  <img src="https://img.shields.io/badge/Core-ARM%20Cortex--M3-green" />
  <img src="https://img.shields.io/badge/EDA-JLCEDA%20Pro-orange" />
  <img src="https://img.shields.io/badge/Hardware-PCB-red" />
</p>

<p align="center">
  <b>STM32 Embedded Development · Multi-Interface · Robotics Control</b>
</p>

## 1. 项目简介

本项目是一款基于 **STM32F103RCT6** 微控制器设计的多接口集成式嵌入式控制开发板，采用模块化硬件设计思路，面向嵌入式系统开发、机器人控制、自动化设备、电子电路实验及综合硬件开发等应用场景。

项目使用 **嘉立创 EDA 专业版（JLCEDA Pro）** 完成原理图设计与 PCB Layout，围绕 STM32F103RCT6 构建了较为完整的硬件控制平台。

与传统的 STM32 最小系统板不同，本设计在主控基础上集成了电源管理、通信接口、电机驱动、PWM 输出、传感器接口及人机交互等功能，旨在减少外围电路搭建工作，提高嵌入式硬件开发的集成度和可扩展性。

本仓库主要开源硬件原理图、PCB 工程及相关设计资料，并持续维护硬件迭代版本。

## 2. 主控芯片

| 参数 | 规格 |
|---|---|
| MCU | STM32F103RCT6 |
| CPU 内核 | ARM Cortex-M3 |
| 最高主频 | 72 MHz |
| Flash | 256 KB |
| SRAM | 48 KB |
| 封装 | LQFP64 |
| 工作温度 | -40℃ ~ +85℃ |
| EDA 软件 | 嘉立创 EDA 专业版 |
| 开发环境 | STM32CubeIDE / Keil MDK |

## 3. 硬件功能模块

### 3.1 主控及引脚扩展

- STM32F103RCT6 主控电路
- MCU 多组 GPIO 引脚扩展
- 外围功能接口引出
- BOOT 启动配置
- 复位及基础时钟电路

### 3.2 电源管理模块

- 电源输入接口
- 电源防反接保护电路
- DC-DC 降压模块
- 主控及外围模块供电

PCB 丝印标注有 24V 输入，具体允许输入范围、各级输出电压及负载能力以实际电路参数和器件数据手册为准。

### 3.3 通信接口模块

| 接口 | 功能 |
|---|---|
| DAPLINK | 程序下载及调试接口 |
| I2C | I2C 总线通信 |
| SPI | SPI 总线通信 |
| UART | 串行通信接口 |
| CAN | CAN 总线通信 |
| RS485 | 差分串行通信 |

**特别说明：** 原理图明确标注串口2不能与 RS485 共用，实际使用时需要注意 UART 资源及引脚复用关系。

### 3.4 电机及运动控制模块

- TB6612 电机驱动电路
- 六路 PWM 接口
- 电机控制信号引出
- 外围运动控制接口

TB6612 用于双通道直流电机驱动，具体电机供电路径及允许电压应以实际原理图和芯片数据手册为准。

### 3.5 传感器模块

- JY62 姿态传感器接口
- 传感器通信信号引出
- 外围扩展接口

为后续机器人姿态检测、运动控制及多传感器融合提供硬件基础。

### 3.6 人机交互模块

- 独立按键电路
- 用户 LED 指示电路
- 蜂鸣器电路
- 电源及运行状态指示

## 4. PCB 设计

本项目采用模块化布局方式，根据功能将不同电路区域进行划分，便于后续硬件维护、调试及功能扩展。

PCB 设计特点：

- 主控与外围功能电路分区布局。
- 多组排针接口，便于外设扩展。
- 预留机械安装孔位。
- 设计板边接口，方便外部设备连接。
- 集成板级功能标识及装饰图案。
- 兼顾接口可访问性与整体结构布局。

## 5. 设计效果展示

### 5.1 原理图总览

<img width="950" height="703" alt="image" src="https://github.com/user-attachments/assets/97a3d809-06f7-4eb6-b0f7-1d377a34d91d" />


### 5.2 PCB Layout

<img width="477" height="435" alt="image" src="https://github.com/user-attachments/assets/1a5f186b-5b48-474b-a48b-adac9df7c28e" />

<img width="645" height="436" alt="image" src="https://github.com/user-attachments/assets/86cdd181-4224-433f-98f3-2e579a6dd11c" />


### 5.3 PCB 三维预览

<img width="956" height="801" alt="image" src="https://github.com/user-attachments/assets/a758f868-1371-41c4-b78d-94b0915087e8" />

<img width="982" height="819" alt="image" src="https://github.com/user-attachments/assets/671c9f50-1397-4990-8ea8-f016f458a0f3" />

## 6. 项目目录结构

```text
stm32f103rct6-core-board/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── hardware/
│   ├── project/             # 嘉立创EDA完整工程
│   ├── schematic/           # 原理图资料
│   ├── pcb/                 # PCB设计资料
│   └── library/             # 自定义器件库
│
├── manufacturing/
│   ├── gerber/              # PCB生产文件
│   ├── bom/                 # 元器件物料清单
│   └── assembly/            # 装配资料
│
├── docs/
│   └── images/              # 原理图、PCB及实物图片
│
└── firmware/
    └── README.md            # 固件开发说明
```

注：原始嘉立创 EDA 工程及必要的配套文件需要完整保留，以上为推荐归档结构。

## 7. 开发环境

### 硬件开发

- 嘉立创 EDA 专业版
- 原理图设计与检查
- PCB Layout
- Gerber 文件导出

### 固件开发

- STM32CubeMX
- STM32CubeIDE
- Keil MDK
- STM32 HAL / LL
- C / C++

### 下载及调试

- DAPLINK
- ST-Link（根据调试接口适配）

## 8. 硬件验证计划

- [ ] 原理图 ERC 检查
- [ ] PCB DRC 检查
- [ ] 电源输入及防反接验证
- [ ] DC-DC 输出电压测试
- [ ] STM32 上电及复位测试
- [ ] DAPLINK 下载调试测试
- [ ] UART 通信测试
- [ ] I2C / SPI 通信测试
- [ ] CAN 通信测试
- [ ] RS485 通信测试
- [ ] TB6612 电机驱动测试
- [ ] 六路 PWM 输出测试
- [ ] JY62 传感器通信测试
- [ ] 按键、LED 及蜂鸣器测试
- [ ] PCB 实物焊接及整板联调

以上为待验证项目，实际测试完成后再更新状态。

## 9. 生产资料

正式发布硬件版本时，建议提供：

| 文件 | 说明 |
|---|---|
| EDA Project | 完整嘉立创 EDA 工程 |
| Schematic PDF | 原理图 PDF |
| Gerber | PCB 制板文件 |
| BOM | 元器件清单 |
| CPL | 元器件坐标文件（如适用） |
| PCB 3D | PCB 三维预览 |
| Assembly Drawing | 装配参考图 |

所有生产资料应与对应硬件版本保持一致。

## 10. 版本管理

本项目采用 Git 进行版本管理。

| 版本 | 说明 |
|---|---|
| v0.1.0 | 初始硬件设计 |
| v0.2.0 | 原理图及 PCB 优化 |
| v0.3.0 | 硬件检查与接口调整 |
| v1.0.0 | 首个正式发布版本 |

具体版本根据实际设计和验证进度发布。

## 11. License

项目暂未指定开源许可证。

正式开源时，请根据实际授权意愿添加 LICENSE 文件，明确硬件设计资料的使用、修改及分发权限。

## 12. Author & Repository

**Author:** LHC0821

**GitHub:** https://github.com/LHC0821

**Repository:** https://github.com/LHC0821/stm32f103rct6-core-board

---

*Designed for embedded development, robotics control and hardware experimentation.*

