## 1.  面向对象基础(一) 封装
###  1.1   面向对象编程介绍

#### 1.1.1 概述
​	如今主流的软件开发思想有两种：⼀个是**⾯向过程**，另⼀个是**⾯向对象**。⾯向过程出现得较早，典型代表为C语⾔，开发中⼩型项⽬的效率很⾼，但是很难适⽤于如今主流的⼤中型项⽬开发场景。⾯向对象则出现得更晚⼀些，典型代表为Java或C++等语⾔，更加适合⽤于⼤型开发场景。两种开发思想各有⻓短。
​	对于⾯向过程的思想： 需要实现⼀个功能的时候,看重的是开发的步骤和过程,每⼀个步骤都需要⾃⼰亲⼒亲为,需要⾃⼰编写代码(⾃⼰来做)
​	对于⾯向对象的思想：当需要实现⼀个功能的时候,看重的并不是过程和步骤,⽽是关⼼谁帮我做这件事(偷懒,找⼈帮我做)

**⾯向对象的三⼤特征有：封装性、继承性、多态** （同Java）

#### 1.1.2 ⽣活举例

 洗⾐服
 ⾯向过程（⼿洗）：脱⾐服、找⼀个盆、加⽔、加洗⾐粉、浸泡30分钟、搓洗、拧⾐服、倒掉⽔、再加⽔、漂洗、拧⾐服、倒掉⽔、晾⾐服。
 ⾯向对象（机洗）：脱⾐服、放⼊洗⾐机、按下开关、拿出⾐服晾晒。

### 1.2 类和对象

​	⾯向对象编程的2个⾮常重要的概念：**类和对象**
​	对象是⾯向对象编程的核⼼，在使⽤对象的过程中，为了将具有共同特征和⾏为的⼀组对象抽象定义，提出了另外⼀个新的概念——类

​	我们学习编程语⾔，就是为了模拟现实世界中的事物，实现信息化来提⾼⼯作效率。例如银⾏的业务系统、超市的结账系统等，都是如此。
**⾯向对象的语⾔当中，“类”就是⽤来模拟现实事物的。**
那么模拟现实世界的事物通常从两⽅⾯模拟：

1. 属性：事物的特征描述信息，⽤于描述某个特征“是什么”。 

2. ⾏为：事物的能⼒⾏动⽅案，⽤于说明事物“能做什么”。

类中也有属性、⾏为两个组成部分，⽽“对象”是类的具体实例。例如：
类：抽象的，是⼀张“⼿机设计图”。
对象：具体的，是⼀个“真正的⼿机实例”。

+ 类：**具有相似内部状态和运动规律的实体的集合(或统称为抽象)。具有相同属性和⾏为事物的统称**

+ 对象：**某⼀个具体事物的存在 ,在现实世界中可以是看得⻅摸得着的。可以是直接使⽤的**

#### 1.2.1 定义类

定义一个类，格式如下：

```python
class 类名:
	⽅法列表
```

demo：定义⼀个Hero类

```python
# class Hero: # 经典类（旧式类）定义形式
# class Hero():
class Hero(object): # 新式类定义形式
	def info(self):
	print("英雄各有⻅，何必问出处。")
```

**说明:**

+ 定义类时有2种形式：新式类和经典类，上⾯代码中的Hero为新式类，前两⾏注释部分则为经典类；
+ object 是Python ⾥所有类的最顶级⽗类；
+ 类名 的命名规则按照"⼤驼峰命名法"；
+ info 是⼀个实例⽅法，第⼀个参数⼀般是self，表示实例对象本身，当然了可以将self换为其它的名字，其作⽤是⼀个变量 这个变量指向了实例对象;

#### 1.2.2 创建对象

python中，可以根据已经定义的类去创建出⼀个或多个对象。创建对象的格式为:

```python
对象名1 = 类名()
对象名2 = 类名()
对象名3 = 类名()
```

创建对象demo:

