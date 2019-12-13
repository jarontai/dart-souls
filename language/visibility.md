# 库与可见性

`库`（library）是 Dart 代码的逻辑组织单元，是`可见性`（访问控制）的实现基础，使用库能够使代码模块化且便于复用。

## 库

注意：通过`library`和`part`关键字，一个库是可以由多个 Dart 文件组成的，但因为官方不再推荐此方式，所以这里不做讲解。

一个 Dart 应用包含多个 Dart 文件，每个 Dart 文件就是一个库，每个库都有对应的URI（统一资源标识符）。

库的 URI 有三种形式，一是以`dart:`开头的 Dart 自带的标准库，如：dart:io；二是文件路径形式，如：'../base.dart'，最后是以`package:`开头的`包`（package）URI（需要包管理器`pub`的支持，具体将在后续章节讲解）。

库的导入是通过`import`关键字加库的 URI 来实现，应用自身的库一般通过文件路径形式相互导入，而外部引入的库（依赖）使用`包`形式URI导入。

```dart
// 三种形式的库导入
import dart:io;
import '../base.dart';
import 'package:test/test.dart';
```

## 可见性

在可见性或者说访问控制方面，很多语言都有相对复杂的实现，如 Java/C# 中，有`public`等多个关键字来声明变量的访问权限，而 Dart 的可见性设计则非常简洁。

Dart 应用由一到多个库（文件）组成，库中又包含了类、函数和变量等，它们都是库的成员，对外默认可见（可以被其他库导入使用）。而如果库成员的标识符是以`_`（下划线）开头，则它是库`私有`的，对外不可见。

默认情况下，`import`会将库中所有成员（私有成员除外）导入到当前代码中，如果想隐藏某些成员，或者只想导入某些成员，则可以使用`hide`或`show`关键字。

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

## 标准库

与其他语言一样，Dart 自带处理常见任务的库，即标准库。Dart 的标准库由核心库`dart:core`及其他17个库组成。

`dart:core`是 Dart 的核心库，其中包含最基础最常用的类型，如：int，List 等。`dart:core`会隐含导入到代码中，无需使用`import`导入（显式导入`dart:core`反而会报错）。

除核心库外的其他库，按照适用平台，划分为三类: 

  1. 通用库，可适用于服务端和Web端；
  2. 仅适用于服务端(VM)
  3. 仅适用于Web端

| 库名 | 适用平台 | 描述 |
| :--- | :--- | :--- |
| dart:async | 通用 | 异步编程库，包含`Future`、`Stream`等常用异步编程类型 |
| dart:collection | 通用 | 集合支持/工具库，对`dart:core`中的集合类型（`List`、`Map`等）提供补充 |
| dart:convert | 通用 | 转换库，用于对各种数据格式的编码/解码，如：`json`和`utf8` |
| dart:developer | 通用 | 开发者库，提供开发者工具，如：`debugger`和`inspector` |
| dart:math | 通用 | 数学库，提供各种数学运算相关函数 |
| dart:typed_data | 通用 | 高效、固定长度的列表类型库 |
| dart:io | VM | io库，提供文件、Socket等常见io操作类 |
| dart:isolate | VM | 并发编程支持库 |
| dart:mirrors | VM | 反射库（API不稳定） |
| dart:html | Web | html库，提供对html元素和dom的操作等 |
| dart:indexed_db | Web | Web端indexed_db数据库支持库 |
| dart:js | Web | JavaScript库，支持对JavaScript对象/方法的访问 |
| dart:js_util | Web | JavaScript交互工具库 |
| dart:svg | Web | svg矢量图形支持库 |
| dart:web_audio | Web | Web端音频处理库 |
| dart:web_gl | Web | Web端3D编程支持库 |
| dart:web_sql | Web | Web端SQL支持库（标准过时，推荐使用dart:indexed_db代替） |
