---
title: RWD筆記
date: 2020-09-15 22:10:57
tags: rwd css
---
### 斷點規劃範例
+ PC - 1200px
+ iPad - 768px
+ iPad以下 - 767px
+ iphone 6 Plus - 414px
+ iphone 6 - 375px
+ iphone 5、SE - 320px

### max-width 設計理念
<font size=2>通常會在最上層給 max-width 在子層使用%方式達到自適應延伸.</font>
``` css
.wrap {
    max-width: 1200px;
    .menu {
        width: 35%;
    }
    .content {
        width: 65%;
    }
}
```

### float版面基礎設計
<font size=2>簡單的左右區塊排版設計</font>
``` css
.wrap {
  width: 600px;
}
.menu {
  width: 25%;
  background-color: LIME;
  float: left;
}
.content {
  width: 60%;
  background-color: LIGHTSALMON;
  margin-left: 150px;
}
```
<img src="float.png" width="35%">
<font size=2> rwd 左右區塊排版設計</font>
``` css
@media(max-width: 768px) {
  .menu {
    width: 100%;
    float: none; 
  }
  .content {
    margin-left: 0;
  }
}
```
<img src="float_none.png" width="35%">