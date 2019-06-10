---
title: 根据月初日期获取月末日期 
author: 
  nick: Viola
  link: https://github.com/TangF
tags:
    - JavaScript
    - JS小技巧
---

#### 需求
根据月初，如`2019-06-01`算出月末的日期。

#### 实现逻辑
根据月初，拼接处下月月初的日期，如`2019-07-01`,然后减`1ms`得到上月月底最后一天。
```
var end = new Date(new Date(start)*1 -1);
```

#### 需要注意的点
IE浏览器下，`new Date(dateStr)`；`dateStr`的格式必须是 `yy/mm/dd 00:00:00`，否则会计算错误。