```python
class Hero(object): # 新式类定义形式
"""info 是⼀个实例⽅法，类对象可以调⽤实例⽅法，实例⽅法的第⼀个参数⼀般是self"""
	def info(self):
		"""当对象调⽤实例⽅法时，Python会⾃动将对象本身的引⽤做为参数传递到实例⽅法的第⼀个参数self⾥"""
        print(self)
        print("self各不同，对象是出处。")
        
# Hero这个类 实例化了⼀个对象 taidamier(泰达⽶尔)
taidamier = Hero()
# 对象调⽤实例⽅法info()，执⾏info()⾥的代码
# . 表示选择属性或者⽅法
taidamier.info()
print(taidamier) # 打印对象，则默认打印对象在内存的地址，结果等同于self
print(id(taidamier)) # id(taidamier) 则是内存地址的⼗进制形式表示
```

```python
<__main__.Hero object at 0x0000010CC70A7940>
self各不同，对象是出处。
<__main__.Hero object at 0x0000010CC70A7940>
1154390587712
```

#### 1.2.3 添加和获取对象的属性

属性即是特征.
对象属性既可以在类外⾯添加和获取，也能在类⾥⾯添加和获取。

```python
class Hero(object):
    """定义了⼀个英雄类，可以移动和攻击"""
    def move(self):
        """实例⽅法"""
        print("正在前往事发地点...")
    def attack(self):
        """实例⽅法"""
        print("发出了⼀招强⼒的普通攻击...")
# 实例化了⼀个英雄对象 泰达⽶尔
taidamier = Hero()
# 给对象添加属性，以及对应的属性值
taidamier.name = "泰达⽶尔" # 姓名
taidamier.hp = 2600 # ⽣命值
taidamier.atk = 450 # 攻击⼒
taidamier.armor = 200 # 护甲值
# 通过.成员选择运算符，获取对象的属性值
print("英雄 %s 的⽣命值 :%d" % (taidamier.name, taidamier.hp))
print("英雄 %s 的攻击⼒ :%d" % (taidamier.name, taidamier.atk))
print("英雄 %s 的护甲值 :%d" % (taidamier.name, taidamier.armor))
# 通过.成员选择运算符，获取对象的实例⽅法
taidamier.move()
taidamier.attack()
```
**问题：**

> 对象创建并添加属性后，能否在类的实例⽅法⾥获取这些属性呢？
> 如果可以的话，应该通过什么⽅式？

**在⽅法内通过self获取对象属性:**

```python
class Hero(object):
    """定义了⼀个英雄类，可以移动和攻击"""
    def move(self):
        """实例⽅法"""
        print("正在前往事发地点...")
    def attack(self):
        """实例⽅法"""
        print("发出了⼀招强⼒的普通攻击...")
    def info(self):
        """在类的实例⽅法中，通过self获取该对象的属性"""
        print("英雄 %s 的⽣命值 :%d" % (self.name, self.hp))
        print("英雄 %s 的攻击⼒ :%d" % (self.name, self.atk))
        print("英雄 %s 的护甲值 :%d" % (self.name, self.armor))
# 实例化了⼀个英雄对象 泰达⽶尔
taidamier = Hero()
# 给对象添加属性，以及对应的属性值
taidamier.name = "泰达⽶尔" # 姓名
taidamier.hp = 2600 # ⽣命值
taidamier.atk = 450 # 攻击⼒
taidamier.armor = 200 # 护甲值
# 通过.成员选择运算符，获取对象的实例⽅法
taidamier.info() # 只需要调⽤实例⽅法info()，即可获取英雄的属性
taidamier.move()
taidamier.attack()
```

**问题：**

> 创建对象后再去添加属性有点不合适，有没有简单的办法，可以在创建对象的时候，就已经拥有这些属性？

#### 1.2.4 魔法方法:\_\_init\_\_()⽅法

在Python中，\_\_xx\_\_()的函数叫做魔法⽅法，指的是具有特殊功能的函数。

**\_\_init\_\_() ⽅法的作⽤：初始化对象。 类似java中的构造函数**

