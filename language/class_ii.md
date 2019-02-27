# 类 - Part II

_类的知识点较多，所以分成两节进行讲解，本节是Part II，上一节是_[_Part I_](/language/class_i.md)_。_

---

本节继续讲解类的知识点，主要包括抽象类/方法，接口，mixin以及枚举。

## 抽象类和抽象方法

没有函数体的方法，即只声明而不实现的方法被称为抽象方法，它只能出现在抽象类中。抽象类是使用`abstract`关键字修饰的类，它可以包含非抽象方法，可以被继承但不能被实例化。

```dart
// 大剑抽象类
abstract class GreatSword {
  // 抽象方法
  upgrade();

  // 非抽象方法
  use() {
    print('attack');
  }
}

// 混种大剑继承大剑
class BastardSword extends GreatSword {
  // 实现父类的抽象方法 
  upgrade() {
    print('upgrade');
  }

  // 重写且使用父类已有的实现
  use() {
    super.use();
  }
}
```

## 接口

Dart 支持接口，但没有定义接口的关键字。Dart 的每个类都隐含定义了一个接口，该接口包含当前类所有的实例变量和方法（包含通过继承和实现其他类而得来的）。通常使用抽象类来定义接口，而接口的实现是通过`implements`关键字，多个接口之间使用逗号分隔。

```dart
// 轻攻击接口
abstract class Light {
  lightAttack();
}

// 重攻击接口
abstract class Heavy {
  heavyAttack();
}

// 大剑同时实现了轻重攻击
class GreatSword implements Light, Heavy {
  lightAttack() {
    print('Light attack!');
  }
  
  heavyAttack() {
    print('Heavy attack!!!');
  }
}
```

## mixin

mixin是一种特殊的专门用于复用的类，Dart 不直接支持多继承（子类继承多个父类），但通过`mixin`可以实现类似于多继承的效果。

mixin有两种书写方式，一种是使用`class`声明一个没有父类和构造函数的类，另一种是直接使用`mixin`关键字（从Dart 2.1开始引入，为了代码的明确性，笔者倾向于直接使用`mixin`关键字）。

在声明其他类时，使用`with`关键字指定一个或多个`mixin`，这些`mixin`的属性和方法就都被"混入"到当前类中，即实现了类的复用。

如果需要限定mixin只能被特定类型使用，可以使用`on`关键字（只适用于`mixin`关键字）,`on`后跟随逗号分隔的多个父类，只有这些父类的子类才能使用当前mixin。

```dart
// 使用class方式声明的轻攻击mixin
class LightAttack {
  lightAttack() {
    print('Light attack!');
  }
}

// 使用mixin声明的重攻击mixin
mixin HeavyAttack {
  heavyAttack() {
    print('Heavy attack!');
  }
}

// 特殊攻击方式mixin，使用on限定能够使用的类型为Weapon的子类
mixin SpecialAttack on Weapon {
  specialAttack() {
    print('Special attack!');
  }
}

// 武器基类Weapon
abstract class Weapon {
}

// 大剑继承Weapon而且复用了LightAttack, HeavyAttack, SpecialAttack实现的方法
class GreatSword extends Weapon with LightAttack, HeavyAttack, SpecialAttack {
  attack() {
    lightAttack();
    heavyAttack();
    specialAttack();
  }
}
```

## 枚举
TODO:
