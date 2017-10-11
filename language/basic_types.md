# 变量与基本类型

## 变量

有两种声明变量的方式，一是不指定类型，即使用 var

```dart
var name = 'bob';
```

另一种是指定类型

```dart
String name = 'bob'; // name为字符串类型
```

Dart是纯面向对象的，如果变量在声明时没有赋值，将被自动赋值为 null。

```dart
var name;
print(name); // 使用print函数打印，输出为null
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