```python
class Hero(object):
    """定义了⼀个英雄类，可以移动和攻击"""
    # Python 的类⾥提供的，两个下划线开始，两个下划线结束的⽅法，就是魔法方法。
    # 如果类⾯没有写__init__⽅法，Python会⾃动创建，但是不执⾏任何操作。
    # 如果为了能够在完成⾃⼰想要的功能，可以⾃⼰定义__init__⽅法，
    # 所以⼀个类⾥⽆论⾃⼰是否编写__init__⽅法 ⼀定有__init__⽅法。
    def __init__(self):
        """__init__⽅法，⽤来做变量初始化 或 赋值 操作，在类实例化对象的时候调用"""
        self.name = "泰达⽶尔" # 姓名
        self.hp = 2600 # ⽣命值
        self.atk = 450 # 攻击⼒
        self.armor = 200 # 护甲值
    def move(self):
        """实例⽅法"""
        print("正在前往事发地点...")
    def attack(self):
        """实例⽅法"""
        print("发出了⼀招强⼒的普通攻击...")
# 实例化了⼀个英雄对象，并⾃动调⽤__init__()⽅法
taidamier = Hero()
# 通过.成员选择运算符，获取对象的实例⽅法
taidamier.info() # 只需要调⽤实例⽅法info()，即可获取英雄的属性
taidamier.move()
taidamier.attack()
```

**说明：**

+ \_\_init\_\_() ⽅法，在创建⼀个对象时默认被调⽤，不需要⼿动调⽤
+ \_\_init\_\_(self) 中的self参数，不需要开发者传递，python解释器会⾃动把当前的对象引⽤传递过去。

**问题：**

>在类的⽅法⾥定义属性的固定值，则每个对象实例变量的属性值都是相同的。
>⼀个游戏⾥往往有很多不同的英雄，能否让实例化的每个对象，都有不同的属性值呢？

#### 1.2.5 有参数的\_\_init\_\_()方法

```python
class Hero(object):
    """定义了⼀个英雄类，可以移动和攻击"""
    def __init__(self, name, skill, hp, atk, armor):
        """ __init__() ⽅法，⽤来做变量初始化 或 赋值 操作"""
        # 英雄名
        self.name = name
        # 技能
        self.skill = skill
        # ⽣命值：
        self.hp = hp
        # 攻击⼒
        self.atk = atk
        # 护甲值
        self.armor = armor
    def move(self):
        """实例⽅法"""
        print("%s 正在前往事发地点..." % self.name)
    def attack(self):
        """实例⽅法"""
        print("发出了⼀招强⼒的%s..." % self.skill)
    def info(self):
        print("英雄 %s 的⽣命值 :%d" % (self.name, self.hp))
        print("英雄 %s 的攻击⼒ :%d" % (self.name, self.atk))
        print("英雄 %s 的护甲值 :%d" % (self.name, self.armor))
# 实例化英雄对象时，参数会传递到对象的__init__()⽅法⾥
taidamier = Hero("泰达⽶尔", "旋⻛斩", 2600, 450, 200)
gailun = Hero("盖伦", "⼤宝剑", 4200, 260, 400)
# 不同对象的属性值的单独保存
print(id(taidamier.name))
print(id(gailun.name))
# 同⼀个类的不同对象，实例⽅法共享
print(id(Hero.move))
```

**说明：**

+ 通过⼀个类，可以创建多个对象，就好⽐ 通过⼀个模具创建多个实体⼀样
+ \_\_init\_\_(self) 中，默认有1个参数名字为self，如果在创建对象时传递了2个实参，那么 \_\_init\_\_(self) 中出了self作为第⼀个形参外还需要2个形参，例如 \_\_init\_\_(self,x,y)

**注意：**

1. 在类内部获取 属性 和 实例⽅法，通过self获取；
2. 在类外部获取 属性 和 实例⽅法，通过对象名获取。
3. 如果⼀个类有多个对象，每个对象的属性是各⾃保存的，都有各⾃独⽴的内存地址；
4. 但是实例⽅法是所有对象共享的，只占⽤⼀份内存空间。类会通过self来判断是哪个对象调⽤了实例⽅法。*（print(id(Hero.move))）*

