# 类

类用于创建对象，是对象的蓝本，所有类都直接或间接继承最顶端的`Object`类。

## 类的声明

类的声明是使用关键字`class`。

类中可以包含数据和函数，即对象的属性和方法。

在类中可以通过`this.`或直接访问属性和方法，官方建议只在命名冲突时才使用`.this`方式

```dart
// 声明一个表示游戏的类
class Game {
  // 属性声明
  String title; // 游戏标题
  String developer; // 游戏开发商
  int playerNum = 1; // 支持玩家数，初始化为1

  // 类中的函数，即对象的方法
  play() {
    print('Play the ' + this.title + ' developed by ' + developer); // 通过this或直接访问属性
    ......
  }

  updateTitle(String title) {
    this.title = title; // 使用this区分同名的参数和属性
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

跟很多语言不同，Dart对象属性的读写是通过getter和setter完成的。

getter和setter是一种特殊的方法，它们虽是方法却有跟属性一样的访问方式。

所有普通属性都有一对隐含的getter跟setter，`final`属性只有getter。

自定义getter和setter也是支持的，方式是在方法名前添加`get`或`set`，`getter`有返回值无参数而`setter`正好相反

```dart
class Game {
  final String title = 'Dark Souls';
  final String developer = 'FromSoftware';
  num price = 100;
  num discount = 0.2;

  // title、developer隐含的getter
  // String get title => title;
  // String get developer => developer;

  // price隐含的getter和setter
  // String get price => price;
  // set price(double title) => this.price = price;

  // 自定义的getter和setter
  num get salePrice {
    if (discount != null) {
      return price * (1 - discount);
    }
    return 0;
  }
  set salePrice(num salePrice) {
    discount = (price - salePrice) / price;
  }

  displayInfo() {
    print('${title} - salePrice: ${salePrice}'); // 像访问title一样访问salePrice
  }
}

main() {
  // 所有对属性的读写都是通过getter和setter
  var game = new Game();
  print(game.title);
  game.price = 200;
  print(game.price);
  print(game.salePrice);
  game.salePrice = 180;
  print(game.discount);
  print(game.displayInfo());

  game.title = 'Mario'; // 错误，title的setter不存在
}
```

getter和setter带来的好处是，你可以随时更改属性的内部实现，而且不用修改外部调用代码

```dart
// 版本1的Game
class Game1 {
  final String title = 'Dark Souls';
}

// 版本2的Game，将title转换为一个getter
class Game2 {
  String get title {
    return souls();
  }

  souls() => 'Dark Souls';
}

main() {
  // 使用两个不同版本的Game，但对title的访问方式不变
  var game1 = new Game1();
  var game2 = new Game2();
  print(game1.title);
  print(game2.title);
}
```



