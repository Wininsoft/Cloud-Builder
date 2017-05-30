# BPL语言

### 概览

BPL语言是Business Process Language（业务处理语言）的缩写， 专门用于在Cloud Builder中用于业务处理操作。

## BPL语言特点

- 参照C#语法进行实现， 90%以上的类似都，快速上手， 让从C，C++,C#,Java等语言背景过来的用户无缝对接，把学习成本降低到最低。
- 内置核心类库， [文档参考](http://www.cloudbuilder.cc/Document)
- 支持断点调试， [视频教程](http://www.cloudbuilder.cc/Video/Detail?id=32)

## 表达式

### 值表达式
- 1
表示数值1
- 1.5
-- 表示数值1.5， 带有小数位
- "字符串"
-- 双引号字符串
- '字符串'
-- 单引号字符串
- true
-- 布尔类型true
- false
-- 布尔类型false

### 单元运算符
exp表示表达式

- exp++
-- 表达式返回的值还是exp，返回后对exp+1
- exp--
-- 表达式返回的值还是exp，返回后对exp-1
- --exp
-- 先对exp-1，然后返回
- ++exp
-- 现对exp+1，然后返回
- !exp
-- 如果exp是 true，则返回false，如果exp是false，则返回true
- (exp)

### 双元运算符
A和B分别表示双元运算符左边和右边的表达式

- A+B
-- A和B的值进行相加返回 
- A-B
-- A的值减去B的值返回
- A*B
-- A的值乘以B的值返回
- A/B
-- A的值除以B的值返回 
- A%B
-- A的值除以B的值返回 余数
- A??B
-- A如果为空，则返回B，否则返回A
- A>B
-- 如果A大于B，则返回true，否则返回false
- A>=B
-- 如果A大于等于B，则返回true，否则返回false
- A==B
-- 如果A等于B，则返回true，否则返回false
- A!=B
-- 如果A不等于B，则返回 true，否则返回false
- A<B
-- 如果A小于B，则 返回true，否则返回false
- A<=B
-- 如果A小于等于B，则返回true，否则返回false
- A^B
-- A和B进行异或运算后的值返回
- A|B
- A&B
- A&&B
-- 如果A和B都是true，则返回 true，否则返回false
- A||B
-- 如果A或B的值有一方是true，则返回true，否则返回false
- A+=B
-- A和B的值相加后赋值给A，然后返回相加结果
- A-=B
-- A和B的值相减后赋值给A，然后返回相减结果
- A*=B
-- A和B的值相乘后赋值给A，然后返回相乘结果
- A/=B
-- A和B的值相除后赋值给A，然后返回相除结果
- A%=B
-- A和B的值相除后的余数赋值给A，然后返回结果
- A^=B

### 三元运算符

- A?B:C
- A between B..C

### 标识符表达式
- this
-- 访问当前表达式执行的当前上下文对象
- base
-- 用于访问当前表达式执行的当前上下文对象的成员
- A
-- 访问当前上下文对象的成员A的值


### 成员访问表达式

- A.B
-- 访问A对象的成员B的值，如果A==null，则抛出异常

- A?.B
-- 访问A对象的成员B的值，如果A==null，则返回null

### 方法调用表达式 
- A()
-- 调用方法A，不传递任何参数

- A(p1,p2)
-- 调用方法A，传递参数p1，p2

- A.B()
-- 调用A对象下的方法B，不传递 任何参数

- A.B(p1,p2)
-- 调用A对象下的B方法，传递参数p1，p2

## 语句

### if语句

语法：
if(exp1)
	语句1
else if(exp2)
	语句2
else
	语句3

其中 
- exp1，exp2要求是有效的布尔类型
- else if子语句为可选语句， 也可以多个else if子语句
- else语句是可选子语句

如果exp1成立，则执行语句1，否则如果exp2成立，则执行语句2， 否则则执行语句3。

- 示例1
var a=0;
if(a==0)
	a++;
执行完毕后，a的值等于1

- 示例2
var a=0;
if(a>0)
	a++;
执行完毕后，a的值等于0

- 示例3
var a=-1;
if(a>0)
	a++;
else if(a<0)
	a--;

执行完毕后，a的值等于-2

- 示例4
var a=-1;
if(a>0)
	a++;
else
	a=10;

执行完毕后，a的值等于10

### foreach语句

语法：
foreach(var item in source)
	循环项语句

其中source表示要进行循环的数据源，必须实现System.Collections.IEnumerable接口，item表示正在循环的数据项，循环项语句中可以访问到。

示例：
var result="";
foreach(var item in new[]{"a","b"}){
	result+=item;
}

循环结束后，result的结果应该是ab