#### 1.2.6 魔法方法：\_\_str\_\_() 方法

当使⽤print输出对象的时候，默认打印对象的内存地址。如果类定义了\_\_str\_\_⽅法，那么就会打印从在这个⽅法中 return 的数据。**类似java中的toString()函数**

```python
class Hero(object):
    """定义了⼀个英雄类，可以移动和攻击"""
    def __init__(self, name, skill, hp, atk, armor):
        """ __init__() ⽅法，⽤来做变量初始化 或 赋值 操作"""
        # 英雄名
        self.name = name # 实例变量
        # 技能
        self.skill = skill
        # ⽣命值：
        self.hp = hp # 实例变量
        # 攻击⼒
        self.atk = atk
        # 护甲值
        self.armor = armor
    def move(self):
        """实例⽅法"""
        print("%s 正在前往事发地点..." % self.name)
    def attack(self):
        """实例⽅法"""
        print("发出了⼀招强⼒的%s..." % self.skill)
        # def info(self):
        # print("英雄 %s 的⽣命值 :%d" % (self.name, self.hp)
        # print("英雄 %s 的攻击⼒ :%d" % (self.name, self.atk
        # print("英雄 %s 的护甲值 :%d" % (self.name, self.arm
    def __str__(self):
        """
        这个⽅法是⼀个魔法⽅法 (Magic Method) ，⽤来显示信息
        该⽅法需要 return ⼀个数据，并且只有self⼀个参数，当在
        """
        return "英雄 <%s> 数据： ⽣命值 %d, 攻击⼒ %d, 护甲值 %d " % (self.name, self.hp,self.atk,self.arm)
taidamier = Hero("泰达⽶尔", "旋⻛斩", 2600, 450, 200)
gailun = Hero("盖伦", "⼤宝剑", 4200, 260, 400)
# 如果没有__str__ 则默认打印 对象在内存的地址。
# 当类的实例化对象 拥有 __str__ ⽅法后，那么打印对象则打印 __str__
print(taidamier)
print(gailun)
# 查看类的⽂档说明，也就是类的注释
print(Hero.__doc__)
```

**说明：**

+ 当使⽤print输出对象的时候，默认打印对象的内存地址。如果类定义了 \_\_str\_\_(self) ⽅法，那么就会打印从在这个⽅法中 return的数据
+ \_\_str\_\_ ⽅法通常返回⼀个字符串，作为这个对象的描述信息

#### 1.2.7 魔法方法：\_\_del\_\_()方法

创建对象后，python解释器默认调⽤ \_\_init\_\_() ⽅法；
当删除对象时，python解释器也会默认调⽤⼀个⽅法，这个⽅法为 \_\_del\_\_() ⽅法

```python
class Hero(object):
    # 初始化⽅法
    # 创建完对象后会⾃动被调⽤
    def __init__(self, name):
        print('__init__⽅法被调⽤')
    	self.name = name
    # 当对象被删除时，会⾃动被调⽤
    def __del__(self):
        print("__del__⽅法被调⽤")
        print("%s 被 GM ⼲掉了..." % self.name)
# 创建对象
taidamier = Hero("泰达⽶尔")
# 删除对象
print("%d 被删除1次" % id(taidamier))
del(taidamier)
print("--" * 10)
gailun = Hero("盖伦")
gailun1 = gailun
gailun2 = gailun
print("%d 被删除1次" % id(gailun))
del(gailun)
print("%d 被删除1次" % id(gailun1))
del(gailun1)
print("%d 被删除1次" % id(gailun2))
del(gailun2)
```

**说明：**

+ 当有变量保存了⼀个对象的引⽤时，此对象的引⽤计数就会加1；
+ 当使⽤del() 删除变量指向的对象时，则会减少对象的**引⽤计数**。如果对象的引⽤计数不为1，那么会让这个对象的引⽤计数减1，当对象的引⽤计数为0的时候，则对象才会被真正删除（内存被回收）。

