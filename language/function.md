# 函数

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

## 可选参数

函数参数有两种：必填参数和可选参数，可选参数只能出现在必填参数之后。

可选参数又分为两种：位置型和命名型，它们不能同时出现，且都使用`=`设置默认值。

```dart
// 一个必填参数和一个位置可选参数
youSay(String words, [String moreWords = 'yoo']) {
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

youSay('yoo');
youSay('yoo', 'hah');
iSay(words: 'yoo');
iSay(words: 'yoo', times: 6);
```

## 函数对象

函数是对象，可以赋给变量，可以作为参数，可以匿名；函数的类型是`Function`

```dart
// 将函数赋给变量，此函数最后一个参数是函数类型
var adder = (int a, int b, Function printer) {
  var result = a + b;
  printer(result);
};

// 匿名函数作为参数
adder(1, 3, (val) => print(val));
```

## 词法作用域和闭包

词法作用域（也称为静态作用域），表示变量的作用域在其定义时就已经确定。

变量作用域由它所处代码块（大括号）的层级决定，层次越深，作用域越小

```dart
var top = true;

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

## main函数

Dart应用都应该有一个顶层函数`main`，它是应用的入口。

main函数的返回值是void，且拥有一个可选的泛型列表参数`List<String>` （`List`与泛型将在后续章节进行讲述）

```dart
// 简单而完整的main函数
void main(List<String> arguments) {
  print(arguments);
}
```



