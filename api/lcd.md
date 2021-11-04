# lcd - lcd驱动模块

> 本页文档由[这个文件](https://gitee.com/openLuat/LuatOS/tree/master/luat/../components/lcd/luat_lib_lcd.c)自动生成。如有错误，请提交issue或帮忙修改后pr，谢谢！

## lcd.init(tp, args)

lcd显示屏初始化

**参数**

|传入值类型|解释|
|-|-|
|string|lcd类型, 当前支持st7789/st7735/st7735s/gc9a01/gc9106l/gc9306/ili9341/custom|
|table|附加参数,与具体设备有关,pin_pwr为可选项,可不设置|

**返回值**

无

**例子**

无

---

## lcd.close()

关闭lcd显示屏

**参数**

无

**返回值**

无

**例子**

```lua
-- 关闭lcd
lcd.close()

```

---

## lcd.on()

开启lcd显示屏背光

**参数**

无

**返回值**

无

**例子**

```lua
-- 开启lcd显示屏背光
lcd.on()

```

---

## lcd.off()

关闭lcd显示屏背光

**参数**

无

**返回值**

无

**例子**

```lua
-- 关闭lcd显示屏背光
lcd.off()

```

---

## lcd.sleep()

lcd睡眠

**参数**

无

**返回值**

无

**例子**

```lua
-- lcd睡眠
lcd.sleep()

```

---

## lcd.wakeup()

lcd唤醒

**参数**

无

**返回值**

无

**例子**

```lua
-- lcd唤醒
lcd.wakeup()

```

---

## lcd.setColor(back,fore)

lcd颜色设置

**参数**

|传入值类型|解释|
|-|-|
|int|背景色|
|int|前景色|

**返回值**

无

**例子**

```lua
-- lcd颜色设置
lcd.setColor(0xFFFF,0x0000)

```

---

## lcd.draw(x1, y1, x2, y2,color)

lcd颜色填充

**参数**

|传入值类型|解释|
|-|-|
|int|左上边缘的X位置.|
|int|左上边缘的Y位置.|
|int|右上边缘的X位置.|
|int|右上边缘的Y位置.|
|string|字符串或zbuff对象|

**返回值**

无

**例子**

```lua
-- lcd颜色填充
buff:writeInt32(0x001F)
lcd.draw(20,30,220,30,buff)

```

---

## lcd.clear(color)

lcd清屏

**参数**

|传入值类型|解释|
|-|-|
|int|屏幕颜色 可选参数,默认背景色|

**返回值**

无

**例子**

```lua
-- lcd清屏
lcd.clear()

```

---

## lcd.drawPoint(x0,y0,color)

画一个点.

**参数**

|传入值类型|解释|
|-|-|
|int|点的X位置.|
|int|点的Y位置.|
|int|绘画颜色 可选参数,默认前景色|

**返回值**

无

**例子**

```lua
lcd.drawPoint(20,30,0x001F)

```

---

## lcd.drawLine(x0,y0,x1,y1,color)

在两点之间画一条线.

**参数**

|传入值类型|解释|
|-|-|
|int|第一个点的X位置.|
|int|第一个点的Y位置.|
|int|第二个点的X位置.|
|int|第二个点的Y位置.|
|int|绘画颜色 可选参数,默认前景色|

**返回值**

无

**例子**

```lua
lcd.drawLine(20,30,220,30,0x001F)

```

---

## lcd.drawRectangle(x0,y0,x1,y1,color)

从x / y位置（左上边缘）开始绘制一个框

**参数**

|传入值类型|解释|
|-|-|
|int|左上边缘的X位置.|
|int|左上边缘的Y位置.|
|int|右下边缘的X位置.|
|int|右下边缘的Y位置.|
|int|绘画颜色 可选参数,默认前景色|

**返回值**

无

**例子**

```lua
lcd.drawRectangle(20,40,220,80,0x001F)

```

---

## lcd.drawCircle(x0,y0,r,color)

从x / y位置（圆心）开始绘制一个圆

**参数**

|传入值类型|解释|
|-|-|
|int|圆心的X位置.|
|int|圆心的Y位置.|
|int|半径.|
|int|绘画颜色 可选参数,默认前景色|

**返回值**

无

**例子**

```lua
lcd.drawCircle(120,120,20,0x001F)

```

---

## lcd.setFont(font)

设置字体

**参数**

|传入值类型|解释|
|-|-|
|string|font|

**返回值**

无

**例子**

```lua
-- 设置为中文字体,对之后的drawStr有效,使用中文字体需在luat_conf_bsp.h.h开启#define USE_U8G2_OPPOSANSM12_CHINESE
lcd.setFont(lcd.font_opposansm12)
lcd.drawStr(40,10,"drawStr")
sys.wait(2000)
lcd.setFont(lcd.font_opposansm12_chinese)
lcd.drawStr(40,40,"drawStr测试")

```

---

## lcd.drawStr(x,y,str,fg_color,bg_color)

显示字符串

**参数**

|传入值类型|解释|
|-|-|
|int|x 横坐标|
|int|y 竖坐标|
|string|str 文件内容|
|int|fg_color str颜色|
|int|bg_color str背景颜色|

**返回值**

无

**例子**

```lua
-- 显示之前先设置为中文字体,对之后的drawStr有效,使用中文字体需在luat_conf_bsp.h.h开启#define USE_U8G2_WQY16_T_GB2312
lcd.setFont(lcd.font_ncenB12_tr)
lcd.drawStr(40,10,"drawStr")
sys.wait(2000)
lcd.setFont(lcd.font_wqy16_t_gb2312)
lcd.drawStr(40,40,"drawStr测试")

```

---
