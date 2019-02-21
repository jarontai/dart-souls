# 运算符和流程控制

本节简述 Dart 的运算符、流程控制与异常处理。

## 运算符

以下列出了 Dart 的运算符，从高到低按照优先级排列：

| 描述 | 运算符 |
| :--- | :--- |
| 一元运算符（后置） | ++   --   \( \)   \[ \]   .   _** ?.**_ |
| 一元运算符（前置） | -   !   ~   ++   -- |
| 乘法运算符 | \*   /   %   **~/** |
| 加法运算符 | +   - |
| 移位运算符 | &lt;&lt;   &gt;&gt; |
| 按位与 | & |
| 按位异或 | ^ |
| 按位或 | \| |
| 关系与类型检测 | &gt;=   &gt;   &lt;=   &lt;   _**as   is   is!**_ |
| 逻辑与 | && |
| 逻辑或 | \|\| |
| 是否为null | _**??**_ |
| 条件运算符 | ? : |
| 级联运算符 | _**..**_ |
| 赋值运算符 | = \*= /= ~/= %= += -= &lt;&lt;= &gt;&gt;= &= ^= \|= _**??=**_ |

与其他类C语言比较，Dart 的运算符大同小异，这里只选出部分 Dart 特有的运算符（即上表中使用斜粗体的运算符）进行讲解:

| 运算符 | 介绍 | 示例 |
| :--- | :--- | :--- |
| ?. | 点符号前加问号，表示当前调用只在被访问者不为`null`的情况下才执行 | var upper = name?.toUpperCase\(\); |
| is  is! | 检查对象是否属于或不属于某种类型 | if \(name is String\) { ... } |
| as | 将对象转换为某类型，如果转换失败将抛出异常 | name as String |
| ?? | 空值检测，如：a1 ?? a2 ，表示如果a1不为`null`，则直接返回a1的值，否则返回a2的值 | var message = input ?? 'Hello'; |
| .. | 级联操作符，用于对同一对象执行一系列操作（链式操作），避免创建多余的临时变量 | 不使用级联：<br>person.name = 'bob';<br>person.age = 28; <br> <br>使用级联：<br> person..name = 'bob' <br> &nbsp;&nbsp; ..age = 28; |
| ??= | 空值判断赋值，只在左值为`null`的情况下才执行赋值操作 | message ??= 'Hello'; |

## 流程控制语句

跟操作符一样，Dart 的流程控制语句也跟主流语言类似，如下：

* if 、esle
* for 循环
* while、do-while 循环
* break、continue
* switch、case
* assert（断言）

有编程经验的开发者，对以上流程控制语句应该都不陌生，这里只对特殊的`assert`作简要说明：

`assert`语句接受一个布尔表达式，如果表达式的值为`false`，抛出assert异常，程序退出执行，表达式为`true`则正常执行。`assert`语句默认不开启，只在`--enable-asserts`选项开启时才生效，一般用于开发阶段的代码调试和验证。

## 异常

Dart的异常包含两种： `Exception`和`Error`。`Exception`表示程序逻辑执行失败，它们大都是可预料的，而且应该被捕获并进行处理。`Error`则表示程序发生了严重错误，它们大都不可预料且应该极力避免，通常是因为代码逻辑存在问题而导致。

如果你熟悉Java语言，请注意：Dart的异常都是`非检查异常`(unchecked exception)，即Dart不存在需要强制进行处理的异常。

### 异常抛出
使用`throw`来抛出异常，`throw`接受任意类型的数据，或者说任意可以转换为字符串的对象都可以被作为异常抛出。在正式项目中，不建议直接抛出字符串，而应该使用dart预定义或自定义的异常。

```dart
  throw 'Exception message'; // 直接抛出字符串信息
  throw FormatException('message'); // 抛出dart的格式化异常
  throw ArgumentError('message'); // 抛出dart的参数错误
  throw CustomException('message'); // 抛出自定义的异常
```

抛出的异常，如果没有被捕获，程序将退出执行并打印当前的堆栈信息，类似如下：

```dart
  Unhandled exception:
  Exception message
  #0      method (package:dart_test/exception_test.dart:2:5)
  #1      main (package:dart_test/exception_test.dart:6:3)
  #2      _startIsolate.<anonymous closure> (dart:isolate/runtime/libisolate_patch.dart:287:32)
  #3      _RawReceivePortImpl._handleMessage (dart:isolate/runtime/libisolate_patch.dart:171:12)
```

### 异常捕获

TODO: