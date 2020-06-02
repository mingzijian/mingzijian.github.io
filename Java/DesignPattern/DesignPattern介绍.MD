DesignPattern介绍
------------------

### 简介
  设计模式（Design Pattern）是一套被反复使用、多数人知晓的、经过分类的、代码设计经验的总结。

### 四人帮（Gang of Four）
  《设计模式》一书的四位作者：Erich Gamma、Richard Helm、Ralph Johnson 和 John Vlissides 。

### 六大原则
  1. 开闭原则（Open Closed Principle，OCP）

  2. 里氏代换原则（Liskov Substitution Principle，LSP）

  3. 依赖倒转原则（Dependency Inversion Principle，DIP）

  4. 接口隔离原则（Interface Segregation Principle，ISP）

  5. 合成/聚合复用原则（Composite/Aggregate Reuse Principle，CARP）

  6. 最小知识原则（Principle of Least Knowledge，PLK，也叫迪米特法则）


### 模式分类
| 分类&描述 | 包含模式  |
|-------|---|
| 结构型模式 这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式，而不是使用 new 运算符直接实例化对象。这使得程序在判断针对某个给定实例需要创建哪些对象时更加灵活。 | 工厂模式（Factory Pattern）抽象工厂模式（Abstract Factory Pattern）单例模式（Singleton Pattern）建造者模式（Builder Pattern）原型模式（Prototype Pattern）  |

| 行为型模式 这些设计模式关注类和对象的组合。继承的概念被用来组合接口和定义组合对象获得新功能的方式。 | 适配器模式（Adapter Pattern）桥接模式（Bridge Pattern）过滤器模式（Filter、Criteria Pattern）组合模式（Composite Pattern）装饰器模式（Decorator Pattern）外观模式（Facade Pattern）享元模式（Flyweight Pattern）代理模式（Proxy Pattern）  |

| 创建型模式 这些设计模式特别关注对象之间的通信。 | 责任链模式（Chain of Responsibility Pattern）命令模式（Command Pattern）解释器模式（Interpreter Pattern）迭代器模式（Iterator Pattern）中介者模式（Mediator Pattern）备忘录模式（Memento Pattern）观察者模式（Observer Pattern）状态模式（State Pattern）空对象模式（Null Object Pattern）策略模式（Strategy Pattern）模板模式（Template Pattern）访问者模式（Visitor Pattern）  |

