# Java学习笔记

## 基础语法

### 注释

注释分为单行注释、多行注释和文档注释。

- 单行注释：//注释信息
- 多行注释：/*注释信息\*/
- 文档注释：/*\*注释信息**/

### 关键字

关键字：被Java语言赋予了特定含义的单词。

关键字特点：关键字的字母全部小写，常用的代码编辑器，针对关键字有特殊的颜色标记。

Java中所有的关键字

| 访问控制            | 类、接口、方法、变量、代码块修饰符 | 程序控制                 | 错误处理 | 基本类型         | 变量引用 | 包相关       | 保留字      |
| ------------------- | ---------------------------------- | ------------------------ | -------- | ---------------- | -------- | ------------ | ----------- |
| private(私有化)     | class(类)                          | for                      | try      | boolean(布尔型)  | new      | import(引入) | goto(跳转)  |
| protected(受保护的) | abstract(抽象)                     | break                    | catch    | byte(字节型)     | super    | package(包)  | const(静态) |
| default(缺省)       | extends(继承)                      | continue                 | finally  | char(字符型)     | this     |              |             |
| public(公共的)      | implements(实现)                   | do                       | throw    | short(短整型)    | void     |              |             |
|                     | interface(接口)                    | while                    | throws   | int(整型)        | null     |              |             |
|                     | final(不可改变)                    | if                       |          | long(长整形)     | true     |              |             |
|                     | strictfp(严格)                     | else                     |          | float(浮点型)    | false    |              |             |
|                     | static(静态)                       | switch                   |          | double(双精度型) |          |              |             |
|                     | transient(短暂)                    | case                     |          |                  |          |              |             |
|                     | synchronized(线程锁)               | default                  |          |                  |          |              |             |
|                     | volatile(易失)                     | instanceof(对象类型判断) |          |                  |          |              |             |
|                     | native(本地)                       | return                   |          |                  |          |              |             |
|                     | enum(枚举)                         | assert(断言)             |          |                  |          |              |             |

### 常量

常量分类

| 常量类型   | 说明                 | 举例                    |
| ---------- | -------------------- | ----------------------- |
| 字符串常量 | 用双引号括起来的内容 | "Hello World"，"程序员" |
| 整型常量   | 不带小数的数字       | 666，-53                |
| 小数常量   | 带小数的数字         | 3.14，-53.1             |
| 字符常量   | 用单引号括起来的内容 | 'A'，'0'，'我'          |
| 布尔常量   | 布尔值，表示真假     | 只有两个值：true，false |
| 空常量     | 一个特殊的值，空值   | 值是：null              |

空常量无法直接输出。

### 数据类型

Java语言是强类型语言，对每种数据都给出了明确的数据类型，不同的数据类型也分配了不同的内存空间所以他们表示的数据大小也是不一样的。

数据类型分为基本数据类型和引用数据类型。

基本数据类型分为数值型和非数值型。

数值型分为整数型（byte,short,int,long），浮点数型（float,double），字符型（char）。

非数值型有布尔类型（boolean）。

引用数据类型分为类（class），接口（interface），数组（[]）。

| 数据类型 | 关键字       | 内存占用（字节） | 取值范围                                                     |
| -------- | ------------ | ---------------- | ------------------------------------------------------------ |
| 整数     | byte         | 1                | -128~127                                                     |
|          | short        | 2                | -32768~32767                                                 |
|          | int(默认)    | 4                | -2的31次方~2的31次方-1                                       |
|          | long         | 8                | -2的63次方~2的63次方-1                                       |
| 浮点数   | float        | 4                | 负数：-3.402823E+38~-1.401298E-45;正数：1.401298E-45~3.402823E+38 |
|          | double(默认) | 8                | 负数：-1.797693E+308~-4.9000000E-324;正数：4.9000000E-324~1.797693E+308 |
| 字符     | char         | 2                | 0-65535                                                      |
| 布尔     | boolean      | 1                | true，false                                                  |

### 变量

变量：在程序运行过程中，其值可以发生改变的量。变量是内存中的一小块区域。

变量的定义格式：

数据类型 变量名 = 变量值

eg.  int a = 20;

变量必须先定义后使用。

在定义long类型的变量时，为防止整数过大，后面要加L；在定义float类型的变量时，为防止类型不兼容，后边要加F。

eg.   long a = 1000000000L;			float b = 3.14F;

### 标识符

标识符：就是给类，方法，变量等起名字的符号。

标识符的定义规则：由数字、字母、下划线(_)和美元符号($)组成；不能以数字开头；不能是关键字；区分大小写。

常见的命名约定：

小驼峰命名法：标识符是由一个单词的时候，首字母大写；标识符是由多个单词组成的时候，第一个单词首字母小写，其余单词首字母大写。

大驼峰命名法：标识符是由一个单词的时候，首字母大写；标识符是由多个单词组成的时候，每个单词的首字母大写。

小驼峰命名法是给方法和变量进行命名；大驼峰命名法是给类进行命名。

### 类型转换

类型转换分为自动类型转换和强制类型转换。

自动类型转换是把一个表示数据范围小的数值或者变量赋值给另一个表示数据范围大的变量。

eg.   double c = 10;

强制类型转换是把表示数据范围大的数值或变量赋值给另一个表示数据范围小的变量。

格式：目标数据类型 变量名 = (目标数据类型)值或变量;

eg.   int d = (int)3.14;

## 运算符

运算符：对常量或者变量进行操作的符号。

表达式：用运算符把常量或者变量连接起来符合Java语法的句子就可以称为表达式。不同运算符连接起来的表达式体现的是不同类型的表达式。

### 算术运算符

算术表达式中包含多个基本数据类型的值时，整个算术表达式的类型会自动进行提升。

提升规则：

byte类型，short类型和char类型将被提升到int类型。

整个表达式的类型将自动提升到表达式中最高等级操作数同样的类型。

等级顺序：byte,short,char->int->long->float->double

当“+”操作中出现字符串时，这个“+”是字符串连接符，而不是算术运算。

### 逻辑运算符

| 符号 | 作用     | 说明                                         |
| ---- | -------- | -------------------------------------------- |
| &    | 逻辑与   | a&b，a和b都为true，结果为true，否则为false   |
| \|   | 逻辑或   | a\|b，a和b都为false，结果为false，否则为true |
| ^    | 逻辑异或 | a^b，a和b结果不同为true，相同为false         |
| !    | 逻辑非   | !a，结果和a的结果正好相反                    |
| &&   | 短路与   | 作用和&相同，但是由短路效果                  |
| \|\| | 短路或   | 作用和 \| 相同，但是有短路效果               |

- 逻辑与&，无论左边真假，右边都要执行。

  短路与&&，如果左边为真，右边执行；如果左边为假，右边不执行。

- 逻辑或 | ，无论左边真假，右边都要执行。

  短路或 ||，如果左边为假，右边执行；如果左边为真，右边不执行。

### 三目运算符

格式：关系表达式?表达式1:表达式2;

eg.   a>b?a:b;

计算规则：首先计算关系表达式的值，如果值为true，表达式1的值就是运算结果；如果值为false，表达式2的值就是运算结果。

### 所有运算符的优先级

| 优先级 | 运算符                                             | 结合性   |
| ------ | -------------------------------------------------- | -------- |
| 1      | ()、[]、{}                                         | 从左向右 |
| 2      | !、+、-、~、++、--                                 | 从右向左 |
| 3      | *、/、%                                            | 从左向右 |
| 4      | +、-                                               | 从左向右 |
| 5      | <<、>>、>>>                                        | 从左向右 |
| 6      | <、<=、>、>=、instanceof                           | 从左向右 |
| 7      | ==、!=                                             | 从左向右 |
| 8      | &                                                  | 从左向右 |
| 9      | ^                                                  | 从左向右 |
| 10     | \|                                                 | 从左向右 |
| 11     | &&                                                 | 从左向右 |
| 12     | \|\|                                               | 从左向右 |
| 13     | ?:                                                 | 从右向左 |
| 14     | =、+=、-=、*=、/=、&=、\|=、^=、~=、<<=、>>=、>>>= | 从右向左 |

## 数据输入

Java中的scanner是一个类，是用于扫描输入文本的新的实用程序；当在编写Java程序时，如果变量是需要手动输入的时候，此时就可以用到scanner类。

Scanner使用的基本步骤

1. 导包

   import java.util.Scanner;

2. 创建对象

   Scanner sc = new Scanner(System.in);

3. 接收数据

   int i = sc.nextInt();

## 流程控制

流程控制语句分为顺序结构、分支结构（if，switch），循环结构（for，while，do…while）。

### if语句

格式1：

if(关系表达式){

​	语句体;

}

执行流程：首先计算关系表达式的值；如果关系表达式的值为true就执行语句体，如果关系表达式的值为false就不执行语句体；继续执行后面的语句内容。

格式2：

if(关系表达式){

​	语句体1;

}else{

​	语句体2;

}

执行流程：首先计算关系表达式的值；如果关系表达式的值为true就执行语句体1，如果关系表达式的值为false就执行语句体2；继续执行后面的语句内容。

格式3：

if(关系表达式1){

​	语句体1;

}else if(关系表达式2){

​	语句体2;

}

……

else{

​	语句体n+1;

}

执行流程：首先计算关系表达式1的值；如果关系表达式的值为true就执行语句体1，如果关系表达式的值为false就计算关系表达式2的值，如果值为true就执行语句体2，如果值为false就计算关系表达式3的值；……，如果没有任何关系表达式为true，就执行语句体n+1。

### switch语句

格式：

switch(表达式){

​	case 值1:

​		语句体1;

​		break;

​	case 值2:

​		语句体2;

​		break;

……

​	default:

​		语句体n+1;

​		[break;]

}

格式说明：表达式取值为byte、short、int、char，JDK5以后可以是枚举，JDK7以后可以是String。case后面跟的是要和表达式进行比较的值。break表示中断，结束的意思，用来结束switch语句。default表示所有情况都不匹配的时候，就执行该处的内容，和if语句的else相似。

在switch语句中，如果case控制的语句体后边不写break，将会出现穿透现象，在不判断下一个case值的情况下，向下运行直到遇到break，或者整体switch语句结束。

### for 循环语句

循环结构的组成：
初始化语句：用于表示循环开启时的始状态，简单说就是循环开始的时候什么样；
条件判断语句：用于表示循环反复执行的条件，简单说就是判断循环是否能一直执行下去；
循环体语句：用于表示循环反复执行的内容，简单说就是循环反复执行的事情；
条件控制语句：用于表示循环执行中每次变化的内容，简单说就是控制循环是否能执行下去。
循环结构对应的语法：
初始化语句：这里可以是一条或者多条语句，这些语句可以完成一些初始化操作；
条件判断语句：这里使用一个结果值为 boolean类型的表达式，这个表达式能决定是否执行循环体。例如：a<3
循环体语句：这里可以是任意语句，这些语句将反复执行；
条件控制语句：这里通常是使用一条语句来改变变量的值，从而达到控制循环是否继续向下执行的效果。常见i++，i--这样的操作。

格式：

for(初始语句;条件判断语句;条件控制语句){

​	循环体语句;

}

执行流程：(1)执行初始化语句；(2)执行条件判断语句，看其结果是true还是false，如果是false，循环结束，如果是true，继续执行；(3)执行循环体语句；(4)执行条件控制语句；(5)回到(2)继续。

### while 循环语句

格式：

while(条件判断句){

​	循环体语句;

​	条件控制语句;

}

执行流程：(1)执行初始化语句；(2)执行条件判断语句，看其结果是true还是false，如果是false，循环结束，如果是true，继续执行；(3)执行循环体语句；(4)执行条件控制语句；(5)回到(2)继续。

### do…while循环语句

格式：

初始化语句;

do{

​	循环体语句;

​	条件控制语句;

}while(条件判断语句);

执行流程：(1)执行初始化语句；(2)执行循环体语句；(3)执行条件控制语句；(4)执行条件判断语句，看其结果是true还是false，如果是false，循环结束，如果是true，继续执行；(5)回到(2)继续。

### continue和break

continue：用在循环中，基于条件控制，跳过某次循环体内容的执行，继续下一次的执行。
break：用在循环中，基于条件控制，终止循环体内容的执行，也就是说结束当前的整个循环。

### Random包

作用：Random包用来产生一个随机数

使用步骤：

1. 导包：import java.util.Random;
2. 创建对象：Random r = new Random();
3. 获取随机数：int number = r.nextInt(10);		//获取数据范围是[0,10)

### 递归

递归：已编程的角度来看，递归指的是方法定义中调用方法本身的现象。

递归解决问题的思路：

把一个复杂问题层层转化为一个与原问题相似的规模较小的问题来求解。

递归策略只需要少量的程序就可描述出解题过程所需要的多次重复计算。

递归解决问题要找出两个内容：

- 递归出口：否则会出现内存溢出；
- 递归规则：与原问题相似的规模较小的问题。

```java
//简单的递归实例
//斐波那契数列
public class FileDemo01 {
    public static void main(String[] args) {
        System.out.println(fn(20));
    }
    public static int fn(int n){
        if (n==1||n==2)
            return 1;
        else
            return fn(n-1)+fn(n-2);
    }
}
//求阶乘
public class FileDemo01 {
    public static void main(String[] args) {
        System.out.println(fn(5));
    }
    public static int fn(int n){
        if (n==1)
            return 1;
        else
            return n*fn(n-1);
    }
}
```

## 数组

数组（array）是一种用于存储多个相同类型数据的存储模型

### 数组定义格式

格式1：  数据类型[] 变量名

定义了一个int类型的数组，数组名是arr。

eg.    int[] arr;

格式2：   数据类型 变量名[]

定义了一个int类型的变量，变量名是arr数组。

eg.     char arr[];

### 数组初始化

数组初始化分为动态初始化和静态初始化。

动态初始化：初始化时指定数组长度，由系统为数组分配初始值。

格式：数据类型[] 变量名 = new 数据类型[数组长度];

eg.     int[] arr = new int[3];

静态初始化：初始化时指定每个数组元素的初始值，由系统决定数组长度。

格式：数据类型[] 变量名 = new 数据类型[]{数据1,数据2,数据3,……};

eg.    int[] arr = new int[]{1,2,3};

简化格式：数据类型[] 变量名 = {数据1,数据2,数据3,……};

eg.     int[] arr = {1,2,3};

### 内存分配

Java 程序在运行时，需要在内存中分配空间。为了提高运算效率，就对空间进行了不同区域的划分，因为每一片区域都有特定的处理数据方式和内存管理方式。

数组在初始化时，会为存储空间添加默认值：

整数：默认值是0；

浮点数：默认值是0.0；

布尔值：默认值是false；

字符型：默认值是 空字符；

应用数据类型：默认值是null。

栈内存和堆内存：

栈内存是存储局部变量，定义在方法中的变量，就是使用的栈内存，使用完毕立即消失。

堆内存是存储new出来的内容（实体、对象），数组在初始化时，会为存储空间添加默认值。每一个new出来的东西都有一个地址值。使用完毕，会在垃圾回收器空闲时被回收。

### 数组常用操作

常见的两个问题：索引越界和空指异常。

索引越界：访问了数组中不存在的索引对应的元素，造成了索引越界问题。会抛出ArrayIndexOutOfBoundsException。

空指针异常：访问的数组已经不再指向堆内存的数据，造成空指针异常。会抛出NullPointerException。

数组的遍历：

通用格式：

int[] arr = {……};

for(int i = 0;i < arr.length;i++){

​	对arr[i]进行操作

}

## 方法

方法（method）是将具有独立功能的代码块组织成一个整体，使其具有特殊功能的代码集。

方法必须先创建才可以使用，该过程称为方法定义。方法创建后并不能直接运行，需要手动使用后才执行，该过程称为方法调用。

### 方法的定义

格式：

访问权限 修饰符 方法类型 方法名(数据类型 参数1,数据类型 参数2,……){

​	//方法体

​	return 返回值;

}

eg.   public static void isNumber(){

}

返回值的类型由方法的类型决定。若没有返回值，方法类型为void。

### 形参和实参

形参：方法定义中的参数。

实参：方法调用中的参数。

### 方法的注意事项

方法不能嵌套定义。

在定义方法是要明确返回值的类型和明确参数。

明确返回值的类型：主要是明确方法操作完毕后是否有数据返回。

明确参数：主要是明确参数的类型和数量。

### 方法重载

方法重载指同一个类中定义的多个方法之间，满足下列条件的多个方法相互构成重载。

- 多个方法在用一个类中；
- 多个方法具有相同的方法名；
- 多个方法的参数不相同，类型不同或者数量不同。

重载仅对应方法的定义，与方法的调用无关，调用方式参照标准格式；

重载仅针对同一个类中方法的名称与参数进行识别，与返回值无关。

## 面向对象

### 类和对象

类是对现实生活中一类具有共同属性和行为的事物的抽象。

对象是能够看得到摸得着的真实存在的实体。

类是对象的抽象，对象是类的实体。

类的特点：类是对象的数据类型；类是具有相同属性和行为的一组对象的集合。

属性：对象具有各种特征，每一个对象的属性都拥有特定的值。

行为：对象能够执行的操作。

在Java中属性和行为的体现：

属性：在类中通过成员变量来体现（类中方法外的变量）；

行为：在类中通过成员方法来体现（和前边的方法相比，去掉static关键字即可）。

#### 类的定义

步骤：

1. 定义类
2. 编写类的成员变量
3. 编写类的成员方法

public class 类名{

​	//成员变量

​	//成员方法

}

#### 对象的使用

创建对象格式：类名 对象名 = new 类名();

eg.    Scanner sc = new Scanner();

### 成员变量和局部变量

成员变量：在类中，方法外的变量是成员变量；

局部变量：在方法中的变量是局部变量。

