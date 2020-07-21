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

### animation
``` css
.heading-primary-main {
    animation-name: moveInLeft;
    animation-duration: 1s;
    animation-timing-function: ease-out;
    animation-iteration-count: 3;
    animation-delay: 1.5s;
}

@keyframes moveInLeft {
    0% {
        opacity: 0;
        transform: translate(-100px) rotate(0deg);
    }

    60% {
        transform: rotate(180deg);
    }

    80% {
        transform: translate(20px);
    }

    100% {
        opacity: 1;
        transform: translate(0);
    }
}
```
![](animation-sample.gif)