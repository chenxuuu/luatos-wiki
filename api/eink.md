# eink - 墨水屏操作库

> 本页文档由[这个文件](https://gitee.com/openLuat/LuatOS/tree/master/luat/packages/eink/luat_lib_eink.c)自动生成。如有错误，请提交issue或帮忙修改后pr，谢谢！

## eink.setup(full, spiid)

初始化eink

**参数**

|传入值类型|解释|
|-|-|
|int|全屏刷新1,局部刷新0,默认是全屏刷新|
|int|所在的spi,默认是0|

**返回值**

|返回值类型|解释|
|-|-|
|boolean|成功返回true,否则返回false|

**例子**

无

---

## eink.clear()

清除绘图缓冲区

**参数**

无

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值,不会马上刷新到设备|

**例子**

无

---

## eink.setWin(width, height, rotate)

设置窗口

**参数**

|传入值类型|解释|
|-|-|
|int|width  宽度|
|int|height 高度|
|int|rotate 显示方向,0/1/2/3, 相当于旋转0度/90度/180度/270度|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---

## eink.getWin()

获取窗口信息

**参数**

无

**返回值**

|返回值类型|解释|
|-|-|
|int|width  宽|
|int|height 高|
|int|rotate 旋转方向|

**例子**

无

---

## eink.print(x, y, str, colored, font)

绘制字符串

**参数**

|传入值类型|解释|
|-|-|
|int|x坐标|
|int|y坐标|
|string|字符串|
|int|默认是0|
|font|字体大小,默认12|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---

## eink.show(x, y)

将缓冲区图像输出到屏幕

**参数**

|传入值类型|解释|
|-|-|
|int|x 输出的x坐标,默认0|
|int|y 输出的y坐标,默认0|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---

## eink.line(x, y, x2, y2, colored)

缓冲区绘制线

**参数**

|传入值类型|解释|
|-|-|
|int|起点x坐标|
|int|起点y坐标|
|int|终点x坐标|
|int|终点y坐标|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

```lua
eink.line(0, 0, 10, 20, 0)

```

---

## eink.rect(x, y, x2, y2, colored, fill)

缓冲区绘制矩形

**参数**

|传入值类型|解释|
|-|-|
|int|左上顶点x坐标|
|int|左上顶点y坐标|
|int|右下顶点x坐标|
|int|右下顶点y坐标|
|int|默认是0|
|int|是否填充,默认是0,不填充|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

```lua
eink.rect(0, 0, 10, 20)
eink.rect(0, 0, 10, 20, 1) -- Filled

```

---

## eink.circle(x, y, radius, colored, fill)

缓冲区绘制圆形

**参数**

|传入值类型|解释|
|-|-|
|int|圆心x坐标|
|int|圆心y坐标|
|int|半径|
|int|默认是0|
|int|是否填充,默认是0,不填充|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

```lua
eink.circle(0, 0, 10)
eink.circle(0, 0, 10, 1, 1) -- Filled

```

---

## eink.qrcode(x, y, str, version)

缓冲区绘制QRCode

**参数**

|传入值类型|解释|
|-|-|
|int|x坐标|
|int|y坐标|
|string|二维码的内容|
|int|二维码版本号|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---

## eink.bat(x, y, bat)

缓冲区绘制电池

**参数**

|传入值类型|解释|
|-|-|
|int|x坐标|
|int|y坐标|
|int|电池电压,单位毫伏|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---

## eink.weather_icon(x, y, code)

缓冲区绘制天气图标

**参数**

|传入值类型|解释|
|-|-|
|int|x坐标|
|int|y坐标|
|int|天气代号|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---

## eink.model(m)

设置墨水屏驱动型号

**参数**

|传入值类型|解释|
|-|-|
|int|型号名称, 例如 eink.model(eink.MODEL_1in54_V2)|

**返回值**

|返回值类型|解释|
|-|-|
|nil|无返回值|

**例子**

无

---
