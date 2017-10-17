# 函数

## 函数声明

函数声明由返回值（可选）、函数名、参数列表以及函数体构成。

如果函数体只包含一个返回表达式，则可以使用=&gt;简写

```dart
// 一个加法函数
int add(int a, int b) {
  return a + b;
}

// 简写方式
int add(int a, int b) => a + b;
```

## 可选参数

函数参数有两种类型：必填参数和可选参数，可选参数只能出现在必填参数之后。

可选参数也有两种类型：位置型和命名型，它们不能同时出现，且可以使用=设置默认值。

```dart
// 一个必填参数和一个位置可选参数
String youSay(String words, [String moreWords = 'yoo']) {
  var result = 'You say $words';
  if (moreWords != null) {
    result += ' $moreWords';
  }
  return result;
}

// 两个命名可选参数
String iSay({String words, int times = 1}) {
  var result = 'I say';
  if (words != null) {
    for (var i = 0; i < times; i++) {
      result += ' $words';
    }
  }
  return result;
}
```

## 函数对象



## 词法作用域



## main函数