| 区别           | 成员变量                                   | 局部变量                                       |
| -------------- | ------------------------------------------ | ---------------------------------------------- |
| 类中的位置不同 | 类中方法外                                 | 方法内或者方法申明上                           |
| 内存中位置不同 | 堆内存                                     | 栈内存                                         |
| 生命周期不同   | 随着对象的存在而存在，随着对象的消失而消失 | 随着方法的调用而存在，随着方法的调用完毕而消失 |
| 初始化值不同   | 有默认的初始化值                           | 没有默认的初始化值，必须先定义，赋值，才能使用 |

### 封装

#### private关键字

- 权限修饰符
- 可以修饰成员（成员变量和成员方法）
- 作用是保护成员不被别的类使用，被private修饰的成员只在本类中才能访问

针对private修饰的成员变量，如果需要被其他类使用，提供相应的操作。

- 提供“get变量名()”方法，用于获取成员变量的值，方法用public修饰。
- 提供“set变量名(参数)”方法，用于设置成员变量的值，方法用public修饰。

#### this关键字

this修饰的变量用于指代成员变量

- 方法的形参如果与成员变量同名，不带this修饰放入变量指的是形参，而不是成员变量。
- 方法的形参没有与成员变量同名，不带this修饰放入变量指的是成员变量。

this用于解决成员变量与形参同名时出现的隐藏成员变量的情况。

this：代表所在类的对象引用。

#### 封装

封装是面向对象三大特征之一（封装、继承、多态），是面向对象编程语言对客观世界的模拟，客观世界里成员棉量都隐藏在对象内部的，外界是无法直接操作。

封装原则：将类的某些信息隐藏在类内部，不允许外部程序直接访问，而是通过该类提供的方法来实现对隐藏信息的操作和访问成员变量private，提供对应的getXxx()/setXxx()方法。

封装的好处：通过方法来控制成员变量的操作，提高了代码的安全性；把代码用方法进行封装，提高了代码的复用性。

### 构造方法

构造方法是一种特殊的方法，用于创建对象。

格式：

public class 类名{

​	修饰符 类名(参数){

​	}

}

构造方法在创建时，如果没有定义构造方法，系统将给出一个默认的无参构造方法。如果定义了构造方法，系统将不再提供默认的构造方法。

如果自定义了带参构造方法，还要使用无参数构造方法，就必须在写一个无参构造方法。

推荐的使用方式：无论是否使用，都手工书写无参构造方法。

### 标准类的制作

1. 成员变量
   - 使用private 修饰
2. 构造方法
   - 提供一个无参构造方法
   - 提供一个带多个参数的构造方法
3. 成员方法
   - 提供每一个成员变量对应的setXxx()/getXxx()
   - 提供一个显示对象信息的show()
4. 创建对象并为其成员变量赋值的两种方式
   - 无参构造方法创建对象后使用setXxx()赋值
   - 使用带参构造方法直接创建带有属性值的对象

## 字符串

### API

API（Application Programming Interface）：应用程序编程接口。

Java API：指的就是JDK中提供的各种功能的Java类，这些类将底层的实现封装起来，我们不需要关心，这些类是如何实现的，只需要学习这些类如何使用即可，我们可以通过帮助文档来学习这些API如何使用。

### String

String类在java.lang包下，所以使用的时候不需要导包。

String类代表字符串，Java程序中的所有字符串文本（例如“abc”）都被实现为此类的实例，也就是说，Java程序中所有的双引号字符串都是String类对象。

字符串的特点：

- 字符串不可变，他们的值在创建后不能更改
- 虽然String的值不可变的，但是他们可以被共享
- 字符串效果上相当于字符数组（char[]），但是底层原理是字节数组（byte[]）。JDK8以前是字符数组，JDK9及以后是字节数组。

String对象的特点：

- 通过new 创建的字符串对象，每一次new 都会申请一个内存空间，虽然内容相同，但地址值不同。
- 以双引号方式给出的字符串，只要字符序列相同（顺序和大小写），无论在程序代码中出现几次，JVM都只会建立一个String对象，并在字符串池中维护。

### String的构造方法

| 方法名                    | 说明                                      |
| ------------------------- | ----------------------------------------- |
| public String()           | 创建一个空白字符串对象，不包含任何内容    |
| public String(char[] chs) | 根据字符数组的内容，来创建字符串对象      |
| public String(byte[] bys) | 根据字节数组的内容，来创建字符串对象      |
| String s = "abc";         | 直接赋值的方式创建字符串对象，内容就是abc |

### 字符串的比较

使用==作比较

- 基本类型：比较的是数据值是否相同
- 引用类型：比较的是地址值是否相同

字符串是对象，他比较内容是否相同，是通过一个方法来实现的，这个方法叫：equals()

public boolean equals(Object anObject)：将此字符串与指定对象进行比较。由于我们比较的是字符串对象所以参数直接传递一个字符串。

### 常用的String方法

1. 求字符串的长度

public int length()：返回该字符串的长度。

2. 求字符串某一位置字符

public char charAt(int index)：返回字符串中指定位置的字符。

3. 提取子串

public String substring(int beginIndex)：该方法从beginIndex位置起，从当前字符串中取出剩余的字符作为一个新的字符串返回。

public String substring(int beginIndex,int endIndex)：该方法从beginIndex位置起，从当前字符串中取出到endIndex-1位置的字符作为一个新的字符串返回。

4. 字符串比较

public int compareTo(String anotherString)：该方法是对字符串内容按照字典顺序进行大小排序，通过返回的整数值指明当前字符串与参数字符串的大小关系。若当前对象比参数大则返回正整数，反之返回负整数，相等返回0。

public int compareTolgnore(String anotherString)：与compareTo方法相似，但忽略大小写。

public boolean equals(Object anotherObject)：比较当前字符串和参数字符串，在两个字符串相等的时候返回true，否则返回false。

public boolean equalslgnoreCase(String anotherString)：与equals方法类似，但忽略大小写。

5. 字符串连接

public String concat(String str)：将参数中的字符串str连接到当前字符串的后面，效果等价于"+"。

6. 字符串中单个字符查找

public int indexOf(int ch/String str)：用于查找当前字符串中字符或子串，返回字符或子串在当前字符串中从左边起首次出现的位置，若没有则返回-1。

public int indexOf(int ch/String str,int fromIndex)：该方法与第一种类似，区别在于该方法从fromIndex位置向后查找。

public int lastIndexOf(int ch/String str)：该方法与第一种类似，区别在于该方法从字符串末尾位置先前查找。

public int lastIndexOf(int ch/String str,int fromIndex)：该方法与第二中方法类似，区别在于该方法从fromIndex位置向前查找。

7. 字符串中字符的大小写转换

public String toLowerCase()：返回当前字符串中所有字符转换成小写后的新串。

public String toUpperCase()：返回当前字符串中所有字符转换成大写后的新串。

8. 字符串中字符的替换

public String replace(char oldChar,char newChar)：用字符newChar 替换当前字符串中所有的oldChar 字符，并返回一个新的字符串。

public String replaceFirst(String regex,String replacement)：该方法用字符replacement的内容替换当前字符串中遇到的第一个和字符串regex相匹配的子串，应将新的字符串返回。

public String replaceAll(String regex,String replacement)：该方法用字符replacement的内容替换当前字符串中遇到的所有和字符串regex相匹配的子串，应将新的字符串返回。

9. 字符串类型转换

public static String valueOf(任何类型变量)：将任何类型变量转换成 String 类型。

10. 其他类方法

String trim()：截去字符串两端的空格，但对于中间的空格不处理。

boolean statWith(String prefix)或者 boolean endWith(String suffix)：用来比较当前字符串的起始字符或者子字符串prefix和终止字符或者子字符串suffix是否和当前字符串相同，重载方法中同时还可以指定比较的开始位置offset。

regionMatches(boolean b,int firstStart,String other,int otherStart,int length)：从当前字符串的firststart位置开始比较，取长度为length的一个子字符串，other字符串从otherStart位置开始，指定另外一个长度为length的字符串，两字符串比较，当b为true时字符串不区分大小写。

contains(String str)：判断参数str是否被包含在字符串中，并返回一个布尔类型的值。

String[] split(String str)：将str作为分隔符进行字符串分解，分解后的字符串在字符串数组中返回。

### 常用的字符串操作

#### 字符串遍历

```java
String s = "wxy";
for(int i = 0;i<s.length();i++){
	s.charAt(i);
}
```

#### 字符串拼接

```java
public static String toString(int[] arr) {
        String s = "";
        s += "[";
        for (int i = 0; i < arr.length; i++) {
            if (i == arr.length - 1)
                s += arr[i];
            else
                s += arr[i] + ", ";
        }
        s += "]";
        return s;
    }
```

#### 字符串反转

```java
public static String reverse(String s) {
        String reverser_str = "";
        for (int i = s.length() - 1; i >= 0; i--) {
            reverser_str += s.charAt(i);
        }
        return reverser_str;
    }
```

### StringBuilder类

StringBuilder是一个可变的字符串类，我们可以把它看成一个容器，这里的可变指的是StringBuilder 对象中内容是可变的。

String和StringBuilder的区别：

- String：内容是不可变的；
- StringBuilder：内容是可变的。

#### StringBuilder的构造方法

| 方法名                           | 说明                                       |
| -------------------------------- | ------------------------------------------ |
| public StringBuilder()           | 创建一个空白可变字符串对象，不含有任何内容 |
| public StringBuilder(String str) | 根据字符串内容，来创建可变字符串对象       |

#### StringBuilder的常用方法

public StringBuilder append(任何类型)：字符串连接，可以没有返回值，在原字符串中修改。

public String toString()：返回String字符串，就是用于将StringBuilder类型字符串转换成String类型

public StringBuilder insert(int offset,任何类型)：在指定位置之前插入对象，可以没有返回值，在原字符串中修改。

public int indexOf(String str,int fromIndex)：返回StringBuilder中从fromIndex开始子串str第一次出现的位置。

public StringBuilder delete(int startIndex,int endIndex)：删除起始位置startIndex（含）到结尾位置endIndex（不含）之间的字符串。可以没有返回值，在原字符串中修改。

public StringBuilder deleteCharAt(int index)：删除Index处的字符。可以没有返回值，在原字符串中修改。

public StringBuilder replace(int start,int end,String str)：用str替换StringBuilder中从start到end位置中的字符串。可以没有返回值，在原字符串中修改。

public StringBuilder reverse()：字符串反转，可以没有返回值，在原字符串中修改。

public String subString(int start)：字符串截取，返回从Start开始的子串，返回String类型。

public String subString(int start,int end)：返回从start开始到end的子串，返回String类型。

## 集合基础

集合类的特点：提供了一种存储空间可变的存储模型，存储的数据容量可以发生改变。

集合类有很多，目前我们先学习一个：ArrayList。

ArrayList<E>:

- 可以调整大小的数据实现
- <E>:是一个特殊的数据类型，泛型。

在出现E的地方我们使用应用数据类型替换即可

eg. ArrayList<String>,ArrayList<Student>

### ArrayList构造方法和添加方法

public ArrayList()：创建一个空的集合对象

public boolean add(E e)：将指定的元素追加到此集合的末尾

public void add(int index,E element)：在此集合中的指定位置插入指定的元素

### ArrayList常用接口方法

public int size()：返回列表中元素的个数

public E get(int index)：返回列表中指定位置的元素

public E set(int index,Object element)：将索引index位置元素替换为元素element并返回被替换的元素。

public void clear()：删除列表中的所有元素，无返回值。

public Boolean isEmpty()：判断列表是否为空，为空返回true，否则返回false。

public Boolean contains(Object o)：如果列表包含指定的元素，则返回true，否则返回false。

public E remove(int index)：移除列表中指定位置的元素，并返回被删元素。

public Boolean remove(Object o)：移除集合中第一次出现的指定元素，移除成功返回true，否则返回false。

## 继承

继承是面向对象三大特征之一。可以使得子类具有父类的属性和方法，还可以在子类中重新定义，追加属性和方法。

格式：

public class 子类名 extends(父类名){}

父类也被称为基类，超类；子类也被称为派生类。

Java类只支持单继承，不支持多继承。Java中类支持多层继承。

### 继承的优点和缺点

优点：

- 提高了代码的复用性（多个类相同的成员可以放在同一个类中）
- 提高了代码的可维护性（如果方法的代码需要修改，修改一处即可）

缺点：

- 继承让类与类之间产生了关系，类的耦合性增强了，当父类发生变化时，子类实现也不得不跟着变化，削弱了子类的独立性。

在子类中访问一个变量或方法，首先在子类局部范围查找，然后在子类成员范围查找，最后在父类成员范围查找，如果没有则报错，不考虑父类的父类。

### super关键字

super关键字的用法和this关键字的用法类似。

- this：代表本类对象引用
- super：代表父类存储空间的标识（可以理解为父类对象引用）

| 关键字 | 访问成员变量                        | 访问构造方法                    | 访问成员方法                             |
| ------ | ----------------------------------- | ------------------------------- | ---------------------------------------- |
| this   | this.成员变量      访问本类成员变量 | this(……)       访问本类构造方法 | this.成员方法(……)       访问本类成员方法 |
| super  | super.成员变量   访问父类成员变量   | super(……)     访问父类构造方法  | super.成员方法(……)     访问父类成员方法  |

### 继承中构造方法的访问特点

子类中所有的构造方法默认都会访问父类中的无参构造方法。

- 因为子类会继承父类中的数据，可能还会使用父类的数据，所以子类在初始化前，一定要完成父类的初始化。
- 没一个子类构造方法的第一条语句默认都是：super()

如果父类中没有无参构造方法，只有带参构造方法。

- 通过使用super关键字去西安市的调用父类的带参构造方法。
- 在父类中自己提供一个无参构造方法。

推荐：自己给出无参构造方法

### 方法重写

子类中出现了和父类中相同的方法声明。

方法重写的应用：

- 当子类需要父类的功能，而功能主体子类有自己特有内容时，可以重写父类中的方法，这样即沿袭了父类的功能，又定义了子类特有的内容。

@Override，是一个注解，可以帮助我们检查重写方法声明的正确性。

子类方法访问权限不能低于父类。

## 修饰符

### package（包）

包其实就是文件夹。

作用是对类进行分类管理。

包的定义格式：

package 包名;			//多级包需要用 . 分开

eg.  package com.test;

带包的Java类编译和执行

- 手动建包：

  编译Java文件：javac 文件

  手动创建包

  把编译完的class文件放到包中

  带包执行 java 包名.文件.class

- 自动建包：

  javac -d . 文件

  带包执行：java 包名.文件.class

### import

使用不同包下的类时，使用的时候要写类的全路径。为了简化带包的操作，Java就提供了导包的功能。

格式：

import 包名;

eg.  import java.util.Scanner;

### 权限修饰符

- private（私有的）：它的访问权限仅限于类的内部，是一种封装的体现。这样，就不能从类的外边直接访问他们，我们提供set和get方法，保证类中数据域的安全。
- default（缺省）：默认修饰符，什么都不加，实际上它限制的范围就是一个包内可以访问。如果不在一个包内，即使继承关系任然是不能访问的。它是针对本包访问而设计的，任何处于本包下的类，接口，异常等，都可以互相访问，即使是父类没有用protected修饰的成员也可以。
- protected（受保护的）：经常需要允许子类访问定义在父类中的数据和方法，但是不允许非子类访问这些数据和方法，这种情况下就可以使用protected，它允许任何包中的子类访问父类。
- public（公共的）：具有最大的访问权限，可以访问任何一个CLASSPATH下的类，接口、异常等。它往往对于对外的情况，也就是对象或类对外的一种接口形式。

| 访问权限  | 本类 | 本包的类 | 子类 | 非子类的外包类 |
| --------- | ---- | -------- | ---- | -------------- |
| public    | 是   | 是       | 是   | 是             |
| protected | 是   | 是       | 是   | 否             |
| default   | 是   | 是       | 否   | 否             |
| private   | 是   | 否       | 否   | 否             |

### 状态修饰符

#### final（最终态）

final关键字是最终的意思，可以修饰成员方法，成员变量，类。

final修饰的特点：

- 修饰方法：表明该方法是最终方法，不能被重写；
- 修饰变量：表明该变量是常量，不能再次被赋值；
- 修饰类：表明该类是最终类，不能被继承。

final修饰局部变量：

- 变量是基本类型：final 修饰指的是基本类型的数据值不能变；
- 变量是引用类型：final 修饰值得是引用类型的地址值不能发生改变，但是地址里边的内容是可以发生改变的。

#### static（静态）

static 关键字是静态的意思，可以修饰成员方法，成员变量。

static 修饰的特点

- 被类的所有对象共享

  这也是我们判断是否使用静态关键字的条件

- 可以通过类名调用

  当然，也可以通过对象名调用

  **推荐使用类名调用**

- 静态成员方法只能访问静态成员变量。

### 抽象修饰符

#### abstract（抽象）

abstract 不能修饰构造方法,不能修饰成员变量,可以修饰类,成员方法。
被修饰的类不能被实例化，只能被继承，被修饰的成员方法在子类中必须被重写。

## 多态

同一个对象，在不同时刻表现出来的不同形态。

eg.  猫

我们可以说猫是猫： 猫 cat = new 猫();

我们也可以说猫是动物： 动物 animal = new 猫();

这里猫在不同的时刻表现出来了不同的形态，这就是多态。

多态的前提和体现：

- 有继承/实现关系
- 有方法重写
- 有父类引用指向子类对象

### 多态的特点及优缺点

多态中成员的访问特点：

- 成员变量：编译看左边，执行看左边；
- 成员方法：编译看左边，执行看右边。

因为成员方法有重写，而成员变量没有，所以成员变量和成员方法的访问不一样。

多态的优点和缺点：

