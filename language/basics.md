# 变量与基本类型

先来认识Dart的变量和基本数据类型。

## 变量声明

有两种基本的变量声明方式，一种是不指定类型，即使用`var`（变量此时的类型为`dynamic`）

```dart
// name变量指向一个内容为'bob'的字符串对象
var name = 'bob';
```

另一种是指定类型

```dart
// 显式指明name变量为字符串类型
String name = 'bob';
```

指定或不指定类型，由开发者自己决定；指定类型将获得更好的开发体验，比如：更多更全面的代码提示。

变量存储的是对象的引用，即变量都指向某个对象（没有初始化的变量指向`null`对象）。

## 默认值

Dart的变量有一个显著区别于其他语言的特点，即无论什么类型的变量，在声明时如果没有赋值，默认值都是`null`

```dart
// 未指定类型的变量
var name;
// 指定为数字类型的变量
int age;
print(name); // 使用print函数打印，输出为null
print(age); // 使用print函数打印，输出也为null
```

## 作用域

Dart使用词法作用域（也称为静态作用域），即变量的作用域在其定义时就已经确定。

作用域由变量所处代码块（大括号）的层级决定，层次越深，作用域越小。

不被任何代码块包含的变量通常称为顶层变量，它们的作用域范围最大

```dart
var top = true; // 顶层变量

main() {
  var inMain = 'main';
  print(inMain); // OK
  print(top); // OK
  print(inFn); // 错误，无法访问
  print(inIf); // 错误，无法访问

  fn() {
    var inFn = 'fn';
    print(inFn); // OK
    print(inMain); // OK
    print(top); // OK
    print(inIf); // 错误，无法访问

    if (top) {
      var inIf = 'if';
      print(inIf); // OK
      print(inFn); // OK
      print(inMain); // OK
      print(top); // OK
    }
  }
}
```

## final与const

如果变量内容不会改变，建议使用`final`或`const`替代`var`，或者搭配类型使用。

`final`表示变量只能被赋值一次；`const`表示变量是编译时常量，`const`变量默认为`final`变量。

需要注意的是，顶层`final`变量与[类变量](/language/class_i.md)在首次访问时才执行初始化

```dart
// 下面的写法等同于 final String name = 'bob';
final name = initName();
// name = 'john'; // 错误，final变量不能再次赋值!

// 定义用于初始化name的函数（函数的知识点将在下一节讲解）
initName() {
  print('name init');
  return 'bob';
}

// 常量
const pi = 3.14;
// 由常量值计算得到的常量
const area = pi * 2 * 2;

main() {
  print(pi); // 3.14
  print(area); // 12.56
  print(name); // 先打印 name init，再打印 bob，即直到访问name时initName函数才执行
}
```

## 基本数据类型

基本数据类型有三种：数字、字符串与布尔。基本数据类型的对象一般都是通过字面量进行创建，如：1，'bob'，true 等。

### 数字

常用的数字类型有两种，一种是整数`int`

```dart
int age = 28;
```

另一种是双精度浮点数`double`

```dart
double percent = 0.23;
```

数字对象具有多种数学计算相关的属性与方法

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

`int`与`double`都继承数字类型`num`，在需要同时支持整数与浮点数时可以使用`num`。

### 字符串

字符串是由单引号或双引号包裹的字符序列，它支持使用`${ 表达式 }`进行插值，插值表达式为标识符时可以省略`{}`

```dart
String name = 'bob';
String message = 'Hi ${name.toUpperCase()}'; // Hi BOB
String text = 'Welcome $name'; // Welcome bob
```

使用`+`使连接多个字符串，多个相邻的字符串也会自动连接在一起；多行字符串则使用`'''`或`"""`来创建

```dart
// 相邻字符串自动连接
String message1 = 'Hi'
                 ' there'; // Hi there
// 使用+号连接                 
String message2 = 'Hi'
                 + ' there'; // Hi there
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

布尔类型只有两个对象，`true`和`false`。

`true`是唯一“正确”的值，所有非true的值都视为`false`

```dart
// 以下常见的JavaScript代码，在Dart中将失效
var name = 'bob';
// name被视为false，if的代码不会执行
if (name) {
  var message = 'hi' + name;
  ......
}
```



