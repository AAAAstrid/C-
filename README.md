# Csharp Note
c#语法笔记，自存用，比较混乱，持续更新中

### 开头

namespace解决方案：大文件夹


# 数据类型

按照取值范围大小排序 

查看默认值：
```c#
Console.WriteLine(default(bool));
```

# 隐式转换

```plain
//c2转换成i2,i2储存转换后的c2
i2 = c2
```
 大范围装小范围——小范围的变量能转换成大范围的，反之不可以。 
#### 整型有符号：long int short sbyte

在涵盖范围的前提下，有符号可以隐式转换成无符号

#### 整型无符号：ulong uint ushort byte

无符号 无法 隐式转换成 有符号

#### 浮点数：decimal double float

浮点数可以装载任何类型的整数

decimal类型无法隐式转换成double或float

float可以隐式转换成double

#### 特殊类型：bool char string

不存在隐式转换

char没法隐式储存其他类型的变量

char 可以隐式转换成整型和浮点型

string 和 bool不参与转换规则


## 显式转换

### 括号强转

括号内为要强制转换的类型 

一定要注意范围，不然可能有异常

bool和string无法括号强转

```c#
short s = 1;
i = (int)l; 
```
### Parse法：string强转其他

变量类型.Parse("字符串")

```c#
int i4 = int.Parse("123"); 
```
### Convert法：各类型间强转

Convert.To目标类型（变量或常量）

```c#
int a = Convert.ToInt32("12");
```
ToSByte
ToInt16

ToInt32

ToInt64

### toString法：其他转string

变量.toString()；

str = 'A'.toString();

字符串拼接时自动调用该方法 你

# String 类


## 字符串转换为char数组

```c#
string str = "abcd"
Console.WriteLine(str[0]);
//转为char数组
char[] chars = str.ToCharArray();
Console.WriteLine(Chars[1]);
```

## 字符串拼接 Format

```c#
str = string.Format("{0}{1}",1,3333);
Console.WriteLine(str);
```

## 正向查找字符位置 IndexOf
返回他们的下标
```c#
str = "abcdefg";
int index = str.IndexOf("a");
Console.WriteLine(index); 
//结果:0
```

## 反向查找指定字符位置 LastIndexOf
找不到则返回-1
```c#
str = "abcde"
index = str.LastIndexOf("c");
Console.WriteLine(index);
//返回结果：2
```

## 去除指定位置后的字符 Remove

Remove（开始位置索引）
Remove（开始位置索引，字符个数）
```c#
str = "abcdsa";
String a = str.Remove(4); //去除第5个位置之后的字符
Console.WriteLine(str); //结果：abcd
str = str.Remove(1,1);
Console.WriteLine(str); 
```


字符串声明时可以为空

```C#
string sexStr = "";
```
## 字符串内插

如果在字符串的左引号前添加 `$`，则可以在大括号之间的字符串内包括变量

```plain
Console.WriteLine($"Hello {aFriend}");
```


## Trim删除空格

方法：

Trim：删除空格

TrimStart：删除前导空格

TrimEnd：删除尾随空格

```c#
string greeting = "      Hello World!       ";
Console.WriteLine($"[{greeting}]");


string trimmedGreeting = greeting.TrimStart();
Console.WriteLine($"[{trimmedGreeting}]");


trimmedGreeting = greeting.TrimEnd();
Console.WriteLine($"[{trimmedGreeting}]");


trimmedGreeting = greeting.Trim();
Console.WriteLine($"[{trimmedGreeting}]");
```
输出：
```plain
[      Hello World!       ]
[Hello World!       ]
[      Hello World!]
[Hello World!]
```


## Replace替换

*.Replace("要替换的字符串","替换后的字符串")

## ToUpper大写/ToLower小写
```c#

```

## Contains查找字符串

找到返回true，否则false

例：

```c#
string songLyrics = "You say goodbye, and I say hello";
Console.WriteLine(songLyrics.Contains("goodbye"));
Console.WriteLine(songLyrics.Contains("greetings"));
```
输出
```plain
True
False
```

## 字符串截取Substring
Substring(开始位置)
Substring(开始位置，指定个数)
```c#
str = str Substring(2,3);
```

## 字符串切割



## StringBuilder
处理字符串的公共类
修改字符串而不创建新的对象

引用 System.Text 命名空间
```c#
using System.Text;
```
使用
StringBuilder(字符串，容量)
```c#
StringBuilder str = new StringBuilder("123123",100);
```
获得容量Capicity
获得字符长度Length
```c#
Console.WriteLine(str.Capacity);
Console.WriteLine(str.Length);
```
增删查改替换
```c#
//增：Append
str.Append("444");
str.AppendFormat("{0}{1}",100,999);
//插入
str.Insert(0,"字符串");
//删
str.Remove(0,10);
//清空
str.Clear();
//查
str[0]; //访问第1个字符
//改
str[0] = 'A'; //把第1个字符改为A
//替换
str.Replace("要修改的字符","修改后的字符")
```
重新赋值stringBuilder：
```c#
str.Clear();
str.Append("123123");
```
判断StringBuilder是否和某一字符串相等
```c#
str.Equals("123123");
```

## 值类型与引用类型

**引用类型**： string，数组，类

储存在堆空间，相互赋值是将两者指向同一个地址

string重新赋值时，会在堆中重新分配空间

**值类型**：其他，结构体

储存在栈空间，相互赋值时将内容拷贝一份放在栈空间

# 计算

乘法和除法的优先级高于加法和减法。

整数除法始终生成整数结果，即使预期结果有小数或分数部分也是如此。

# 数组

### 声明

声明方式1：变量类型[] 数组名；    只是声明数组，并没有开放

```C#
int[] arr1;
```
声明方式2：变量类型[] 数组名 = new 变量类型[数组长度]；
```c#
int[] arr2 = new int[5];
```
声明方式3：变量类型[] 数组名 = new 变量类型[数组长度]{内容1，内容2......}；
```c#
int[] arr3 = new int[5]{1,2,3,4,5};
```
声明方式4：变量类型[] 数组名 = new 变量类型[]{内容1，内容2......}；
```c#
int[] arr3 = new int[]{1,2,3,4,5};
```
声明方式5：变量类型[] 数组名 = {内容1，内容2......}；
```c#
int[] arr3 = {1,2,3,4,5};
```
### 二维数组

#### 声明

//变量类型[,] 数组变量名

