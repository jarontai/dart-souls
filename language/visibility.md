# 库与可见性

`库`（library）是Dart代码的逻辑组织单元，是`可见性`（访问控制）的实现基础，使用库能够使代码模块化且便于复用。

## 库

注意：通过`library`和`part`关键字，一个库是可以由多个Dart文件组成的，但因为官方不再推荐此方式，所以这里不做讲解。

一个Dart应用包含多个Dart文件，每个Dart文件就是一个库，每个库都有对应的URI（统一资源标识符）。

库的URI有三种形式，一是以`dart:`开头的 Dart 自带的标准库，如：dart:io；二是文件路径形式，如：'../base.dart'，最后是以`package:`开头的`包`（package）URI（需要包管理器`pub`的支持，具体将在后续章节讲解）。

库的导入是通过`import`关键字加库的URI来实现，应用自身的库一般通过文件路径形式相互导入，而外部引入的库（依赖）使用`包`形式URI导入。

```dart
// 三种形式的库导入
import dart:io;
import '../base.dart';
import 'package:test/test.dart';
```

## 可见性

在可见性或者说访问控制方面，很多语言都有相对复杂的实现，如Java/C#中，有public等多个关键字来声明变量的访问权限，而Dart的可见性设计则非常简洁。

Dart应用一般由多个库（Dart文件）组成，库中又包含多个类、函数和变量，它们都是库的成员，对外默认可见（可以被其他库导入使用）。如果库成员的标识符以`_`（下划线）开头，则它是库`私有`的，对外不可见。

默认情况下，导入库会所有将该库所有成员（私有成员除外）导入到当前代码中，如果想隐藏某些成员，或者只想导入某些成员，则可以使用`hide`或`show`关键字。

在导入多个库时，不同库中的成员可能会重名，导致代码无法编译，解决方法是使用`as`给库添加前缀，库成员将通过`前缀.成员名称`方式访问。

```dart
// lib1.dart
class _Base {
}
class Class1 extends _Base {
}
class Class2 extends _Base {
}

// lib2.dart
class Class1 {
}
class Class2 {
}

// main.dart
import 'lib1.dart' hide Class2; // 隐藏lib1中的Class2
import 'lib2.dart' as lib2 show Class1; // 只导入lib2的Class1，同时添加库前缀lib2，避免Class1命名冲突

main() {
  // var base = _Base(); // 错误，无法访问lib1的私有成员
  var cls1 = Class1(); // 访问lib1的Class1
  var cls2 = lib2.Class1(); // 通过前缀访问lib2中的Class1
}
```
