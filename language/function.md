# 函数

Dart是纯面向对象语言，所以函数也是对象。

## 函数声明

函数声明由返回值（可选）、函数名、参数列表以及函数体构成。

如果函数体只包含一个返回表达式，则可以使用`=>`简写。

函数中也可以声明函数，即本地函数

```dart
// 声明一个加法函数
int add1(int a, int b) {
  return a + b;
}

// 简写版本的加法函数
int add2(int a, int b) => a + b;

// 外层函数
outFun() {
  add3(int a, int b) => a + b; // 函数内声明的本地函数
  print(add3(1, 1)); // 调用本地函数
}
```

## 函数对象

函数是对象，可以赋给变量，可以匿名；函数的类型是`Function`，可以作为参数或返回值

```dart
// 将函数赋给变量，函数最后一个参数的类型是函数
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
String youSay(String words, [String moreWords = 'yah']) {
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

main() {
  print(youSay('yah'));
  print(youSay('yah', 'hoo'));
  print(iSay(words: 'yah'));
  print(iSay(words: 'yah', times: 6));
}
```

## 返回值

所有函数都有返回值，如果函数体内没有`return`语句，则语句`return null;`将被隐含地追加到函数体尾部。

## 闭包

闭包（_closure_）是指一个函数对象，即使不在初始作用域内，也仍然能够访问其中的变量。

```dart
// makeSpeaker生成一个将参数跟person相连的函数
Function makeSpeaker(String person) {
  return (String words) => '$person say $words';
}

main() {
  var bob = makeSpeaker('bob'); // person为bob
  var john = makeSpeaker('john'); // person为john

  // 不在makeSpeaker内，仍然可以访问makeSpeaker的参数变量person
  print(bob('hi')); // bob say hi
  print(john('hello')); //  john say hello
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