- 多态的优点：提高了程序的扩展性。具体的体现：定义方法的时候，使用父类型作为参数，将来在使用的时候，使用具体的子类型参与操作。
- 多态的弊端：不能使用子类的特有功能。

### 多态中的转型

- 向上转型：从子到父，父类引用指向子类对象
- 向下转型：从父到子，父类引用转为子类对象

格式：

向上转型

父类 对象名 = new 子类();

向下转型：将父类对象强制转换为子类对象。

子类 新对象名 = (子类)对象名;

通过向下转型，解决了多态中存在的无法使用子类特有功能的缺点。

## 抽象类和接口

### 抽象类概述

在Java中，一个没有方法体的方法应该定义为抽象方法，而类中如果有抽象方法，该类必须定义为抽象类。

抽象类和抽象方法必须使用abstract关键字修饰

public abstract class 类名{};

public abstract void eat();

### 抽象类的特点

- 抽象类中不一定有抽象方法，有抽象方法的类一定是抽象类。

- 抽象类不能实例化

  可以参照多态的方式，通过子类对象实例化，这叫抽象类多态。

- 抽象类的子类

  要么重写抽象类中的所有抽象方法

  要么是抽象类

### 抽象类的成员特点

- 成员变量

  可以是变量，也可以是常量

- 构造方法

  有构造方法，但是不能实例化。

  构造方法用于子类访问父类数据的初始化

- 成员方法

  可以有抽象方法：限定子类必须完成某些动作；也可以有非抽象方法，提高代码的复用性。

### 接口概述

接口就是一种公共的规范标准，只要符合规范标准，大家都可以通用。

Java中的接口更多的体现在对行为的抽象。

### 接口的特点

- 接口用关键字 interface 修饰

  public interface 接口名{}

- 类实现接口用 implements 表示

  public class 类名 implements 接口名{}

- 接口不能实例化

  接口实例化需要参照多态的方式，通过实现对象实例化，这叫接口多态。

  多态的形式：具体类多态，抽象类多态，接口多态。

  多态的前提：有继承或者实现关系；有方法重写；有父（类/接口）引用指向（子/实现）类对象。

- 接口的实现类

  要么重写接口中的所有抽象方法

  要么是抽象类

### 接口的成员特点

- 成员变量

  只能是常量

  默认修饰符：public static final

- 构造方法

  接口没有构造方法，因为接口主要是对行为进行抽象的，是没有具体存在的。

  一个类如果没有父类，默认继承自Object类。

- 成员方法

  只能是抽象方法

  默认修饰符：public abstract

  关于接口中的方法，JDK8和JDK9中有一些新特性。

### 类和接口的关系

- 类和类的关系：继承关系，只能单继承，但是可以多层继承。
- 类和接口的关系：可以单实现，还可以在继承一个类的同时实现多个接口。
- 接口和接口的关系：继承关系，可以单继承，也可以多继承。

### 抽象类和接口的区别

- 成员区别

  抽象类				变量，常量；有构造方法，也有非抽象方法。

  接口					常量，抽象方法。

- 关系区别

  类与类				继承，单继承

  类与接口			实现，可以单实现，也可以多实现

  接口与接口		继承，单继承，多继承

- 设计理念区别

  抽象类				对类进行抽象，包括属性、行为

  接口					对行为抽象，主要是行为

抽象类

抽象类是用来捕捉子类的通用特性的 。它不能被实例化，只能被用作子类的超类。抽象类是被用来创建继承层级里子类的模板。

接口

接口是抽象方法的集合。如果一个类实现了某个接口，那么它就继承了这个接口的抽象方法。这就像契约模式，如果实现了这个接口，那么就必须确保使用这些方法。接口只是一种形式，接口自身不能做任何事情。

### 什么时候使用抽象类和接口

- 如果你拥有一些方法并且想让它们中的一些有默认实现，那么使用抽象类吧。
- 如果你想实现多重继承，那么你必须使用接口。由于Java不支持多继承，子类不能够继承多个类，但可以实现多个接口。因此你就可以使用接口来解决它。
- 如果基本功能在不断改变，那么就需要使用抽象类。如果不断改变基本功能并且使用接口，那么就需要改变所有实现了该接口的类。
- 假如有一个接口，五个实现类，现在的需求可能要往接口加一个方法，这样就要改动五个实现类，但需求只需要改动其中两个实现类，可以再定义一个抽象类去实现这个接口，在抽象类中新增这个方法，然后其他两个实现类实现这个抽象类就好了，或者使用 Java 8 中的新特性，在接口中新增默认方法或者静态方法。

### 类、抽象类、接口作为形参和返回值

- 类作为形参和返回值：
  - 方法的形参是类名，其实需要的是该类的对象；
  - 方法的返回值是类名，其实返回的是该类的对象。
- 抽象类作为形参和返回值
  - 方法的形参是抽象类，其实需要的是该抽象类的子类对象。
  - 方法的返回值是抽象类，其实返回值是该抽象类的子类对象。
- 接口作为形参和返回值
  - 方法的形参是接口，其实需要的是该接口的实现类对象。
  - 方法的返回值是接口名，其实返回的是该接口的实现类对象。

## 内部类

内部类就是在一个类中定义一个类。

在一个类A的内部定义了一个类B，类B就被称为内部类，类A就是外部类。

内部类的定义格式：

public class 类名{

​	修饰符 class 类名{

​	}

}

内部类的访问特点

- 内部类可以直接访问外部类的成员，包括私有。
- 外部类要访问内部类的成员，必须创建对象。

按照内部类在类中定义的位置不同，可以分为如下两种形式：

- 在类的成员位置：成员内部类
- 在类的局部位置：局部内部类

### 成员内部类

在外界创建内部类对象

格式：

外部类名.内部类名 对象名 = 外部类对象.内部类对象;

eg.   Outer.Inner oi = new Outer().new Inner();

在使用时，内部类通常需要 private 修饰，不允许外部直接调用。在外部类中使用方法调用内部类对象。

### 局部内部类

局部内部类是在方法中定义的类，所以外界是无法直接使用，需要在方法内部创建并使用。

该类可以直接访问外部类的成员，课可以访问方法内的局部变量。

### 匿名内部类

匿名内部类是局部内部类的一种特殊形式。

前提：存在一个类或者接口，这里的类可以是具体类也可以是抽象类。

匿名内部类的本质是一个继承了该类或者实现了该接口的子类匿名对象。

格式：

new 类名或者接口名(){

​	重写方法;

}

eg.   new Inter(){

​			public void show(){

​			}

​		};

## 常用API

工具类的设计思路：

- 构造方法用 private 修饰。
- 成员用public static修饰。

### Math

Math 类包含执行基本数字运算的方法。

Math 类没有构造方法，不能被实例化，所有成员都是静态的，可以通过类名直接调用。

#### Math 类中的常量

Math.E：自然对数，值为 2.718281828459045

Math.PI：π的值，值为 3.141592653589793

#### Math 类的常用方法

public static int abs(int a)：返回参数的绝对值

public static double ceil(double a)：返回参数的向上取整值。

public static double floor(double a)：返回参数的向下取整值。

public static int round(float a)：按照四舍五入返回最接近参数的int。

public static int max(int a,int b)：返回两个int值中的较大值。

public static int min(int a,int b)：返回两个int值中的较小值。

public static double pow(double a,double b)：返回a的b次幂的值。

public static double sqrt(double a)：返回a的平方根。

public static double cbrt(double a)：返回a的立方根。

public static double random()：返回值为 double 的正值，[0.0,1.0)。

### System

System 类提供的方法包括标准输入，标准输出和错误输出流；访问外部定义的属性和环境变量；一种加载文件和库的方法；以及用于快速复制阵列的一部分的实用方法。

System 类没有构造方法，不能被实例化，所有成员都是静态的，可以通过类名直接调用。

#### System 类的成员变量

System.in：标准输入流。

System.out：标准输出流。

System.err：标准错误输出流。

#### System 类的常用方法

public static void exit(int status)：终止当前运行的虚拟机，非零表示异常终止。

public static long currentTimeMillis()：返回当前时间（以毫秒为单位），与1970年1月1日UTC时间的差值。

public static void gc()：运行垃圾回收器。

public static void arraycopy(Object src,int srcPos, Object dest,int destPos, int length)：从源数组 src 中复制一个数组，复制从指定的起始位置 srcPos 开始，到目标数组 dest 的指定起始位置 destPos结束，长度为length。



### Object

Object 类是类层结构的根，每个类都可以将 Object 类作为超类，所有类都直接或间接继承自 Object 类。所有对象（包括数组）都实现了这个类的方法。

构造方法：public Object(){}

#### Object的常用方法

public String toString()：返回对象的字符串表示形式，形式是getClass(),getName()+'@'+Integer.toString(hasCode())。在实践中建议所有子类重写此方法。

public Boolean equals()：比较对象是否相等，默认比较地址，在实践中建议重写此方法，使其可以比较内容。

### Arrays

#### 冒泡排序

冒泡排序是一种排序的方式，对要进行排序的数据中相邻的数据进行两两比较，将较大的数据放在后面，依次对所有的数据进行操作，直到所有数据按要求完成排序。

- 如果有 n 个数据进行排序，总共需要比较 n-1 次。
- 每一次比较完毕，下一次的比较就会少一个数据参与。

```java
    //冒泡排序
public static int[] maopao(int[] arr){
    for (int x = 0;x<arr.length-1;x++)
        for (int i = 0;i<arr.length-1-x;i++)
            if (arr[i]>arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
    return arr;
}
```

#### Arrays 类概述

Arrays 类在java.util 下，因此，使用时，需要导入。

Arrays 包含用于操作数组的各种方法（如排序和搜索）。

#### Arrays 类的常用方法

public static String toString(int[] a)：返回指定数组的内容的字符串表示形式。

public static void sort(int[] a)：按照数字顺序排序（从小到大）指定的数组，在原数组中修改。

public static boolean equals(array1,array2)：比较两个数组是否相等。

public static void fill(array,val)：把数组array 中所有的元素都赋值为 val 。

public static int binarySearch(array,val)：查询元素值 val 在数组 array 中的下标。

public static array copyof(array,length)：把数组 array 复制成一个长度为 length 的新数组。

### 基本类型包装类

将基本数据类型封装成对象的好处在于可以在对象中定义更对的功能方法操作该数据。

常用的操作之一：用于基本数据类型与字符串之间的转换。

基本数据类型与包装类的对应关系

| 基本数据类型 | 包装类    |
| ------------ | --------- |
| byte         | Byte      |
| short        | Short     |
| int          | Integer   |
| long         | Long      |
| float        | Float     |
| double       | Double    |
| char         | Character |
| boolean      | Boolean   |

#### 基本类型和包装类之间的关系

以 int 和 Integer 为例，其他类型也基本相同。

Integer 类用于包装一个对象中的原始 int 的值。

Integer 的构造方法有两个，但是目前已经不再使用，现在使用下边的两个方法实现。

Integer 的常用方法

public static Integer valueOf(int i)：返回表示指定的 int 值的 Integer 实例。

public static Integer valueOf(String s)：返回一个保存指定值的 Integer 对象 String。

public int intValue()：将Integer 类型对象转换成基本类型 int。

public long longValue()：将Integer类型对象转换成基本类型 long。

public static int parseInt(String s)：将字符串类型转换成基本类型 int。

#### 案例：字符串中的数据排序

```java
//将数字字符串排序
public class Test {
    public static void main(String[] args) {
        String s = "91 25 63 84 27";
        String[] strArray = s.split(" ");		//将字符串分隔成字符串数组
        int[] intArray = new int[strArray.length];		//定义一个数字数组
        StringBuilder sb = new StringBuilder();		//定义一个StringBuilder
        for (int i = 0;i<strArray.length;i++)		//将分隔完的字符串数组转换成数字数组
            intArray[i] = Integer.parseInt(strArray[i]);
        Arrays.sort(intArray);		//对数字数组中的数据排序
        for (int i = 0; i<intArray.length;i++){		//将数字数组拼接成字符串，放入StringBuilder
            if (i == intArray.length-1)
                sb.append(intArray[i]);
            else
                sb.append(intArray[i]).append(" ");
        }
        String result = sb.toString();		//将StringBuilder转换成String
        System.out.println(result);
    }
}
```

#### 自动装箱和拆箱

装箱：把基本数据类型转换成对应的包装类类型。

拆箱：把包装类类型转换成对应的基本数据类型。

在正常情况下，对包装类进行计算时，需要先对包装类类型进行拆箱，才能进行计算。但是在JDK5之后，可以省略装箱和拆箱，会自动进行装箱和拆箱操作。

```java
eg.
Integer i = 100;	//自动装箱
i = i + 200;		//i+200   自动拆箱；i=i+200   自动装箱；
```

注意：在使用包装类类型的时候，如果做操作，最好先判断是否为null。我们推荐的是，只要是对象，在使用前就必须进行不为null的判断。

### 日期类

#### Date 类

Date 类在java.sql 下有，在java.util 下也有一个。

这里说的是java.util 下的Date 类。

Date 类代表了一个特定的时间。

构造方法：

public Date()：分配一个Date 对象，并初始化，以便它代表它分配的时间，精确到毫秒。

public Date(long date)：分类一个Date 对象，并将其初始化为表示从基准时间起指定的毫秒数。

Date 类的常用方法：

public long getTime()：获取的是日期对象从基准时间到现在的毫秒值。

public void setTime(long time)：设置时间，给的是毫秒值。

#### SimpleDateFormat 类

SimpleDateFormat 类是一个具体的类，用于以区域设置敏感的方式格式化和解析时间。

日期和时间格式由日期和时间模式字符串指定，在日期和时间模式字符串中从'A'到'Z'以及从'a'到'z'引号的字母被解释为表示日期或时间字符串的组件的字母模式。

常用的模式字母及对应关系如下：

- y		年
- M		月
- d		日
- H		时
- m		分
- s		秒

构造方法：

public SimpleDateFormat()：构造一个SimpleDateFormat对象，使用默认模式和日期格式。

public SimpleDateFormat(String pattern)：构造一个SimpleDateFormat使用给定的模式和默认的日期格式。

SimpleDateFormat 格式化和解析日期：

- 格式化（从 Date 到 String）

  public final String format(Date date)：将日期格式化成日期/时间字符串。

- 解析（从 String 到 Date）

  public Date parse(String source)：从给定字符串的开始解析文本以生成日期。

#### 案例：日期工具类

```java
//创建日期工具类。完成字符串转换为日期，日期转换为字符串的功能。
//日期工具类定义
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class Test1 {
    private Test1(){}
    public static String dateToString(Date date, String format){
        SimpleDateFormat sdf = new SimpleDateFormat(format);
        String s = sdf.format(date);
        return s;
    }
    public static Date stringToDate(String s,String format){
        SimpleDateFormat sdf = new SimpleDateFormat(format);
        Date d = null;
        try {
            d = sdf.parse(s);
            return d;
        } catch (ParseException e) {
            e.printStackTrace();
        }
        return d;
    }
}
//日期工具类的测试
import java.util.Date;

public class Test3 {
    public static void main(String[] args) {
        Date d = new Date();
        String s = Test1.dateToString(d,"yyyy年MM月dd日 HH:mm:ss");
        System.out.println(s);
        String s1 = "2021-04-23 12:23:43";
        Date dd = Test1.stringToDate(s1,"yyyy-MM-dd HH:mm:ss");
        System.out.println(dd);
    }
}
```

#### Calendar 类

Calendar 类为某一时刻和一组日历字段之间的转换提供了一些方法，并为操作日历字符提供了一些方法。

Calendar提供了一个类方法 getInstance 用于获取Calendar对象，其日历字符已使用当前日期和时间初始化：

Calendar rightNow = Calendar.getInstance();

Calendar 类的常用方法：

public int get(int field)：通过Calendar 类提供的日历字段，返回指定的日期值。

注意：月的字段 MONTH 在该类中初始值为0，所以使用时需要加一。

```java
//eg.
Calendar c = Calendar.getInstance();
int year = c.get(Calendar.YEAR);		//年
int month = c.get(Calendar.MONTH)+1;	//月
int date = c.get(Calendar.DATE);		//日
```

public abstract void add(int field,amount)：根据日历的规则，将指定的时间量添加或减去给定的日历字段。

public final void set(int year,int month,int date)：设置当前日历的年月日。

## 异常

异常就是程序出现了不正常的情况。

### 异常体系

- Throwable
  - Error
  - Exception
    - RuntimeException
    - 非RuntimeException

Throwable 类是 Java 所有错误和异常的超类。

Error：严重问题，Java 虚拟机一般无法处理。

Exception：称为异常类，他表示程序本身可以处理的问题。

- RuntimeException：在编译期不检查，出现问题后，需要我们回来修改代码。
- 非RuntimeException：在编译期就必须处理的，否则程序不能通过编译，就更不能正常运行了。

学习异常，主要学习RuntimeException。

如果程序出现了异常，JVM会 new 异常类对象，异常类对象会带一个包含异常信息的参数，如果不对异常进行处理。最终JVM会做默认处理。

- 把异常的名称，异常原因及异常出现的位置等信息输出在了控制台。
- 程序停止运行。

### Throwable 的成员方法

public String getMessage()：返回此 throwable 的详细消息字符串。

public String toString()：返回此可抛出的简短描述。

public void printStackTrace()：吧异常的错误信息输出在控制台上。

### 编译时异常和运行时异常的区别

Java中的异常被分为两大类：编译时异常和运行时异常，也被称为受检异常和非受检异常。

所有的 RuntimeException 类及其子类被称为运行时异常，其他的异常都是编译时异常。

- 编译时异常：必须显示处理，否则程序就会发生错误，无法通过编译。
- 运行时异常：无需显示处理，也可以和编译时异常一样处理。

### 异常处理

