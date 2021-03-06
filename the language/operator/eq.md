# 等式运算符

 等式运算符比较两个操作数是否相等，并返回boolean类型的值(true 或false)。

## 一、等式运算符

等式运算符判断两个操作数是否相等。

|  运算符 |  说明 |
| --- | --- |
|  == |  等式运算符 |
| != |  不等式运算符 |
|  = |  在表达式中可以替代== |

### 1.1、操作数数据类型相同


 对于数值(type.number)、字符串(type.string)、指针(type.pointer)，布尔值(type.boolean)等传值类型比较值是否相对。


|  示例 |  结果 |
| --- | --- |
|  "abc" == "abc" | true |
| 123 != 456 | true |


 对于table、cdata等传引用类型，当引用同一个对象时相等、或者调用_eq元方法判断是否相等


|  示例 |  结果 |  说明 |
| --- | --- | --- |
| ::User32 != ::Kernel32 | true |  引用了不同的对象 |
| {} == {} | false |  引用了不同的对象 |
| time.now() == time.now() | true |  调用time.now()._eq元方法比较 |



### 1.2、非布尔值与布尔值比较

0,null与false相等，而所有非零、非false、非null值与true相等。

|  表达式 |  结果 |
| --- | --- |
| 0==false | true |
| null==false | true |
| 1==false | false |
| if( 1 ) io.print("true") |  条件符合，执行代码 io.print("true") |



### 1.2、非数字值与字符串值

如果字符串可以转换为等值的数字，则返回true,否则返回false

|  表达式 |  结果 |
| --- | --- |
|  "123"==123 | true |
|  "abc"==123 | false |



### 1.2、其他不同类型的操作数

如果数据类型不同、会尝试进行类型转换、或调用_eq元方法进行比较。如果类型转换失败、该对象也无_eq元方法、则返回false。

## 二、全等式运算符

全等式又称为恒等式，要求数据类型绝对相等、并且不会调用_eq元方法.
因此，不能重载恒等操作符,恒等操作符的运行速度也快于普通的等式操作符。 

|  运算符 |  说明 |
| --- | --- |
|  === |  恒等运算符 |
| !== |  非恒等运算符 |

如果是数字，字符串，指针，布尔值，在值与类型都相等时恒等式返回真，返则返回假．
如果是其他传址对象，指向同一个对象返回真，否则返回假．

|  示例 |  结果 |
| --- | --- |
|  "abc" === "abc" | true |
| null === false | false |
