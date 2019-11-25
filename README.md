# SHT3X

## 1、介绍

这是一个在RT-Thread上，SHT3X系列温湿度传感器的驱动。实现了温湿度的单次查询(single-shot)读取，并支持`Finsh/MSH`测试命令。
本驱动编程实现方便读取多个SHT3X传感器。地址IO的控制和数据的滤波留给用户自行编程处理。

### 1.1 目录结构

| 名称 | 说明 |
| ---- | ---- |
| docs  | 文档目录 |
| docs/datasheets  | 数据手册目录 |
| docs/api.md  | 应用编程接口说明 |
| docs/version.md  | 版本说明 |
| sht3x.h  | 头文件 |
| sht3x.c  | 源代码 |
| SConscript | RT-Thread 默认的构建脚本 |
| README.md | 软件包使用说明 |

### 1.2 许可证

SHT3x package 遵循 `LGPLv2.1` 许可，详见 `LICENSE` 文件。

### 1.3 依赖

依赖 `RT-Thread I2C` 设备驱动框架。

## 2、如何获取软件包

使用 sht3x package 需要在 RT-Thread 的包管理器中选择它，具体路径如下：

```
RT-Thread online packages
    peripheral libraries and drivers  --->
        [*] sht3x: digital humidity and temperature sensor sht3x driver library
```

然后让 RT-Thread 的包管理器自动更新，或者使用 `pkgs --update` 命令更新包到 BSP 中。

## 3、使用 sht3x

本驱动实现基于RT-Thread的I2C设备驱动框架，在打开 sht3x package 后，请务必打开至少1个I2C设备。

* 完整的 API 手册可以访问这个[链接](docs/api.md)
* 更多文档位于 [`/docs`](/docs) 下，使用前 **务必查看**

## 4、注意事项

- 请注意SHT3X芯片的地址引脚默认是上拉还是下拉电阻。上拉对应地址0x45，下拉对应地址0x44。

## 5、联系方式 & 感谢

* 维护：hao.dong
* 邮箱：hao.dong.nanjing@outlook.com
* 主页：https://github.com/donghao2nanjing/sht3x