## 2. 面向对象（二）继承
### 2.1 继承的概念

**继承**是面向对象编程（OOP）的核心概念之一，它允许一个类（称为子类或派生类）通过继承方式获得另一个类（称为父类或基类）的属性和方法。

### 2.2 单继承：⼦类只继承⼀个⽗类

```python
# 1. 师⽗类
class Master(object):
    def __init__(self):
    	self.kongfu = '[古法煎饼果⼦配⽅]'
    def make_cake(self):
   		print(f'运⽤{self.kongfu}制作煎饼果⼦')
# 2. 徒弟类
class Prentice(Master):
	pass

# 3. 创建对象daqiu
daqiu = Prentice()
# 4. 对象访问实例属性
print(daqiu.kongfu)
# 5. 对象调⽤实例⽅法
daqiu.make_cake()
```

**说明：**

+ 虽然⼦类没有定义 \_\_init\_\_ ⽅法初始化属性，也没有定义实例⽅法，但是⽗类有。所以只要创建⼦类的对象，就默认执⾏了那个继承过来的 \_\_init\_\_ ⽅法

**总结:**

+ ⼦类在继承的时候，在定义类时，⼩括号()中为⽗类的名字
+ ⽗类的属性、⽅法，会被继承给⼦类

### 2.3 多继承:⼦类继承多个⽗类

所谓多继承意思就是⼀个类同时继承了多个⽗类。

```python
# 创建师父类
class Master(object):
    def __init__(self):
    	self.kongfu = '[古法煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
# 创建学校类
class School(object):
    def __init__(self):
    	self.kongfu = '[新东方煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
class Prentice(School, Master):
    pass

daqiu = Prentice()
print(daqiu.kongfu)
daqiu.make_cake()
```

**说明：**

+ 多继承可以继承多个⽗类，也继承了所有⽗类的属性和⽅法
+ 注意：如果多个⽗类中有同名的 属性和⽅法，则默认使⽤第⼀个⽗类的属性和⽅法（根据类的魔法属性\_\_mro\_\_的顺序来查找）
+ 多个⽗类中，不重名的属性和⽅法，不会有任何影响。

### 2.4 子类重写父类的同名属性和方法

```python
class Master(object):
    def __init__(self):
    	self.kongfu = '[古法煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
class School(object):
    def __init__(self):
    	self.kongfu = '[⿊⻢煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
# 独创配⽅
class Prentice(School, Master):
    def __init__(self):
    	self.kongfu = '[独创煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
daqiu = Prentice()
print(daqiu.kongfu)
daqiu.make_cake()
print(Prentice.__mro__)
```

> ⼦类和⽗类具有同名属性和⽅法，默认使⽤⼦类的同名属性和⽅法。

### 2.5 子类调用父类同名属性和方法

```python
class Master(object):
    def __init__(self):
    	self.kongfu = '[古法煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
class School(object):
    def __init__(self):
    	self.kongfu = '[新东方煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
class Prentice(School, Master):
    def __init__(self):
    	self.kongfu = '[独创煎饼果⼦配⽅]'
    def make_cake(self):
        # 如果是先调⽤了⽗类的属性和⽅法，⽗类属性会覆盖⼦类属性，故在
        self.__init__()
        print(f'运⽤{self.kongfu}制作煎饼果⼦')
    # 调⽤⽗类⽅法，但是为保证调⽤到的也是⽗类的属性，必须在调⽤⽅法前
    def make_master_cake(self):
        Master.__init__(self)
        Master.make_cake(self)
    def make_school_cake(self):
        School.__init__(self)
        School.make_cake(self)
daqiu = Prentice()
daqiu.make_cake()
daqiu.make_master_cake()
daqiu.make_school_cake()
daqiu.make_cake()
```

> ⽆论何时何地，self都表示是⼦类的对象。在调⽤⽗类⽅法时，通过传递self参数，来控制⽅法和属性的访问修改。



### 通过super()来调用父类中的方法

