# pm - 电源管理

> 本页文档由[这个文件](https://gitee.com/openLuat/LuatOS/tree/master/luat/modules/luat_lib_pm.c)自动生成。如有错误，请提交issue或帮忙修改后pr，谢谢！

## pm.request(mode)

请求进入指定的休眠模式

**参数**

|传入值类型|解释|
|-|-|
|int|休眠模式,例如pm.IDLE/LIGHT/DEEP/HIB|

**返回值**

|返回值类型|解释|
|-|-|
|boolean|处理结果,即使返回成功,也不一定会进入, 也不会马上进入|

**例子**

```lua
-- 请求进入休眠模式
pm.request(pm.HIB)

```

---

## pm.dtimerStart(id, timeout)

启动底层定时器,在休眠模式下依然生效. 只触发一次

**参数**

|传入值类型|解释|
|-|-|
|int|定时器id,通常是0-3|
|int|定时时长,单位毫秒|

**返回值**

|返回值类型|解释|
|-|-|
|boolean|处理结果|

**例子**

```lua
-- 添加底层定时器
pm.dtimerStart(0, 300 * 1000) -- 5分钟后唤醒

```

---

## pm.dtimerStop(id)

关闭底层定时器

**参数**

|传入值类型|解释|
|-|-|
|int|定时器id|

**返回值**

无

**例子**

```lua
-- 关闭底层定时器
pm.dtimerStop(0) -- 关闭id=0的底层定时器

```

---

## pm.dtimerCheck(id)

检查底层定时器是不是在运行

**参数**

|传入值类型|解释|
|-|-|
|int|定时器id|

**返回值**

|返回值类型|解释|
|-|-|
|boolean|处理结果,true还在运行，false不在运行|

**例子**

```lua
-- 检查底层定时器是不是在运行
pm.dtimerCheck(0) -- 检查id=0的底层定时器

```

---

## pm.lastReson()

开机原因,用于判断是从休眠模块开机,还是电源/复位开机

**参数**

无

**返回值**

|返回值类型|解释|
|-|-|
|int|0-上电开机, RTC开机, WakeupIn/Pad开机|
|int|0-普通开机(上电/复位),3-深睡眠开机,4-休眠开机|

**例子**

```lua
-- 是哪种方式开机呢
log.info("pm", "last power reson", pm.lastReson())

```

---

## pm.force(mode)

强制进入指定的休眠模式

**参数**

|传入值类型|解释|
|-|-|
|int|休眠模式,仅pm.DEEP/HIB|

**返回值**

|返回值类型|解释|
|-|-|
|boolean|处理结果,若返回成功,大概率会马上进入该休眠模式|

**例子**

```lua
-- 请求进入休眠模式
pm.force(pm.HIB)

```

---

## pm.check()

检查休眠状态

**参数**

无

**返回值**

|返回值类型|解释|
|-|-|
|boolean|处理结果,如果能顺利进入休眠,返回true,否则返回false|
|int|底层返回值,0代表能进入最底层休眠,其他值代表最低可休眠级别|

**例子**

```lua
-- 请求进入休眠模式,然后检查是否能真的休眠
pm.request(pm.HIB)
if pm.check() then
    log.info("pm", "it is ok to hib")
else
    pm.force(pm.HIB) -- 强制休眠
end

```

---

