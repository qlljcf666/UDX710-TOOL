# Unisoc UDX710 Download Tool

This project is the firmware download tool package for the Unisoc UDX710 (SC9600/Orca) chip platform, version number R27.23.0101.

## Project Introduction

The UDX710 Download Tool is a collection of tools used to flash firmware to the Unisoc UDX710 chip platform in scenarios such as factory production, R&D testing, and device upgrades. The tool supports multiple download modes, including:

- **FactoryDownload** - Mass production factory download mode
- **ResearchDownload** - R&D debugging mode  
- **UpgradeDownload** - Upgrade download mode

## Main Features

- Supports flashing of multiple firmware format image files
- Supports NV data backup and restoration
- Integrated MES (Manufacturing Execution System) interface
- Supports automatic device detection and monitoring
- Comprehensive logging system
- Supports various download channels such as USB/Serial ports

## Directory Structure

```
Download_R27.23.0101/
├── Bin/                          # Compiled executables and DLLs
│   ├── App/                      # Application core components
│   ├── ImageFiles/               # Firmware image file directory
│   ├── Log/                      # Download log directory
│   ├── ReadFlash/                # Read Flash data
│   ├── Setting/                  # Configuration files
│   ├── System/                   # System dependency files
│   └── CmdDloader.exe           # Command line download tool
├── Source/                       # Source code directory
│   ├── Common/                   # Common components
│   │   ├── CheckAlgo/           # Verification algorithms (MD5, SHA256, CRC16)
│   │   ├── DLFWDef/             # Download framework definitions
│   │   ├── Drv/                 # Driver interfaces
│   │   ├── Helper/              # Auxiliary tools
│   │   ├── Include/             # Header file definitions
│   │   ├── PhaseCheck/          # Phase checks
│   │   ├── Thread/              # Thread management
│   │   └── UtilFn/              # Utility functions
│   └── Customized/              # Customized components
│       └── AuthenticationLib/   # Authentication encryption library
└── Doc/                          # Documentation materials
```

## Firmware Image Files

The tool supports the following types of firmware image files:

- `boot-sign.img` - Boot image
- `u-boot-sign.bin` - U-Boot bootloader
- `fdl1-sign.bin` / `fdl2-sign.bin` - Download loader
- `rootfs.ubifs` / `recoveryfs.ubifs` - Filesystem images
- `SC9600_*_modem-sign.bin` - Modem firmware
- `Orca_*_DSP-sign.bin` - DSP firmware
- `userdata_b128k_p2k.img` - User data partition

## Configuration File Description

| File | Usage |
|------|------|
| FactoryDownload.ini | Factory download configuration |
| ResearchDownload.ini | R&D download configuration |
| UpgradeDownload.ini | Upgrade download configuration |
| BMFileType.ini | File type mapping |
| BMTimeout.ini | Timeout configuration |
| BinPack.ini | Image packaging configuration |

## Technical Specifications

### Verification Algorithms

- **MD5**: File integrity verification
- **SHA256**: Secure Hash Algorithm
- **CRC16**: Cyclic Redundancy Check

### Encryption Support

- **RSA**: 2048-bit asymmetric encryption
- **AES**: Advanced Encryption Standard
- Supports secure boot signature verification

## Usage Instructions

### 1. Prepare Firmware

Place the firmware image files to be downloaded into the corresponding version folder under the `Bin/ImageFiles/` directory.

### 2. Select Download Mode

- Double-click `FactoryDownload.exe` or `FactoryDownload_CN.exe` to launch the factory download tool
- Double-click `ResearchDownload.exe` or `ResearchDownload_CN.exe` to launch the R&D download tool
- Double-click `UpgradeDownload.exe` or `UpgradeDownload_CN.exe` to launch the upgrade download tool

### 3. Connect Device

Connect the target device via USB or Serial port, then click the "Download" button on the tool interface to start flashing.

### 4. View Logs

Download logs are saved under the `Bin/Log/` directory, organized by date.

## System Requirements

- Windows 7/8/10/11 operating system
- Microsoft Visual C++ 2010 Runtime Library
- Recommended 4GB or more RAM
- At least 500MB available disk space

## Technical Support

If you encounter issues, please refer to:

- `Doc/Download Tool User Guide V4.3.pdf` - Detailed user manual
- `Doc/Download Error Message Description.xlsx` - Error code descriptions

## Version History

- **R27.23.0101**: Current version, supports UDX710/SC9600 platform

## Precautions

1. Do not disconnect the device connection during the download process
2. Ensure stable power supply to avoid power outages midway
3. Different versions of firmware may require corresponding versions of the download tool
4. It is recommended to back up NV data before first use

---

**Note**: This tool is for authorized factory production and R&D testing use only.