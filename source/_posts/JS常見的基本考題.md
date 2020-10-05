---
title: JS常見的基本考題
date: 2020-09-30 22:48:20
tags: 基本考題
---

### this 概念

> 這題觀念在於 this 作用域範圍
>
> 第一個印出來的 this 範圍在 obj 裡, 因為是執行了函式
>
> 第二個印出來的 this 範圍是 window, 原因在於 test 是被 assign 一個函式,看底下可以知道此作用域範圍已不在 obj 裡, 所以會印出最外層的 fullname

```javascript
ƒ () {
      return this.fullname;
    }
```

```javascript
var fullname = 'John';
var obj = {
  fullname: 'Marry',
  prop: {
    fullname: 'Fred',
    getFullname: function() {
      return this.fullname;
    },
  },
};
console.log(obj.prop.getFullname()); //Fred
var test = obj.prop.getFullname;
console.log(test()); // John
```

### Call By Value vs Call By Sharing

>  傳值與共享(有 call by reference 記憶體的概念)的概念

```javascript
var a = {
  a1: 5,
  a2: [1, 2, 3],
};
var b = a.a1;
var c = a.a2;
a.a1 = 6;
a.a2[0] = 4;

console.log(b); //5
console.log(c); //[4,2,3]
```

### hoisting 概念

> 觀念在於變數的宣告被「提升」到最上面去了
>
> 第一題與第二題很容易搞混,特地寫在一起

```javascript
// 第一種
myName = 'Fred';
function getName() {
  console.log(myName); //undefined
  var myName = 'Chen';
  console.log(myName); //Chen
}
getName();

// 第二種
myName = 'Fred';
function getName() {
  console.log(myName); //Fred
  myName = 'Chen';
  console.log(myName); //Chen
}
getName();
```

### function 執行

> 顧名思義考你瞭不瞭解 function 執行,
>
> 如果 this.name(); 改成 this.name; 那就不會執行了

```javascript
var obj = function(msg) {
  this.msg = msg;

  this.name = function() {
    console.log('name: ', this.msg);
  };

  this.waitAndShot = function() {
    setTimeout(() => {
      this.name();
    }, 2000);
  };
};

var myName = new obj('Fred');
myName.waitAndShot(); // 兩秒後印 name: Fred
```

### 閉包

> 將變數生命週期延續在內層

```javascript
function myFunc() {
  return {
    count: 0,
    getCount: function() {
      this.count++;
      console.log(this.count);
    },
  };
}

var obj = myFunc();
obj.getCount(); // 1
obj.getCount(); // 2
obj.getCount(); // 3
```

### 立即函式

> 只會執行一次,不會影響全域

```javascript
// var a = b =3;
// 實際上是長這樣
// b = 3;
// var a = b;
// 因為 b 不是用 var 宣告, 所以就變成全域變數
(function() {
  var a = (b = 3);
})();
console.log('a defined?' + (typeof a !== 'undefined')); // a is not defined
console.log('b defined?' + (typeof b !== 'undefined')); // b is 3
```

### 字串運算子

> 運算子遇到字串就會自動轉成字串串接

```javascript
console.log('3' + 4 + 5); //'345'
console.log(3 + 4 + '5'); //'75'
```

### ++運算元

> ++在前面代表回傳運算完的值, 反之++在後就是回傳加前的值

```javascript
function cal(init) {
  var counter = init;
  return function() {
    return counter++;
  };
}

var myCal1 = cal(5);
var myCal2 = cal(105);
console.log(myCal1()); //5
console.log(myCal2()); //105
console.log(myCal1()); //6
console.log(myCal2()); //106
```
