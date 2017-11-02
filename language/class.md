# 类

类用于创建对象，是对象的蓝本，所有类都直接或间接继承最顶端的`Object`类。

## 类的声明

类的声明是使用关键字`class`。

类中可以包含数据和函数，即对象的属性和方法。

在类中可以通过`this.`或直接访问自身的属性和方法

```dart
// 声明一个表示游戏的类
class Game {
  // 属性声明
  String title; // 游戏标题
  String developer; // 游戏开发商
  int playerNum = 1; // 支持玩家数，初始化为1

  // 类中的函数，即对象的方法
  play() {
    print('Play the ' + this.title + ' developed by ' + developer); // 通过this或直接访问自身属性
    ......
  }
}
```

## 构造函数

构造函数用于将类实例化为对象，配合关键字`new`或`const`使用。

没有显式声明构造函数的类，将默认拥有一个与类同名且没有参数的构造函数。

除了普通的构造函数，Dart还支持`Class.name`方式的命名构造函数。

```dart
class Game {
  String title;
  String developer;

  // 构造函数
  Game(String title, String developer) {
    this.title = title;
    this.developer = developer;
  }

  // 命名构造函数
  Game.dark() {
    this.title = 'Dark Souls';
    this.developer = 'FromSoftware';
  }
}

main() {
  // 实例化
  var mario = new Game('Mario', 'Nintendo'); // 普通构造函数
  var ds = new Game.dark(); // 使用命名构造函数
}
```

// TODO - const class

## Getter/Setter

getter和setter是对属性进行读写的特殊方法，它们虽是方法却使用跟属性一样的书写方式。

所有普通属性都会隐含生成一对getter跟setter，`final`属性只有getter。

```dart
class Game {
  final String title = 'tetris';
  double price; 
  
  // title隐含的getter
  // String get title => title;

  // price隐含的getter和setter
  // String get price => price;
  // set price(double title) => this.price = price;
}

var game = new Game();
print(game.tetris);
game.price = 10.0;
```



