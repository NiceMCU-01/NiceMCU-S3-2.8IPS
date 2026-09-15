# NiceMCU-S3-2.8IPS

NiceMCU-S3-2.8IPS 开发板的小智 AI 固件工程，基于 ESP32-S3（16 MB Flash / 8 MB Octal PSRAM）和 2.8 英寸 ST7789 屏幕。

## 克隆项目

```bash
git clone --recurse-submodules https://github.com/NiceMCU-01/NiceMCU-S3-2.8IPS.git
cd NiceMCU-S3-2.8IPS
```

如果已经克隆主仓库，但没有拉取子模块：

```bash
git submodule update --init --recursive 
```

也可以仅克隆固件仓库：

```bash
git clone --recurse-submodules https://github.com/NiceMCU-01/xiaozhi-esp32.git
```

## 编译

推荐安装 **ESP-IDF v6.0.2** 及 ESP32-S3 工具链。以下以 Linux 为例，替换 ESP-IDF 环境脚本路径：

```bash
source /path/to/esp-idf/export.sh
idf.py --version
cd xiaozhi-esp32
python3 scripts/build.py nicemcu-s3-2.8ips --name nicemcu-s3-2.8ips
```

构建脚本会自动选择 `esp32s3` 芯片和 `nicemcu-s3-2.8ips` 板型，无需先手动选择开发板。注意：脚本会重新生成本地 `sdkconfig`，自定义配置请先备份。

构建成功后，应用固件位于 `xiaozhi-esp32/build/xiaozhi.bin`，合并烧录固件位于 `xiaozhi-esp32/build/merged-binary.bin`。构建命令末尾添加 `--zip` 可额外生成 `releases/` 下的发布包。

## 烧录与串口监视

在 `xiaozhi-esp32` 目录及已加载的 ESP-IDF 环境中执行，将串口替换为实际设备：

```bash
idf.py -p /dev/ttyACM0 flash monitor
```

按 `Ctrl+]` 退出串口监视器。

板卡引脚及硬件说明见 [板级 README](xiaozhi-esp32/main/boards/nicemcu-s3-2.8ips/README.md)，更多项目说明见 [小智中文文档](xiaozhi-esp32/README_zh.md)。