编译时异常必须要进行处理，有两种方案：try … catch … 和 throws ，如果采用throws 这种方案，将来谁调用谁处理。

运行时异常可以不处理，出现问题后，需要我们回来修改代码。

#### try … catch … finally …

格式：

```java
try{
	可能出现的异常的代码；
}catch(异常类名 变量名){
		异常的处理方案代码;
}finally{
    执行所有清除操作;
}
```

执行流程：

程序从try里面的代码开始执行；出现异常，会自动生成一个异常类对象，该异常对象将被提交给Java运行时系统；当Java运行时系统接收到异常对象时，回到 catch 中去找匹配的异常类，找到后进行异常的处理；执行完毕后，程序还可以继续向下执行。

finally：在异常处理时提供 finally 块在执行所有清除操作。被 finally 控制的语句一定会执行，除非JVM退出。

#### throws

虽然我们通过 try … catch … 可以对异常进行处理，但是并不是所有的情况我们都有权限进行异常的处理，也就是说，有些时候可能出现的异常是我们处理不了的。

针对这种情况，Java提供了 throws 的处理方案。

格式： throws 异常类名;

注意：这个格式是跟在方法的括号后边的。

### 自定义异常

```java
//格式：
public class 异常类名 extends Exception{
    无参构造;
    带参构造;
}
//范例：
public class ScoreException extends Exception{
    public ScoreException(){}
    public ScoreException(String message){
        super(message);
    }
}
```

```java
//自定义异常代码示例：
//自定义异常类
public class ScoreException extends Exception{
    public ScoreException(){}
    public ScoreException(String message){
        super(message);
    }
}
//测试类
public class Teacher{
    public void checkScore(int score) throws ScoreException{
        if (score<0||score>100)
            throw new ScoreException("你给的分数有误，分数应该在0-100之间");
        else
            System.out.println("分数正常");
    }
}
//实例测试类
import java.util.Scanner;
public class Test3 {
    public static void main(String[] args) {
        Teacher t = new Teacher();
        Scanner sc = new Scanner(System.in);
        int score = sc.nextByte();
        try{
            t.checkScore(score);
        }catch(ScoreException e){
            e.printStackTrace();
        }
    }
}
```

throws和throw的区别

| throws                                         | throw                              |
| ---------------------------------------------- | ---------------------------------- |
| 用在方法声明后面，跟的是异常类名               | 用在方法体内，跟的是异常对象名     |
| 表示抛出异常，由该方法的调用者来处理           | 表示抛出异常，由方法体没的语句处理 |
| 表示出现异常的一种可能性，并不一定发生这些异常 | 执行 throw 一定会抛出某种异常      |

## 集合进阶

### 集合类体系结构

- 集合
  - Collection（单列集合）（接口）
    - List（可重复集合）（接口）
      - ArrayList（实现类）
      - LinkedList（实现类）
      - ……
    - Set（不可重复集合）（接口）
      - HashSet（实现类）
      - TreeSet（实现类）
      - ……
  - Map（双列集合）（接口）
    - HashMap（实现类）
    - ……

### Collection集合概述和使用

Collection 集合是单列集合的顶层接口，他表示一组对象，这些对象也称为 Collection 的元素。JDK 不提供子接口的任何直接实现，他提供更具体的子接口（如 List 和 Set ）实现。

创建 Collection 集合的对象采用多态的形式，通过 ArrayList 实现。

Collection<String> c = new ArrayList<String>();

#### Collection 集合的遍历

public Iterator<E> iterator()：返回此集合中元素的迭代器。

Iterator：迭代器，一个接口，集合的专用遍历方式。

- Iterator<E> iterator：返回此集合中元素的迭代器，通过集合的 iterator() 得到。
- 迭代器是通过集合的 Iterator() 方法得到的，所以我们说它是依赖于集合而存在的。

Iterator 中的常用方法：

E next()：返回迭代中的下一个元素。

boolean hasNext()：如果迭代具有更多元素，则返回true。

```java
//集合的遍历实例：
import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

public class Test3 {
    public static void main(String[] args) {
        Collection<String> c = new ArrayList<>();
        c.add("Hello");
        c.add("World");
        c.add("java");
        Iterator<String> it = c.iterator();
        while(it.hasNext())
            System.out.println(it.next());
    }
}
```

###  List 集合概述和使用

#### List 集合概述

- 有序集合（也称为序列），用户可以精确控制每个元素的插入位置，用户可以通过整数索引访问元素，并搜索列表中的元素。
- 与 Set 集合不同，列表通常允许重复的元素。

#### 并发修改异常

并发修改异常：ConcurrentModificationException

产生原因：迭代器遍历的过程中，通过集合对象修改了集合中元素的长度，造成了迭代器获取元素中预期修改值和实际修改值不一致。

解决方案：解决方案：用for循环遍历，然后用集合对象做操作即可。

简单来说就是在迭代器在迭代过程中不能修改。

#### ListIterator

ListIterator：列表迭代器。这是一个接口。

- 通过List集合的listIterator() 方法得到，所以它是List集合特有的迭代器。
- 用于允许程序员沿任一方向遍历列表的列表迭代器，在迭代期间修改列表，并获取列表中迭代器的当前位置。

ListIterator 中的常用方法：

E next()：返回迭代器中的下一个元素。

boolean hasNext()：如果迭代具有更多元素，则返回true。

E previous()：返回列表中的上一个元素。

boolean hasPrevious()：如果此列表迭代器在相反方向遍历列表时，具有更多元素，则返回true。

void add(E e)：将指定的元素插入列表。

在ListIterator 迭代器中不会出现并发修改异常。

#### 增强for循环

增强for：简化数组和Collection集合的遍历

- 实现 Iterator 接口的类允许其对象成为增强 for 语句的目标。
- 它是JDK5 之后出现的，其内部原理是一个 Iterator 迭代器。

增强for 的格式：

for(元素数据类型 变量名: 数据或 Collection 集合){

​	//在此处使用变量即可，该变量就是元素

}

```java
//范例
for(int i:arr){
    System.out.println(i);
}
```

#### 数据结构基础

数据结构是计算机存储、组织数据的方式。是指相互之间存在一种或多种特定关系的数据元素的集合，通常情况下，精心选择的数据结构可以带来更高的运行或者存储效率。

常见的数据结构

- 栈
  - 这种数据模型是一种单出口的模式。栈是一种数据先进后出的模型。
  - 数据进入栈模型的过程称为：压/进栈；数据离开栈模型的过程称为：弹/出栈。
- 队列
  - 这种数据模型的数据进出口在两端。队列是一种数据先进先出的模型。
  - 数据从后端进入队列模型的过程称为：入队列；数据从前端离开队列模型的过程称为：出队列。
- 数组
  - 数组是一种查询快，增删慢的模型。
  - 查询数据通过索引定位，查询任意数据耗时相同，查询效率高；删除数据时，要讲原始数据删除，同时后面的每个数据前移，删除效率低；添加数据时，添加位置后的每个数据后移，在添加元素，添加效率极低。
- 链表
  - 链表是一种增删慢，查询快的模型（对比数组而言）。链表中的元素由内存地址、数据和下一个元素地址组成的。
  - 添加元素时，只需要更改其前边一个元素的下一个元素地址和要添加元素的下一个元素地址就可以了；删除元素时，需要将其前边一个元素的下一个元素地址改为要删除元素的下一个元素地址，然后删除元素；查询则需要从前向后逐个进行查询。

#### List集合子类特点

List集合常用子类：ArrayList，LinkedList。

- ArrayList：底层数据结构是数组，查询快，增删慢。
- LinkedList：底层数据结构是链表，查询慢，增删快。

#### LinkedList集合的特有方法

public void addFirst(E e)：在该列表开头插入指定的元素。

public void addLast(E e)：将指定的元素追加到此列表的末端。

public E getFirst()：返回此列表中的第一个元素。

public E getLast()：返回此列表中的最后一个元素。

public E removeFirst()：从此列表中删除并返回第一个元素。

public E removeLast()：从此列表中删除并返回最后一个元素。

### Set集合

Set集合没有特有的功能，都所有功能都继承自 Collection 集合。针对Set 集合主要学习如何确保没有重复元素。

Set集合特点：

- 不包含重复元素的集合
- 没有带索引的方法，所以不能使用普通for 循环遍历。

#### 哈希值

哈希值是JDK 根据对象的地址或字符串或者数字计算出来的int 类型的数值。

Object 类中有一个方法 可以获取对象的哈希值。

- public int hashCode()：返回对象的哈希码值。

对象的哈希值特点

- 统一个对象多次调用hashCode() 方法返回的哈希值是相同的。
- 默认情况下，不同对象的哈希值是不同的。而重写 hashCode() 方法，可以实现让不同对象的哈希值相同。

#### HashSet 集合概述和特点

HashSet 集合特点

- 底层数据结构是哈希表
- 对底层的迭代顺序不作任何保证，也就是说不保证存储和取出的元素顺序一致
- 没有带索引的方法，所以不能使用普通 for 循环遍历
- 由于是 Set 结合，所以是不包含重复元素的集合

#### 数据结构之哈希表

JDK8 之前，底层采用数组+链表实现，介意说是一个元素为链表的数组。

JDK8 之后，在长度比较长的时候，底层实现了优化。

#### HashSet集合保证元素唯一性源码分析

HashSet 集合添加一个元素的过程：

1. 调用对象的 HashCode() 方法获取对象的哈希值；
2. 根据对象的哈希值计算对象的存储位置；
3. 判断该位置是否存在元素；
   1. 如果有，则遍历该位置的所有元素，和新存入的元素比较哈希值是否相同；
      1. 若哈希值有相同的，则调用 equals() 方法比较对象内容是否相等；
         1. equal() 方法返回true，说明元素重复，不存储。
         2. equal() 方法返回false，说明元素不重复，将元素添加到该位置。
      2. 若哈希值都不相同，则将元素添加到该位置。
   2. 如果没有，则将元素添加到该位置。

HashSet 集合存储元素要保证元素唯一性，需要重写HashCode() 和equal() 方法。

#### LinkedHashSet 集合概述和特点

LinkedHashSet 集合特点：

- 哈希表和链表实现的Set接口，具有可预测的迭代次序
- 由链表保证元素有序，也就是说元素的存储和取出顺序是一致的
- 由哈希表保证元素唯一，也就是没有重复元素

#### TreeSet 集合概述和特点

TreeSet 集合特点：

- 元素有序，这里的顺序不是指存储和取出的顺序，而是按照一定的规则进行排序，具体的排序方法取决于构造方法。

  TreeSet()：根据其元素的自然排序进行排序。

  TreeSet(Comparator comparator)：根据指定的比较器进行排序。

- 没有带索引的方法，所以不能使用普通 for 循环遍历
- 由于是Set 集合，所以不包含重复元素的集合

自然排序Comparable 的使用：

- 用TreeSet 集合存储自定义对象，无参构造方法使用的是自然排序对元素进行排序的
- 自然排序，就是让元素所属的类实现Comparable 接口，重写compareTo(T o) 方法
- 重写方法时，一定要注意排序规则必须按照要求的主要条件和次要条件来写。

比较器 Comparator 的使用：

- 用TreeSet 集合存储自定义对象，带参构造方法使用的是比较器排序对元素进行排序的
- 比较器排序，就是让集合构造方法接受 Comparator 的实现类对象，重写compare(T o1,T o2) 方法
- 重写方法时，一定要注意排序规则必须要按照要求的主要条件和次要条件来写。

## 泛型

泛型是JDK5 中引入的特性，他提供了编译时类型安全检测机制，该机制允许在编译时检测到非法的类型，它的本质是一个参数化类型，也就是说所操作的数据类型被指定为一个参数。

参数化类型就是将类型由原来的类型参数化，然后在使用/调用时传入具体的类型。这种参数类型可以用在类、方法和接口中，分别被称为泛型类，泛型方法，泛型接口。

泛型定义格式：

- <类型>：指定一种类型的格式，这里的类型可以看成是形参
- <类型1，类型2…>：指定多种类型的格式，多种类型之间用逗号隔开。这里的类型可以看成是形参
- 将来具体调用时候给定的类型可以看成是实参，并且实参的类型只能是引用数据类型。

泛型的好处：

- 把运行时期的问题提前到了编译期间
- 避免了强制类型转换

### 泛型类

泛型类的定义格式：

修饰符 class 类名 <类型>{}

eg.    public class Generic<T> {}			//此处T可以随意写成任意标识，常见的如T、E、K、V 等形式的参数常用于表示泛型

```java
//泛型类定义
public class Generic<T> {
    private T t;
    public T getT(){
        return t;
    }
    public void setT(T t){
        this.t = t;
    }
}
//泛型类使用
public class GenericDemo {
    public static void main(String[] args){
        Generic<String> g1 = new Generic<>();
        g1.setT("wxy");
        System.out.println(g1.getT());
        Generic<Integer> g2 = new Generic<>();
        g2.setT(100);
        System.out.println(g2.getT());
    }
}
```

### 泛型方法

泛型方法的定义格式：

修饰符 <类型> 返回值类型 方法名(类型 变量名){}

eg. 	public <T> void show(T t){}

```java
//泛型方法的定义
public class Generic {
    public<T> void show(T t){
        System.out.println(t);
    }
}
//泛型方法的使用
public class GenericDemo {
    public static void main(String[] args){
        Generic g1 = new Generic();
        g1.show("wxy");
        g1.show(200);
        g1.show(23.14);
    }
}
```

### 泛型接口

泛型接口的定义格式：

修饰符 interface 接口名<类型> {}

eg. 	public interface Generic<T>{}

```java
//泛型接口定义
public interface Generic<T> {
    public void show(T t);
}
//泛型接口实现
public class Genericimpl<T> implements Generic<T> {
    @Override
    public void show(T t) {
        System.out.println(t);
    }
}
//泛型接口的使用
public class GenericDemo {
    public static void main(String[] args){
        Generic<String> g1= new Genericimpl<>();
        g1.show("wxy");
        Generic<Integer> g2 = new Genericimpl<>();
        g2.show(300);
    }
}
```

### 类型通配符

为了表示各种泛型 List 的父类，可以使用类型通配符

- 类型通配符：<?>
- List<?>：表示元素类型未知的List，它的元素可以匹配任何类型
- 这种带通配符的 List 仅表示它是各种泛型 List 的父类，并不能把元素添加到其中

如果说我们不希望 List<?> 是任何泛型 List 的父类，只希望表示它代表某一类泛型 List 的父类，可以使用类型通配符的上限。

- 类型通配符上限：<?extends 类型>
- List<?extends Number>：它表示的类型是 Number 或者其他子类型。

除了可以指定类型通配符的上限，也可以指定类型通配符的下限

- 类型通配符下限：<?super 类型>
- List<?super Number>：它表示的类型是 Number 或者其他父类型。

```java
List<?extends Number> list1 = new ArrayList<Float>();
List<?> list2 = new ArrayList<String>();
List<?super Integer> list3 = new ArrayList<Number>();
```

### 可变参数

可变参数又称参数个数可变，用作方法的形参出现，那么方法参数个数就是可变的了

格式：

修饰符 返回值类型 方法名(数据类型... 变量名){}

eg. 	public static int sum(int... a){}

```java
//可变参数的使用
public class GenericDemo {
    public static void main(String[] args){
        System.out.println(sum(1,2,3,4));
    }
    public static int sum(int... a){
        int sum = 0;
        for (int i : a)
            sum+=i;
        return sum;
    }
}
```

可变参数的主意事项：

- 这里的变量其实是一个数组
- 如果一个方法有多个参数，包含可变参数，可变参数要放在最后。

包含可变参数的常用方法：

Arrays 工具类中有一个静态方法：

public static <T> List<T> asList(T... a)：返回由指定数组支持的固定大小的列表。

**返回的集合不能做增删操作，可以做修改操作。**

List 接口中有一个静态方法：

public static <E> List<E> of(E... elements)：返回包含任意数量的不可变列表。

**返回的集合不能做增删改操作**。

Set 接口中有一个静态方法：

public static <E> Set<E> of<E... elements)：返回一个包含任意数量元素的不可变集合。

**在给元素的时候，不能给元素重复的元素。返回的集合不能做增删改操作，没有修改方法。**

## Map集合

Map集合概述：

- interface Map<K,V> 	K：键的类型；V：值的类型
- 将键映射到值的对象；不能包含重复的键；每个键可以映射到最多一个值

创建Map集合的对象采用多态的形式，使用HashMap实现。

### Map集合的基本功能

public V put(K key,V value)：添加元素，若 key 已存在，则替换 value。

public V remove(Object key)：根据键删除键值对元素，并返回 value；若key不存在，返回null。

public void clear()：移除所有键值对元素

public boolean containsKey(Object key)：判断集合是够包含指定的键

public boolean containsValue(Object value)：判断集合是否包含指定的值

public boolean isEmpty()：判断集合是否为空。

public int size()：返回集合的长度，也就是集合中键值对的个数。

### Map集合的获取功能

public V get(Object key)：根据键获取值；若 key 不存在，返回 null。

public Set<key> keySet()：获取所有键的集合。

public Collection<V> values()：获取所有值的集合。

public Set<Map.Entry<K,V> entrySet()：获取所有键值对对象的集合。

### Map集合的遍历

方式一：

```java
public static void main(String[] args){
    Map<String,String> map = new HashMap<>();
    map.put("qwe001","王晓勇");
    map.put("qwe002","高鑫鑫");
    map.put("qwe003","王森豪");
    Set<String> keySet = map.keySet();
    for (String key:keySet){
        String value = map.get(key);
        System.out.println(key+"："+value);
    }
}
```

方式二：