```python
class Master(object):
def __init__(self):
self.kongfu = '[古法煎饼果⼦配⽅]'
def make_cake(self):
print(f'运⽤{self.kongfu}制作煎饼果⼦')
class School(Master):
def __init__(self):
self.kongfu = '[⿊⻢煎饼果⼦配⽅]'
def make_cake(self):
print(f'运⽤{self.kongfu}制作煎饼果⼦')
# ⽅法2.1
# super(School, self).__init__()
# super(School, self).make_cake()
# ⽅法2.2
super().__init__()
super().make_cake()
class Prentice(School):
def __init__(self):
self.kongfu = '[独创煎饼果⼦技术]'
def make_cake(self):
self.__init__()
print(f'运⽤{self.kongfu}制作煎饼果⼦')
# ⼦类调⽤⽗类的同名⽅法和属性：把⽗类的同名属性和⽅法再次封装
def make_master_cake(self):
Master.__init__(self)
Master.make_cake(self)
def make_school_cake(self):
School.__init__(self)
School.make_cake(self)
# ⼀次性调⽤⽗类的同名属性和⽅法
def make_old_cake(self):
# ⽅法⼀：代码冗余；⽗类类名如果变化，这⾥代码需要频繁修改
# Master.__init__(self)
# Master.make_cake(self)
# School.__init__(self)
# School.make_cake(self)
# ⽅法⼆: super()
# ⽅法2.1 super(当前类名, self).函数()
# super(Prentice, self).__init__()
# super(Prentice, self).make_cake()
# ⽅法2.2 super().函数()
super().__init__()
super().make_cake()
daqiu = Prentice()
daqiu.make_old_cake()
```

**说明：**

>⼦类继承了多个⽗类，如果⽗类类名修改了，那么⼦类也要涉及多次修改。⽽且需要重复写多次调⽤，显得代码臃肿。
>
>使⽤super() 可以逐⼀调⽤所有的⽗类⽅法，并且只执⾏⼀次。调⽤顺序遵循 mro 类属性的顺序。
>
>如果继承了多个⽗类，且⽗类都有同名⽅法，则默认只执⾏第⼀个⽗类的(同名⽅法只执⾏⼀次，⽬前super()不⽀持执⾏多个⽗类的同名⽅法)
>
>super() 在Python2.3之后才有的机制，⽤于通常单继承的多层继承



## 3. 面向对象（三）多态
### 3.1 私有属性和私有方法

在Python中，可以为实例属性和⽅法设置私有权限，即设置某个实例属性或实例⽅法不继承给⼦类。
故事：daqiu把技术传承给徒弟的同时，不想把⾃⼰的钱(2000000个亿)继承给徒弟，这个时候就要为 钱 这个实例属性设置私有权限。
设置私有权限的⽅法：在属性名和⽅法名 前⾯ 加上两个下划线 __。

```python
class Master(object):
    def __init__(self):
    	self.kongfu = '[古法煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
class School(object):
    def __init__(self):
    	self.kongfu = '[新东方煎饼果⼦配⽅]'
    def make_cake(self):
    	print(f'运⽤{self.kongfu}制作煎饼果⼦')
class Prentice(School, Master):
    def __init__(self):
    	self.kongfu = '[独创煎饼果⼦配⽅]'
        # 定义私有属性
        self.__money = 2000000
    # 定义私有⽅法
    def __info_print(self):
        print(self.kongfu)
        print(self.__money)
    def make_cake(self):
        self.__init__()
        print(f'运⽤{self.kongfu}制作煎饼果⼦')
    def make_master_cake(self):
        Master.__init__(self)
        Master.make_cake(self)
    def make_school_cake(self):
        School.__init__(self)
        School.make_cake(self)
# 徒孙类
class Tusun(Prentice):
	pass
daqiu = Prentice()
# 对象不能访问私有属性和私有⽅法
# print(daqiu.__money)
# daqiu.__info_print()
xiaoqiu = Tusun()
# ⼦类⽆法继承⽗类的私有属性和私有⽅法
# print(xiaoqiu.__money) # ⽆法访问实例属性__money
# xiaoqiu.__info_print()
```

