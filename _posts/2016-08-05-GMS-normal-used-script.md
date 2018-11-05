---
layout: post
title: GMS:一些常用脚本
excerpt: "禁用双击、和手机设备的倾斜判断脚本"
category: GMS
comments: false
tag:
- GMS
- 脚本语言
---

## GMS:一些常用脚本

### 禁用双击
脚本如下：

```php
device_mouse_dbclick_enable(false);
```

### 手机倾斜判断

脚本如下：

```lua
if (os_type == os_ios or os_type == os_android)
{
    turn_device =  device_get_tilt_x();    //return value (-1,1);
    if turn_device <-0.2
    {
        obj_character_nomal.hspeed = 10 + turn_device*10;
        obj_character_nomal.image_xscale = 1;
    }else if turn_device > 0.2 {    
        obj_character_nomal.hspeed = -10 - turn_device*10;
        obj_character_nomal.image_xscale = -1;
    }
}
```

