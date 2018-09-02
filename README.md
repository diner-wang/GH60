# GH60(OK60RGB)刷固件（macOS）

## PCB型号

在淘宝店铺[YMDK](https://shop111633771.taobao.com/?spm=2013.1.1000126.2.75a85b46iGHy6M)购买的GH60，OK60RGB的PCB。

## 环境准备
### 软件安装

用brew安装dfu-programmer和crosspack-avr。

前者用于 build firmware，后者用于刷入键盘。

```bash
brew install dfu-programmer
brew install Caskroom/cask/crosspack-avr
```

### 进入dfu模式

按PCB板背面开关即可进入dfu模式刷写固件。

运行命令

```bash
system_profiler SPUSBDataType
```

可查看到如下输出，则已进入dfu模式

```bash
ATm32U4DFU:
 
          Product ID: 0x2ff4
          Vendor ID: 0x03eb  (Atmel Corporation)
          Version: 0.00
          Serial Number: 1.0.0
          Speed: Up to 12 Mb/sec
          Manufacturer: ATMEL
          Location ID: 0x14500000 / 60
          Current Available (mA): 500
          Extra Operating Current (mA): 0
          Built-In: Yes
```

## 配置键位
打开[https://kbfirmware.com/](https://kbfirmware.com/)，选择S60-X_RGB-generic，配置相应配列，并下载hex文件。

![下载hex文件](https://github.com/diner-wang/GH60/blob/master/picture/pic1.png)

## 刷写固件

```bash
dfu-programmer atmega32u4 erase --force
dfu-programmer atmega32u4 flash gh60.hex
dfu-programmer atmega32u4 reset
```