注意：

> 私有属性和私有⽅法只能在类⾥⾯访问和修改。

### 3.2 修改私有属性的值

+ 如果需要修改⼀个对象的属性值，通常有2种⽅法
+ 私有属性不能直接访问，所以⽆法通过第⼀种⽅式修改，⼀般的通过第⼆种⽅式修改私有属性的值：定义⼀个可以调⽤的公有⽅法，在这个公有⽅法内访问修改。

```python
class Master(object):
    def __init__(self):
    	self.kongfu = "古法煎饼果⼦配⽅"
    def make_cake(self):
    	print("[古法] 按照 <%s> 制作了⼀份煎饼果⼦..." % self.kongfu)
        
class School(object):
    def __init__(self):
    	self.kongfu = "现代煎饼果⼦配⽅"
    def make_cake(self):
        print("[现代] 按照 <%s> 制作了⼀份煎饼果⼦..." % self.kongfu)
        
class Prentice(School, Master):
    def __init__(self):
        self.kongfu = "猫⽒煎饼果⼦配⽅"
        # 私有属性，可以在类内部通过self调⽤，但不能通过对象访问
        self.__money = 10000
    # 现代软件开发中，通常会定义get_xxx()⽅法和set_xxx()⽅法来获取
    # 返回私有属性的值
    def get_money(self):
    	return self.__money
    # 接收参数，修改私有属性的值
    def set_money(self, num):
    	self.__money = num
    def make_cake(self):
    	self.__init__()
        print("[猫⽒] 按照 <%s> 制作了⼀份煎饼果⼦..." % self.kongfu)
    def make_old_cake(self):
        Master.__init__(self)
        Master.make_cake(self)
  	def make_new_cake(self):
        School.__init__(self)
        School.make_cake(self)
   
class PrenticePrentice(Prentice):
	pass

damao = Prentice()
# 对象不能访问私有权限的属性和⽅法
# print(damao.__money)
# damao.__print_info()
# 可以通过访问公有⽅法set_money()来修改私有属性的值
damao.set_money(100)
# 可以通过访问公有⽅法get_money()来获取私有属性的值
print(damao.get_money())
```

### 3.3 多态

多态指的是⼀类事物有多种形态，（⼀个抽象类有多个⼦类，因⽽多态的概念依赖于继承）。

+ 定义：多态是⼀种使⽤对象的⽅式，⼦类重写⽗类⽅法，调⽤不同⼦类对象的相同⽗类⽅法，可以产⽣不同的执⾏结果
+ 好处：调⽤灵活，有了多态，更容易编写出通⽤的代码，做出通⽤的编程，以适应需求的不断变化！
+ 实现步骤：
  + 定义⽗类，并提供公共⽅法
  + 定义⼦类，并重写⽗类⽅法
  + 传递⼦类对象给调⽤者，可以看到不同⼦类执⾏效果不同

```python
class Dog(object):
    def work(self): # ⽗类提供统⼀的⽅法，哪怕是空⽅法
    print('指哪打哪...')
class ArmyDog(Dog): # 继承Dog类
    def work(self): # ⼦类重写⽗类同名⽅法
    print('追击敌⼈...')
class DrugDog(Dog):
    def work(self):
    print('追查毒品...')
class Person(object):
    def work_with_dog(self, dog): # 传⼊不同的对象，执⾏不同的
    dog.work()
ad = ArmyDog()
dd = DrugDog()
daqiu = Person()
daqiu.work_with_dog(ad)
daqiu.work_with_dog(dd)
```

### 3.4 类属性和实例属性

在前⾯的例⼦中我们接触到的就是实例属性（对象属性），顾名思义，类属性就是 类 所拥有的属性，它被所有 类 的 实例对象 所共有，在内存中只存在⼀个副本，这个和java中类的静态属性有点类似。对于公有的类属性，在类外可以通过 类 和 实例对象 访问