```c#
int[,] arr;
```
//变量类型[,] 数组变量名 = new 变量类型[行数,列数];
```c#
int[,] arr2 = new int[3,3];
```
变量类型[，] 数组变量名 = new 变量类型[,]{
{0行内容1,0行内容2,0行内容3......}，

{1行内容1,1行内容2,1行内容3......}

```c#
int[,] arr3 = new int[,]{{1，2，3},
                         {4，5，6},
                         {7，8，9}};                                       {4，5，6},
```
#### 获取数组长度

```c#
array.GetLength()
```
得到行：array.GetLength(0);
得到列：array.GetLength(1);

获取数组元素：

```c#
array[0,1];
array[1,2];
```



## 分支

### if else条件语句 

不识别缩进

```c#
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```
### while循环



# 集合

### 用[]访问索引

```c#
var names = new List<string> { "Aaaa", "Ana", "Felipe" };
names[0]
```
### count属性确定列表长度

```c#
Console.WriteLine($"The list has {names.Count} people in it");
```
### `IndexOf` 方法搜索列表项

```c#
var index = names.IndexOf("Felipe");
if (index != -1)
{
  Console.WriteLine($"The name {names[index]} is at index {index}");
}
var notFound = names.IndexOf("Not Found");
Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");
```
### Sort方法排序

```c#
names.Sort();
foreach (var name in names)
{
  Console.WriteLine($"Hello {name.ToUpper()}!");
}
```
输出
```plain
Hello AAAA!
Hello BILL!
Hello FELIPE!
Hello MARIA!
```
## 记录

结构与类相似，区别于类

```c#
public record Person(string FirstName, string LastName);


public static class Program
{
    public static void Main()
    {
        Person person = new("Nancy", "Davolio");
        Console.WriteLine(person);
        // output: Person { FirstName = Nancy, LastName = Davolio }
    }


}
```
## 注释

### ///三杠注释

在类中声明后，可以在创建对象时看见注释

```c#
///<summary>
///注释内容
///</summary>
```


# 枚举

被命名的整型常量的集合

### 每个枚举名都有默认值，逐次向下加

如果枚举名的值重置，那么向下的值也会在此基础上加

```c#
enum E_自定义枚举名
{
  自定义枚举名 = 5 //第一个枚举名
  自定义枚举名1 //6
}
```
### namespace语句块中声明枚举

不能再函数语句块中声明枚举，比如if for 

```c#
enum E_MonsterType
{
  Normal, //1
  Boss,   //2
}
```
### 枚举的使用

声明枚举变量

自定义枚举类型 变量名 = 默认值

```c#
//默认值为 自定义枚举类型.枚举名 
E_MonsterType MonsterType = E_MonsterType.Normal
```
枚举和Switch是天生一对
```c#
switch(monsterType)
{
  case E_MonsterType.Normal;
    break;
  case E_MonsterType.Normal;
    break;
  default:
    break;
}
```
### 枚举的类型转换

枚举转int

```c#
int i = (int)playerType;
Console.WriteLine(i)
```
int转枚举
```plain
playerType = 0;
```
枚举转String
```c#
string str = playerType.ToString();
```
String转枚举
```c#
//方法：parse(要转换的枚举类型，转换用的字符串)
//（E_playerTyper)：通过括号转换成需要对应的类型
playerTyper = （E_playerTyper)Enum.Parse(Typeof(E_PlayerType),"Other");
```
### 在游戏开发中

对象很多时候有许多状态

如玩家有一个动作状态，需要用一个变量或者标识来表示当前玩家处于哪种状态：1行走 2待机 3跑步 4跳跃......

枚举可以帮助我们更清楚分清状态的含义

# 转义字符

用来表示特殊含义的字符

常用转义字符

### 引号\' \"

```c#
string str = "\'哈哈哈\'";
output:'哈哈哈'
```
### 换行\n

```c#
str = "1231\n234";
output:
1231
234
```
### 斜杠\\

```c#
str = "哈\\哈哈";
output:哈\哈哈
```
### 制表符\t（一个tab键）

```c#
str = "哈\t哈哈";
output:哈  哈哈
```
### 光标退格\b

### 空字符\0

### 警报音\a

### 取消转义字符：加@符号

## 可空类型

公式：

```c#
< data_type> ? <variable_name> = null;
//例：
int? num1 = null;
int? num2 = 45;
double? num3 = new double?();
double? num4 = 3.14157;
```


# 函数

## **语法：**

static 返回数据类型 函数名 （参数类型1 参数名1，参数类型2，参数名2，......）{

函数的代码逻辑......

return 返回值;（如果有返回类型）

}

**注意：**

函数名：帕斯卡命名法（每个单词首字母大写）

参数不是必须的，可以有0-n个

参数名用驼峰命名法

当返回类型不为void时，必须通过return返回值


### ref和out：参数的修饰符

ref和out传入的参数a在函数内部被修改时，让外部的参数a也被修改，使用和声明一致，条件不同

#### ref
传入的变量必须初始化，但是在函数内部可改可不改
```C#
static void ChangeValueRef(ref int value){
	value = 3;
}
```
调用方法：参数前要加**ref**
```c#
ChangeValueRef(ref a);
```
#### out
传入的变量不用初始化，但是在函数内部必须赋值
```c#
static void ChangeValueOut(out int value){
	value = 99;
}
```


### 变长参数params
params int[] 意味着可以传入n个int参数 n可以等于0 传入的参数会存在在arr数组中
params 后面必接数组
数组类型可以任意
函数参数中只能最多出现一个params，并且放在最后的参数那，前面可以有n个其他类型参数
```c#
static int Sum(String name,int a ,params int[] arr){
n 
}
```

### 参数默认值
有参数默认值的函数可以不传入参数
```c#
static void Speak(String str = "参数默认值"){
Console.Writeline(str);
}
```
调用时可以不传参数：
```c#
Speak();
```
有默认值的参数必须写在最后：
```c#
static void Speak2(string a ; string name = "AAA"){

}
```

### 函数重载
函数名相同
参数的数量/类型/顺序不同，有无ref和out

```c#
static float CalcSum(ref float f ,int a){
return f + a;
}
```

```c#
static float CalcSum(int a,int b,params int[] arr){
return 1;
}
```


### 递归函数
函数自己调用自己
正确的递归函数
	必须有结束调用的条件
	

```c#
static void Fun(){
	if (a > 10){  //结束递归的条件
		return;
	}
	Console.WriteLine(a);  //函数要求
	++a;  //递归后的变化
	Fun(a);  //构造递归
}
```

# 结构体struct
自定义变量类型
数据和函数的集合
在结构体中，可以申明各种变量和方法
作用：用来表现存在关系的数据集合
**帕斯卡命名法**

**构造函数**
	没有返回值
	名字和结构体名相同
	必须有参数
	如果申明了构造函数 必须在其中对所有变量数据初始化

结构体中的方法不需要加static关键字

学生数据的 结构体
```c#
struct Student{
	//变量
	int age;
	bool sex;
	int number;
	string name;
	//构造函数
	public Student(int age ,bool sex,int number,string name){
	this.age = age;
	this.sex = sex;
	this.number = number;
	this.name = name;
	}
	
	//结构体中的方法不需要加static关键字
	
}
```
结构体的声明：
```c#
static void Main(string[] args){
	//结构体声明几个方法：
	//方法1：直接声明默认调用无参构造
	Student s1;
	s1.age = 10;
	s1.sex = false;
	//方法2：利用构造函数声明
	Student s2 = new Student(18,false,)
}
```


# 类
***
## 随机数Random
```c#
Random rd = new Random();
int i =rd.Next();
```

## 类声明

### **结构：**
访问修饰符 class 类名
{
	特征——成员变量
	行为——成员方法
	保护特征——成员属性
	构造函数
	析构函数
	运算符重载
	静态成员
}
注意
	帕斯卡命名法
	同一个语句块中不同类不能重名
	不能在类中对自己实例化（在class 中 new 一个自己）

**实例：**
```c#
class Person
{
	//特征——成员变量
	public string name = "人名";
	public int age;
	public E_SexType sex;
	//行为——成员方法
	//保护特征——成员属性
	//构造函数
	//析构函数
	//运算符重载
	//静态成员
	
}
```

### **成员变量**
不赋值时会采用默认值

### **构造函数**
	没有返回值
	函数名必须与类名相同
	一般接个public
	可以被重载
	类允许自己声明无参构造函数，结构体不行
	不声明无参构造而用有参构造，则默认无参会失效
```c#
//无参构造
public Person()
{
	name = "人名"
}
//有参构造
public Person(string name)
{
	this.name = name;
} 
```

**特殊声明方法**
先调用冒号后的构造函数，后调用括号里的
```c#
public Person(int age,string name):this(name)
{
	Console.WriteLine("Person两个参数构造函数调用");
}
```

### 成员方法（函数）
不加static关键字
必须通过实例化对象后使用
有访问修饰符

```c#
public void speak(string str)
{
Console.WriteLine("{0}说{1}",name,str)
}
```
**使用**成员方法
```c#
Person p = new Person();
p.name = "人名";
p.age = 18;
p.speak("我爱你");
```


### 成员属性

帕斯卡命名法
```c#
public string Name
{
	get
	{
		//可以添加一些逻辑规则，如解密
		return name;
	}
	set
	{
		//可以加密
		//value关键字表示外部传入的值
		name = value;
	}
}
```

**使用**成员属性
```c#
Person p = new Person();
p.Name = "人名";  //set属性
Console.Write(p.Name);  //get属性
```

**自动属性**
外部可以获取但不可以修改，又没什么特殊处理的变量，则可以使用自动属性
```c#
public float Height
{
	get;
	set;
}
```

### 析构函数
```c#
~Person()
{

}

```

**垃圾回收机制**

```c#

GC.collect();

```

### 索引器
让对象像数组一样通过索引访问其中元素
语法：访问修饰符 返回值 this[参数类型 参数名，参数类型 参数名.......]
{

}
声明：
```c#
public Person this[int index]
{
	get
	{
		//可以根据需求写逻辑
		//成员变量有friends[]这个数组
		return friends[index];
	}
	set
	{
		friends[index] = value;
	}
}
```

使用：
```c#
Person p = new Person();
p[0] = new Person(); //访问set方法
Console.WriteLine(p[0]);  //访问set方法
```

### 静态static
关键字static
#### 静态成员
用static 修饰的成员变量、方法、属性等，称为静态成员
静态成员在程序开始运行时便分配内存空间，直到程序结束时，静态成员的内存才会释放

**注意**
	静态函数 中直接不能使用 非静态成员，成员实例化后才可以使用
	非静态函数 可以使用 静态成员


```c#
//静态成员变量
public static float PI = 3.1415926f;
//静态成员方法
public static float Cala(float r)
{
	return PI * r * r;
}

```

**常量const**
	一种特殊的静态
	与static都可以通过类名点出使用
	const必须初始化

#### 静态类
用static修饰的类
只能包含静态成员
不能被实例化

**静态构造函数**
调用类时会率先使用

```c#
static class Static
{
	//静态成员变量
	public static int testIndex = 0;
	//静态构造函数
	static Static()
	{
		Console.WriteLine("静态构造函数");
		testInt = 200;
	}
}
```

### 拓展方法
为现有的 非静态 变量类型、类 或 结构体 添加 新方法
一定写在静态类中
静态函数
第一个参数为拓展目标，用this修饰
如果拓展方法名与类中方法重名，则使用类中原方法，拓展方法失效

实例：为 int 拓展一个方法
```c#
public static void SpeakValue(this int value)
{
	//拓展方法的逻辑
	Console.WriteLine("唐老狮为int拓展的方法" + value);
}
```

使用拓展方法：
```c#
int i = 10;
i.SpeakValue();
```

### 运算符重载operator
让自定义类和结构体能够使用运算符
公共静态方法
返回值写在operator前
逻辑处理自定义
**注意**
条件运算符需要成对实现
一个符号可以重载多次
不能使用ref 和out

**不可重载的运算符**
```
逻辑与（&&） 逻辑或（||）
索引符 []
强转运算符 （）
特殊运算符：
点.
三目运算符 ? :
赋值符号=
```

**语法**
public static 返回类型 operator 运算符（参数列表）

实例：
```c#
class Point
{
	public int x;
	public int y;

	public static Point operator + (Point p1,Point p2)
	{
		Point p = new Point();
		p.x = p1.x + p2.x;
		p.y = p1.y + p2.y;
		
		return p;
	}
}
```
使用：
```c#
Point p = new Point();
p.x = 1;
p.y = 1;
Point p2 = new Point();
p2.x = 2;
p2.y = 2;
Point p3 = p + p2;
```


### 内部类
一个类中再声明一个类

```c#
class Person
{
	//内部类
	public class Body
	{
		Arm leftArm;
		Arm rightArm;
	}
	class Arm
	{
	}

}
```

使用内部类：要用包裹者点出自己
```c#
Person p = new Person();
Person.Body = new Person.Body(); //声明内部类
```

### 分部类partial
把一个类分成几部分声明
**注意：**
访问修饰符一致
分部类中不能有重复成员

```c#
partical class Student
{
	public bool sex;
	public string name;
}

partical class Student
{
	public int number;
	public void Speak(string str)
}
```

### 分部方法
将方法的申明和实现分离
访问修饰符一致

```c#
partical void Speak(string str);

partical void Speak()
{
	//实现逻辑
}
```

## 继承
被继承的类：父类 基类 超类
继承的类： 子类 派生类

子类可以使用父类方法

### 语法
class 类名 ： 被继承类名
```c#
class Teacher
{
	public string name;
	public int number;
	public void SpeakName()
	{
		Console.WriteLine(name);
	}
}
//继承teacher类
class Teaching :Teacher
{
	public string subject;
	public void Speaksubject()
	{
		Console.WriteLine(""继承的基本规则);
	
	}
}
```

**访问修饰符对继承的影响**
public 是不是子类都能用
privited 子类不能用
protected 子类可以用，外部不能用

### 里氏替换原则
任何父类出现的地方，子类都可以替代
注意：
	能用父类容器装子类对象
	但不能用子类容器装父类对象

实例：
```c#
//父类
class GameObject 
{
}
//子类
class Player:GameObject
{
	public void PlayerAtk()
	{
		Console.WriteLine("玩家攻击")
	}
}

class Monster:GameObject
{
	public void PlayerAtk()
	{
		Console.WriteLine("怪物攻击")
	}
}
```
声明：
```c#
static void Main(String[] args)
{
	Console.WriteLine("里氏替换原则");
	//父类容器装在子类对象
	GameObject player = new Player();
	GameObject monster = new Monster();
}
```

**is关键字**
判断一个对象是否为指定类对象
返回值bool 是为true 否为false
语法：类对象 is 类名
**as关键字**
将一个对象转换为指定类对象
返回值：指定类对象
转换成功返回直到类型对象，失败返回null
语法：类对象 as ，类名


```c#
if(player is Player)
{
	Player p = player as Player;
	p.PlayerAtk();
}
else if (player is Monster)
{

}
```

### 继承中的构造函数
申明子类对象时
先执行父类的构造函数
再执行子类的构造函数
子类实例化时，默认调用父类的无参构造，如果父类的无参构造被有参构造替代，则会报错
解决方法：
1.始终保持无参构造
通过base关键字调用父类构造

```c#
//父类
class GameObject
{
	public GameObject()
	{
		Console.WriterLine("GameObject的构造函数");
	}
}
//子类
class Player:GameObject
{
	public Player()
	{
		Console.WriteLine("Player的构造函数");
	}
}
//孙类
class MainPlayer : Player
{
	public MainPlayer()
	{
		Console.WriteLine("MainPlayer的构造函数");
	}

}
```


**base调用指定父类构造函数**
```c#
class Father{
	public Father(int i)
	{
		Console.WriteLine("Father构造");
	}
}

class Son:Father
{
	public Son(int i) : base(i)
	{
	}
	public Son(int i,string str):this(i)
	{
	}
}

```

### 万物之父Object
所有类型的基类
容器可以用来装载所有的子类
引用类型用is和as来转换
值类型用强转
```c#
object 0 = new Son();

//引用类型用is和as来转换
is(0 i Son)
{
	(o as Son).Speak();
}

object arr = new int[10];
int[] ar = arr as int[];

//值类型用强转
object o2 = 1f;
float f1 = (float)02;
```

特殊的string类型

```c#
object str = "123";
string str2 = str as string;
```

#### 装箱拆箱
把object存值类型（装箱）
	把值类型用引用类型存储
	堆内存会迁移到栈内存中
再把object转为值类型 （拆箱）
	把引用类型存储的值类型取出来
	堆内存会迁移到栈内存中
好处
	不确定类型时可以方便参数的存储与传递
坏处
	存在内存迁移，增加性能消耗
	
```c#
//装箱
object v = 3;
//拆箱
int intValue = (int)v;
```

#### object中的静态方法
##### Equals相等判断
两个类型的地址是否相等
```c#
Console.WriteLine(Object.Equal(1,1));
//true
```
结果相等为true，不等为false

##### ReferenceEquals
比较两个引用对象的引用地址是否相同
如果比较值类型则返回false
```c#
Test t = new Test();
Test t2 = t;
Console.WriteLine(Object.ReferenceEquals(t,t2));
//true
```

#### 普通方法
##### GetType
获取对象运行时的类型
```c#
Type type = t.GetType();
```

##### MemberwiseClone
获取对象的浅拷贝对象：
一个与老对象引用变量一致的新对象
```c#
public Test Clone()
{
	return MemberwiseClone() as Test;
}
```

#### 虚方法
Equals
比较两者是否为同一个引用

GetHashCode
获取哈希值

ToString
返回当前对象代表的字符串

### 密封类sealed
用sealed关键字修饰的类
让类无法再继承

```c#
sealed class Son:Father
{
}
```

### 密封方法
密封关键字sealed 修饰的重写函数
作用：让虚方法或者抽象方法之后不能再被重写
和override一起出现

```c#
public sealed override void Eat()
{
	base.Eat();
}
```

## 多态
让继承同一父类的子类们，执行相同方法时有不同表现
函数重载
**vob:**
v：virtual（虚函数）
o：override（重写）
b:  base（父类）

override关键字
重写虚函数
虚函数可以选择是否写逻辑

```c#
class GameObject
{
	public string name;
	public GameObject(string name)
	{
		this.name = name;
	}
}

public virtual void Atk()
{
	Console.WriteLine("游戏对象进行攻击");
}

class Player:GameObject
{
	public Player(string name):base(name)
	{
	}

	//override重写虚函数
	public override void Atk()
	{
		//通过base关键字保留父类的行为
		base.Atk();
		//后面再加行为
		Console.WriteLine("玩家对象进行攻击");
	}

}

```

## 抽象abstract
abstract关键字修饰
### 抽象类
不能被实例化的类
可以包含抽象方法
继承抽象类必须重写其抽象方法
其子类遵循里氏替换原则，用抽象类装子类

```c#
abstract class Thing
{
	public string name;
}
//子类可以继承
class Water :Thing
{

}```

### 抽象方法（纯虚方法）
又称纯虚方法
只能在抽象类中声明
没有方法体
不能是私有的
继承后必须继承抽象方法，用override重写

```c#
abstract class Fruits
{
	public string name;
	public abstract void Bad();
}

class Apple:Fruits
{
	public override void Bad()
	{
		//实现逻辑
	}
}
```

## 接口interface
行为的抽象规范

**申明规范：**
	不包含成员变量
	只包含方法、属性、索引器、事件
	成员不能被实现
	成员可以不用写访问修饰符，不能是私有的
	接口不能继承类，但可以继承另一个接口
**使用规范：**
	类可以继承多个接口
	类继承接口后，必须实现接口中所有成员
	遵循里氏转换原则

**语法**
	interface 接口名
	{
	}
接口命名规范：帕斯卡命名法前加个I

```c#
interface IFly
{
	//方法
	void Fly();
	//属性
	string Name
	{
		get;
		set;
	}
	
	//索引器
	int this[int index]
	{
		get;
		set;
	}
	
	event Action doSomthing;
	
}
```

使用接口：继承接口
实现的接口函数，可以加virtual再在子类重写
```c#
class Animal{}
//一个类可以同时继承一个类和多个接口
class Person : Animal,IFly
{
	//实现接口的方法
	
	public virtual void Fly()
	{
	}
	string Name
	{
		get;
		set;
	}
}
```

接口遵循里氏替换原则：
```c#
IFly f = new Person();
```

可以继承接口后，把接口的函数变成抽象函数，供子类去实现


# 抽象类和接口的区别
**相同点**
	都可以被继承
	都不能直接实例化
	都可以包含方法申明
	子类必须实现未实现的方法
	都遵循里氏替换原则
**不同点**
	抽象类中可以有构造函数：接口中不能
	抽象类只能被单一继承，接口可以被继承多个
	抽象类可以有成员变量，接口中不能
	抽象类中可以申明成员方法，虚方法，抽象方法，静态方法；接口中只能申明没有实现的抽象方法
	抽象类方法可以使用访问修饰符，接口中不建议写，默认public
**如何选择抽象类和接口**
	表示对象的用抽象类，表示行为拓展的用接口
	不同对象拥有的共同行为，我们往往可以使用接口来实现

# 结构体和类的区别

结构体是值，类是引用
存储位置：结构体在栈上，类在堆上
**结构体**
	只具备封装特性，不具备继承和多态特性
	不能用protected保护访问修饰符
	成员变量不能申明指定初始值
	不能申明无参构造函数，析构函数
	申明有参构造后，无参构造不会被顶掉
	不能被继承
	需要在构造函数中初始化所有成员变量
	不能用static修饰
	不能在自己内部申明和自己一样的结构体变量
	可以继承接口

**如何选择类和结构体**
	有继承和多态——选择类
	对象是数据集合时——优先考虑结构体，如坐标、向量、旋转
	

# 命名空间
组织和重用代码
类在命名空间中申明
语法：
namespace
{
类
}
命名空间可以分开来写
一个命名空间中不允许有重复类名
不同命名空间中可以有同名类

```c#
namespace MyGame
{
	class GameObject
	{
	}

}

namespace MyGame
{
	class Player:GameObject
	{
	}
}
```


不同命名空间相互使用的 需要引用命名空间或指明出处
```c#
//引用命名空间
using MyGame;

//指明出处
MyGame.GameObject g = new MyGame.GameObject();
```


# 排序

## 冒泡排序
两两比较
交换位置
m个循环，有多少个数，就循环多少轮

```c#
for (int m = 0;m< arr.Length; m++){ //m个循环
	for (int n = 0;n<arr.Length-1; n++){
	//两两比较
	if(arr[n] > arr[n+1]){
	//交换位置
	int temp = arr[n];
	arr[n] = arr[n+1];
	arr[n+1] = temp;
	}
}
```

**优化算法**
1.确定位置的数字 不用比较了
2.在外声明一个标识isSort，来表示该轮是否有交换
```c#
bool isSort = false;
for (int m = 0;m< arr.Length; m++){ 
//n<arr.Length-1-m
//让已经确定位置的数字不再比较
	for (int n = 0;n<arr.Length-1-m; n++){
		//两两比较
		if(arr[n] > arr[n+1]){
		//
		isSort = true;
		//交换位置
		int temp = arr[n];
		arr[n] = arr[n+1];
		arr[n+1] = temp;
		}
	}
	//一轮过后，若isSort还是false，则代表是最终序列，跳出排序
	if(!isSort){
	break;
	}
}
```

# 脚本文件

申明一个接口，类，结构体，就新建一个脚本文件

# 面向对象七大原则

**高内聚低耦合**
	减少类内部，对其他类的调用
	减少模块之间的复杂度

**单一职责原则**
类应该专注于单一的功能

**开闭原则OCP**
拓展开放：模块的行为可以被拓展
修改关闭：少修改模块的源代码
举例：继承

**里氏替换原则**
任何父类出现的地方，子类都可以替代

**依赖倒转原则**
要依赖于抽象，不要依赖于具体的实现
接口，抽象类

**迪米特原则/最少知识原则**
一个对象的成员，尽可能少直接于其他类建立关系
为了降低耦合性

**接口分离原则**
一个接口尽量只提供一个对外功能

**合成复用原则**
尽量使用对象组合，而非继承达到目的
继承关系是强耦合，组合关系是低耦合


# 数据集合

## ArrayList
可以存储任意类型的数据
### 申明
需要引用命名空间using.System.Collections
```c#
ArrayList array = new ArrayList();
```

### 增删查改

增：Add
```c#
array.Add(1);
array.Add("123");
array.Add(true);
array.Add(new object());
array.Add(new Test());

//把另一个list容器加到后面
ArrayList array2 = new ArrayList();
array.AddRange(array2);
//(插入位置，插入数据)
array.Insert(1,"123"); 
```

删：remove
```c#
//移除指定元素，从头找
array.Remove(1);
//移除指定位置元素
array.RemoveAt(2);
//清空
array.clear(;)
```

查
```c#
//得到指定位置的元素
Console.WriteLine(array[0]);
//查看元素是否存在
array.Contains("123");//返回布尔值
//正向查找元素位置
array.IndexOf(true); //找到返回位置，找不到返回-1
//反向查找元素位置
array.LestIndexOf(true);//返回从头开始的索引数
```

改
```c#
//修改指定位置元素
array[0] = "999";
```

### 遍历
```c#
//长度
array.Count
//容量
array.Capacity
//遍历
for(int i = 0;i<array.Count;i++)
{
	Console.WriteLine(array[i]);
}
```

迭代器遍历
```c#
Foreach(object item in array)
{
	Console.WriteLine(item);
}
```

### 装箱拆箱
往其中储存值类型：装箱
将值类型对象取出来转换使用：拆箱
```c#
int i = 1;
array[0] = i; //装箱
i = array[0]; //拆箱
```

## Stack
c#为我们封装好的类
stack是栈存储容器，一种先进后出的数据结构
先存入的数据后获取，后存入的数据先获取
栈是先进后出

### 申明
要引用命名空间System.Collections
```c#
Stack stack = new Stack();
```

### 增取查改

增：压栈
```c#
stack.Push(1);
stack.Push("123");
stack.push(true);
```

取：弹栈
不存在删除的概念，会弹出栈顶的元素
```c#
stack.Pop();
```

查：无法查看指定元素的内容，只能查看栈顶的元素
```c#
//查看栈顶
stack.Peek();
//查看元素是否存在于栈中
stack.Contains(1);
//结果：true  
```

改：无法改变其中的元素，只能压和弹，或者清空
```c#
stack.clear();
```

### 遍历

foreach遍历
```c#
foreach(object item in stack)
{
	Console.WriteLine(item);
}
```

将栈转换为object数组遍历
```c#
object[] array = stack.ToArray();
for(int i = 0;i<array.Length; i++)
{
	Conso;e.WriteLine(array[i]);
}
```

循环弹栈：挨个把栈里的东西弹出来
```c#
while(stack.count>0)
{
	object o = stack.Pop();
	Console.Writeline(o);
}
```

### 装箱拆箱


## Queue
队列储存容器
先存入的数据先获取，后存入的数据后获取
先进先出

### 申明
引用命名空间System.Collections

```c#
Queue queue = new Queue();
```

### 增取查改

增
```c#
queue.Enqueue(1);
queue.Enqueue("123");
queue.Enqueue(1.4f);
```

取：不存在删的概念，取出先加入的对象
```c#
object v = queue.Dequeue();//取出1
```

查：
查看队列头部元素
```c#
v = queue.Peek();
```
查看元素是否存在于队列当中
```c#
queue.Contains(1.4f);
//结果：true
```

改：无法改变其中的元素，只有进出和清除
```c#
queue.Clear();
```

### 遍历

foreach遍历
```c#
foreach(objcet item i queue)
{
	Console.WriteLine(item);
}
```

将队列转换为object数组
```c#
object[] array = queue.ToArray()
for(int i = 0;i<arrat.Length;i++)
{
	Console.WriteLine(array[i]);
}
```

循环出列
```c#
while(queue.Count>0)
{
	object o = queue.Dequeue();
	Console.WriteLine(o);
}
```

### 装箱拆箱


## Hashatble
又称散列表，是基于键的哈希代码组织起来的键值对
使用键来访问集合中的元素

### 申明
引用命名空间 System.Collections
```c#
Hashtable hashtable = new Hashtable();
```

### 增删查改

增：能放任何类型，add（键，值）
不能出现相同的键
```c#
hashtable.Add(1,"123");
hashtable.Add("123",2);
hashtable.Add(true,false);
```

删：
只能通过键取删除
```c#
hashtable.Remove(1);
```
或者直接清空
```c#
hashtable.Clear();
```

查
通过键查看值，找不到会返回null
hashtable[键] ，返回值
```c#
hashtable[1];
//返回"123";
```
查看是否存在
```c#
//根据键检测
hashtable.Contains(1);
hashtable.ContainsKey(1);

//根据值检测
hastable.ContainsValue(12);
```

改：只能改键对应的值内容，不能修改键
```c#
hashtable[1] = 100.5f;
```
### 遍历
对数
```c#
hashtable.Count;
```
遍历所有键
```c#
foreach(object item in hashtable.Keys)
{
	Console.WriteLine("键" + item);
	Console.WriteLine("值" + hashtable[item]);
}
```

遍历所有值
```c#
foreach(object item in hashtable.Values)
{
	Console.WriteLine("值" + item);
}
```

键值对一起遍历
```c#
foreach(DictionaryEntry item in hashtable)
{
	Console.WriteLine("键" + item.Key + "值" + item.Value);
}
```

迭代器遍历法
```c#
IDictionaryEnumerator myEnumerator = hashtable.GetEnumrator();
bool flag = myEnumerator.MoveNext();
while(flag)
{
	Console.WriteeLine("键：" + myEnumerator.key + "值：" + myEnumerator.Value);
	flag = myEnumerator.MoveNext();
}
```

### 装箱拆箱
存在装箱拆箱

# 泛型
实现类型参数化，达到代码重用目的
相当于类型占位符

分类：泛型类和泛型接口
语法：
class 类名<泛型占位字母>
interface 接口名<泛型占位字母>
占位字母用帕斯卡命名法


## 泛型类
```c#
class TestClass<T>
{
	public T value;
}
```
使用泛型
```c#
static void main(string[] args)
{
	TestClass<int> t = new TestClass<int>();
	t.value = 10;
	
	TestClass<string> t2 = new TestClass<string>();
	t2.value = "123";
}
```

使用多个占位字母
```c#
class TestClass2<T1,T2,K,LL,Key>
{
	public T1 value1;
	public T2 value2;
	public K v3;
	public LL v4;
	public Key v5;
}
```
使用泛型类
```c#
TestClass2<int,string,float,double,TestClass<int>> t3 = new TestClass2<int,string,float,double,TestClass<int>> 
```

## 泛型接口

```c#
interface TestInterface<T>
{
	T Value
	{
		get;
		set;
	}
}
```
继承接口
```c#
class Test : TestInterface<int>
{
	public int value
}
```

## 泛型方法

申明
```c#
class Test2
{
	public void TestFun<T>(T value)
	{
		Console.WriteLine(value);
	}
	public T TestFun<T>(string v)
	{
		return default(T);
	}
}
```

使用
```c#
Test tt = new Test2();
tt.TestFun<string>("123123");
```



## 泛型约束
让泛型的类型有一定限制
where
语法：where 泛型字母:(约束的类型)
6种约束
	值类型：where 泛型字母:sturuct
	引用类型：where 泛型字母:class
	存在无参公共构造函数：where 泛型字母:new()
	一个类本身以及其派生类：where 泛型字母:类名
	某个接口的派生类：where 泛型字母：接口名
	另一个泛型本身以及其派生类型：where 泛型字母：另一个泛型字母

### 值类型约束
```c#
class Test1<T> where T:struct
{
	public T value;
	public void TestFun<K>(K v) where K:struct
	{
	}
}
```
使用
```c#
Test1<int> t = new Test1<int>();
```

### 引用类型约束
```c#
class Test2<T> where T:class
{
	public T value;
	public void TestFun<K>(K v) where K:class
	{
	}
}
```
使用
```c#
Test2<Random> t2 = new Test2<Random>();
```

公共无参构造函数
```c#
class Test3<T> where T:new()
{
	public T value;
	public void TestFun<k>(K k) where K : new()
	{
	
	}
}
```
使用
```c#
Test3<test1> t3 = new Test3<Test1>();
```

### 类约束
```c#
class Test4<T> where T: Test1
{
	public T value;
	public void TestFun<k>(K k) where K: Test1
	{
	}
}
```
使用
```c#
Test4<Test1> t4 = new Test4<Test2>();
```

### 接口约束
```c#
interface IFly
{
}
class Test4:IFly
{
}

//使用接口约束
class Test5<T> where T:IFly
{
}
```
使用
```c#
使用接口本身
Test5<IFly> t5 = new Test5<IFly>()；
或者派生类
t5.value = new Test4();
```

### 多个泛型约束
加多个where
```c#
class Test8<T,K> where T:class,new() where K:struct
{
}
```

## 常用泛型数据结构类

### List
封装好的一个类
可变类型的泛型数组
帮助我们实现了很多方法，比如泛型数组的增删查改

#### 申明
引用命名空间 using System.Collections.Generic

```c#
List<int> list == new List<int>();
```

#### 增删查改

增
```c#
list.Add(1);
list.Add(2);
list.Add(3);

指定位置插入(插入位置,插入元素)
list.Insert(0,99)
```

删
```c#
//移除指定元素
list.Remove(1);
//移除指定位置元素
list.RemoveAt(0);
```

查
```c#
得到指定位置的元素
Console.WriteLine(List[0]);
查看元素是否存在
list.Contains(1));
正向查找元素位置
int index = list.IndexOf(2);
反向查找元素
index = list.LastIndexOf(2);
```

改
```c#
list[0] = 99;
```

#### 遍历

长度和容量
```c#
list.Count;
list.Capacity;
```
循环遍历
```c#
for(int i = 0;i < list.Count;i++)
{
	Console.WriteLine(List[i]);
}
```

迭代器

```c#
foreach(int item in list)
{
	Console.WriteLine(item);
}
```

#### 排序

List自带排序方法sort()
```c#
List<int> list = new List<int>();
list.add(1);
list.add(5);
list.add(3);

list提供了排序方法
list.Sort();
for(int i = 0;i < list.Count; i++)
{
	Console.WriteLine(list[i]);
}
```

自定义类排序：继承排序接口
List的sort方法调用自定义类的CompareTo方法来排序
```c#
首先自定义类：
class Item : Icomparable<Item>
{
	public int money;
	public Item(int money)
	{
		this.money = money;
	}
	public int CompareTo(Item other)
	{
		返回值的含义：
		小于0：放在传入对象的前面
		等于0：保持当前的位置不变
		大于0：放在传入对象的后面

		if(this.money > other.money)
		{
			return 1;
		}
		else
		{
			return -1;
		}
		return 0;
	}
}

自定义类的排序：
List<Item> itemList = new List<Item>();
itemList.Add(new Item(11));
itemList.Add(new Item(1));
itemList.Add(new Item(33));
//排序方法
itemList.Sort();
```

自定义类使用lambad排序
```c#
shopItems.Sort(deIegate(ShopItem a,ShopItem b){
	if(a.id > b.id)
	{
		return -1;
	}
	else
	{
		return 1;
	}
});
```

匿名函数写sort
```c#
shopItems.Sort((a,b)=>
{
	return a.id > b.id ? 1 : -1;
});
```

### Dictionary字典
拥有泛型的Hashtable
基于哈希代码组织的键值对
键值对类型由任意类型变为可以指定类型
#### 申明
引用命名空间 System,Collections.Generic
```c#
Dictionary<int,string> dictionary = new Dictionary<int,string>();
```

#### 增删查改

增：不能出现相同的键
```c#
dictionary.Add(1,"123");
dictionary.Add(2,"222");
dictionary.Add(3,"333");
```

删：只能通过键去删除（键元素）
```c#
dictionary.Remove(1);
清空：
dictionary.Clear();
```

查：
```c#
1.通过键查看值，找不到会直接报错，不会返回null：
dictionary[2]; "222"
dictionary[4]; 报错

2.查看是否存在：
根据键检测：
dictionary.ContainsKey(1);
根据值检测：
dictionary.ContainsValue("1234");
```

#### 遍历



遍历所有键
```c#
foreach(int item in dictionary.Keys)
{
	Console.WriteLine(item);
	Console.WriteLine(dictionary[item]);
}
```

遍历所有值
```c#
foreach(string item in dictionary.Values)
{
	Console.WriteLine(item);
}
```

键值对一起遍历
```c#
foreach(KeyValuePair<int,string> item in dictionary)
{
	Console.WriteLine("键：" + item.Key + "值：" + item.Value);
}
```

### 顺序存储和链式存储

**线性表**
数组，ArrayList，stack，Queue，链表等等
**顺序存储**
用一组连续地址的存储单元依次存储线性表的各个数据元素
**链式存储**
用一组任意的存储单元存储线性表中的各个数据元素
单项链表，双向链表，循环链表

实现最简单的单项链表
```c#
头节点：
class LinkedNode<T>
{
	private T value;
	下一个存储元素：
	public LinkedNode<T> nextNode;
}

中间节点
class LinkedList<T>
{
	记录头节点：
	public LinkedNode<T> head;
	添加节点：
	public void Add(T value)
	{
		LinkedNode<T> node = new LinkedNode<T>(value);
		if(head == null)
		{
			head = node;
		}
		else
		{
			last,nextNode = node;
			last = node;
		}
	}
	
	删除节点：
	public void Remove(T value)
	{
		if(head == null)
		{
			return;
		}
		if(head.value.Equals(value))
		{
			head = head.nextNode;
			如果头节点被移除清空
			那证明只有一个节点，尾节点也要清空
			if(head == null)
			{
				last = null;
			}
			return;
		}
		
		LinkedNode<T> node = head;
		while(node.nextNode != null)
		{
			找到下一个节点
			if(node.nextNode.value.Equals(value))
			{
				让上一个节点指向当前节点的下一个节点
				跳过当前节点
				node.nextNode = node.nextNode.nextNode;
				break;
			}
			node = node.nextNode;
		}
	}
	
}
```
使用
```c#
LinkedNode<int> node = new LinkedNode<int>(1);
```

![[Pasted image 20250204013640.png]]


### LinkedList
可变类型的泛型双向链表

#### 申明
引用命名空间 System.Collections.Generic
```c#
LinkedList<string> linkedList = new Linkedlist<string>();
```

#### 增删查改

增
```c#
链表尾部添加元素:
linkedList.AddLast(10);
链表头部添加元素：
linkedList.AddFirst(20);

在某个节点后添加一个节点：
	1.先得到一个节点：
	LinkedListNode<int> n = linkedList.Find(20);
	2.插入节点
	LinkedList.AddAfter(n,15);
在某个节点之前添加一个节点：
	LinkedList.AddBefore(n,11);
```

删
```c#
移除头节点：
linkedList.RemoveFirst();
移除尾节点：
linkedList.RemovelLast();
移除指定节点：
linkedList.Remove(20);
清空:
linkedList.Clear();
```

查
```c#
头节点：
LinkedListNode<int> first = linkedList.First;
尾节点：
LinkedListNode<int> first = linkedList.First;
找到指定值的节点：无法通过下标获取，只能遍历
LinkedListNode<int> node = LinkedList.Find(3);
判断是否存在：
linkedList.Contains(1);
```

改：要先得到节点，再改变其中的值
```c#
linkedList.First.Value = 10l;
```

#### 遍历

foreach遍历
```c#
foreach(int item in linkedList)
{
	Console.WriteLine(item);
}
```
通过节点遍历
```c#
从头到尾：
LinkedListNode<int> nowNode = linkedList.First;
while(nowNode != null)
{
	Console.WriteLine(nowwNode.Value);
	nowNode = nowNode.Next;
}
从尾到头：
nowNode = linkedList.Last;
while(nowNode != null)
{
	Console.WriteLine(nowNode.Value);
	nowNode = nowNode.Previous;
}
```

### 泛型栈和队列

#### 申明
命名空间：System.Collections.Generic
使用上和之前的stack和queue一模一样
```c#
Stack<int> stack = new Stack<int>();
Queue<Object> queue = new Queue<object>();
```

## delegate委托

### 委托
函数的容器类
表示函数的变量类型

语法：访问修饰符 delegate 返回值 委托名（参数列表）
写在namespace和class语句块中，一般在namespace
访问修饰符默认（public）不写
不能在同一语句块中重名

委托常用在
1.作为类的成员
2.作为函数的参数

```c#
申明一个可以用来存储无参无返回值的容器：
delegate void MyFun();
有参有返回值：表示用来装载或者传递返回值为int、有一个int参数的函数的委托
delegate int MyFun1(int a);
```

委托装载：
```c#
static void Fun()
{
}
把函数Fun装在在f这个容器里：
MyFun f = new MyFun(Fun);

static int Fun2(int value)
{
	return value;
}
MyFun1 f1 = new Fun2;
```

调用委托f相当于调用函数Fun：
```c#
f.Invoke();
f1(1);
```

使用委托
```c#
class Test
{
	public MyFun fun;
	public MyFun2 fun2;

	public void TestFun(MyFun fun,MyFun2 fun2)
	{
		int i = 1;
		i*= 2;
		fun();
		fun2(i);
	}
}
```

委托变量可以存储多个函数
```c#
MyFun ff = Fun;
ff += Fun; 多存一次Fun，调用ff相当于调用两次Fun
ff();
```

增
```c#
public void AddFun(MyFun fun,MyFun2 fun2)
{
	this.fun += fun;
	this.fun2 += fun2;
}
```

删
```c#
public void RemoveFun(MyFUn fun.MyFun2 fun2)
{
	this.fun -= fun;
}
```

**系统自带的委托**
引用using System;
系统一共提供了16个参数的委托

Action无参无返回值
```c#
Action action = Fun;
action += Fun3;
action();
```

Func可返回指定类型
```c#
Func<string> funcString = Fun4;
```



泛型委托
```c#
delegate T MyFun3<T,K>(T v,K k);
```


### 事件event
一种特殊的变量类型
基于委托的存在，委托的安全包裹
相对于委托，不能在类外部赋值或调用
只能作为成员在于类和接口以及结构体中
相当于对委托进行封装

语法：访问修饰符 event 委托类型 事件名；

```c#
class Test
{
	//声明委托：
	public Action myFun;
	//声明事件成员变量：
	public event Action myEvent;

	public Test()
	{
		myFun = TestFun;
		myEvent = TestFun;
	}
	
	public void TestFun()
	{
	}
}
```

事件的使用和委托一模一样：
```c#
myEvent = TestFun;
myEvent += TestFun;
myEvent -= TestFun;
myEvent();
myEvent.Invoke();
myEvent = null;
```


## 协变逆变
用来修饰泛型的泛型字母，只有泛型接口和泛型委托能使用
**协变：** out
和谐的变化
如子类变父类，string 变成 object
**逆变：** in
不常规的变化
如父类变子类，object 变成 string

作用
用out修饰的泛型，只能作为返回值，不能作为参数
```c#
delegate T TestOut<out T>();
```
用in修饰的泛型，只能作为参数
```c#
delegate void TestIn(in T)(T t);
```
接口使用
```c#
interface Test<out T>
{
	T TestFun();
}
```

结合里氏替换原则理解
```c#
class Father{
}
class Son : Father{
}
```
里氏替换原则：
协变：父类能被子类替换
```c#
TestOut<Son> os =() =>
{
	return new Son();
};
TestOut<Father> of = os;
Father f = of();   返回的时os装的son函数
```
逆变：父类能被子类替换
```c#
TestIn<Father> iF =(value) =>
{
};
TestIn<Son> is = iF;

is(new Son());
```

# 匿名函数
没有名字的函数
与委托和事件配合使用

**声明**

无参无返回Action委托容器存储匿名函数
```c#
Action a = delegate()
{
	Console.WriteLine("匿名函数逻辑");
};
```

有参
```c#
Action<int,string> b = delegate(int a,string b)
{
	Console.WriteLine(a);
	Console.WriteLine(b);
}
```

有返回值
```c#
Func<string> c = delegate()
{
	return "123123";
}
Console.WriteLine(c());
```

**匿名函数作用：**

例子使用类Test：
```c#
class Test{
	public void Dosomthing(int a,Action fun)
	{
		Console.WriteLine(a);
		fun();
	}
	public Action GetFun()
	{
		return null;
	}
}
```
参数传递：
```c#
Test t = new Test();
Action ac = delegate()
{
	随参数传入的匿名函数逻辑
}
t.Dosomthing(100,delegate()
{
	在这里写匿名函数逻辑	
});
```

返回值
```c#
Action ac2 = t.GetFun();
ac();
t.GetFun()();  //t.GetFun()前部分执行委托，后部分()调用委托函数
```

**匿名函数的缺点：**
因为匿名函数没有名字，所以没办法指定移除某一个匿名函数

### lambad表达式
匿名函数的简写
语法：
(参数列表) =>
{
	//函数体
}

使用
```c#
无参无返回值的lambad表达式：
Action = () =>
{
	//这里写函数逻辑
}

有参数的：
Action<int> a2 = (int value) =>
{
	//函数逻辑
}

参数类型与委托和事件容器一致时可以省略
Action<int> a3 = (value) =>
{
	Console.WriteLine("省略参数类型的写法{0}",value);
}

有返回值有参数的：
Func<string,int> a4 = (value) =>
{
	Console.WriteLine("有返回值有参数的表达式{0}",value)
}
```

#### 闭包
内层的函数可以引用包含在它外层的函数的变量
即使外层函数的执行已经终止
该变量提供的值并非变量创建时的值，而是在父函数范围内的最终值

```c#
class Test
{
	public event Action action;
	public Test()
	{
		int value = 10;
		action = () =>
		{
			Console.WriteLine(value);
		}

		for(int i =0; i<10;i++)
		{
			int index = i;
			action += () =>
			{
				Console.WriteLine(index);
			}
		}
	}
}
```


# 多线程

进程：
线程：操作系统能够运算调度的最小单位
多线程：代码多写管道
多线程使用的内存是共享的，都属于本应用的进程


语法：
引用命名空间 System.Threading
申明一个新的线程：
```c#
Thread t = new Thread(NewthreadLogic);
//启动线程
t.Start();
```
线程执行的代码需要封装道一个函数中
```c#
class Program{

	设置线程关闭开启变量：
	static bool isRuning = true;

	线程函数：
	static void NewThreadLogic()
	{
		while(isRuning)
		{
			Console.WriteLine("新开线程代码逻辑");
		}
		
	}
}
```

把线程设置为后台线程
```c#
t.IsBackground = true;
```

关闭释放线程
1.while循环中增加bool表示
```c#
isRuning = false;
Console.ReadKey();
```
2.线程提供的终止方法
```c#
t.Abort();
t = null;
```

**线程休眠**
单位：毫秒
```c#
Thread.Sleep(1000);
```

加锁避免同一内存区域可能出现的问题
```c#
while(true)
{
	lock()
	{
		Console.SetCursorPosition(0,0)'
		Console.ForegroundColor = ConsoleColor.Redl
		Console.Write("A");
	}
}
```


# 预处理器
编译器：翻译程序

预处理器指令，以#号开始的
指导编译器在编译开始时进行预处理

常用预处理器指令

define  undef 写在脚本文件最前面
```c#
#define
定义一个符号，类似于没有值的变量
#undef
取消定义一个符号

例子：
#define unity4
```

if else if else endif 
```c#
#if unity4
//如果有unity4符号，则执行这里的指令
Console.WriteLine("版本为unity4");
#elif unity2017
Console.WriteLine("版本为unity2017");
#else
Console.WriteLine("其他版本");
#endif
```

warning警告编译器
```c#
#warning 这个版本不合法
```
error 报错
```c#
#error 出现错误
```

# 反射
程序集是由编译器编译得到的，供进一步编译执行的中间产物
文件后缀为.dll（库文件）或.exe（可执行文件）

反射的作用：
可以在程序编译后获得信息
包括所有元数据和特性
实例化对象和操作对象
创建新对象，用这些对象执行任务

例子：
```c#
class Test
{
	private int i=1;
	public int j = 0;
	public string str = 123;
	public Test()
	{
	}

	public Test(int i)
	{
		this.i = i;
	}

	public Test(int i,string str):this(i)
	{
		this.str = str;
	}
}
```

**使用实例：**
获取对象的Type
1.GetType()方法
```c#
int a = 42;
Type type = a.GetType();
↑得到a的所有信息
```
2.typeof关键字传入类名
```c#
Type type2 = typeof(int);
```
3.通过类名获取type，类名必须包含命名空间
```c#
Type type3 = Type.GetType("System.Int32");
```

**使用反射：**
得到类的程序集信息：
```c#
type.Assembly;
```

获取类的所有公共成员MemberInfoo
```c#
//首先得到type
Type t = typeof(Test);
//需要引用命名空间using System.Reflection
MemberInfoo[] infos = t.GetMembers();
for(int i = 0;i < infos.Length;i++)
{
	Console.WriteLine(infos[i]);
}
```

获取类的所有公共构造函数并调用
1.获取所有构造函数ConstructorInfo
```c#
ConstructorInfo[] ctors = t.GetConstructors();
for(int i = 0;i<ctors.Length ; i++)
{
	Console.WriteLine(ctors[i]);
}
```

2.获取其中一个构造函数并执行
得到构造函数传入type数组，内容按顺序是参数类型
执行构造函数传入object数组，表示按顺序传入的类型

1.无参构造
```c#
ConstructorInfo info =t.GetConstructor(new Type[0]);
//无参构造没有参数传null
Test obj = info.Invoke(null) as Test;
```
2.有参构造
```c#
ConstructorInfo info2 = t.GetConstructor(new Type[] {new Type[]{typeof(int)}});
obj = info2.Invoke(new object[]{2})as Test;
```


获取类的公共成员变量
1.得到所有成员变量
```c#
FieldInfo[] fieldinfos = t.GetFields();
```
2.得到指定名称的公共成员变量
```c#
FieldInfo infoJ = t.GetField("j");
```
3.通过反射获取对象某个变量的值
```c#
infoJ.GetValue(test);
```
4.设置指定对象的变量的值
```c#
infoJ.SetValue(test,100);
```

获取类的公共成员方法
得到类的方法
```c#
Type strType = typeof(string);
MethodInfo[] methods = strType.GetMethods();
for(int i =0; i< methods.Length;i++)
{
	Console.WriteLine(methods[i]);
}
MethodInfo subStr = strType.GetMethod("Substring",new Type[] {typeof(int),typeof(int)});
```
调用该方法:
```c#
string str = "Hello";
subStr.Invoke(str,new object[]{7,5});
Console.WriteLine(result);
```

## Activator
用于快速实例化对象的类
用于将Type对象快捷实例化为对象
语法：
类名 对象名 = Activator.CreateInstance(类的Type名,参数值) as 类名

先得到Type
```c#
Type testType = typeof(Test);
```
然后快速实例化一个对象：
无参构造
```c#
Test testObj = Activator.CreateInstance(testType) as Test;
```
有参构造
```c#
testObj = Activator.CreateInstance(testType,99) as Test;
```

## Assembly
程序集类
用来加载其他程序集
三种加载其他程序集的函数
```c#
Assembly asembly2 = Assembly.Load("程序集名称");
Assembly asembly = Assembly.LoadFrom("包含程序集清单的文件的名称或路径");
Assembly asembly = Assembly.LoadFile("要加载的文件的完全限定路径");
```

使用
1.先加载一个指定程序集
路径前加@用来取消\的转义字符
```c#
Assembly asembly = Assembly.LoadFrom(@"路径地址");
Type[] types = assembly.GetTypes();
for(int i = 0; i < types.Length;i++)
{
	Console.WriteLine(types[i]);
}
```
2.再加载程序集中的一个类对象，之后才能使用反射
```c#
Type icon = asembly.GetType("名为Icon的类地址");
MemberInfo[] members =icon.GetMembers();
```

通过反射实例化一个icon对象
1.首先反射枚举
```c#
Type moveDir = asembly.GetType("枚举E_MoveDir的地址");
FieldInfo right = moveDir.GetField("Right");
```
实例化icon对象：
```c#
object iconObj = Activator.CreateInstance(icon,10,5,right.GetValue(null));
```
反射得到对象中的方法：
```c#
MethodInfo move = icon.GetMethod("Move");
```

# 特性
用于保存程序结构的某种特殊类型的类
为元数据添加额外信息

## 自定义特性
继承特性基类 Attribute
```c#
class MyCustomAttribute : Attribute
{
	public string info;

	public MyCustomAttribute(string info)
	{
		this.info = info;
	}
}
```

特性基本语法：
[特性名（参数列表）]
写在类、函数、变量的上一行

装载特性
```c#
[MyCustom("本特性的解释内容")]
class MyClass
{
	[MyCustom("这是一个成员变量")]
	public int value;
}
```

使用特性
```c#
MyClass mc = new MyClass();
Type t = mc.GetType();
```
判断是否使用某个特性（特性的类型，是否搜索继承链）
```c#
if(t.IsDefined(typeof(MyCustomAttributr),false))
{
	Console.WriteLine("该类型应用了MyCustome特性")
}
```
反射获取Type元数据中的所有特性
```c#
object[] array = t.GetCustomAttributes(true);
for(int i = 0; i<array.length;i++)
{
	if(array )
}
```

## **特性上挂特性：限制自定义特性的使用范围**
AttributrTargets：限制特性用在哪些地方
AllowMultiple：是否允许多个特性实例用在同一目标
Inherited：特性能否被派生类和重写成员继承
```c#
[AttributeUsage(AttributrTargets.Class|AttributrTargets.Struct,AllowMultiple = true,Inherited =true)]
public class MyCustom2Attribute : Attribute
{
}
```

## 系统自带特性：

过时特性：Obsolete
用于提示使用的方法等成员已经过时
true 使用该方法报错，false使用该方法时直接警告
```c#
[Obsolete("此方法已过时，请使用新方法Speak",true)]
public void OldSpeak(string str)
{
}

public void Speak()
{
}
```

调用者信息特性

# 迭代器
又称光标
一种设计模式
提供一股方法顺序访问遍历聚合对象的各个元素，而又不暴露起内部标识

关键接口：IEnumerator,IEnumerable
命名空间：using System.Collections

```c#
class CustomList : IEnumerable,IEnumerator
{
	private int[] list;
	public CustomList()
	{
		list = new int[]{1,2,3,4,5,6,7,8};
	}
	//接口IEnumerable的方法
	public IEnumerator GetEnumerator()
	{
		throw new NotImplementedException();
	}

	//接口IEnumerator的方法
	public object Current
	{
		get
		{
			return list[position];
		}
	}

	public bool MoveNext()
	{
		//移动光标
		++position;
		//是否溢出，溢出就不合法
		return position < list.Length;
	}

	//reset是重置光标
	public void Reset()
	{
		position = -1;
	}
}
```
使用迭代器
foreach本质：
先获取in后的对象的IEnumerator
调用对象其中的GetEnumerator方法
执行MoveNext方法，返回true，则得到Current然后复制给item
```c#
CustomList list = new CustomList();
foreach(int item in list)
{
	Console.WriteLine(item);
}
```

## 语法糖实现迭代器
语法糖：将复杂逻辑简单化，增加程序可读性
使用yield return语法糖
关键接口：IEnumerable
命名空间：using System.Colletions

```c#
class CustomList2 : IEnumerable
{
	private int[] list;
	public CustomList2()
	{
		list = new int []{1,2,3,4,5,6,7,8};
	}
	//接口IEnumerable的方法
	public IEnumerator GetEnumerator()
	{
		for(int i = 0;i<list.Length;i++)
		{
			yield return list[i];
		}
	}
}
```

# 特殊语法
## var隐式类型
可以标识任意类型的变量
不能作为类的成员，只能用于临时变量声明
必须初始化
```c#
var i =5;
var s = "123";
```

## 设置对象初始值
申明对象时，可以直接用大括号初始化公共成员变量和属性
实例：
```c#
class Person
{
	private int money;
	public bool sex;

	public string Name
	{
		get;
		set;
	}

	public int Age
	{
		get;
		set;
	}
}
```
初始化对象
```c#
Person p = new Person{sex = true;Age = 18,Name = "AAA"};
```

## 设置集合初始值
申明集合时，可以通过大括号直接初始化内部属性
```c#
int[] arrats = new int[]{1,23,5};
List<int> listInt = new List<int>({1,2,3,4});
List<Person> listPerson = new List<Person>(){
	new Person(200),
	new Person(100){Age = 10},
	new Person(1){sex = ture,Name = "AAA"}
}
Dictionary<int,string> dict = new Dictionary<int,string>(){
	{1,"A"},
	{2,"2"}
}
```

## 匿名类型
变量可以申明为自定义的匿名类型
```c#
var v = new{age = 10,money = 11,name ="A"};
```
## 可空类型
值类型赋值时不能为空
但申明时在值类型后加？可以赋值为空
```c#
int? c = null;
if(c.HasValue)
{
	Console.WriteLine(c);
	Console.WriteLine(c.Value);
}
```
安全获取可空类型的值
```c#
int? value = null;
//如果为空，默认返回值类型的默认值
Console.WriteLine(value.GetValueOrDefault());
//也可以指定一个默认值
Console.WriteLine(value.GetValueOrDefault(100));
```
引用类型也能用
```c#
object o =null;
o?.ToString();
```
## 空合并操作符
左边值 ?? 右边值
如果左边为null，就返回右边，否则返回左边
```c#
int? intV = null;
int intI = intV ?? 100; //结果为100
```
## 内插字符串
内插字符串
用$构造字符串，让字符串可以拼接变量
```c#
string name = "AAA";
Comesole.WriteLine($"名字:{name}") //结果：名字：AAA
```
## 单句逻辑省略写法
里面只有一行代码，则可以省略大括号
```c#
if(true)
	Console.WriteLine("123");
```
