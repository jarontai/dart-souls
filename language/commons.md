# 常用内置类

除了[2.1节](/language/basics.md)介绍的基本类型，Dart的核心库内置很多常用类（类型）。

## 集合

常用的集合类型有：`List`，`Map` 和 `Set`。

### List

`List`就是其他语言中常见的数组（array），可以使用字面量（`[a1, a2]的形式`）或构造函数创建

```dart
var gameArray = ['Halo', 'Gears of War']; // 字面量形式

var gameList = new List(); // 使用构造函数
gameList.add('The Witcher'); // 使用add方法添加数据
gameList.add('Dark Souls');
```

### Map

### Set

## 日期/时间

日期与时间运算主要涉及两个类：`DateTime` 和 `Duration`。

### DateTime

### Duration

## 正则表达式

### RegExp



## 异常处理

异常处理涉及两个类：`Exception` 和 `Error`。

### Exception

Exception类表示程序执行过程中的异常，它们如果没有被捕获，应用通常会挂起并中止执行。

异常抛出使用`throw`，捕获使用`try`

```

```

### Erro