```java
public static void main(String[] args){
    Map<String,String> map = new HashMap<>();
    map.put("qwe001","王晓勇");
    map.put("qwe002","高鑫鑫");
    map.put("qwe003","王森豪");
    Set<Map.Entry<String, String>> entrySet = map.entrySet();
    for (Map.Entry<String,String> entry : entrySet)
        System.out.println(entry.getKey()+"："+entry.getValue());
}
```

### 案例：统计字符串中字符出现的次数

```java
//需求：键盘录入字符串，要求统计字符串中每个字符出现的次数
//举例：输入“qazwsxqwe”，输出
import java.util.*;

public class GenericDemo {
    public static void main(String[] args) {
        //创建HashMap集合，键是Character，值是Integer。
        HashMap<Character,Integer> hashMap = new HashMap<>();	
        Scanner sc = new Scanner(System.in);
        System.out.print("请输入字符串：");
        String str = sc.nextLine();	//键盘录入字符串
        for (int i = 0;i<str.length();i++){	//遍历字符串，得到每个字符。
            char key = str.charAt(i);
            //拿得到的每个字符作为键，到HashMap集合中去找对应的值，看其返回值
            Integer value = hashMap.get(key);
            //若是 null ，说明该字符不存在HashMap 集合中，就把该字符作为键，1作为值存储
            if (value == null)	
                hashMap.put(str.charAt(i),1);
            //若不是 null ，则说明该字符在HashMap 集合中，把键值对中的值加 1 ，然后重新存储该键值对。
            else{
                value++;
                hashMap.put(str.charAt(i),value);
            }
        }
        //遍历HashMap 集合，按照要求进行拼接。
        StringBuilder sb = new StringBuilder();
        Set<Character> keySet = hashMap.keySet();
        for (Character key : keySet){
            Integer value = hashMap.get(key);
            sb.append(key).append('(').append(value).append(')');
        }
        System.out.println(sb.toString());
    }
}
```

## Collections 类

Collections 类是针对集合操作的工具类。与 Arrays 类 类似。

Collections 类常用的方法：

public static <T extends Comparable<?super T>> void sort(List<T> list)：将指定的列表按照升序排列。

public static void reverse(List<?> list)：反转指定列表中的元素的顺序。

public static void shuffle(List<?> list)：使用默认的随机源排列指定的列表。

### 集合的综合实例

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashMap;
import java.util.TreeSet;
//模拟斗地主
//2.0版本
/*
    1. 创建HashMap，键是编号，值是牌
    2. 创建ArrayList，存储编号
    3. 创建花色数组，和点数数组
    4. 从0开始向HashMap里边存储编号，并存储对应的牌。同时向ArrayList里边存储编号
    5. 洗牌（洗的是编号），用Collections.shuffle()方法实现
    6. 发牌（发的是编号），为了保证编号是排序的，创建TreeSet集合接收）
    7. 定义方法看牌（遍历TreeSet 集合，获取编号，到HashMap集合找对应的牌
    8. 调用看牌方法
* */
public class pokerDemo2 {
    public static void main(String[] args){
        //创建HashMap集合，键是编号，值是牌
        HashMap<Integer,String> hashMap = new HashMap<>();
        //创建ArrayList，存储编号
        ArrayList<Integer> array = new ArrayList<>();
        //创建花色数组，和点数数组
        String[] colors = {"红桃","方片","黑桃","梅花"};
        String[] numbers = {"A","2","3","4","5","6","7","8","9","10","J","Q","K"};
        //从0开始向HashMap里边存储编号，并存储对应的牌。同时向ArrayList里边存储编号
        //遍历顺序不同会影响最终排序结果
        int index = 0;
//        for (String number:numbers)
//            for (String color:colors){
//                hashMap.put(index,color+number);
//                array.add(index++);
//            }
        for (String color:colors)
            for (String number:numbers){
                hashMap.put(index,color+number);
                array.add(index++);
            }
        hashMap.put(index,"小王");
        array.add(index++);
        hashMap.put(index,"大王");
        array.add(index);
        //洗牌（洗的是编号），用Collections.shuffle()方法实现
        Collections.shuffle(array);
        //发牌（发的是编号），为了保证编号是排序的，创建TreeSet集合接收）
        System.out.println(hashMap);
        TreeSet<Integer> player1 = new TreeSet<>();
        TreeSet<Integer> player2 = new TreeSet<>();
        TreeSet<Integer> player3 = new TreeSet<>();
        TreeSet<Integer> dpSet = new TreeSet<>();
        for (int i = 0; i<array.size();i++){
            int x = array.get(i);
            if (i>=array.size()-3)
                dpSet.add(x);
            else if(i%3==0)
                player1.add(x);
            else if(i%3==1)
                player2.add(x);
            else if(i%3==2)
                player3.add(x);
        }
        //调用看牌方法
        lookPoker("王晓勇",player1,hashMap);
        lookPoker("王森豪",player2,hashMap);
        lookPoker("高鑫鑫",player3,hashMap);
        lookPoker("底牌",dpSet,hashMap);
    }
    //定义方法看牌（遍历TreeSet 集合，获取编号，到HashMap集合找对应的牌
    public static void lookPoker(String name,TreeSet<Integer> ts,HashMap<Integer,String> hm){
        System.out.print(name+"的牌是：");
        for (Integer key : ts){
            System.out.print(key+ " ");
            String poker = hm.get(key);
            System.out.print(poker+" ");
        }
        System.out.println();
    }
}
```

## IO流

IO流概述：

- IO：输入输出（Input/Output）
- 流：是一种抽象概念，是对数据传输的总称，也就是说数据在设备间的传输称为流，流的本质就是数据传输。
- IO流就是用来处理设备间数据传输问题的，常见的应用：文件复制，文件上传，文件下载。

IO 流分类

- 按照数据的流向分为：
  - 输入流：读数据
  - 输出流：写数据
- 按照数据类型分为：
  - 字节流：字节输入流和字节输出流
  - 字符流：字符输入流和字符输出流
- 按照功能分为：
  - 节点流：建立起应用程序和数据源之间的连接
  - 处理流：在节点流的基础上工作，加快读写的速度，提高读写的安全性。

InputStream和OutputStream是所有输入输出字节流的父类，Reader与Writer是所有输入输出字符流的父类。

节点流（介质流）：

| 父类   | InputStream          | OutputStream         | Reader          | Writer          |
| ------ | -------------------- | -------------------- | --------------- | --------------- |
| 文件   | FileInputStream      | FileOutStream        | FileReader      | FileWriter      |
| 数组   | ByteArrayInputStream | ByteArrayInputStream | CharArrayReader | CharArrayWriter |
| 字符串 |                      |                      | StringReader    | StringWriter    |
| 管道   | PipedInputStream     | PipedOutputStream    | PipedReader     | PipedWriter     |

处理流（装饰流）：

| 父类   | InputStream         | OutputStream         | Reader            | Writer             |
| ------ | ------------------- | -------------------- | ----------------- | ------------------ |
| 转换流 |                     |                      | InputStreamReader | OutputStreamWriter |
| 缓冲流 | BufferedInputStream | BufferedOutputStream | BufferedReader    | BufferedWriter     |
| 数据流 | DataInputStream     | DateOutputStream     |                   |                    |
| 对象流 | ObjectInputStream   | ObjectOutputStream   |                   |                    |
| 打印流 |                     | PrintStream          |                   | PrintWriter        |

### File 类

File 类在 java.io 下，需要导包。

File：它是文件和目录路径名的抽象表示。

- 文件和目录是可以通过 File 封装成对象的。
- 对于 File 而言，其封装的并不是一个真正存在的文件，仅仅是一个路径名而已，它可以是存在的，也可以是不存在的。将来是要通过具体的操作把这个路径的内容转换为具体存在的。

构造方法：

File(String pathname)：通过将给定的路径名字符串转换为抽象路径名来创建新的 File 实例。

File(String parent,String child)：从父路径名字符串中和子路径字符串创建新的 File 实例。

File(File parent,String child)：从父抽象路径名和子路径名字符串创建新的 File 实例。

```java
//举例：
File f1 = new File("F:\\javafiles\\src\\NewTest4\\模拟斗地主.txt");
System.out.println(f1);
File f2 = new File("F:\\javafiles\\src\\NewTest4","模拟斗地主.txt");
System.out.println(f2);
File f3 = new File("F:\\javafiles\\src\\NewTest4");
File f4 = new File(f3,"模拟斗地主.txt");
System.out.println(f4);
```

#### File 类常见的方法

File 类创建功能：

绝对路径：完整的路径名，不需要任何其他信息就可以定位它所表示的文件。

相对路径：必须使用取自其他路径名的信息进行解释。默认根目录是项目位置。

public boolean createNewFile()：当具有该名称的文件不存在时，创建一个由该抽象路径命名的新空文件。若文件不存在，则创建文件，并返回true；若文件已存在，则不创建文件，并返回false。该方法需要使用异常处理。

public boolean mkdir()：创建由此抽象路径名命名的目录。若目录不存在，则创建目录，并返回true；若目录已存在，则不创建目录，并返回false。

public boolean mkdirs()：创建由此抽象路径名命名的目录，包括任何必需但不存在的父目录。若目录不存在，则创建目录，并返回true；若目录已存在，则不创建目录，并返回false。

Flie 类判断和获取功能：

public boolean isDirectory()：测试此抽象路径名表示的 File 是否为目录。

public boolean isFile()：测试此抽象路径名表示的 File 是否为文件。

public boolean exists()：测试此抽象路径名表示的 File 是否存在。

public String getAbsolutePath()：返回此抽象路径名的绝对路径名字符串。

public String getPath()：将此抽象路径名转换为路径名字符串。

Public String getName()：返回此抽象路径名表示的文件或目录的名称。

public String[] list()：返回此抽象路径名表示的目录中的文件和目录的名称字符串数组。

public File[] listFlies()：返回此抽象路径名表示的目录中的文件和目录的 File 对象数组。

File 类的删除功能：

public boolean delete()：删除由此抽象路径名表示的文件或目录。若该目录下其他内容，则删除失败，返回false。

### 案例：遍历目录

```java
import java.io.File;

/*案例：遍历目录
 * 1. 根据给定的路径创建一个File 对象。
 * 2. 定义一个方法，用于获取给定目录下的所有内容，参数为第一步创建的File对象
 * 3. 获取给定的File 目录下所有的文件或者目录的File 数组
 * 4. 遍历该 File数组，得到每一个File 对象
 * 5. 判断该File对象是否为目录
 *       是：递归调用
 *       否：获取绝对路径输出在控制台
 * 6. 调用方法
 * */
public class FileDemo01 {
    public static void main(String[] args) {
        File f = new File("D:\\工作文件夹");
        getAllFilePath(f);
    }

    public static void getAllFilePath(File f) {
        File[] listFiles = f.listFiles();
        if (listFiles != null) {
            for (File file : listFiles) {
                if (file.isDirectory())
                    getAllFilePath(file);
                else
                    System.out.println(file.getAbsolutePath());
            }
        }
    }
}
```

### 字节流

字节流抽象基类：

- InputStream：这个抽象类是表示字节输入流的所有类的超类
- OutputStream：这个抽象类是表示字节输出流的所有类的超类
- 这两个类的子类名特点：子类名都是以其父类名作为子类名的后缀。

#### 字节流写数据

FileOutputStream：文件输出流用于写入File。

在写入数据时若要实现换行，在不同的操作系统中识别方式不一样，在Windows系统中采用“\r\n”识别换行，在Linux系统中“\n”识别换行，在Mac系统中“\r”识别换行。

构造方法：

public FileOutputStream(File file)：创建文件输出流以写入由指定的 File 对象表示的文件。

public FileOutputStream(String name)：创建文件输出流以指定的名称写入文件。

public FileOutputStream(String name,boolean append)：创建文件输出流以指定的文件写入文件，若append为true，则字节将写入文件的末尾而不是开头。

此构造方法做了三件事：调用系统功能创建了文件，创建字节流对象，让字节输出流对象指向文件。

常用方法：

public void write(int b)：将指定的字节写入此文件输出流。一次写一个字节数据。

public void write(Byte[] b)：将 b.length 字节从指定的字节数据写入此文件输入流。一次写一个字节数组数据。

public void wirte(byte[],int off,int len)：将字节数组中从偏移量 off 开始的 len 长度的字节写入此文件输出流。一次写一个直接数组的部分数据。

public void close()：释放资源（关闭此文件输出流并释放与此相关连的任何系统资源）。

#### 字节流写数据加异常处理

```java
//针对字节流抛出异常的写法
import java.io.FileOutputStream;
import java.nio.charset.StandardCharsets;

