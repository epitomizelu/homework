[TOC]
# 基本概念 
##  数据类型
###  基础知识
> javascript共六种类型，如下表所示

|数据类型|字面量|typeOf运算结果(字符串)|
|------------------|------------------|---------------------|
|  null               |    null             |    “object”          |
|  undefined     |    undefined   |    “ undefined ”   |
|  number        |        1             |    “number”       |
|  string            |        "hello"     |    "string"          |
|  boolean        |        true         |    "bolean"        |
|  object           |       {a:"a"}      |     "object"         |


  


> 公共方法 toString(),valueOf()。除了null和undefined这两个值之外，这两个方法都可以通过各种类型的字面量或者变量来调用。
![]( http://ov4zbm8w2.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20170823194030.png)




> 用数字字面量调用toString()，valueOf()方法时要两个点符号，因为第一个点会被当作小数点
![](http://ov4zbm8w2.bkt.clouddn.com/image/js%E6%95%B0%E5%AD%97%E5%AD%97%E9%9D%A2%E9%87%8F%E8%B0%83%E7%94%A8%E6%96%B9%E6%B3%95.png )


###   null和undefined  
 > 允许的操作（typeOf 和 数据类型转换）
![]( http://ov4zbm8w2.bkt.clouddn.com/%E6%93%8D%E4%BD%9Cnull.png)




###  数据类型转换
> 一，转string类型，除了null和undefined，其他类型都有toString()方法，直接调用toString()方法可转换为字符串；对于null和undefined，可以使用String()来转换
![]( http://ov4zbm8w2.bkt.clouddn.com/%E8%BD%AC%E5%8C%96%E4%B8%BA%E5%AD%97%E7%AC%A6%E4%B8%B2.png)




> 二 转number类型
1.使用  “+”  号隐式转换；

![](http://ov4zbm8w2.bkt.clouddn.com/%E6%95%B0%E5%AD%97%E9%9A%90%E5%BC%8F%E8%BD%AC%E6%8D%A2.png)

2.使用Number(),parseInt(),parseFloat()等方法强制转换
![]( http://ov4zbm8w2.bkt.clouddn.com/parseInt.png)

3. Number(),parseInt(),parseFloat()三个方法的区别

3.1 处理null有区别

![]( http://ov4zbm8w2.bkt.clouddn.com/parseInt%E5%92%8Cfloat%E5%8C%BA%E5%88%AB.png)

3.2 处理空字符有区别

![]( http://ov4zbm8w2.bkt.clouddn.com/parseInt%E5%A4%84%E7%90%86%E7%A9%BA%E5%AD%97%E7%AC%A6%E4%B8%B2.png)

3.3 parseInt可以指定按何种进制进行转换

![]( http://ov4zbm8w2.bkt.clouddn.com/parseInt%E6%8C%87%E5%AE%9A%E8%BF%9B%E5%88%B6.png)




###  Object类型转换为number类型

>  ** 将对象转换为number类型的逻辑稍微复杂**，在转换的过程中会调用到对象的valueOf和toString方法。

![]( http://ov4zbm8w2.bkt.clouddn.com/parseInt%E5%92%8CNumber%E8%BD%AC%E6%8D%A2obj%E7%9A%84%E5%B7%AE%E5%BC%82.png)


** 从上图可以得出重要结论一：1.  parseInt将对象转换为number时，直接调用toString方法，基于该方法的返回值进行转换；2. Number将对象转换为数值类型时，先调用valueOf方法，然后根据该方法返回值判断是否需要调用toString方法（见下图) **


![]( http://ov4zbm8w2.bkt.clouddn.com/parseInt%E5%92%8CNumber%E8%BD%AC%E6%8D%A2obj%E7%9A%84%E5%B7%AE%E5%BC%822.png)


**从上图可以得出重要结论二：1. Number将对象转换为数值类型时，先调用valueOf方法，如果该方法的返回值是null，undefined，boolean，string，number，则基于该返回值进行数值转换；
2. 如果该方法返回的是对象，则需要调用toString方法，根据toString方法的返回值进行数值转换**





## 操作符

#### 类型
>一，一元运算符；
>二，算术运算符；
>三，移位运算符；
>四，关系运算符
>五，按位与、或、非、亦或
>六，逻辑与、或、非
>七，赋值运算符


#### 优先级
>优先级总体规律如下：
>一元运算符> 算术运算符> 移位运算符 >关系运算符 >按位运算符 >逻辑运算符 >赋值运算符（速记：袁（元）术移位，关系为（位）继（辑）父（赋））
>>特殊：1，逻辑运算符中的 逻辑非（！）和按位运算符中的按位取反（~）为一元运算符，优先级高；
>>2，delete,new,typeof,void 和一元运算符具有相同的优先级，其使用方法也类似于一元运算符；
>>3，instanceof 的用法和关系运算符类似，用来比较两个对象的关系，其结果也是boolean类型，可以当作一个关系运算符，其优先级和关系运算符相同；

|运算符|    描述|
|--------|--------|
|. [] ()  |  字段访问、数组下标、函数调用以及表达式分组|
|++ -- - ~ ! delete new typeof void  |  一元运算符、返回数据类型、对象创建、未定义值|
| \* / %   | 乘法、除法、取模|
|   \+ \- +    |加法、减法、字符串连接|
|<< >> >>>  |  移位|
|< <= > >= instanceof |   小于、小于等于、大于、大于等于、instanceof|
|== != === !== |   等于、不等于、严格相等、非严格相等|
|&   | 按位与|
|^    |按位异或|
| \|  |  按位或|
|&&  |  逻辑与|
|\|\|  |  逻辑或|
|?: |   条件|
|= oP= |   赋值、运算赋值|
|,|    多重求值|





#### 总结

>**1,算术运算符 +(加)、-（减）、*（乘）、/（除）、%(取模)**
>>**1.1,除了加号操作符比较特殊之外，其他几个运算符两侧的操作数无论是何种类型，都会转换为Number类型进行运算；**
>>**1.2,而对于加号（+）运算符，两侧的操作数只要有一个是字符串，将另一个操作数转换为字符串然后继续字符串拼接；**
>>**1.3,如果 + 操作符的两个操作数都不是string类型，其中有一个是boolean类型，会将布尔类型转换为数字； **
>>**1.4,如果 + 操作符的两个操作数都不是string类型，其中有一个是Object类型，首先调用valueOf方法，根据返回值的类型按之前的规则进行运算；如果没有valueOf（）方法，会调用toString（）方法 **



>**2, 逻辑与(&&)， 逻辑或(||)**
>>**2.1,对于逻辑与(&&)，只要左侧操作数为真，则表达式的结果一定返回右侧操作数，否则返回左侧操作数**
>>**2.2,对于逻辑与(||)，只要左侧操作数为真，则表达式的结果一定返回左侧操作数，否则返回右侧操作数**

>>记住这两点，以不变应万变


>**3,关系运算符：>,<,<=,>,不包括 ==，===**
>>**3.1,关系运算符两侧操作数都是字符串，则按照字符编码比较；**
>>**3.2,除此之外，会将关系运算符都转换为数字进行大小比较**




>**4,相等运算符==**
>>**4.1,相等运算符两侧操作数都是字符串，则按照字符编码比较；**
>>**4.2,相等运算符两侧操作数都是对象，则比较是否是同一个对象；**

>>**4.3,除此之外，会将相等运算符都转换为数字进行大小比较**



>**5,关于null和undefined**
>>**5.1,相等运算符不会对这两个值进行转换；**
>>**5.2,+ 会将这两个值调用 String()方法转为字符串；**

>>**5.3,undefined派生自null，所以undefined==null为真；**




##  声明提升
#### **you must konw：**
下载一个网页后，浏览器会解析、执行html文件的内部脚本或者外部脚本，解析的过程中会将全局函数、全局变量的声明提升，提升可简单理解为函数、变量声明前置。
>>(下面图中第一个框是原始题目，第二个是根据我的理解写出来的等价代码)
![]( http://ov4zbm8w2.bkt.clouddn.com/%E5%A3%B0%E6%98%8E%E5%89%8D%E7%BD%AE1.png)
![]( http://ov4zbm8w2.bkt.clouddn.com/%E5%A3%B0%E6%98%8E%E5%89%8D%E7%BD%AE2.png)

>>另外一个例子

![]( http://ov4zbm8w2.bkt.clouddn.com/%E5%87%BD%E6%95%B0%E5%A3%B0%E6%98%8E%E6%8F%90%E5%8D%873.png)




##  正则表达式

####  元字符
|符号|备注|
|----|----|
|^|行首|
|$|行尾|
|.|除空白字符（6个，见下方表格）之外的所有字符|
|\d|数字字符|
|\D|非数字字符|
|\s|空白字符|
|\S|非空白字符|
|\w|单词字符（_，数字，大小写字母）|
|\W|非单词字符|
|（）|捕获组|
|[]|取值区间|
|{}|指定匹配长度|
|？|用在*，+，{n,}等长度不定符号后面表示非贪婪模式|
|?|0个或1个|
|\||或|


#### DEMO
>DEMO1
```javascript
   var reg=/|/g;
   reg.test('any string')
/*
*这个正则表达式只有一个‘|’符号，而‘|’符号两边什么都没有，表示空，故只能匹配到空
*/
```
![](http://ov4zbm8w2.bkt.clouddn.com/%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8Fdemo.png)


>DEMO2

```javascript
//将以 0 开头的所有的四位数字取出
var reg=/0\d{3}/g, str='a000456500add40043300',res =[];
while(matches=reg.exec(str)){

  res.push(matches[0]);

   reg.lastIndex = reg.lastIndex - 3;
}

//res  : 0004,0045,0456,0043,0433
```



>DEMO3
```JAVASCRIPT
//将 20000123  转换为  20,000,123
var reg=/\d(?=(\d{3})+$)/g  
'20000123'.replace(reg,'$&,')


//注意上面的正则表达式 /\d(?=(\d{3})+$)/g 与下面的正则表达式的区别（行尾符号$移到紧挨其右的小括号的右边）
var reg =  /\d(?=(\d{3})+)$/g
'2000'.match(reg) //匹配不到任何内容


//1, ?=是预判标志，其并会在匹配结果中反映，只是作为匹配的条件，这里理解为匹配一个数字，当这个数字后面的数字的个数必须是3的整数倍
//2,上面两个正则表达式将行尾符 $ 放在不同的位置导致结果不同，原因是第二个表达式是一，要匹配到一个数字这个数字的后面紧挨行尾，二，同时其后又要有3的整数倍个数的数字，这两个条件互斥，不可能满足。
```































