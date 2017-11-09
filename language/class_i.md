# 类 - Part I

_类的知识点较多，所以分成两节进行讲解，本节是Part I，下一节是_[_Part II_](/language/class_ii.md)_。_

类用于创建对象，是对象的蓝本。

类的声明是使用关键字`class`，所有类都直接或间接继承最顶端的`Object`类。

## 属性和方法

类中可以包含数据和函数，即对象的属性和方法，其中属性可以使用`final`修饰。

在类中通过`this`或直接访问属性和方法，官方建议只在命名冲突时才使用`this`

```dart
// 声明一个表示'大剑'（黑暗之魂系列游戏的一种武器）的类
class GreatSword {
  // 属性
  String name; // 名称
  final int damage = 100; // 基础伤害值
  int extraDamage = 0; // 其他附加伤害

  // 类中可以声明函数，即定义对象的方法
  // 打印信息
  info() {
    print('GreatSword ${name} - damage: ' + this.damage.toString()); // 通过this或直接访问属性
  }

  // 武器升级（增加附加伤害值）
  upgrade(int extraDamage) {
    this.extraDamage += extraDamage; // 使用this区分同名的参数和属性
  }
}
```

// TODO

类的普通属性和方法通常也被称为实例变量和实例方法，如果它们跟类绑定的就叫做类变量和类方法。

类变量和类方法的声明方法是在普通属性之前添加`static`关键字，它们也常被称为静态变量。

```dart
class GreatSword {
  String name; // 名称
  final int damage = 100; // 基础伤害值
  int extraDamage = 0; // 其他附加伤害
}
```

## 构造函数

构造函数用于将类实例化为对象，配合关键字`new`或`const`使用。

没有显式声明构造函数的类，将默认拥有一个与类同名且没有参数的构造函数。

构造函数最常见的操作是使用参数对属性赋值，Dart为此提供了简写方式（参数列表中直接使用`this.属性`）。

除了普通的构造函数，Dart还支持`Class.name`方式的命名构造函数

```dart
class GreatSword {
  String name; // 名称
  final int damage = 100; // 基础伤害值
  int extraDamage = 0; // 其他附加伤害

  // 构造函数
  GreatSword(String name) {
    this.name = name;
  }
  // 以上构造函数的简写方式
  // GreatSword(this.name);

  // 命名构造函数
  GreatSword.enhanced(this.name, this.extraDamage); 
  // 等同于以下写法
  // GreatSword.enhanced(String name, int extraDamage) {
  //   this.name = name;
  //   this.extraDamage = extraDamage;
  // }
}

main() {
  // 实例化
  var sword = new GreatSword('Claymore'); // 普通大剑
  var enhancedSword = new GreatSword.enhanced('Bastard Sword', 20); // 强化版混种大剑
}
```

// TODO - const / Factory class

## 初始化列表

构造函数还支持初始化列表，书写方式是在参数列表后跟一个以冒号开头的，使用逗号分隔的赋值列表。

初始化列表先于构造函数体执行，常用于`final`属性的初始化，即没有初始化的`final`属性可以在初始化列表中进行赋值。

初始化列表还可使用`this`进行构造函数转发，即复用构造函数逻辑，构造函数转发和赋值操作不能同时出现

```dart
class GreatSword {
  String name; // 名称
  final int damage; // 基础伤害值（没有初始化）
  int extraDamage = 0; // 其他附加伤害

  // 在初始化列表中设置final变量damage
  GreatSword(this.name, [this.extraDamage = 0]) : damage = 100; // 普通大剑基础伤害100

  // 在初始化列表中调用静态方法计算extraDamage
  GreatSword.magic(this.name, this.damage) : extraDamage = magicPower(damage); // 魔法大剑的附加伤害要根据基础伤害计算得出

  // 通过初始化列表转发到其他构造函数，其中this代表类名
  GreatSword.bastard(): this('Bastard Sword', 10); // 混种大剑
  GreatSword.moonlight(): this.magic('Moonlight GreatSword', 80); // 月光大剑

  // 计算魔法武器的附加伤害
  static magicPower(int damage) {
    return damage * 0.15;
  }
}

main() {
  var sword = new GreatSword('Claymore');
  var bastard = new GreatSword.bastard();
  var moonlight = new GreatSword.moonlight();
  print(sword.name);
  print(sword.damage);
  print(sword.extraDamage);
  print(bastard.name);
  print(bastard.damage);
  print(bastard.extraDamage);
  print(moonlight.name);
  print(moonlight.damage);
  print(moonlight.extraDamage);
}
```

## Getter/Setter

跟很多语言不同，Dart对象属性的读写是通过getter和setter完成的。

getter和setter是一种特殊的方法，它们虽是方法却有跟属性一样的访问方式。

所有普通属性都有一对隐含的getter跟setter，`final`属性只有getter。

自定义getter和setter也是支持的，书写方式是在方法名前添加`get`或`set`，`getter`有返回值无参数而`setter`正好相反

```dart
class GreatSword {
  String name; // 名称
  final int damage = 100; // 基础伤害值
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

## 子类

使用`extends`来创建子类，使用`super`来访问父类。

除了构造函数，父类所有的属性（setter/getter）和方法都被子类继承，而且都可以被重写（override）。

子类的构造函数在执行前，将隐含调用父类的`无参构造函数`（没有参数的构造函数，默认或显式声明的都可）。

如果父类没有`无参构造函数`，则子类的构造函数必须在初始化列表中通过`super`显式调用父类的某个构造函数。

```dart
// 大剑
class GreatSword {
  String name; // 名称
  final int damage = 100; // 基础伤害值

  // 总伤害的getter
  int get totalDamage => damage; // 总伤害

  // 一个参数的构造函数（即没有无参构造函数）
  GreatSword(this.name);
}

// 特大剑
class UltraGreatSword extends GreatSword {
  int extraDamage = 20; // 附加伤害值

  // 重写getter
  int get totalDamage => super.damage + extraDamage; // 父类的伤害加上自己的附加伤害为总伤害（super可省略）

  // 必须使用super（代表父类名）调用父类的构造函数，否则错误
  UltraGreatSword(String name) : extraDamage = 50, super(name);
}

main() {
  var black = new UltraGreatSword('Black Knight Greatsword');
  print(black.name);
  print(black.damage);
  print(black.extraDamage);
}
```

## 抽象类和抽象方法



