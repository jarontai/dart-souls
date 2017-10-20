# 类

对象都是某个类的实例，而所有类都继承自最顶层的`Object`。

类使用关键字`class`声明，对象使用关键字`new`创建。

## 构造函数

构造函数与类同名，也可以使用命名构造函数

```dart
class Game {
  String title;
  String developer;

  // 构造函数，
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

var mario = new Game('Mario', 'Nintendo');
var ds = new Game.dark();
```

类中可以定义数据和函数，即对象的属性和方法。

