# SHT3x API

## 单次读出温湿度

`rt_err_t sht3x_read_singleshot(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 软件复位

`rt_err_t sht3x_softreset(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 状态寄存器清零

`rt_err_t sht3x_clear_status(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 读取状态寄存器

`rt_err_t sht3x_read_status(sht3x_device_t dev)`
读取的状态寄存器的值存储在SHT3x设备结构体内的sht3x_status联合体中。

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 使能heater

`rt_err_t sht3x_enable_heater(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 关闭heater

`rt_err_t sht3x_disable_heater(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 加速响应时间

`rt_err_t sht3x_acc_resp_time(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 跳出连续读出模式

`rt_err_t sht3x_break(sht3x_device_t dev)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`dev`              | SHT3x设备结构体指针                 |
| **返回**          | **描述**                            |
|RT_EOK             | 正确执行                            |
|-RT_ERROR          | 失败                                |


## 初始化SHT3x设备

`sht3x_device_t sht3x_init(const char *i2c_bus_name, rt_uint8_t sht3x_addr)`

| 参数              | 描述                                |
|:------------------|:------------------------------------|
|`i2c_bus_name`     | i2c设备名称                         |
|`sht3x_addr`       | SHT3x的i2c地址                      |
| **返回**          | **描述**                            |
|SHT3x设备地址      | 指向SHT3x设备结构体的指针           |
|RT_NULL            | SHT3x初始化失败，返回空指针         |


## sht3x MSH命令

`void sht3x(int argc, char *argv[])`

- sht3x probe <i2c_dev_name> <pu/pd>  --挂载SHT3x设备，需要指定i2c设备名称和上下拉方式，默认下拉
- sht3x read --阅读SHT3x温湿度
- sht3x status --读取查看状态寄存器值
- sht3x reset --软件复位SHT3x
- sht3x heater <on/off> --开/关heater

MSH用例:
```
msh >sht3x
Usage:
        sht3x probe <i2c dev name> <pu/pd> -- probe sensor by i2c dev name and pull config
        sht3x read -- read sensor sht3x data
        sht3x status -- status register of sht3x
        sht3x reset -- send soft reset command to sht3x
        sht3x heater <on/off> -- turn on/off heater of sht3x

msh>sht3x probe i2c1
sht3x probed, addr:0x44

msh >sht3x heater on
sht3x heater cmd sent

msh >sht3x status
sht3x status:
        checksum:       0       - 0 means checksum correct
        command:        0       - 0 means last cmd executed OK
        reset deteced:  0
        alert pending:  0
        T track alert:  0
        RH track alert: 0
        heater enabled: 1

msh >sht3x heater off
sht3x heater cmd sent

msh >sht3x status
sht3x status:
        checksum:       0       - 0 means checksum correct
        command:        0       - 0 means last cmd executed OK
        reset deteced:  0
        alert pending:  0
        T track alert:  0
        RH track alert: 0
        heater enabled: 0

msh >sht3x read
sht3x humidity   : 39.9
sht3x temperature: 24.5

```
