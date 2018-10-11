---
title: 'JavaScript高级程序设计笔记（一）'
date: 2018/10/11 14:52:25
tags: 《JavaScript高级程序设计》笔记
---

# 一、引用类型

---

## 1、indexOf()，全等运算符（===）

<!--more-->

```
var person = {
    name: "Nicholas"
};
var people = [{
    name: "Nicholas"
}];
var morePeople = [person];
alert(people.indexOf(person)); //-1
alert(morePeople.indexOf(person)); //0
```

### 因为 `indexOf()` 会执行 `===` 操作，全等操作符会比较两个值的 `地址` ，所以以上返回 `-1`。

## 2、值传递，址传递（这一块可能还是理解的有问题，暂时这么理解吧，后面再来修改）

```
function sum(num1, num2) {
    return num1 + num2;
}
alert(sum(10, 10)); //20
var anotherSum = sum;
alert(anotherSum(10, 10)); //20
sum = null;
alert(anotherSum(10, 10)); //20
```

### 函数参数的传递都是值传递，引用类型的赋值都是址传递。`sum = null` 是`sum`被重新赋了新的地址，不是修改了原方法，所以 `anotherSum()`不受影响，还是指向之前的内存地址。
