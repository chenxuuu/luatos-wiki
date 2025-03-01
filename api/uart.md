# uart - 串口操作库

> 本页文档由[这个文件](https://gitee.com/openLuat/LuatOS/tree/master/luat/modules/luat_lib_uart.c)自动生成。如有错误，请提交issue或帮忙修改后pr，谢谢！

## uart.setup(id, baud_rate, data_bits, stop_bits, partiy, bit_order, buff_size)

配置串口参数

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1, 如此类推, 最大值取决于设备|
|int|波特率, 默认115200，可选择波特率表:{2000000,921600,460800,230400,115200,57600,38400,19200,9600,4800,2400}|
|int|数据位，默认为8|
|int|停止位，默认为1|
|int|校验位，可选 uart.None/uart.Even/uart.Odd|
|int|大小端，默认小端 uart.LSB, 可选 uart.MSB|
|int|缓冲区大小，默认值1024|
|int|485模式下的转换GPIO, 默认值0xffffffff|
|int|485模式下的rx方向GPIO的电平, 默认值0|
|int|485模式下tx向rx转换的延迟时间，默认值12bit的时间，单位us|

**返回值**

|返回值类型|解释|
|-|-|
|int|成功返回0,失败返回其他值|

**例子**

```lua
-- 最常用115200 8N1
uart.setup(1, 115200, 8, 1, uart.NONE)
-- 可以简写为 uart.setup(1)

```

---

## uart.write(id, data)

写串口

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|
|string/zbuff|待写入的数据，如果是zbuff会从指针起始位置开始读|
|int|可选，要发送的数据长度，默认全发|

**返回值**

|返回值类型|解释|
|-|-|
|int|成功的数据长度|

**例子**

```lua
uart.write(1, "rdy\r\n")

```

---

## uart.tx(id, buff, start, len)

buff形式写串口,等同于c语言uart_tx(uart_id, &buff[start], len);

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|
|zbuff|待写入的数据，如果是zbuff会从指针起始位置开始读|
|int|可选，要发送的数据起始位置，默认为0|
|int|可选，要发送的数据长度，默认为zbuff内有效数据，最大值不超过zbuff的最大空间|

**返回值**

|返回值类型|解释|
|-|-|
|int|成功的数据长度|

**例子**

```lua
uart.tx(1, buf)

```

---

## uart.read(id, len)

读串口

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|
|int|读取长度|
|file/zbuff|可选：文件句柄或zbuff对象|

**返回值**

|返回值类型|解释|
|-|-|
|string|读取到的数据 / 传入zbuff时，返回读到的长度，并把zbuff指针后移|

**例子**

```lua
uart.read(1, 16)

```

---

## uart.read(id, buff)

buff形式读串口，一次读出全部数据存入buff中，如果buff空间不够会自动扩展，目前只有air105支持这个操作

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|
|zbuff|zbuff对象|
|return|返回读到的长度，并把zbuff指针后移|

**返回值**

无

**例子**

```lua
uart.read(1, buff)

```

---

## uart.rx_size(id)

读串口Rx缓存中剩余数据量，目前只有air105支持这个操作

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|
|return|返回读到的长度|

**返回值**

无

**例子**

```lua
local size = uart.rx_size(1)

```

---

## uart.close(id)

关闭串口

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

```lua
uart.close(1)

```

---

## uart.on(id, event, func)

注册串口事件回调

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|
|string|事件名称|
|function|回调方法|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

```lua
uart.on(1, "receive", function(id, len)
    local data = uart.read(id, len)
    log.info("uart", id, len, data)
end)

```

---

## uart.wait485(id)

等待485模式下TX完成，mcu不支持串口发送移位寄存器空或者类似中断时才需要，在sent事件回调后使用

**参数**

|传入值类型|解释|
|-|-|
|int|串口id, uart0写0, uart1写1|

**返回值**

|返回值类型|解释|
|-|-|
|int|等待了多少次循环才等到tx完成，用于粗劣的观察delay时间是否足够，返回不为0说明还需要放大delay|

**例子**

无

---

