# 类

类用于创建对象，是对象的蓝本，所有类都直接或间接继承最顶端的`Object`类。

## 类的声明

类的声明是使用关键字`class`。

类中可以包含数据和函数，即对象的属性和方法。

在类中可以通过`this.`或直接访问属性和方法，官方建议只在命名冲突时才使用`.this`方式

```dart
// 声明一个表示大剑（黑暗之魂系列游戏的武器）的类
class GreatSword {
  // 属性
  String name; // 名称
  int damage = 100; // 伤害值
  int extraDamage = 0; // 其他附加伤害

  // 类中可以声明函数，即定义对象的方法
  // 打印信息
  info() {
    print('GreatSword ${name} - damage: ' + this.damage.toString()); // 通过this或直接访问属性
  }

  // 武器升级（增加伤害值）
  upgrade(int damage) {
    this.damage += damage; // 使用this区分同名的参数和属性
  }
}
```

## 构造函数

构造函数用于将类实例化为对象，配合关键字`new`或`const`使用。

没有显式声明构造函数的类，将默认拥有一个与类同名且没有参数的构造函数。

构造函数最常见的操作是使用参数对属性赋值，Dart为此提供了简写方式（参数列表中直接使用`this.属性`）。

除了普通的构造函数，Dart还支持`Class.name`方式的命名构造函数

```dart
class GreatSword {
  // 属性
  String name; // 名称
  final int damage = 100; // 伤害值
  int extraDamage = 0; // 其他附加伤害

  // 构造函数
  GreatSword(String name) {
    this.name = name;
  }
  // 以上构造函数的简写方式
  // GreatSword(this.name);

  // 命名构造函数（使用简写方式）
  GreatSword.enhanced(this.name, this.extraDamage);
}

main() {
  // 实例化
  var sword = new GreatSword('Bastard Sword'); // 普通构造函数
  var enhancedSword = new GreatSword.enhanced('Claymore', 20); // 使用命名构造函数
}
```

// TODO - const class

## Getter/Setter

跟很多语言不同，Dart对象属性的读写是通过getter和setter完成的。

getter和setter是一种特殊的方法，它们虽是方法却有跟属性一样的访问方式。

所有普通属性都有一对隐含的getter跟setter，`final`属性只有getter。

自定义getter和setter也是支持的，书写方式是在方法名前添加`get`或`set`，`getter`有返回值无参数而`setter`正好相反

```dart
class GreatSword {
  // 属性
  String name; // 名称
  final int damage = 100; // 伤害值
  int extraDamage = 0; // 其他附加伤害

  // damage隐含的getter
  // int get damage => damage;

  // name和extraDamage隐含的getter和setter
  // String get name => name;
  // set name(String name) => this.name = name;
  // int get extraDamage => extraDamage;
  // set extraDamage(int extraDamage) => this.extraDamage = extraDamage;

  // 自定义的getter和setter
  // 总伤害
  int get totalDamage {
    return damage + extraDamage; // 基础伤害与附加伤害之和
  }
  set totalDamage(int totalDamage) {
    extraDamage = totalDamage - damage; // 通过总伤害计算出附加伤害
  }

  // 打印信息
  info() {
    return '${name} - totalDamage: ' + this.totalDamage.toString(); // 通过this或直接访问属性
  }
}

main() {
  // 所有对属性的读写都是通过getter和setter
  var sword = new GreatSword();
  sword.name = 'GreatSword';
  sword.totalDamage = 200;
  print(sword.damage);
  print(sword.extraDamage);
  print(sword.info());

  sword.damage = 180; // 错误，damage的setter不存在  
}
```

getter和setter带来的好处是，你可以随时更改属性的内部实现，而且不用修改外部调用代码

```dart
// 版本1的GreatSword
class GreatSword1 {
  final String name = 'GreatSword';
}

// 版本2的GreatSword，将属性name转换为一个getter
class GreatSword2 {
  String get name {
    return greatName();
  }

  greatName() => 'GreatSword';
}

main() {
  // 使用两个不同版本的GreatSword，对name的访问方式不变
  var sword = new GreatSword1();
  print(sword.name);
  sword = new GreatSword2();
  print(sword.name);
}
```

## 初始化列表

构造函数还支持初始化列表，其书写方式是在参数列表后跟一个以冒号开头，使用逗号分隔的赋值列表。

初始化列表先于构造函数体执行，常用于`final`属性的初始化，即没有初始化的`final`属性可以在初始化列表中进行赋值。

初始化列表还可用于构造函数转发（复用构造函数逻辑），构造函数转发跟赋值操作不能同时出现

```dart
class GreatSword {
  // 属性
  String name; // 名称
  final int damage; // 伤害值（没有初始化）
  int extraDamage = 0; // 其他附加伤害

  // 普通大剑基础伤害100
  GreatSword(this.name) : damage = 100;

  // 强化版大剑基础伤害120
  GreatSword.enhanced(this.name, this.extraDamage) : damage = 120;

  // 通过初始化列表转发到其他构造函数，复用构造逻辑
  GreatSword.bastard(): this('Bastard Sword'); // 混种大剑
  GreatSword.moonlight(): this.enhanced('Moonlight GreatSword', 10); // 月光大剑
}

main() {
  var bastard = new GreatSword.bastard();
  var moonlight = new GreatSword.moonlight();
  print(bastard.name);
  print(bastard.damage);
  print(bastard.extraDamage);
  print(moonlight.name);
  print(moonlight.damage);
  print(moonlight.extraDamage);
}
```

## 子类

使用`extends`来创建子类，使用`super`来访问父类。

除了构造函数，父类所有的属性（setter/getter）和方法都被子类继承，而且都可以被重写（override）

```dart
// 大剑
class GreatSword {
  int damage = 100; // 基础伤害值

  int get totalDamage => damage; // 总伤害
}

// 特大剑
class UltraGreatSword extends GreatSword {
  int extraDamage = 50; // 附加伤害值

  // 重写getter
  int get totalDamage => super.damage + extraDamage; // 父类的伤害加上自己的附加伤害为总伤害（super可以省略）
}
```

默认构造函数

