# 变量与基本类型

## 变量

变量都是引用，它们都指向某个对象。

有两种基本的变量声明方式，一种是不指定类型，即使用var

```dart
var name = 'bob'; // name变量指向一个内容为'bob'的字符串对象
```

另一种是指定类型

```dart
String name = 'bob'; // 显式指明name为字符串
```

指定或不指定类型，由开发者自己决定；指定类型将获得更好的开发体验，比如：更多更全面的代码提示。

## 默认值

Dart是纯面向对象的，变量声明时如果没有赋值，其默认值为 null

```dart
var name;
print(name); // 使用print函数打印，输出为null
```

## final与const

如果变量内容不会改变，鼓励使用final或const。

final表示变量只能被赋值一次；const表示变量是编译时常量，const变量默认为final变量。

```dart
final name = 'bob'; // 也可以这样写：final String name = 'bob';
name = 'john'; // 再次赋值将报错!

const pi = 3.14;
const area = pi * 2 * 2; // 由常量值计算得到的常量
```

## 基本数据类型

### 数字

数字类型有两种，一种是整数 int

```dart
int age = 28;
```

另一种是双精度浮点数 double

```dart
double percent = 0.23;
```

数字对象具有多种数学计算相关的属性与方法

```dart
int size = 9;
print(size.isEven); // 是否偶数
print(size.isOdd); // 是否奇数
print(size.toRadixString(6)); // 转换为6进制字符串
...

double pi = 3.1415926;
print(pi.ceil()); // 向上取整
print(pi.toInt()); // 转成整形
print(pi.toStringAsPrecision(2)); // 转换为固定精度字符串
...
```

### 字符串

使用单引号或双引号创建字符串，支持使用 ${ } 进行插值

```dart
String name = 'bob';
String message = 'Hi ${name.toUpperCase()}'; // Hi BOB
message = 'Welcome $name'; // 直接使用变量时可以省略{}
```

多个相邻字符串将自动连接在一起，或者显式使用+；多行字符串则使用'''或"""来创建

```dart
String message1 = 'Hi'
                 ' there'; // Hi there
String message2 = 'Hi'
                 + ' there'; // Hi there
String multiMessage = '''
Hello
again!
'''; // 多行字符串
```

字符串对象不可变，自带多种实用属性与方法

```dart
String name = 'bob';
print(name.length); // 长度
print(name.isEmpty); // 是否为空
print(name.substring(1)); // 子字符串
print(name.startsWith('b')); // 是否以某字符开头
print(name.replaceAll('b', 'l')); // 替换所有
...
```

### 布尔

布尔类型只有两个对象，true和false。

true是唯一“正确”的值，所有非true的值都视为false

```dart
// 以下常见的JavaScript代码，在Dart中将失效
var name = 'bob';
if (name) { // name被视为false，后续代码不再执行
  var message = 'hi' + name;
  ...
}
```



