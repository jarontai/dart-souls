# 变量与基本类型

本节讲解 Dart 的变量与基本数据类型。

_\*示例代码使用了dart核心库的_`print`_函数，用于打印信息_

## 变量

变量用于存储数据，Dart 中"万物皆对象"，即变量存储的都是对象的引用，或者说它们都指向某个对象。

### 变量声明

有两种基本的变量声明方式，一是不指定类型，即使用`var`

```dart
// name变量存储一个内容为'bob'的字符串对象
var name = 'bob';
```

另一种是指定类型

```dart
// 显式指明类型，效果与第一种方式一样
String name = 'bob';
```

因为有类型推导，以上两种声明方式的效果实际是一样的。官方推荐在函数内的本地变量尽量使用`var`声明。

在变量类型并不明确的场景下，可以使用`dynamic`关键字，如下：

```dart
// dynamic变量可以进行任意类型的赋值以及变量和方法的访问
dynamic cache = 'bob';
cache = 123;
cache = new SomeClass();
cache.method();
print(cache.name);
```

注意：`dynamic`变量不会进行类型检查，它的类型安全完全由开发者自己负责!

### 默认值

显著区别于其他语言，无论什么类型的变量，在没有赋初始值的情况下，默认值为`null`

```dart
// 未指定类型的变量
var name;
// 指定为数字类型的变量
int age;

// 使用print函数打印，两个变量都为null
print(name); // null
print(age); // null
```

`null`也是对象，所以也可以理解为：未初始化的 Dart 变量都指向`null`对象。

### 作用域

Dart 使用词法作用域（也称为静态作用域），即变量的作用域在定义时确定。

作用域范围由变量所处代码块（大括号）的层级决定，层级越深，作用域越小，层级越浅，作用域越大。

不被任何代码块包含的变量通常称为顶层变量，它们的作用域最大

```dart
var top = 'top'; // 顶层变量，作用域最大

main() {
  var inMain = 'main';
  print(top); // top
  print(inMain); // main
  print(inFn); // 错误，无法访问
  print(inIf); // 错误，无法访问

  fn() {
    var inFn = 'fn';
    print(top); // top
    print(inMain); // main
    print(inFn); // fn
    print(inIf); // 错误，无法访问

    if (top) {
      var inIf = 'if'; // 最内层的变量，作用域最小
      print(top); // top
      print(inMain); // main
      print(inFn); // fn      
      print(inIf); // if
    }
  }
}
```

### final 与 const

如果变量内容不会改变，建议使用`final`或`const`替代`var`，或者搭配类型使用。

`final`表示变量只能被赋值一次；`const`表示变量是编译时常量，`const`变量默认为`final`变量。

需要注意的是，顶层`final`变量与[类变量](/language/class_i.md)在首次访问时才执行初始化

```dart
// 定义final变量并使用函数进行初始化
final name = getName();
// name = 'john'; // 错误，final变量不能再次赋值!

// 定义获取name的函数（下一节将对函数进行讲解）
String getName() {
  print('getName');
  return 'bob';
}

// 常量
const pi = 3.14;
// 由常量值计算得到的也是常量
const area = pi * 2 * 2;

main() {
  print(pi); // 3.14
  print(area); // 12.56
  print(name); // 先打印 getName，再打印 bob，即直到name变量被访问时getName函数才执行
}
```

---

## 基本数据类型

Dart 有三种基本数据类型：数字、字符串与布尔。基本数据类型一般通过字面量进行创建，如：1，'bob'，true 等。

### 数字

数字类型有两种，一种是整数`int`，另一种是双精度浮点数`double`。

`int`与`double`都继承自数字类型`num`，在需要同时支持整数与浮点数时可以使用`num`

```dart
int age = 28;
double percent = 0.23;
num price = 2.3;
```

数字对象具备多种数学计算相关的属性与方法

```dart
int size = 9;
// 是否偶数
print(size.isEven); // false
// 是否奇数
print(size.isOdd); // true
// 转换为6进制字符串
print(size.toRadixString(6)); // 13
......

double pi = 3.1415926;
// 向上取整
print(pi.ceil()); // 4
// 转成整形
print(pi.toInt()); // 3
// 转换为固定精度字符串
print(pi.toStringAsPrecision(2)); // 3.1
......
```

### 字符串

字符串是由单引号或双引号包裹的字符序列，它支持使用`${ 表达式 }`进行插值，当表达式为变量时可以省略`{}`

```dart
String name = 'bob';
String message = 'Hi ${name.toUpperCase()}'; // Hi BOB
String text = 'Welcome $name'; // Welcome bob
```

连接多个字符串可以使用`+`，而多个相邻的字符串也会自动连接在一起，多行字符串则使用`'''`或`"""`创建

```dart
// 连接字符串
String message1 = 'Hello' + ' World'; // Hello World

// 相邻字符串会自动连接
String message2 = 'Hello'
                 ' World'; // Hello World

// 使用'''创建多行字符串
String multiMessage = '''
Hello
again!
'''; // Hello
     // again!
```

字符串对象自带多种实用属性与方法

```dart
String name = 'bob';
// 长度
print(name.length); // 3
// 是否为空
print(name.isEmpty); // false
// 子字符串
print(name.substring(1)); // ob
// 是否以某字符开头
print(name.startsWith('b')); // true
// 替换所有
print(name.replaceAll('b', 'w')); // wow
......
```

### 布尔

布尔类型只包含两个对象，`true`和`false`。

有别于很多动态语言，Dart 中的`true`是唯一“正确”的值，所有非`true`的值都被视为`false`

```dart
// 以下Dart代码也是合法的JavaScript代码，但执行结果完全不同
var name = 'bob';
if (name) {
  // 在JavaScript中，name被视为true，此处代码会执行
  // 在Dart中，name被视为false，此处代码不会执行
  var message = 'Hi ' + name;
  ......
}
```



