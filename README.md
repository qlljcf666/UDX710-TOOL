# Unisoc UDX710 下载工具

本项目是紫光展锐（Unisoc）UDX710（SC9600/Orca）芯片平台的固件下载工具包，版本号为 R27.23.0101。

## 项目简介

UDX710 下载工具是一套用于在工厂生产、研发测试和设备升级场景中向 Unisoc UDX710 芯片平台烧录固件的工具集合。该工具支持多种下载模式，包括：

- **FactoryDownload** - 工厂批量下载模式
- **ResearchDownload** - 研发调试模式  
- **UpgradeDownload** - 升级下载模式

## 主要特性

- 支持多种固件格式镜像文件烧录
- 支持 NV 数据备份与恢复
- 集成 MES（制造执行系统）接口
- 支持设备自动检测与监控
- 完整的日志记录系统
- 支持 USB/串口等多种下载通道

## 目录结构

```
Download_R27.23.0101/
├── Bin/                          # 编译后的可执行文件和 DLL
│   ├── App/                      # 应用程序核心组件
│   ├── ImageFiles/               # 固件镜像文件目录
│   ├── Log/                      # 下载日志目录
│   ├── ReadFlash/                # 读取Flash数据
│   ├── Setting/                  # 配置文件
│   ├── System/                   # 系统依赖文件
│   └── CmdDloader.exe           # 命令行下载工具
├── Source/                       # 源代码目录
│   ├── Common/                   # 公共组件
│   │   ├── CheckAlgo/           # 校验算法 (MD5, SHA256, CRC16)
│   │   ├── DLFWDef/             # 下载框架定义
│   │   ├── Drv/                 # 驱动接口
│   │   ├── Helper/              # 辅助工具
│   │   ├── Include/             # 头文件定义
│   │   ├── PhaseCheck/          # 阶段检查
│   │   ├── Thread/              # 线程管理
│   │   └── UtilFn/              # 工具函数
│   └── Customized/              # 定制组件
│       └── AuthenticationLib/   # 认证加密库
└── Doc/                          # 文档资料
```

## 固件镜像文件

工具支持以下类型的固件镜像文件：

- `boot-sign.img` - 启动镜像
- `u-boot-sign.bin` - U-Boot 引导程序
- `fdl1-sign.bin` / `fdl2-sign.bin` - 下载加载器
- `rootfs.ubifs` / `recoveryfs.ubifs` - 文件系统镜像
- `SC9600_*_modem-sign.bin` - 调制解调器固件
- `Orca_*_DSP-sign.bin` - DSP 固件
- `userdata_b128k_p2k.img` - 用户数据分区

## 配置文件说明

| 文件 | 用途 |
|------|------|
| FactoryDownload.ini | 工厂下载配置 |
| ResearchDownload.ini | 研发下载配置 |
| UpgradeDownload.ini | 升级下载配置 |
| BMFileType.ini | 文件类型映射 |
| BMTimeout.ini | 超时配置 |
| BinPack.ini | 镜像打包配置 |

## 技术规格

### 校验算法

- **MD5**: 文件完整性校验
- **SHA256**: 安全哈希算法
- **CRC16**: 循环冗余校验

### 加密支持

- **RSA**: 2048 位非对称加密
- **AES**: 高级加密标准
- 支持安全启动签名验证

## 使用说明

### 1. 准备固件

将待下载的固件镜像文件放入 `Bin/ImageFiles/` 目录下对应的版本文件夹中。

### 2. 选择下载模式

- 双击 `FactoryDownload.exe` 或 `FactoryDownload_CN.exe` 启动工厂下载工具
- 双击 `ResearchDownload.exe` 或 `ResearchDownload_CN.exe` 启动研发下载工具
- 双击 `UpgradeDownload.exe` 或 `UpgradeDownload_CN.exe` 启动升级下载工具

### 3. 连接设备

通过 USB 或串口连接目标设备，点击工具界面上的"下载"按钮开始烧录。

### 4. 查看日志

下载日志保存在 `Bin/Log/` 目录下，按日期组织。

## 系统要求

- Windows 7/8/10/11 操作系统
- Microsoft Visual C++ 2010 运行库
- 建议 4GB 及以上内存
- 至少 500MB 可用磁盘空间

## 技术支持

如遇到问题，请查阅：

- `Doc/Download Tool User Guide V4.3.pdf` - 详细用户手册
- `Doc/Download Error Message Description.xlsx` - 错误代码说明

## 版本历史

- **R27.23.0101**: 当前版本，支持 UDX710/SC9600 平台

## 注意事项

1. 下载过程中请勿断开设备连接
2. 确保电源稳定，避免中途断电
3. 不同版本的固件可能需要对应版本的下载工具
4. 首次使用建议先备份 NV 数据

---

**注意**: 本工具仅供授权的工厂生产和研发测试使用。