**类属性**

```python
class People(object):
    name = 'Tom' # 公有的类属性
    __age = 12 # 私有的类属性
p = People()
print(p.name) # 正确
print(People.name) # 正确
print(p.__age) # 错误，不能在类外通过实例对象访问私有的类属性
print(People.__age) # 错误，不能在类外通过类对象访问私有的类属性
```

**实例属性(对象属性)**

```python
class People(object):
    address = '⼭东' # 类属性
    def __init__(self):
        self.name = 'xiaowang' # 实例属性
        self.age = 20 # 实例属性
p = People()
p.age = 12 # 实例属性
print(p.address) # 正确
print(p.name) # 正确
print(p.age) # 正确
print(People.address) # 正确
print(People.name) # 错误
print(People.age) # 错误
```

**通过实例(对象)去修改类属性**

```python
class People(object):
    country = 'china' #类属性
print(People.country)
p = People()
print(p.country)
p.country = 'japan'
print(p.country) # 实例属性会屏蔽掉同名的类属性
print(People.country)
del p.country # 删除实例属性
print(p.country)
```

**总结**

如果需要在类外修改 类属性 ，必须通过 类对象 去引⽤然后进⾏修改。

如果通过实例对象去引⽤，会产⽣⼀个同名的 实例属性 ，这种⽅式修改的是 实例属性 ，不会影响到 类属性 ，并且之后如果通过实例对象去引⽤该名称的属性，实例属性会强制屏蔽掉类属性，即引⽤的是 实例属性 ，除⾮删除了该 实例属性 。

### 3.5 静态方法和实例方法

#### 3.5.1 类⽅法

是类对象所拥有的⽅法，需要⽤修饰器 @classmethod 来标识其为类⽅法，对于类⽅法，第⼀个参数必须是类对象，⼀般以 cls 作为第⼀个参数（当然可以⽤其他名称的变量作为其第⼀个参数，但是⼤部分⼈都习惯以'cls'作为第⼀个参数的名字，就最好⽤'cls'了），能够通过实例对象和类对象去访问。

```python
class People(object):
    country = 'china'
    #类⽅法，⽤classmethod来进⾏修饰
    @classmethod
    def get_country(cls):
    	return cls.country
p = People()
print(p.get_country()) #可以⽤过实例对象引⽤
print(People.get_country()) #可以通过类对象引⽤
```

类⽅法还有⼀个⽤途就是可以对类属性进⾏修改：

```python
class People(object):
    country = 'china'
    #类⽅法，⽤classmethod来进⾏修饰
    @classmethod
    def get_country(cls):
    	return cls.country
    @classmethod
    def set_country(cls,country):
    	cls.country = country
p = People()
print(p.get_country()) #可以⽤过实例对象访问
print(People.get_country()) #可以通过类访问
p.set_country('japan')
print(p.get_country())
print(People.get_country())
```

结果显示在⽤类⽅法对类属性修改之后，通过类对象和实例对象访问都发⽣了改变

#### 3.5.2 静态⽅法

需要通过修饰器 @staticmethod 来进⾏修饰，静态⽅法不需要多定义参数，可以通过对象和类来访问。

```python
class People(object):
    country = 'china'
    @staticmethod
    #静态⽅法
    def get_country():
    return People.country
p = People()
# 通过对象访问静态⽅法
p.get_contry()
# 通过类访问静态⽅法
print(People.get_country())
```



#### 3.5.3 总结

1. 从类⽅法和实例⽅法以及静态⽅法的定义形式就可以看出来，类⽅法的第⼀个参数是类对象cls，那么通过cls引⽤的必定是类对象的属性和⽅法；
2. 实例⽅法的第⼀个参数是实例对象self，那么通过self引⽤的可能是类属性、也有可能是实例属性（这个需要具体分析），不过在存在相同名称的类属性和实例属性的情况下，实例属性优先级更⾼。
3. 静态⽅法中不需要额外定义参数，因此在静态⽅法中引⽤类属性的话，必须通过类实例对象来引⽤。