public class FileDemo01 {
    public static void main(String[] args){
        FileOutputStream fos1 = null;
        try{
            fos1 = new FileOutputStream("F:\\javafiles\\text.txt");
            fos1.write("abcde".getBytes(StandardCharsets.UTF_8));
        }catch(Exception e){
            e.printStackTrace();
        }finally{
            if (fos1 != null){
                try {
                    fos1.close();
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

#### 字节流读数据

FileInputStream：从文件系统中的文件获取输入字节。

构造方法：

public FileInputStream(String name)：通过打开与实际文件连接来创建一个 FileInputStream 对象，该文件由文件系统中的路径名 name 命名。

常用方法：

public int read()：从输入流中读取一个字节的数据。如果达到文件末尾，则返回-1。

public int read(byte[] b)：从该输入流读取最多 b.length 个字节的数据到一个字节数组b。返回读取的实际字节数。如果文件达到末尾，则返回-1。

public void close()：同FileOutputStream。

```java
//基本的读数据代码示例
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class FileDemo01 {
    public static void main(String[] args) throws IOException {
        int by;
        try (FileInputStream fis = new FileInputStream("F:\\javafiles\\test.txt")) {
            while ((by = fis.read()) != -1) {
                System.out.print((char) by);
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
    }
}
```

```java
//在使用read(byte[] b)时，使用String(byte[] bytes,int offset,int length)构造方法
//示例
FileInputStream fis = new FileInputStream("test.txt");
byte[] bys = new byte[1024];
int len = 0;
while((len=fis.read(bys))!=-1){
    System.out.print(new String(bys,0,len));
}
fis.close();
```

#### 字节缓冲流

字节缓冲流：

- BufferedOutputStream：该类实现缓冲输出流，通过设置这样的输出流，应用程序可以向底层输入流写入字节，而不必为写入的每个字节导致底层系统的调用。
- BufferedInputStream：创建BufferedInputStream 将创建一个内部缓冲数组，当从流中读取或跳过字节时，内部缓冲区将根据需要从所包含的输入流中重新填充，一次很多字节。

字节缓冲流仅仅提供缓冲区，而不是真正的读写数据，读写数据还得依靠基本的字节流对象进行操作。

构造方法：

字节缓冲输出流：BufferedOutputStream(OutputStream out)

字节缓冲输入流：BufferedInputStream(InputStream in)

#### 案例：文件复制

```java
/*案例1：复制文本
 * 1. 根据数据源创建字节输入流对象
 * 2. 根据目的地创建字节输出流对象
 * 3. 读写数据，复制文本文件（一次读取一个字节，一次写入一个字节）
 * 4. 释放资源
 * */
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileDemo01 {
    public static void main(String[] args) throws IOException {
        FileInputStream fis = new FileInputStream("D:\\工作文件夹\\学习文档\\python笔记.txt");
        FileOutputStream fos = new FileOutputStream("F:\\javafiles\\python.txt");
        int by;
        try{
            while((by=fis.read())!=-1){
                fos.write(by);
            }
        }catch(Exception e){
            e.printStackTrace();
        }finally{
            fis.close();
            fos.close();
        }
    }
}
/*案例2：复制图片
 * 1. 根据数据源创建字节输入流对象
 * 2. 根据目的地创建字节输出流对象
 * 3. 读写数据，复制图片（一次读取一个字节数组，一次写入一个字节数组）
 * 4. 释放资源
 * */
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileDemo01 {
    public static void main(String[] args) throws IOException {
        FileInputStream fis = new FileInputStream("F:\\一见倾心系列三周年图包\\67一见倾心系列第六十七期（汉服）\\4K片头壁纸.jpg");
        FileOutputStream fos = new FileOutputStream("F:\\javafiles\\4K图片.jpg");
        FileInputStream fis2 = new FileInputStream("test.txt");
        byte[] bys = new byte[1024];
        int len = 0;
        while((len=fis.read(bys))!=-1){
            fos.write(bys,0,len);
        }
        fis.close();
        fos.close();
    }
}

/*案例：复制视频
 * 1. 根据数据源创建字节输入缓冲流对象
 * 2. 根据目的地创建字节输出缓冲流对象
 * 3. 读写数据，复制文本文件（一次读取一个字节，一次写入一个字节）
 * 4. 计算耗时
 * 5. 释放资源
 * */
import java.io.*;

public class FileDemo01 {
    public static void main(String[] args) throws IOException {
        long startTime = System.currentTimeMillis();
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream("D:\\工作文件夹\\视频1.mp4"));
        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("F:\\javafiles\\视频2.mp4"));
        byte[] bys = new byte[1024];
        int len = 0;
        while((len=bis.read(bys))!=-1){
            bos.write(bys,0,len);
        }
        bis.close();
        bos.close();
        long endTime = System.currentTimeMillis();
        System.out.println("共耗时"+(endTime-startTime)+"毫秒");
    }
}

```

### 字符流

由于字节流操作中文不是特别方便，所以Java就提供了字符流。

字符流 = 字节流 + 编码表

用字节流赋值文本文件时，文本文件也会出现中文，但是没问题，原因是最底层操作会自动进行字节拼接成中文。

汉字在存储的时候，无论选择哪种编码格式存储，第一个字节都是负数。系统通过是否为负数进行识别拼接。其中GBK格式，中文占用2个字节；UTF-8格式，中文占用3个字节。

#### 编码表

字符集是一个系统支持的所有字符的集合，包括各个国家文字，标点符号，图形符号，数字等。计算机要准确的存储和识别各种字符集符号，就需要进行字符编码，一套字符集必然至少有一套字符编码。常见的字符集有ASCII字符集、GB系列字符集、Unicode字符集等。

ASCII字符集

- ASCII（American Standard Code for Information Interchange，美国信息交换标准代码）：是基于拉丁字母的一套电脑编码系统，用于显示现代英语，主要包括控制字符（回车键、退格、换行键等）和可显示字符（英文大小写字符、阿拉白数字和西文符号）。

- 基本的ASCII字符集，使用7位表示一个字符，共128字符。ASCII的扩展字符集使用8位表示一个字符，共
  256字符，方便支持欧洲常用字符。是一个系统支持的所有字符的集合，包括名国家文字、标点符号、图形符号、数字等。

GB系列字符集

- GB2312：简体中文码表。一个小于127的字符的意义与原来相同，但两个大于127的字符连在一起时，就表示一个汉字，这样大约可以组合了包含7000多个简体汉字，此外数学符号、罗马希腊的字母、日文的假名等都编进去了，连在ASCII里本来就有的数字、标点、字母都统统重新编了两个字节长的编码，这就是常说的“全角”字符，而原来在127号以下的那些就叫“半角”字符了。
- GBK：最常用的中文码表。是在GB2312 标准基础上的扩展规范，使用了双字节编码方案，共收录了21003个汉字，完全兼容GB2312 标准，同时支持繁体汉字以及日韩汉字等。
- GB18030：最新的中文码表。收录汉字70244个，采用多字节编码，每个字可以由1个、2个或4个字节组成。支持中国国内少数民族的文字，同时支持繁体汉字以及日韩汉字等。

Unicode字符集

- 为表达任意语言的任意字符而设计，是业界的一种标准，也称为统一码、标准万国码。它最多使用4个字节的数字来表达每个字母、符号或者文字。有三种编码方案：UTF-8、UTF-16和UTF32。最为常用的是UTF-8编码。

- UTF-8编码：可以用来表示 Unicode 标准中任意字符，它是电子邮件、网页及其他存储或传送文字的应用中，优先采用的编码。互联网工程工作小组(IETF)要求所有互联网协议都必须支持 UTF-8 编码。它使用一至四个字节为每个字符编码。

  编码规则：128个US-ASCII字符,只需一个字节编码；拉丁文等字符，需要二个字节编码；大部分常用字(含中文)，使用三个字节编码；其他极少使用的 Unicode 辅助字符，使用四字节编码。

小结：采用何种规则编码，就要采用对应规则解码，否则就会出现乱码。

Java程序中的编码和解码：

编码：

- byte[] getBytes()：使用平台默认字符集将该 String 编码为一系列字节，将结果存储到新的字节数组中。
- byte[] getBytes(String charsetName)：使用指定的字符集将该 String 编码为一系列字节，将结果存储到新的字节数组中。

解码：

- String(byte[] bytes)：通过使用平台的默认字符集解码指定的字节数组来构造新的String。
- String(bytes[] bytes,String charsetName)：通过指定的默认字符集解码指定的字节数组来构造新的String。

#### 字符流的输入输出数据

字符流抽象基类：

- Reader：字符输入流的抽象基类
- Writer：字符输出流的抽象基类

字符流中和编码解码问题相关的两个类：

- InputStreamReader：这是字节流到字符流的桥梁，它读取字节，并使用指定的编码将其解码为字符。使用的字符集可以由名称指定，也可以被明确指定，或者可以接受平台的默认字符集。
- OutputStrreamWriter：这是字符流到字节流的桥梁，使用指定的编码将写入的字符集编码为字节。使用的字符集可以由名称指定，也可以被明确指定，或者可以接受平台的默认字符集。

构造方法：

InputStreamReader(InputStream in)：创建一个使用默认字符集的InputStreamReader。 

InputStreamReader(InputStream in,String charsetName)：创建一个使用指定字符集的InputStreamReader。

OutputStreamWriter(OutputStream out)：创建使用默认字符编码的OutputStreamWriter。

OutputStreamWriter(OutputStream out, String charsetName)：创建使用指定charset的OutputStreamWriter。

字符流写数据：

public void wirte(int c)：写入一个字符。

public void wirte(char[] cbuf)：写入一个字符数组。

public void wirte(char[] cbuf,int off,int len)：写入一个字符数组的一部分。

public void wirte(String str)：写入一个字符串。

public void wirte(String str, int off, int len)：写入一个字符串的一部分。

字符流相对于字节流会有缓冲区。可以使用flush 方法，刷新流。

public void flush()：刷新流。

public void close()：关闭流，释放资源，但在关闭之前会先刷新流，一旦关闭，就不能再写数据。

字符流读数据：

public int read()：一次读一个字符数据。

public int read(char[] cbuf)：一次读一哥字符数组数据。

#### 字符流的便捷类

FileWriter：继承自OutputStreamWriter。无法修改字符集。

FileReader：继承自InputStreamReader。无法修改字符集。

构造方法：

public FileWriter(String fileName)：构造一个给定文件名的FileWriter对象。

public FileReader(String fileName)：创建一个新的FileReader，给定要读取的文件的名称。

这两个方法与其父类相同，但不能修改字符集。

#### 字符缓冲流

字符缓冲流：

- BufferedWriter：将文本写入字符输出流，缓冲字符，以提供单个字符，数组和字符串的高效写入，可以指定缓冲区大小，或者可以接受默认大小。默认值足够大，可用于大多数用途。
- BufferedReader：从字符输入流读取文本，缓冲字符，以提供字符，数组和行的高效读取，可以指定缓冲区大小，或者可以使用默认大小。默认值足够大，可用于大多数用途。

构造方法：

BufferedWriter(Writer out)

BufferedReader(Reader in)

字符缓冲流特有功能

BufferedWriter：

public void newLine()：写一行 行分隔符，行分隔符字符串由系统属性定义。

BufferedReader：

public String readLine()：读一行文字。结果包含行的内容的字符串，不包含任何终止字符，如果流的结尾已经到达，则返回null。

#### 案例：文件复制

```java
/*案例：复制文本
 * 1. 根据数据源创建字符缓冲流对象
 * 2. 根据目的地创建字符缓冲流对象
 * 3. 读写数据，复制文本文件（一次读取一行，一次写入一行）
 * 4. 计算耗时
 * 5. 释放资源
 * */
import java.io.*;

public class FileDemo01 {
    public static void main(String[] args) throws IOException {
        long startTime = System.currentTimeMillis();
        BufferedReader br = new BufferedReader(new FileReader("D:\\工作文件夹\\学习文档\\python笔记.txt"));
        BufferedWriter bw = new BufferedWriter(new FileWriter("F:\\javafiles\\python.txt"));
        String str;
        while ((str = br.readLine())!=null){
            bw.write(str);
            bw.newLine();
            bw.flush();
        }
        br.close();
        bw.close();
        long endTime = System.currentTimeMillis();
        System.out.println(endTime-startTime);
    }
}
```

#### 案例：目录复制

```java
package NewTest4.test3;

import java.io.*;

//复制单级目录
/*
* 创建数据源目录File对象
* 获取数据源目录File对象的名称
* 创建目的地目录File 对象，路径名是模块名+文件名 组成
* 判断目的地目录对应的File 是否存在，如果不存在，就创建
* 获取数据源目录下所有文件的File 数组
* 遍历FIle 数组，得到每一个File对象，该File对象，其实就是数据源文件
* 获取数据源文件File 对象的名称
* 创建目的地文件File对象，路径名是目的地目录+文件名 组成
* 复制文件（由于文件不仅是文本文件，还有图片，视频等，所以采用字节流复制文件）
* */
public class Cpydir{
    public static void main(String[] args) throws IOException {
        File src_dir = new File("D:\\工作文件夹\\4.22测试题");
        String src_dirname = src_dir.getName();
        File des_dir = new File("F:\\javafiles\\src\\NewTest4\\test3",src_dirname);
        if(!des_dir.exists()){
            des_dir.mkdir();
        }
        File[] listfiles = src_dir.listFiles();
        for(File src_file:listfiles){
            String src_filename = src_file.getName();
            File des_filename = new File(des_dir,src_filename);
            copyfile(src_file,des_filename);
        }
    }

    private static void copyfile(File src_file, File des_file) throws IOException {
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream(src_file));
        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(des_file));
        byte[] bys = new byte[1024];
        int len = 0;
        while ((len=bis.read(bys))!=-1){
            bos.write(bys,0,len);
        }
        bis.close();
        bos.close();
    }
}
```

```java
import java.io.*;

//复制多级目录
/*
* 创建数据源File对象和目的地File对象
* 写方法实现文件夹的复制，参数为数据源File对象和目的地File对象
* 判断数据源File是否是目录
*   是：
*       1.在目的地下创建和数据源File名称一样的目录
*       2.获取数据源File 下所有文件或者目录的File数组
*       3.遍历该File 数据，得到每一个File对象
*       4.把该File作为数据源File对象，递归调用复制文件夹的方法
*   不是：
*       说明是文件，直接复制，用字节流
* */
public class Cpydirs {
    public static void main(String[] args) throws IOException{
        File src_dir = new File("D:\\工作文件夹\\Python-100-Days-master");
        File des_dir = new File("F:\\javafiles\\src\\NewTest4\\test3");
        copydir(src_dir,des_dir);
    }
    //复制文件夹
    private static void copydir(File src_dir, File des_dir) throws IOException{
        if(src_dir.isDirectory()){
            //在目的地下创建和数据源File名称一样的目录
            String src_filename = src_dir.getName();
            File newdir = new File(des_dir,src_filename);
            if (!newdir.exists()){
                newdir.mkdir();
            }
            //获取数据源File下所有文件或者目录的File数组
            File[] fileArray = src_dir.listFiles();
            for (File file: fileArray){
                //把该File作为数据源File对象，递归调用复制文件夹的方法
                copydir(file,newdir);
            }
        }else{
            File newFile = new File(des_dir,src_dir.getName());
            copyfile(src_dir,newFile);
        }
    }

    private static void copyfile(File src_file,File des_file) throws IOException{
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream(src_file));
        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(des_file));
        byte[] bys = new byte[1024];
        int len = 0;
        while ((len=bis.read(bys))!=-1){
            bos.write(bys,0,len);
        }
        bis.close();
        bos.close();
    }
}
```

### 标准操作流

#### 标准输入输出流

System 类中有两个静态的成员变量：

- public static final InputStream in: 标准输入流。通常该对应于键盘输入或由主机环境或用户指定的另一个输入源。
- public static final PrintStream out: 标准输出流。通常该流对应于显示输出或由主机环境或用户指定的另一个输出源。

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
/*
public static final InputStream in: 标准输入流。
自己实现键盘输入数据：
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
这样书写太过麻烦，Java提供了一个类实现键盘录入：
Scanner sc = new Scanner(System.in);
但这是 Scanner 类的实现原理，Java只是对它进行了封装，并提供了相应的一些方法。
 */
public class SystemInDemo {
    public static void main(String[] args) throws IOException {
        //将System.in的字节输入流通过BufferedStreamReader字符转换流转换为字符流，
        //再通过BufferedReader包装成字符缓冲输入流。
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.println("请输入一个字符串：");
        String line = br.readLine();
        System.out.println("你输入的字符串是："+line);
        System.out.println("请输入一个数字：");
        // 获取想要的类型必须通过相应的包装类进行转换。
        int num = Integer.parseInt(br.readLine());
        System.out.println("你输入的数字是："+num);
    }
}
```

```java
import java.io.PrintStream;
/*
* public static PrintStream out:标准输出流。
* System.out 本质是一个字节输出流
* PrintStream 有的方法，System.in都可以使用。
* */
public class SystemOutDemo {
    public static void main(String[] args) {
        PrintStream ps = System.out;
        ps.println("Hello World");
        ps.print('a');
        ps.print(100);
        System.out.println("Hello World!");
        System.out.println();
    }
}
```

#### 打印流

打印流分为字节打印流和字符打印流

- 字节打印流：PrintStream
- 字符打印流：PrintWriter

打印流的特点：只负责输出数据，不负责读取数据；有自己特有的方法。

字节打印流：

- PrintStream(String fileName)：使用指定的文件名创建新的打印流。
- 使用继承父类的方法写数据，查看的时候会转码，使用自己的特有方法写数据，数据会原样输出。

字符打印流：

两个主要的构造方法：

PrintWriter(String fileName)：使用指定的文件名创建一个新的PrintWriter，而不需要自动执行刷新。

PrintWriter(Writer out,boolean autoFlush)：创建一个新的PrintWriter。out：字符输出流；autoFlush：一个布尔值，如果为真，则println，printf，format方法将会刷新输出缓冲区。

因为字符打印流需要Flush方法才能输出到文件，因此可以通过第二个构造方法使其自动刷新。

```java
import java.io.*;

public class PrintWriterDemo {
    public static void main(String[] args) throws IOException {
        PrintStream ps = new PrintStream("src/NewTest4/test4/ps.txt");
        //使用字节输出流写数据
        //输出 100 会进行转码，转换为 d。
        ps.write(100);
        //使用特有方法写数据
        ps.println("王");
        ps.close();
        PrintWriter pw = new PrintWriter("src/NewTest4/test4/pw.txt");
        //因为是字符输出流，使用需要Flush。
        pw.write("Hello");
        pw.write("\r\n");
        pw.flush();
        pw.println("World!");
        pw.flush();
        pw.close();
        //使用这种构造方法，不需要手动Flush了。
        PrintWriter pw2 = new PrintWriter(new FileWriter("src/NewTest4/test4/pw2.txt"),true);
        pw2.println("Hello");
        pw2.println("World");
        pw2.close();
    }
}
```

案例：文件复制

```java
import java.io.*;

public class CopyFileDemo {
    public static void main(String[] args) throws IOException {
        //创建字符输入流对象
        BufferedReader br = new BufferedReader(new FileReader("F:\\javafiles\\python.txt"));
        //创建字符输出流对象
        PrintWriter pw = new PrintWriter(new FileWriter("F:\\javafiles\\src\\NewTest4\\test4\\copy.txt"),true);
        //读写数据，复制文件
        String line;
        while((line = br.readLine())!= null)
            pw.println(line);
        br.close();
        pw.close();
    }
}
```

### 对象序列化流

对象序列化：就是将对象保存到磁盘中，或者在网络中传输对象。

这种机制就是使用一个字节序列表示一个对象，该字节序列包含：对象的类型，对象的数据和对象中存储的属性等信息。字节写到文件之后，相当于文件中持久保存了一个对象的信息。反之，该字节序列还可以从文件中读取出来，重构对象，对它进行反序列化。

要实现序列化和反序列化就要使用对象序列化流和对象反序列化流：

- 对象序列化流：ObjectOutputStream
- 对象反序列化流：ObjectInputStream

#### 对象序列化流：

将Java对象的原始数据类型和图形写入OutputStream。可以使用ObjectInputStream读取（重构）对象。可以通过使用流的文件来实现对象的持续存储。如果流是网络套接字流，则可以在另一个主机上或另一个进程中重构对象。

构造方法：

ObjectOutputStream(OutStream out)：创建一个写入指定OutputStream的ObjectOutputStream对象。

序列化对象的方法：

void writeObject(Object obj)：将指定的对象写入ObjectOutputStream。

注意：

- 一个对象要想被序列化，该对象所属的类必须实现Serializable 接口。

- Serializable 是一个标记接口，实现该接口，不需要重写任何方法。

> 如果将没有继承Serializable的类序列化会抛出NotSerializableException异常。Serializable 接口在java.io 包下

#### 对象反序列化流

ObjectInputStream 反序列化先前使用ObjectOutputStream编写的原始数据和对象。

构造方法：

ObjectInputStream(InputStream in)：创建从指定的InputStream 读取的ObjectInputStream。

反序列化对象的方法：

Object readObject()：从ObjectInputStream读取一个对象。

```java
import java.io.*;

public class ObjectOutputStreamDemo {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        //创建序列化流
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("src/NewTest4/test4/oos.txt"));
        //创建一个对象
        StudentSerializableDemo ssd_out = new StudentSerializableDemo("王晓勇",23);
        //将指定对象写入序列化流指定的文件中
        oos.writeObject(ssd_out);
        //释放资源
        oos.close();
        //创建反序列化流
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream("src/NewTest4/test4/oos.txt"));
        //从ObjectInputStream读取一个对象
        Object obj = ois.readObject();
        //将读取到的对象向下转型，还原成原来的对象。
        StudentSerializableDemo ssd_in = (StudentSerializableDemo)obj;
        System.out.println(ssd_in.getName()+","+ssd_in.getAge());
        ois.close();
    }
}
```

#### 对象序列化流的问题

用对象序列化了一个对象后，假如我们修改了对象所属的类文件，读取数据会抛出InvalidClassException异常。因此我们需要给对象所属的类添加一个serialVersionUID。

private static final long serialVersionUID = 42L;

如果一个对象中的某个成员变量的值不想被序列化，则需要给该成员变量添加transient 关键字修饰，该关键字标识的成员变量不参与序列化过程。

#### Properties

properties 类是一个Map 体系的集合类；该类可以保存到流中或从流中加载。

properties类的特有方法：

Object setProperty(String key,String value)：设置集合的键和值，都是String 类型，底层调用Hashtable方法put。

String getProperty(String key)：使用此属性列表中指定的键搜索属性。

Set<String> StringPropertyNames()：从该属性列表中返回一个不可修改的键集，其中键及其所对应的值是字符串。

```java
import java.util.Properties;
import java.util.Set;

public class PropertiesDemo {
    public static void main(String[] args) {
        Properties prop1 = new Properties();
        //properties作为Map集合的使用
        prop1.put("wxy","王晓勇");
        prop1.put("zml","赵明蕾");
        Set<Object> keySet = prop1.keySet();
        for(Object key: keySet){
            Object value = prop1.get(key);
            System.out.println(key+","+value);
        }
        Properties prop2 = new Properties();
        //properties特有方法的使用
        prop2.setProperty("lqx","林青霞");
        prop2.setProperty("zmy","张曼玉");
        Set<String> names = prop2.stringPropertyNames();
        for(String key: names){
            String value = prop2.getProperty(key);
            System.out.println(key+","+value);
        }
    }
}
```

Properties和IO流结合的方法：

void load(InputStream inStream)：从输入字节流读取属性列表（键和元素对）

void load(Reader reader)：从输入字符流读取属性列表（键和元素对）

void store(OutputStream out,String comments)：将此属性列表（键和元素对）写入此Properties 表中，以合适于使用load(InputStream)方法的格式写入输出字节流。

void store(Writer writer,String comments)：将此属性列表（键和元素对），写入此Properties表中，以适合使用load(Reader)方法的格式写入输出字符流。

```java
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Properties;
public class PropertiesDemo2 {
    public static void main(String[] args) throws IOException{
        myStore();
        myLoad();
    }
    //从文件中读取
    private static void myLoad() throws IOException{
        Properties prop = new Properties();
        FileReader fr = new FileReader("src/NewTest4/test4/fw.txt");
        prop.load(fr);
        System.out.println(prop);
        fr.close();
    }
	//把Properties对象写入文件
    private static void myStore() throws IOException {
        Properties prop = new Properties();
        prop.setProperty("lqx","林青霞");
        prop.setProperty("zmy","张曼玉");
        FileWriter fw = new FileWriter("src/NewTest4/test4/fw.txt");
        prop.store(fw,null);
        fw.close();
    }
}
```

## 多线程

### 进程和线程

进程是正在运行的程序。

- 是系统进行资源分配和调用的独立单位
- 每一个进程都有它自己内存空间和系统资源

线程是进程中的单个顺序控制流，是一条执行路径。

- 单线程：一个进程如果只有一条执行路径，称为单线程程序。
- 多线程：一个进程如果有多条执行路径，称为多线程程序。

### 多线程的实现和使用方式

#### 多线程的实现方法一

继承Thread 类

​	定义一个类MyThread继承Thread 类，在类中重写run()方法，创建MyThread类的对象，通过start()方法启动线程。

重写run()方法是用来封装被线程执行的代码。

run()方法和start()方法的区别：

run()：封装线程执行的代码，直接调用相当于普通方法的调用。

start()：启动线程，然后由 JVM 调用此线程的run()方法。

#### 设置和获取线程名称

void setName(String name)：将此线程的名称更改为参数name。

String getName()：返回此线程的名称。

也可以使用Thread的带参构造方法，直接设置线程名称。前提是需要在继承Thread的类中重载Thread的构造方法。

currentThread() 是Thread类中的一个静态方法，返回对当前正在执行的线程对象的引用。

Thread.currentThread().getName()：获取当前正在执行线程的名称。

```java
// 继承类
public class MyThread extends Thread{
    public MyThread(){}
    public MyThread(String name){
        super(name);
    }
    @Override
    public void run() {
        for(int i = 0;i<100;i++)
            System.out.println(getName()+i);
    }
}
//测试类
public class MyThreadDemo{
    public static void main(String[] args) {
        MyThread my1 = new MyThread("高铁");
        MyThread my2 = new MyThread("飞机");
        my1.setName("火车");
        my2.setName("大巴");
        my1.start();
        my2.start();
        System.out.println(Thread.currentThread().getName());
    }
}
```

#### 线程调度

线程有两种调度模型：

- 分时调度模型：所有线程轮流使用CPU的使用权，平均分配每个线程占用CPU的时间片。
- 抢占式调度模型：优先让优先级高的线程使用CPU，如果线程的优先级相同，name会随机选择一个，优先级高的线程获取的CPU时间片相对多一些。

Java使用的是抢占式调度模型。

Thread类中设置和获取线程优先级的方法：

线程优先级最小是1，最大是10，默认是5。线程优先级高仅仅表示线程获取的CPU时间片的几率高。

public final int getPriority()：返回此线程的优先级。

public final void setPriority(int newPriority)：更改此线程的优先级。

#### 线程控制

static void sleep(long mills)：使当前正在执行的线程停留（暂停执行）指定的毫秒数。

void join()：等待这个线程死亡。

void setDaemon(boolean on)：将此线程标记为守护线程，当运行的线程都是守护线程时，Java虚拟机将退出。

```java
public class MyThreadDemo{
    public static void main(String[] args) {
        MyThread my1 = new MyThread();
        MyThread my2 = new MyThread();
        my1.setName("关羽");
        my2.setName("张飞");
        //设置守护线程
        my1.setDaemon(true);
        my2.setDaemon(true);
        my1.start();
        my2.start();
        //设置主线程为刘备
        Thread.currentThread().setName("刘备");
        //主线程执行代码
        for (int i = 0;i<10;i++){
            System.out.println(Thread.currentThread().getName()+":"+i);
        }
    }
}
```

#### 线程的生命周期

![线程生命周期](D:\工作文件夹\学习文档\线程生命周期.png)

#### 多线程的实现方式二

实现Runnable 接口

- 定义一个类MyRunnable 实现Runnable接口
- 在MyRunnable 类中重写run()方法
- 创建MyRunnable类的对象
- 创建Thread类的对象，把MyRunnable对象作为构造方法的参数
- 启动线程

```java
//继承类
public class MyRunnable implements Runnable{
    @Override
    public void run() {
        for (int i = 0;i<100;i++){
            System.out.println(Thread.currentThread().getName()+":"+i);

        }
    }
}
//实现类
public class MyRunnableDemo {
    public static void main(String[] args) {
        MyRunnable my = new MyRunnable();
        Thread t1 = new Thread(my,"高铁");
        Thread t2 = new Thread(my,"飞机");
        t1.start();
        t2.start();
    }
}
```

相比于继承Thread类，实现Runnable 接口的好处：

- 避免了Java单继承的局限性
- 适合多个相同程序的代码去处理同一个资源的情况，把线程和程序的的代码、数据有效分离，较好的体现了面向对象的设计思想。

#### 案例：买票

```java
/*
* 1. 定义一个类SellTicket 实现Runnable接口，里边定义成员变量private int tickets = 100;
* 2. 在SellTicket类中重写run()方法实现买票：
*       A: 判断票数大于0，就卖票，并告知在哪个窗口卖的
*       B: 卖完票之后，总票数减 1
*       C: 票卖完，跳出循环
* 3. 定义一个测试类SellTicketDemo，对SellTicket进行实现：
*       A: 创建SellTicket类的对象
*       B: 创建三个Thread类的对象，把SellTicket对象作为构造方法的参数，并给出对应的窗口名称
*       C: 启动线程
* */
public class SellTicket implements Runnable{

    private int tickets = 100;
    @Override
    public void run() {
        while(true){
            if (tickets > 0){
                System.out.println(Thread.currentThread().getName()+"正在出售第"+(tickets--)+"票");
            }else
                break;
        }
    }
}
//测试类
public class SellTicketDemo {
    public static void main(String[] args) {
        SellTicket st = new SellTicket();
        Thread t1 = new Thread(st,"窗口1");
        Thread t2 = new Thread(st,"窗口2");
        Thread t3 = new Thread(st,"窗口3");
        t1.start();
        t2.start();
        t3.start();
    }
}
```

### 线程同步

上边的买票案例可能会存在数据安全性问题。

判断多线程程序是否会有数据安全性问题的标准：

- 是否是多线程环境
- 是否有共享数据
- 是否有多条语句操作共享数据

解决多线程安全问题的方法：

把多条语句操作共享数据的代码锁起来，让任意时刻只能有一个线程执行即可。

格式：

```java
synchronzied(任意对象){
	//多条语句操作共享数据的代码
}
```

synchronized(任意对象)：就相当于给代码加了锁，任意对象就可以看成一把锁。

同步的好处和弊端：

- 好处：解决了多线程的数据安全问题；
- 弊端：当线程很多时，因为每个线程都会去判断同步上的锁，这是很耗费资源的，无形中会降低程序的运行效率。  

同步方法：

同步方法：就是把synchronized 关键字加到方法上

格式：

修饰符 synchronized 返回值类型 方法名(参数){ }

同步方法的锁对象是this。

同步静态方法：就是把synchronized关键字加到静态方法上

格式：

修饰符 static synchronized 返回值类型 方法名(参数){ }

同步静态方法的锁对象是 类名.class 。

### 线程安全类

StringBuffer

- 线程安全，可变的字符串序列
- 从版本JDK5 开始，被StringBuilder替代。通常应该使用StringBuilder类，因为它支持所有相同的操作，但它们更快，因为她不执行同步。

Vector

- 从Java2 平台v1.2开始，该类改进了List接口，使其成为Java Collections Framework 的成员。与新的集合实现不同，Vector被同步。如果不需要线程安全的实现，建议使用ArrayList代替Vector。

HashTable

- 该类实现了一个哈希表，它将键映射到值。任何非null对象都可以用作键或者值。
- 从Java2平台1.2 开始，该类进行了改进，实现了Map接口，使其成为Java Collections Framework的成员。与新的集合实现不同，HashMap被同步。如果不需要线程安全的实现，建议使用HashMap代替HashTable。

在多线程环境中，StringBuffer类会被使用到，但是Vector和HashTable一般不会被使用到。这两个类被Collections集合工具类中的synchronizedList(List<T> list)，synchronizedMap(Map<T> map)和synchronizedSet(Set<T> set)替代了。

static <T> List<T> synchronizedList(List<T> list)：返回有指定列表支持的同步(线程安全)列表。

```java
List<String> list = Collections.synchronizedList(new ArrayList<String>());
```

### Lock锁

虽然我们可以理解同步代码块和同步方法的锁对象问题，但是我们并没有直接看到在哪里上锁，在哪里释放锁，为了更清晰的表达如何加锁和释放锁，JDK5以后提供了一个新的锁对象Lock。

Lock实现提供比使用synchronized方法和语句可以获得更广泛的锁定操作。

Lock中提供了获得锁和释放锁的方法：

void lock()：获得锁

void unlock()：释放锁

Lock是接口不能直接实例化，这里采用它的实现类ReentrantLock来实例化。

ReentrantLock的构造方法：

ReentrantLock()：创建一个ReentrantLock的实例。

```java
//在实际使用中，被锁的程序可能会出错，出错后就不会释放锁了。因此一般使用try……finally进行修饰。
//修改上边的类
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class SellTicket implements Runnable{

    private int tickets = 100;
    private Lock lock = new ReentrantLock();
    @Override
    public void run() {
        while(true){
            try{
                lock.lock();
                if (tickets > 0){
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println(Thread.currentThread().getName()+"正在出售第"+tickets+"票");
                    tickets--;
                }
            }finally {
                lock.unlock();
            }
        }
    }
}
```

### 生产者和消费者

生产者消费者模式是一个十分经典的多线程协作模式，生产者消费者问题能够让我们对多线程编程的理解更加深刻，所谓生产者消费者问题，实际上主要是包含了两类线程：

- 一类是生产者线程用于生产数据
- 一类是消费者线程用于消费数据

为了解耦生产者和消费者的关系，通常会采用共享的数据区域，就像一个仓库

- 生产者生产数据之后直接放置在共享数据区域中，并不关心消费者的行为。
- 消费者只需要从共享数据区中去获取数据，并不需要关心生产者的行为。

为了体现生产和消费过程中的等待和唤醒，Java就提供了几个方法供我们使用，这几个方法在Object类中。

void wait()：导致当前线程等待，直到另一个线程调用该对象的notify()方法或notifyAll()方法。

void notify()：唤醒正在等待对象监视器的单个线程。

void notifyAll()：唤醒正在等待对象监视器的所有线程。

#### 实例：生产者与消费者

```java
/*
* 奶箱类（Box）：定义一个成员变量，表示第 x 瓶奶，提供存储牛奶和获取牛奶的操作
* 生产者类（Producer）：实现Runnable接口，重写run()方法，调用存储牛奶的操作
* 消费者类（Customer）：实现Runnable接口，重写run()方法，调用获取牛奶的操作
* 测试类（BoxDemo）：里面有main()方法，main方法中的代码步骤如下：
*    1. 创建奶箱对象，这里共享数据区域
*    2. 创建生产者对象，把奶箱对象作为构造方法参数传递，因为在这个类中要调用存储牛奶的操作
*    3. 创建消费者对象，把奶箱对象作为构造方法参数传递，因为在这个类中要调用获取牛奶的操作
*    4. 创建2个线程对象，分别把生产者和消费者对象作为构造方法参数传递
*    5. 启动线程。
*/
//奶箱类
public class Box {
    //定义一个成员变量，表示第x瓶奶
    private static int milk;
    //定义一个成员变量表示奶箱的状态
    private boolean status = false;
    public synchronized void put(int milk){
        //如果有牛奶，等待消费
        if (status){
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        //如果没有牛奶，就生产牛奶
        this.milk = milk;
        System.out.println("送奶工将第"+this.milk+"瓶奶放入奶箱");
        //生产完毕之后，修改奶箱状态
        status = true;
        //唤醒其他等待的线程
        notifyAll();
    }
    public synchronized void get(){
        //如果没有牛奶，等待生产
        if (!status){
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        //如果有牛奶，就消费牛奶
        System.out.println("用户拿到第"+this.milk+"瓶奶");
        //消费完毕之后，修改奶箱状态
        status = false;
        //唤醒其他等待的线程
        notifyAll();
    }
}
//生产者类
public class Producer implements Runnable{
    private Box b;
    public Producer(Box b){
        this.b = b;
    }
    @Override
    public void run() {
        for (int i = 1;i<=30;i++){
            b.put(i);
        }
    }
}
//消费者类
public class Customer implements Runnable{
    private Box b;
    public Customer(Box b){
        this.b = b;
    }
    @Override
    public void run() {
        while(true){
            b.get();
        }
    }
}
//测试类
public class BoxDemo {
    public static void main(String[] args) {
        Box b = new Box();
        Producer p = new Producer(b);
        Customer c = new Customer(b);
        Thread t1 = new Thread(p);
        Thread t2 = new Thread(c);
        t1.start();
        t2.start();
    }
}
```

## 网络编程

计算机网络：是指将地理位置不同的具有独立功能的多台计算机及其外部设备，通过通信线路连接起来，在网络操作系统，网络管理软件及网络通信协议的管理和协调下，实现资源共享和信息传递的计算机系统。

网络编程：在网络通行协议下，实现网络互连的不同计算机上运行的程序键可以进行数据交换。

网络编程的三要素：IP地址，端口，协议。

**IP地址**：要想让网络中的计算机能够互相通信，必须为每台计算机指定一个标识号，通过这个标识号来指定要接收数据的计算机和识别发送的计算机，而IP地址就是这个标识号。也就是设备的标识。

**端口**：网络的通信，本质上是两个应用程序的通信。每台计算机都有很多的应用程序，那么在网络通信时,如何区分这些应用程序呢？如果说IP地址可以唯一标识网络中的设备，那么端口号就可以唯一标识设备中的应用程序了。也就是应用程序的标识。

端口号：用两个字节标识的整数，它的取值范围是0~65535.其中0~1023之间的端口号用于一些知名的网络服务和应用，普通的应用程序需要使用1024以上的的端口号，如果端口号被另一个服务或应用锁占用，会导致当前程序起动失败。

**协议**：通过计算机网络可以使多台计算机实现连接，位于同—个网络中的计算机在进行连接和通信时需要遵守一定的规则，这就好比在道路中行驶的汽车一定要遵守交通规则样。在计算机网络中，这些连接和通信的规则被称为网络通信协议，它对数据的传输格式传输速率、传输步骤等做了统规定，通信双方必须同时遵守才能完成数据交换。常见的协议有UDP协议和TCP协议。

**UDP协议**：用户数据包协议(User Datagram Protocol)，UDP是无连接通信协议，即在数据传输时，数据的发送端和接收端不建立逻辑连接。简单来说，当一台计算机向另外一台计算机发送数据时，发送端不会确认接收端是否存在，就会发出数据，同样接收端在收到数据时，也不会向发送端反馈是否收到数据。由于使用UDP协议消耗资源小，通信效率高，所以通常都会用于音频、视频和普通数据的传输。例如视频会议通常采用UDP协议，因为这种情况即使偶尔丢失一两个数据包，也不会对接收结果产生影响。但是在使用UDP协议传送数据时，由于UDP的面向无连接性，不能保证数据的完整性，因此在传输重要数据时不建议使用UDP协议。

**TCP协议**：传输控制协议(Transmission Control Protocol)，Tcp协议是面向连接的通行协议，即传输数据前，在发送端和接收端建立逻辑连接，然后再传输数据，它提供了两台计算机之间可靠无差错的数据传输。在TCP连接中必须要明确客户端和服务器端，有客户端向服务器端发出连接请求，每次连接的创建都需要经过“三次握手”。完成三次握手，建立连接后，客户端和服务器端就可以开始进行数据传输例如。由于这种面向连接的特性，TCP协议可保证传输数据的安全，所以应用十分广泛。例如上传文件，下载文件，浏览网页等。

三次握手：TCP协议中，在发送数据的准备阶段，客户端与服务器之间三次交互，以保证连接的可靠。

- 第一次握手，客户端向服务器端发出连接请求，等待服务器确认
- 第二次握手，服务器端想客户端回送一个响应，通知客户端收到了连接请求
- 第三次握手，客户端再次向服务器端发送确认信息，确认连接

### InetAddress 类

此类表示Internet协议(IP)地址

常用方法：

public static InetAddress getByName(String host)：确定主机名称的IP地址。主机名称可以是机器名称，也可以是IP地址。

public String getHostName()：获取此IP地址的主机名。

public String getHostAddress()：返回文本中显示的IP地址字符串。

### UDP通信原理

UDP协议是一种不可靠的网络协议，它在通信的两端各建立一个Socket对象，但是这两个Socket只是发送、接收数据的对象，因此对于基于UDP协议的通信双方而言，没有所谓的客户端和服务器端的概念。

Java提供了DatagramSocket类作为基于UDP协议的Socket。

### UDP发送和接收数据

发送数据的步骤：

1. 创建发送端的Socket对象(DatagramSocket)

   DatagramSocket()

2. 创建数据，并把数据打包

   DatagramPacket(byte[] buf,int length,InetAddress address,int port)

3. 调用DatagramSocket对象的方法发送数据

   void send(DatagramPacket p)

4. 关闭发送端

   void close()

```java
import java.io.IOException;
import java.net.*;

public class UDPsendDemo {
    public static void main(String[] args) throws IOException {
        DatagramSocket ds = new DatagramSocket();
        byte[] bys = "Hello World,I'm coming".getBytes();
        int length = bys.length;
        InetAddress address = InetAddress.getByName("192.168.1.106");
        int port = 10086;
        DatagramPacket dp = new DatagramPacket(bys,length,address,port);
        ds.send(dp);
        ds.close();
    }
}
```

接收数据的步骤：

1. 创建接收端的Socket对象(DatagramSocket)

   DatagramSocket(int port);

2. 创建一个数据包，用于接收数据

   DatagramPacket(byte[] buf,int length);

3. 调用DatagramSocket对象的方法接收数据

   void receive(DatagramPacket p);

4. 解析数据包，并把数据在控制台显示

   byte[] getData();

   int getLength();

5. 关闭接收端

   void close();

```java
import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;

public class UDPReceiveDemo{
    public static void main(String[] args) throws IOException {
        DatagramSocket ds = new DatagramSocket(10086);
        byte[] bys = new byte[1024];
        DatagramPacket dp = new DatagramPacket(bys,bys.length);
        ds.receive(dp);
        byte[] datas = dp.getData();
        int len = dp.getLength();
        String dataString = new String(datas,0,len);
        System.out.print("数据是"+dataString);
        ds.close();
    }
}
```

### UDP通信程序练习

按照下面的要求实现程序

- UDP发送数据：数据来自键盘录入，知道输入的数据是886，发送数据结束
- UDP接收数据：因为接收端不知道发送端什么时候停止发送，故采用死循环接收

```java
//发送端
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

public class SendDemo {
    public static void main(String[] args) throws IOException {
        DatagramSocket ds = new DatagramSocket();
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String line;
        while((line = br.readLine())!=null) {
            if ("886".equals(line))
                break;
            byte[] bys = line.getBytes();
            DatagramPacket dp = new DatagramPacket(bys,bys.length, InetAddress.getByName("192.168.1.106"),22233);
            ds.send(dp);
        }
        ds.close();
        br.close();
    }
}
//接收端
import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;

public class ReceiveDemo {
    public static void main(String[] args) throws IOException {
        DatagramSocket ds = new DatagramSocket(22233);
        while(true){
            byte[] bys = new byte[1024];
            DatagramPacket dp = new DatagramPacket(bys,bys.length);
            ds.receive(dp);
            System.out.println("数据是："+new String(dp.getData(),0,dp.getLength()));
        }
    }
}
```

### TCP通信原理

TCP通信协议是一种可靠的网络协议，它在通信的两端各建立一个Socket对象，从而在通信的两端形成网络虚拟链路。

一旦建成了虚拟的网络链路，两端的程序就可以通过虚拟链路进行通信。

Java对基于TCP协议的网络提供了良好的封装，使用Socket对象来代表两端的通行端口，并通过Socket产生IO流来进行网络通信。

Java为客户端提供了Socket类，为服务器端提供了ServerSocket类。

### TCP发送和接收数据

发送数据的步骤：

1. 创建客户端的Socket对象(Socket)

   Socket(String host,int port);

2. 获取输出流，写数据

   OutputStream getOutputStream();

3. 释放资源

   void close();

```java
import java.io.IOException;
import java.io.OutputStream;
import java.net.Socket;

public class ClientDemo {
    public static void main(String[] args) throws IOException {
        Socket s = new Socket("192.168.1.106",10086);
        OutputStream os = s.getOutputStream();
        os.write("Hello TCP,I'm coming".getBytes());
        s.close();
        os.close();
    }
}
```

接收数据的步骤：

1. 创建服务器端的Socket对象(ServerSocket)

   ServerSocket(int port);

2. 监听客户端连接，返回一个Socket对象

   Socket accept();

3. 获取输入流，读数据，并把数据显示在控制台

   InputStream getInputStream();

4. 释放资源

   void close();

```java
import java.io.IOException;
import java.io.InputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class ServerDemo {
    public static void main(String[] args) throws IOException {
        ServerSocket ss = new ServerSocket(10086);
        Socket s = ss.accept();
        InputStream is = s.getInputStream();
        byte[] bys= new byte[1024];
        int len = is.read(bys);
        String data = new String(bys,0,len);
        System.out.println("数据是："+data);
        s.close();
        ss.close();
        is.close();
    }
}
```

### TCP通信程序练习

练习1：

- 客户端：发送数据，接收服务器反馈
- 服务器：接收数据，给出反馈

```java
//客户端
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;

public class ClientDemo1 {
    public static void main(String[] args) throws IOException {
        Socket s = new Socket("192.168.1.106",10086);
        //获取输出流，写数据
        OutputStream os = s.getOutputStream();
        os.write("hello,tcp,我来了".getBytes());
        //接收服务器反馈
        InputStream is = s.getInputStream();
        byte[] bys = new byte[1024];
        int len = is.read(bys);
        String data = new String(bys,0,len);
        System.out.println("客户端："+data);
        s.close();
    }
}
//服务器端
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class ServerDemo1 {
    public static void main(String[] args) throws IOException {
        //创建服务器端的Socket对象
        ServerSocket ss= new ServerSocket(10086);
        //监听客户端连接，返回一个Socket对象
        Socket s = ss.accept();
        //获取输出流，读数据，并把数据显示在控制台
        InputStream is = s.getInputStream();
        byte[] bys = new byte[1024];
        int len = is.read(bys);
        String data = new String(bys,0,len);
        System.out.println("服务器："+data);
        //给出反馈
        OutputStream os = s.getOutputStream();
        os.write("数据已收到".getBytes());
        ss.close();
    }
}
```

练习2：

- 客户端：数据来自于键盘录入，知道输入的数据是886，发送数据结束
- 服务器：接收到的数据在控制台输出

```java
//客户端
import java.io.*;
import java.net.Socket;

public class ClientDemo2 {
    public static void main(String[] args) throws IOException {
        //创建客户端Socket对象
        Socket s = new Socket("192.168.1.106",10086);
        //数据来自于键盘录入，直到输入的数据是886，发送数据结束
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        //封装输出流对象
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
        String line;
        while((line = br.readLine())!=null){
            if ("886".equals(line))
                break;
            //获取输出流对象
            bw.write(line);
            bw.newLine();
            bw.flush();
        }
        s.close();
    }
}
//服务器端
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.ServerSocket;
import java.net.Socket;

public class ServerDemo2 {
    public static void main(String[] args) throws IOException {
        //创建服务器Socket对象
        ServerSocket ss = new ServerSocket(10086);
        //监听客户端的链接，返回一个对应的Socket对象
        Socket s = ss.accept();
        //获取输入流
        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
        String line;
        while((line = br.readLine())!=null){
            System.out.println(line);
        }
        ss.close();
    }
}
```

练习3：

- 客户端：数据来自键盘录入，直到输入的数据是886，发送数据结束
- 服务器：接收到的数据写入文件

```java
//客户端代码与练习2相同
//服务器端
import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

public class ServerDemo3 {
    public static void main(String[] args) throws IOException {
        //创建服务器Socket对象
        ServerSocket ss = new ServerSocket(10086);
        //监听客户端连接，返回一个对应的Socket对象
        Socket s = ss.accept();
        //接收数据
        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
        //把数据写入文件
        BufferedWriter bw = new BufferedWriter(new FileWriter("src/NewTest6/s.txt"));
        String line;
        while((line = br.readLine())!=null){
            bw.write(line);
            bw.newLine();
            bw.flush();
        }
        //释放资源
        bw.close();
        ss.close();
    }
}
```

练习4：

- 客户端：数据来自于文本文件
- 服务器：接收到的数据写入文本文件

```java
//服务器端代码与练习3相同
//客户端
import java.io.*;
import java.net.Socket;

public class ClientDemo4 {
    public static void main(String[] args) throws IOException {
        //创建客户端Socket对象
        Socket s = new Socket("192.168.1.106",10086);
        //封装文本文件的数据
        BufferedReader br = new BufferedReader(new FileReader("test.txt"));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
        String line;
        while((line = br.readLine())!=null){
            bw.write(line);
            bw.newLine();
            bw.flush();
        }
        br.close();
        s.close();
    }
}
```

练习5：

- 客户端：数据来自于文本文件，接收服务器反馈
- 服务器：接收到的数据写入文本文件，给出反馈

出现的问题：程序一直等待

原因：读数据的方法是阻塞式的。

解决方法：使用shutdownOutput()方法给出一个结束标记

```java
//客户端
import java.io.*;
import java.net.Socket;

public class ClientDemo5 {
    public static void main(String[] args) throws IOException {
        Socket s = new Socket("192.168.1.106",10086);
        BufferedReader br = new BufferedReader(new FileReader("test.txt"));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
        String line;
        while((line = br.readLine())!=null){
            bw.write(line);
            bw.newLine();
            bw.flush();
        }
        //文件上传结束标记
        s.shutdownOutput();
        //接收反馈
        BufferedReader brClient = new BufferedReader(new InputStreamReader(s.getInputStream()));
        String data = brClient.readLine();
        System.out.println("服务器反馈："+data);
        br.close();
        s.close();
    }
}
//服务器端
import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

public class ServerDemo5 {
    public static void main(String[] args) throws IOException {
        ServerSocket ss = new ServerSocket(10086);
        Socket s = ss.accept();
        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
        BufferedWriter bw = new BufferedWriter(new FileWriter("src/NewTest6/test2.txt"));
        String line;
        while((line = br.readLine())!=null){
            bw.write(line);
            bw.newLine();
            bw.flush();
        }
        //给出反馈
        BufferedWriter bwServer = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
        bwServer.write("文件上传成功！");
        bwServer.newLine();
        bwServer.flush();
        bw.close();
        ss.close();
    }
}
```

练习6：

客户端：数据来自文本文件：接收服务器反馈

服务器端：接收到的数据写入文本文件，给出反馈，代码用线程封装，为每个客户端开启一个线程

```java
//客户端代码与练习5相同
//服务器端
public class ServerDemo6 {
    public static void main(String[] args) throws IOException {
        ServerSocket ss = new ServerSocket(10086);
        while(true){
            Socket s = ss.accept();
            //为每个客户端开启一个线程
            new Thread(new ServerThread(s)).start();
        }
    }
}
//多线程代码
import java.io.*;
import java.net.Socket;

public class ServerThread implements Runnable {
    private Socket s;
    public ServerThread(Socket s) {
        this.s = s;
    }
    @Override
    public void run() {
        try {
            BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
            //解决文件名冲突问题
            int count = 0;
            File file = new File("src/NewTest6/Serverfile/test["+count+"].txt");
            while(file.exists()){
                count++;
                file = new File("src/NewTest6/Serverfile/test["+count+"].txt");
            }
            BufferedWriter bw = new BufferedWriter(new FileWriter(file));
            String line;
            while((line = br.readLine())!= null){
                bw.write(line);
                bw.newLine();
                bw.flush();
            }
            BufferedWriter bwServer = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
            bwServer.write("文件上传成功！");
            bwServer.newLine();
            bwServer.flush();
            //bwServer.close();
            s.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## Lambda表达式

Lambda表达式是函数式编程思想的体现。

### Lambda表达式的标准格式

```java
public class LambdaDemo1 {
    public static void main(String[] args) {
        //通过匿名内部类的方式实现多线程
        new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("多线程程序启动了");
            }
        }).start();
        //通过lambda表达式实现多线程
        new Thread(()->{
            System.out.println("多线程程序启动了"));
        }).start();
    }
}
```

Lambda表达式的格式：

格式：(形式参数)->{代码块}

形式参数：如有多个参数，参数之间用逗号隔开，如果没有参数，留空即可。

->：由英文中划线和大于号组成，固定写法，代表指向动作。

代码块：是具体要做的事，也就是以前的方法体内容。

### Lambda表达式的使用

Lambda表达式的使用前提：

- 有一个接口
- 接口中有且只有一个抽象方法

练习1：

- 定义一个接口(Eatable)，里面定义一个抽象方法：void eat();

- 定义一个测试类(EatableDemo)，在测试类中提供两个方法

  一个方法是：useEatable(Eatable e)

  一个方法是主方法，在主方法中调用useEatable方法

```java
//Eatable接口
public interface Eatable {
    void eat();
}
//测试类
public class EatableDemo {
    public static void main(String[] args) {
        useEatable(() ->{
            System.out.println("一天一个苹果，医生远离我！");
        });
    }
    private static void useEatable(Eatable e){
        e.eat();
    }
}
```

练习2：

- 定义一个接口(Flyable)，里面定义一个抽象方法，void fly(String s);

- 定义一个测试类(FlyableDemo)，在测试类中提供两个方法

  一个方法是useFlyable(Flyable f)

  一个方法是主方法，在主方法中调用useFlyable方法

```java
//Flyable接口
public interface Flyable {
    void fly(String s);
}
//测试类
public class FlyableDemo {
    public static void main(String[] args) {
        useFlyable((String s) ->{
            System.out.println(s);
            System.out.println("老鹰在飞翔");
        });
    }
    private static void useFlyable(Flyable f){
        f.fly("小鸟在飞翔");
    }
}
```

练习3：

- 定义一个接口(Addable)，里面定义一个抽象方法：int add(int x,int y);

- 定义一个测试类(AddableDemo)，在测试类中提供两个方法。

  一个方法是：useAddable(Addable a)

  一个方法是主方法，在主方法中调用useAddable方法

```java
//Addable接口
public interface Addable {
    int add(int x,int y);
}
//测试类
public class AddableDemo {
    public static void main(String[] args){
        useAddable((int x,int y) ->{
            return x+y;
        });
    }
    private static void useAddable(Addable a){
        int sum = a.add(10,20);
        System.out.println(sum);
    }
}
```

### Lambda表达式的省略形式

- ()中的参数类型可以省略
- 如果参数有且仅有一个，那么小括号可以省略
- 如果代码块的语句只有一条，可以省略大括号和分号，如果有return，retuen也要省略掉

```java
//实例1
public static void main(String[] args){
    useAddable((x,y) -> x + y);
}
//实例2
public static void main(String[] args) {
    useFlyable(s -> System.out.println("老鹰在飞翔"));
}
```

### Lambda注意事项

- 使用Lambda必须要有接口，并且有且仅有一个抽象方法

- 必须有上下文环境，才能推导出Lambda对应的接口

  根据局部变量得知Lambda对应的接口：Runnable r = () -> System.out.println("Lambda表达式");

  根据调用方法的参数得知Lambda对应的接口：new Thread(()-> System.out.println("Lambda表达式")).start();

### Lambda表达式和匿名内部类的区别

所需类型不同

- 匿名内部类：可以是接口，也可以是抽象类，还可以是具体类
- Lambda表达式：只能是接口

使用限制不同

- 如果接口中有且仅有一个抽象方法，可以使用Lambda表达式，也可以使用匿名内部类
- 如果接口中多于一个抽象方法，只能使用匿名内部类，，而不能使用Lambda表达式

实现原理不同

- 匿名内部类编译之后，产生一个单独的.class字节码文件
- Lambda表达式编译之后，没有一个单独的.class字节码文件。对应的字节码会在运行的时候动态生成

## 接口组成更新

接口的组成

- 常量	修饰符：public static final
- 抽象方法	修饰符：public abstract
- 默认方法(Java8)
- 静态方法(Java8)
- 私有方法(Java9)

### 接口中的默认方法

接口中的默认方法主要用于开发完成后，添加新功能时，不需要让所有实现类都重写新方法。

接口中默认方法的定义格式：

public default 返回值类型 方法名(参数列表){}

eg. 	public default void show3(){ }

接口中默认方法的主意事项：

- 默认方法不是抽象方法，所以不强制被重写，但是可以被重写，重写的时候去掉default关键字
- public 可以省略，default 不能省略

### 接口中的静态方法

接口中静态方法的定义格式：

public static 返回值类型 方法名(参数列表){ }

eg.	public static void show3(){ }

接口中静态方法的注意事项：

- 静态方法只能通过接口名调用，不能通过实现类名调用或者对象名调用
- public 可以省略，static 不能省略

### 接口中的私有方法

Java9中新增了带方法的私有方法，这其实在Java8中就埋下了伏笔，Java8允许在接口中定义带方法的默认方法和静态方法。这可能会引发一个问题：当两个默认方法或者静态方法中包含一段相同的代码实现时，程序必然考虑将这段代码抽取成一个共性方法，而这个共性方法是不需要让别人使用的，因此用私有方法给隐藏起来，这是Java9增加私有方法的必然性。

接口中私有方法的定义格式：

格式1：private 返回值类型 方法名(参数列表){ }

范例1：private void show(){ }

格式2：private static 返回值类型 方法名(参数类型){ }

范例2：private static void method(){ }

接口中私有方法的注意事项：

- 默认方法可以调用静态方法和非静态方法
- 静态方法之能调用私有的静态方法

