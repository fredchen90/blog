---
title: CSS筆記
date: 2020-07-20 21:00:26
tags: css
---
### default
``` css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
### clip-path
透過剪裁方式改變形狀,以(x,y)方式來裁切.
``` css
.polygon {
    clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%);
}
```
![](clip-path.png)