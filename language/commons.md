# 常用类型

除了[变量与基本类型](/language/basics.md)介绍的基本类型，Dart 标准库还提供了很多其他类型，本章将挑选部分常用类型进行讲解。

## 集合

Dart 的集合类型主要包括：`List`，`Map` 和 `Set`。

注意：Dart 的集合类型都支持泛型，相关内容将在[泛型](/language/generics.md)进行讲解。

### List

`List`表示有序的数据列表，它其实就是其他语言中常见的数组（array）。

`List` 可以使用字面量（如：`[a1, a2]的形式`）或构造函数创建。

```dart
var gameList = ['Halo', 'God of War']; // 字面量形式

gameList = new List(); // 使用构造函数
gameList.add('The Witcher'); // 使用add方法添加数据
gameList.add('Dark Souls');

// 通过getter或索引访问元素
print(gameList.frist);
print(gameList.last);
print(gameList[0]);

// 通过for...in循环遍历
for (var game in gameList) {
    print(game);
}
```

### Set

`Set`是无序的数据集合，其中对象不可（不会）重复。

`Set` 可以使用字面量（`如：{'dart', 'javascript'}`）或构造函数创建。

注意：访问`Set`中的元素时，它们的顺序不能得到保证，默认顺序为元素的添加顺序。

```dart
var gameSet = {'Halo', 'God of War'}; // 字面量形式

gameSet = new Set(); // 使用构造函数
gameSet.add('The Witcher'); // 使用add方法添加数据
gameSet.add('Dark Souls');

// 通过getter访问元素
print(gameSet.frist);
print(gameSet.last);

// 通过for...in循环遍历
for (var game in gameSet) {
    print(game);
}
```

### Map

`Map`是无序的键值对集合，键(key)和值(value)可以是任意类型，其中键不可（不会）重复，值可以重复。

`Map` 可以使用字面量（`如：{'first': 'dart', 'second': 'javascript'}`）或构造函数创建。

注意：在没有[泛型](/language/generics.md)参数的情况下，空`Map`字面量和空`Set`字面量的写法都是`{}`。因为 Dart 的`Set`字面量是后加入的，所以`{}`将默认识别为`Map`类型。

```dart
var gameMap = {'microsoft': 'Halo', 'sony' :'God of War'}; // 字面量形式

gameMap = new Map(); // 使用构造函数
gameMap['cdpr'] = 'The Witcher'; // 使用[]添加数据
gameMap['fromsoft'] = 'Dark Souls';

print(gameMap['fromsoft']); // 使用[]访问数据

// 通过for...in循环遍历值
for (var game in gameMap.values) {
    print(game);
}
```

### TODO: 更多类型
### TODO: the spread operator (...) and the null-aware spread operator (...?),
