---
title: SASS語法
date: 2020-07-29 14:43:43
tags: [css,sass]
---
## 變數
```scss
$color-primary: red;
.color { 
  background-color: $color-primary
}
```
## ＠mixin
以 @mixin 開頭定義是可以重複使用的功能，可以在名稱後面加 () 放入參數做進階的使用
```scss
$color-primary: #f9ed69;
@mixin example {
  &::after {
    content: '';
    background-color: $color-primary;
    display: block;
  }
}
nav {
	@include example;
	margin: 30px;
	background-color: $color-primary;
}

// 搭配變數 random
$hotImage: sport live chess lottery slot fish;
@mixin hot-image {
  @each $img in $hotImage {
    .hotgame-#{$img} {
      height: 7rem;
      background: url('./assets/hot-#{$img}.png') no-repeat;
      background-size: 100% 100%;
      margin-top: 0.5rem;
    }
  }
}
```
## extend
主要是拿來合併相同程式碼用的
```scss
%title {
	font-size:18px;
	line-height:1.8;
}
.nav {
  @extend title;
}
.content {
  @extend title;
}
```