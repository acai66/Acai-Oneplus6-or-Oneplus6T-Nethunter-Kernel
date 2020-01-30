# Acai-Oneplus6-or-Oneplus6T-Nethunter-kernel
[README](README.md) | [中文文档](README_zh.md)

适用于一加6的Nethunter内核

## 内核信息
- 版本: V1
- 内核版本: 4.9.212
- 支持系统: 氢安卓10，理论也支持氧10
- 编译链: Clang11

![内核版本](resources/images/version.jpg)

### 当前已完成功能
1. HID补丁
2. 帧注入补丁
3. 添加部分usb网卡驱动
4. rtl8812au驱动 (5Ghz wifi)
5. 以及其他可能正常工作的设备驱动，(例如Hackrf、usb蓝牙) 

### Bugs
1. 开机会弹窗 "您的设备内部出现了问题",直接忽略就好
2. 息屏手势失效

### TODO
1. 测试各种能
2. 尝试修复已知bug
3. 跟进内核源码更新

### 说明
1. 未在一加6t上测试，理论支持一加6t
2. 只测试了rtl8812au网卡，其余网卡未测试
3. 没有Hackrf、usb蓝牙设备，也未测试，如有测试可用的，请反馈
4. #### 如何安装?
请确保你的系统为官方安卓10，并且已刷入twrp与magisk，然后在recovery模式下刷入最新发布内核即可。
5. #### 如何加载内核模块？
使用`modprobe`命令加载内核模块，例如加载rtl8812au模块，运行`modprobe 88XXau`。
更多模块请参考`/system/lib/modules/`下有哪些ko文件。
6. #### 如何进行HID测试？
参考[`USB ARMY`](https://forum.xda-developers.com/oneplus-5/development/burgerhunter-t3638810)
例:
    以root身份在终端运行
    ```
    setprop sys.usb.config win,hid
    ```
    即可开启hid的支持
7. #### 如何切换网卡到监听模式？
在测试`rtl8812au`时，使用`airmon-ng start wlan1`打开监听模式总是有异常，经过搜索测试发现运行如下命令即可打开监听模式
```
ifconfig wlan1 down
iwconfig wlan1 mode monitor
ifconfig wlan1 up
```

![开启监听模式](resources/images/enable_monitor_mode.jpg)

### 致谢
- [simonpunk](https://forum.xda-developers.com/oneplus-5/development/burgerhunter-t3638810)、[johanlike(DJY)](https://github.com/johanlike) for HID补丁和wifi补丁
- [Boos4721](https://github.com/Boos4721/op6_kernel)的内核源码
- [osm0sis](https://github.com/osm0sis/AnyKernel3)的AntKernel3

