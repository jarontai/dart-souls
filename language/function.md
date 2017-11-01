# 函数

Dart是纯面向对象语言，所以函数也是对象，它们的类型是`Function`。

## 函数声明

函数声明由返回值（可选）、函数名、参数列表以及函数体构成。

如果函数体只包含一个返回表达式，则可以使用`=>`简写

```dart
// 一个加法函数
int add(int a, int b) {
  return a + b;
}

// 简写方式
int add(int a, int b) => a + b;
```

## 函数对象

函数是对象，可以赋给变量，可以作为函数的参数或返回值，可以匿名

```dart
// 将函数赋给变量，此函数最后一个参数是函数类型
var adder = (int a, int b, Function printer) {
  var result = a + b;
  printer(result);
};

// 匿名函数作为参数
adder(1, 3, (val) => print(val));
```

## 可选参数

函数参数有两种：必填参数和可选参数，可选参数只能出现在必填参数之后。

可选参数又分为两种：位置型（使用`[]`）和命名型（使用`{}`）。

位置和命名型可选参数不能同时出现，且都使用`=`设置默认值 （命名型还支持使用`:`设置默认值，但已不再推荐使用）

```dart
// 一个必填参数和一个位置可选参数
youSay(String words, [String moreWords = 'yah']) {
  var result = 'You say $words';
  if (moreWords != null) {
    result += ' $moreWords';
  }
  print(result);
}

// 两个命名可选参数
iSay({String words, int times = 1}) {
  var result = 'I say';
  if (words != null) {
    for (var i = 0; i < times; i++) {
      result += ' $words';
    }
  }
  print(result);
}

youSay('yah');
youSay('yah', 'hoo');
iSay(words: 'yah');
iSay(words: 'yah', times: 6);
```

## 返回值

所有函数都有返回值，如果函数体内没有`return`语句，则语句`return null;`将被隐含地追加到函数体尾部。

## 闭包

闭包（_closure_）是指一个函数对象，即使不在初始作用域内，也仍然能够访问其中的变量

```dart
// makeAdder生成一个将参数跟base相加的函数
Function makeAdder(int base) {
  return (int i) => base + i;
}

main() {
  var add2 = makeAdder(2); // base为2
  var add4 = makeAdder(4); // base为4

  // 不在makeAdder内，仍然可以访问makeAdder的参数变量base
  print(add2(3)); // 5
  print(add4(3)); // 7
}
```

## main函数

Dart应用都应该有一个顶层函数`main`，它是应用的入口。

`main`函数的返回值是`void`，且拥有一个可选的泛型列表参数`List<String>` （`List`与泛型将在后续章节进行讲解）

```dart
// 简单而完整的main函数
void main(List<String> arguments) {
  print(arguments);
}
```



