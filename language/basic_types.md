# 变量与基本类型

## 变量

变量都是引用，它们都指向某个对象。

有两种基本的变量声明方式，一种不指定类型，即使用 var

```dart
var name = 'bob'; // name变量指向一个内容为'bob'的字符串对象
```

另一种指定类型

```dart
String name = 'bob'; // 显式指明name为字符串
```

Dart是纯面向对象的，在声明时没有赋值的变量，其默认值为 null

```dart
var name;
print(name); // 使用print函数打印，输出为null
```

## final与const

变量内容如果不变，应当使用final或const。

final表示变量只能被赋值一次；const表示变量是编译时常量，const变量默认就是final变量。

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

数字对象具有多种属性与方法

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

### 布尔



