# 异步

Dart 的底层实现跟 JavaScript/Node.js 类似，是单线程且"天生"异步的，而对比 Node.js，Dart 标准库对异步的支持更加全面且统一。

Dart 通过`async`/`await`关键字声明异步代码，通过`dart:async`库的`Future`和`Stream`表示异步操作（的结果）。

## 核心概念

`async`用于声明异步函数，`await`用于调用异步函数，且`await`只能在异步函数中使用。

`Future`代表一个异步执行的操作(结果)，而`Stream`表示一连串异步操作（结果）。异步操作返回的可能是正常的值，也可能是错误。

一般情况下，`Future`和`Stream`只参与函数的声明，在复杂场景下才需要直接使用它们。

## 基础用法

将`async`关键字放置于函数体之前，函数就变为异步；在同步函数调用之前添加`await`即变为异步调用；

```dart
// 使用async声明异步函数
// 因为有类型推断，函数返回值可以不写，但不推荐
asyncHello() async {
  return 'hello'; // 结果将被封装在Futrue中，即实际返回类型是 Future<String>
}

// 使用await调用异步函数，注意main本身也是异步
main() async {
  var t = await asyncHello();
  print(t);
}
```

和同步调用一样，`async`/`await`也是使用`try`、`catch`和`finally`进行错误处理

```dart
try {
  var result = await asyncFn();
} catch (e) {
  // 错误处理
}
```

## 进阶使用

// TODO:

## 实例

// TODO: