---
title: JavaScript基础
date: 2023-02-14 12:54:59
categories:
- 笔记
tags:
- [JS基础]
---

## P4:基本语法

- 1.JS中严格区分大小写
- 2.JS中每一条语句以分号（;）结尾 --约定俗成
- 3.JS中会忽略多个空格和换行，所以我们可以利用空格和换行对代码进行格式化

## P5:字面量和变量
```
/*
	字面量，都是一些不可改变的值
         比如： 1 2 3 4 5
         字面量都是可以直接使用的，但是我们一般都不会直接使用字面量

  变量， 变量可以用来保存字面量，而且变量的值是可以任意改变的
        变量更加方便我们使用，所以在开发中都是通过变量去保存一个字面量，而很少直接使用字面量

        可以通过 标识符(变量名)对字面量进行描述
      	如： let age = 30;
*/
```
**在js中声明一个变量，使用var，let，const关键字来声明**

## P6:标识符

- 在JS中所有的可以由我们自主命名的都可以称为是标识符
- 例如：变量名、函数名、属性名都属于标识符
- 命名一个标识时需要遵守如下规则
  	1.标识符中可以含有字母、数字、_、$
  	2.标识符不能以数字开头
  	3.标识符不能是ES中的关键字和保留字
  	4.标识符一般都采用驼峰命名法
      	- 首字母小写，每个单词的开头字母大写，其余字母小写
        	liXueFeng  xxxYyyZzz
            
- JS底层保存标识符时，实际上是采用Unicode编码，所以理论上讲，
  所有的utf-8中含有的内容都可以作为标识符，例如：使用中文
  let 锄禾日当午 = 123;    // 不要这样使用

	

## P7:数据类型

**js中一共有8中数据类型：**

- 其中有7种`基本数据`类型：
- ES5的5种: String、Nnumer、Boolean、Null、Undefined
- ES6新增： Symbol 表示独一无二的值
- ES10新增：BigInt 表示任意大的整数

- 一种引用数据类型：
- Object (本质上是有一组无序的键值对组成)
- 包含 `function`,`Array`,`Date`等。JavaScript不支持创建任何自定义类型的数据，
也就是说JavaScript中所有的值的类型都是上面的8种之一。


`String`字符串
--
- 在JS中字符串需要使用引号引起来
- 使用双引号或者单引号都可以，但是不要混合使用
- 引号不能嵌套，`""""` 或者 `''''`
- 在字符串中我们可以使用 `\` 作为转义字符
- 当表示一些特殊符号时可以使用 \ 进行转义
- \" 表示 "
- \' 表示 '
- \n 表示换行
- \t 制表符 tab
- \\ 表示 \


--------------------------------------------------------

`Number`类型 在JS中所有的数值都是Number类型，包括整数和浮点数（小数）


js中可以表示的数字的最大值

- Number.MAX_VALUE 
- 1.7976931348623157e+308
  
如果使用Number表示的数字超过了最大值，则会返回一个
- Infinity  表示正无穷
- -Infinity  表示负无穷
- 使用typeof检查 Infinity 也会返回 number
- Infinity 是一个字面量。js中规定
     
`NaN` 是一个特殊的数字，表示 Not a Number
  	使用 typeof 检查 一个 NaN也会返回 number
    c = 'abc'*'bcd' // NaN 

```
var a = 123;  // number
var b = '123'; // string 
```

可以使用一个运算符 typeof ，来检查一个变量的类型
语法：typeof 变量

```
console.log(typeof a); // number
console.log(typeof b); // string
console.log(typeof c); // number
```

如果使用JS进行浮点运算，可能得到一个不精确的结果，所以千万不要使用JS进行对精度要就比较高的运算

let d = 0.1+0.2;
console.log(d); //0.30000000000000004

--------------------------------------------------------


`Boolean` 布尔值
```
/**
 *  Boolean 布尔值
 *  布尔值只有两个，主要用来做逻辑判断
 *  true
 *      - 表示真
 *  false 
 *      - 表示假
 */

let boola = 'true';
let boolb = false;

console.log(boola); // true
console.log(typeof boola); // string


console.log(boolb); // false
console.log(typeof boolb); // boolean
```

--------------------------------------------------------
```
/**
 * Null（空值） 类型的值只有一个，就是null
 *  null这个值是专门用来表示一个为空的对象
 *  使用typeof 检查一个null值时，会返回 object
 * 
 * 
 * Undefined （定义未赋值） 类型的值只有一个，就是undefined
 *  当声明一个变量，但是并不给变量赋值时，它的值就是undefined
 * 
 * 和直接使用一个变量，x is not defined 区分
 */

let a = null;
console.log(typeof a); // object

let b;
console.log(b); // undefined
console.log(typeof b); // undefined

console.log(c); // c is not defined

null 与 undefined的异同
```

- 相同点：
	Undefined 和 Null 都是基本数据类型，这两个基本数据类型分别都只有一个值，就是 undefined 和 null
- 不同点：
	undefined 代表的含义是未定义， null 代表的含义是空对象。
	typeof null 返回'object'，typeof undefined 返回'undefined'

- null == undefined  // true
- null === undefined // false

- 其实 null 不是对象，虽然 typeof null 会输出 object，但是这只是 JS 存在的一个悠久 Bug。
- 在 JS 的最初版本中使用的是 32 位系统，为了性能考虑使用低位存储变量的类型信息，
- 000 开头代表是对象，然而 null 表示为全零，所以将它错误的判断为 object 。
- 虽然现在的内部类型判断代码已经改变了，但是对于这个 Bug 却是一直流传下来。

## P11 强制类型转换
```
/**
 * 强制类型转换
 *  - 指将一个数据类型，强制转换为其他的数据类型，
 *  - 类型转换主要指，将其他的数据类型，转换为，
 *      String Number Boolean
 * 
 */
```
将其他的数据类型转换为 String
===
```
/**
 * 
 *      方式一： 
 *          - 调用被转换数据类型的toString()方法
 *          - 改方法不会影响到原变量，它会将转换的结果返回，需要用一个变量来接受
 *          - 但是注意： null和undefined这两个值没有toString()方法
 *                      如果用它们调用toString()方法 会报错
 *      方式二：
 *          - 调用String()函数。并将被转换的数据作为参数传递给函数
 *          - 使用String()函数做强制类型转换时，
 *              对于Numer和Boolean实际上就是调用的toString()方法
 *              但是对于null和undefined,就不会调用toString()方法
 *                  它会将 null 直接转换为 "null"
 *                  它会将 undefined 直接转换为 "undefined"
 * 
 */
```
```
let a = 123;


console.log(typeof a); //number
console.log(a); // 123

a = a.toString();

console.log(typeof a); //string
console.log(a); // "123"

a = true;

console.log(typeof a); //boolean
console.log(a); // true


a = a.toString();

console.log(typeof a); //string
console.log(a); // "true"

a = null;
console.log(typeof a); //object
console.log(a); // null


// a = a.toString();  // 报错 Cannot read properties of null (reading 'toString')  无法读取null的属性 


a = undefined;

console.log(typeof a); // undefined
console.log(a); //undefined

// a = a.toString();  // 报错 Cannot read properties of null (reading 'toString')  无法读取null的属性 

```


将其他的数据类型转换为 Number
===
```
/**
 * 转换方式一：
 *      使用Number()函数
 *          - 字符串 --> 数字
 *                  1.如果是纯数字的字符串，则直接将其转换为数字
 *                  2.如果字符串有非数字的内容，则转换为 NaN
 *                  3.如果字符串是一个空字符串或者是一个全是空格的字符串，则转换为0
 * 
 *          - 布尔值 --> 数字
 *                  true == 1
 *                  true == 0
 * 
 *          - null --> 数字  --> 0
 * 
 *          - nudefined --> 数字  --> NaN
 *                  
 * 转换方式二：
 *      - 这种方式专门用来处理 字符串
 *      - parseInt()函数 。 把一个字符串转换为一个整数
 *      - parseFloat()函数 。 把一个字符串转换为一个浮点数
 * 
 *      - 如果对非 String使用，parseInt()或者parseFloat()
 *          它会先将其转换为String然后再操作
 *          
 *          let a = null;
 *             a = parseInt(a);
 *             console.log(typeof a);  // number
 *             console.log(a); // NaN
 */
```
```
let a = '123';

parseFloat
a = Number(a)

console.log(typeof a); // number
console.log(a); // 123

a = '1213aa'

a = Number(a)

console.log(typeof a); // number
console.log(a); // NaN


a = null

a = Number(a)

console.log(typeof a); // number
console.log(a); // 0

a = undefined

a = Number(a)

console.log(typeof a); // number
console.log(a); // 0


a = null;
a = parseInt(a);
console.log(typeof a);  // number
console.log(a); // NaN

```
## P13:其他数据类型
- 笔记本 git 访问配合 ssh 
- 在JS中，如果要表示16进制的数字，
    - 则需要以0x开头
    - 如果要表示8进制的数字，则需要以0开头
    - 如果要表示2进制的数组，则需要以0b 开头
    - 但是不是所有浏览器都支持 ，比如ie浏览器



```
// 十六进制
let a = 0x10;

console.log(a); //16
console.log(typeof a); //number 

a = 0xff;

console.log(a); //255
console.log(typeof a); //number 



// 八进制
a = 070;

console.log(a); //56
console.log(typeof a); //number 

c = '070'

// 八进制装换为十进制时，个浏览器表现可能不一致 ie8 中时56， 是按八进制规则转换的
// 传入第二个参数，表示转换进制
b = parseInt(c,10)

console.log('b='+b); // chrome,firefox = 70

// 二进制数字
a = 0b11;

console.log(a); //2
console.log(typeof a); //number 
```



## P14:转换为Boolean类型
将其他的数据类型转换为Boolean
---

使用Boolean() 函数

	- 数字 ---> 布尔
       - 除了0和NaN,别的都是true
       
	- 字符串 ---> 布尔
       - 除了空字符串，别的都是true
       
	- null和undefined 都会转换为 false 

	- 对象也会转换为true   



## P15：算数运算符

    当对非Number类型的值进行运算时，会将这些值转换为Number然后再运算
    任何值和NaN做运算都得NaN


    `+` 可以对两个值进行加法运算，并将结果返回
    如果对两个字符串进行加法运算，则会进制字符串拼接，并返回
    *任何的值和字符串加法运算，都会先转换为字符串，然后再和字符串做拼串的操作*

    利用这个特点，可以做一些隐式类型转换
    let a = 123;
    a = a+''; 
    a = "123" 

    字符串相加时，遵循基本的运算逻辑，相加从左到右计算，先乘除后加减

    let b = 1+2+'3';  // "33"  
    let c = '1'+2+3; // "123"

    `-`
        可以对两个值进行减法运算，并将结果返回
            先转换为Number 在计算的特点，进行隐式类型转换

        let a = '123'-0;  
        console.log(typeof a) // number 
				console.log(a); // 123
        
`*`
  	可以对两个值，进行乘法运算
`/`
    可以对两个值，进行除法运算
`%`
  	可以对两个值，进行取余运算





P16：一元运算符

一元运算符，只需要一个操作数

	`+` ：正号
     正号不会对数字产生任何影响
     
  `- `：负号
  	- 负号可以对数字进行负号的取反

	- 对于非Number类型的值
    - 他会先转换为Number,然后再运算
    - 可以对一个其他的数据类型使用+，来将其转换为number
    - 它的原理和Number()函数一样
```
let result = 1 + '2' + 3;

console.log(result) // "123"

let result = 1 + +'2' + 3;

console.log(result) // 6
```

## P17:自增和自减

    - 自增
        - 通过自增可以使变量再自身的基础上增加1
    - 对于一个变量自增之后，原变量的值会立即自增1
    - 自增分成两种：后++（a++) 和前++ （++a）
    - 不论是a++ 还是 ++a， 都会立即使原变量的值自增1
        - 不同的是a++ 和 ++a的值不同，
        - a++的值等于原变量的值（自增前的值）
        - ++a的值等新值（自增后的值）


    - 自减
        - 通过自减可以使变量再自身的基础上减1
    - 自减分成两种，后-- (a--) 和 前-- (--a)
        - 无论是a-- 还是 --a 都会立即使原变量的值自减1
        - 不同的是 a-- 和 --a 的值不同
            -	a-- 是变量的原值（自减前的值）
        -	--a 是变量的现值 （自减后的值） 
	

    自减和自增同理，记住一个是自增/自减前的值（a++,a--） 一个这是自增/自减后的值（++a,--a)

```
let a = 10;
a++
console.log(a++); // 11  ++ 前的值
console.log('a = '+ a); // 12

let b = 10;

++b;

console.log(++b); // 12  ++ 后的值

console.log(b); // 12

let d = 11;

// 11 + 13 + 13 = 37
var result = d++ + ++d + d;  //37

console.log(result);
```

练习
---

```
var n1 = 10, n2 = 20;
var n = n1++;

console.log(n); // 10
console.log(n1); // 11

n = ++n1; // 11
console.log(n); // 12
console.log(n1); // 12

n = n2--;

console.log(n); //20
console.log(n2); // 19

n = --n2; // 18

console.log(n); // 18
console.log(n2); // 18

```

## P18:逻辑运算符

**JS中为我们提供了三种逻辑运算符**

    ! 非
        !可以用来对一个值进行非运算
    所谓非运算就是指对一个布尔值进行取反操作
        - true 变 false， false变true
    如果对一个进行两次取反，他不会变化

    - 如果对非布尔值进行运算，则会将其先转化为布尔值，然后再取反
    - 所以我们可以利用该特点，来将一个其他来的数据类型转换为布尔值
    - 可以为一个任意数据类型取两次反，来将其转换为布尔值
    - 原理和Boolean()函数一样
  
   ```
   	let a = '111';
  
    let b = !a;
    let c = !!a;
    
    console.log(b); // false
    console.log(typeof b); // boolean
    
    
    console.log(c); // true
    console.log(typeof c); //boolean
```

    && 与
        - && 可以对符号两侧的值进行‘与’运算并返回结果
    - 运算规则
        - 两个值中只要有个值为false 就返回 false
        - 只有两个值都为true 时，才会返回 true
        - 
    - JS中的“与”运算属于短路操作
    - 如果第一个值为false，则不会检查第二个值


    || 或
        - || 可以对符号两侧的值进行或运算并返回结果
    - 运算规则
        - 两个值中只要有一个值为true是，就返回true
        - 只有两个值都为false时，才会返回 false
        - 
        - JS 中的“或”,属于短路操作
        - 如果第一个值为true,则不会检查第二个值
        - 如果第一个值为false，则会检查第二个值


    && ||  非布尔值的情况
    ● 对于非布尔值进行与或运算，会先将其转换为布尔值，然后再运算，并且返回原值
    ● 如果两个值都为true，则返回后边的
    ● 如果两个值中有false ， 则返回靠前的false

    与运算：
        ● 如果第一个值为true，则必然返回第二个值，并且返回的是原值，不是布尔值
        ● 如果第一个值为false，则直接返回第一个值，并且返回的是原值，不是布尔值
    或运算：
        ● 如果第一个值为true，则直接返回第一个值
        ● 如果第一个值为false，则直接返回第二个值
```       
// true && true
// 与运算：如果两个值都为true，则返回后边的
var result = 1 && 2;


console.log(result); // 2 



// 如果两个值中有false ， 则返回靠前的false
// false && true;
result = 0 && 2;


console.log(result); // 0



// false && false 
result = NaN && 0;


console.log(result); // NaN


result = 0 && NaN;


console.log(result); // 0
let result;


// true || 
result = 2 || 1; // 2
result = 23 || NaN; // 23
result = 123 || 0; // 123


console.log(result);


// false ||
result = 0 || undefined; // undefined
result = NaN || 111; // 111


console.log(result);
```

## P19:运算符：

    赋值运算符：
    ● = 
    ○ 可以将符号右侧的值，赋值给符号左侧的变量
    ● +=
    ○ a += 5   等价与  a = a +5;
    ● -= 
    ○ a -= 5   等价与  a = a -5;
    ● *=
    ○ a *= 5   等价与  a = a * 5;
    ● /=
    ○ a  /= 5   等价与  a = a / 5;
    ● %=
    ○ a %= 5   等价与  a = a % 5;
    关系运算符
    ● 通过关系运算符可以比较两个值之间的大小关系
    ○ 如果关系成立，它会返回true，如果关系不成立，它会返回false 
    ● > 大于号
    ○ 判断符号左侧的值是否大于右侧的值
    ○ 如果关系成立，返回true ， 如果关系不成立，则返回false
    ● < 小于好
    ○ 判断符号左侧的值是否小于右侧的值
    ○ 如果关系成立，则返回true， 如果关系不成立，则返回false 
    ● >= 大于或等于
    ● <= 下于或等于
    ● == 是否相等，会做隐式类型转换，之后再进行比较
    ○ 大部分情况下会将两个值转换成Number后再判断
    ○ 除 null == 0  // false
    ○ undefined衍生自null
        ■ 所以这两个值做相等判断时，会返回true
        ■ console.log(undefined == null)  // true
    ○ NaN不和任何值相等，包括它本身
        ■ consloe.log(NaN == NaN) // false 
        ■ 检查一个值是否是NaN ,使用isNaN() 函数，返回一个布尔值
    ● !=  不等于
    ● === 是否完全相等，不会做类型转换，类型不同直接返回false
    ● !== 不全等
    关系运算符--非数值情况下的比较
    ● 任何值和NaN做任何比较都是false
    ● 对于非数值进行比较时，会先将其转换为数字然后再比较
    ○ 如果符号两侧的值都是字符串时，不会将其换成为数字进行比较
    ○ 而是会分别比较字符串中字符的Unicode编码
    ○ 比较字符串编码时，是一位一位进行比较，如果第一位一样，则比较下一位，所以可以利用这个特性，做英文字母的排序
    ○ 这样比较对中文没有意义
    ● 如果比较两个字符串型的数字，可能会得到不可预期的结果
    ● 注意：在比较两个字符串型的数字时，一定一定一定要转型
    console.log('12323' > '55'); // false
    console.log('12323' > +'55'); // true
    console.log('12323' > 55); // true

    console.log('a' > 'b'); // false

    console.log('您' > '我'); // false


    console.log(undefined == null)  // true
    console.log(NaN == NaN)  // false

## P20:条件运算符也叫三元运算符
    条件运算符也叫三元运算符
    ● 语法
    ○ 条件表达式 ? 语句1 : 语句2
    ○ 执行的流程
        ■ 条件运算符在执行时，首先对条件表达式进行求职
        ● 如果该值为true，则执行语句1，并返回结果
        ● 如果该值为false，则执行语句2，并返回结果
        ■ 如果条件表达式的求值结果是一个非布尔值
        ● 会将其转换为布尔值，然后在运算
    true ? console.log('a') : console.log('b'); // a
    false ? console.log('a') : console.log('b'); // b


    let a = 10;
    let b = 20;
    let c = 50;


    a > b ? console.log(a) : console.log(b); // 20


    // 会返回结果
    let max = a > b ? a : b;
    console.log('max = ' + max); // max = 20


    // 三个数中的最大数
    max = max > c ? max : c;
    console.log(max); // 50


    max = a > b ? (a > c ? a : c) : (b > c ? b : c);
    console.log(max); // 50

    // 表达式为非布尔值时，会先进行类型转换，再运算
    'sksk' ? console.log('a') : console.log('b'); // a
    '' ? console.log('a') : console.log('b'); // b

## P21:运算符的优先级
    运算符的优先级
    ● ,运算符
    ○ 使用 ,可以分割多个语句，一般可以再声明变量时使用。
    ● 先乘除后加减
    ○ let result = 1 +3 *2; // 7
    ● 在JS中有一个运算符优先级的表，在表中越考上优先级越高，优先级越高，越优先计算
    ○ 如果优先级一样高，则从左到右依次计算
    ○ 可以使用()改变优先级，不确定时可以使用()来控制执行顺序
    // , 运算符
    let a , b = 2 , c;
    console.log(b); // 2
    console.log(c); // undefined

    // 如果||的优先级高或者一样高，返回5
    // 如果&&的优先级高，返回2

    let result = 2 || 3 && 5;
    console.log(result); //2
    P22:语句
    {
        console.log(a);
        alert('hello');
        document.write('hello world');
    }
    在JS中上面的都是一条一条语句，语句是按照自上向下的顺序一条一条执行的
    { } 来为语句分组

流程控制语句
==
    a. 条件判断语句
    ⅰ. 使用条件判断语句可以再执行某个语句之前进行判断
    ⅱ. 如果条件成立，则才会执行语句，条件不成立则语句不执行
        1. if() 语句
        a. 语法: if(条件表达式) { 语句... }
            ⅰ. if语句再执行时，会先对条件表达式进行求职判断
            ⅱ. 如果条件表达式的值为true，则执行if后的语句
            ⅲ. 如果条件表达式的值为false。则不会执行if后的语句
            ⅳ. if语句只能控制紧随其后的那个语句，如果希望if语句可以控制多条语句，可以将这些语句统一放到一个代码块中
        b. 语法2：if(条件表达式){ 语句... } else {  语句... }
            ⅰ. if...else... 语句，当该语句执行是，会先对if后的条件表达式进行求值判断
            ⅱ. 如果该值为true，这执行if后的语句
            ⅲ. 如果该值为false，这执行else后的语句
        c. 语法3： if(条件表达式){ 语句... }else if(条件表达式){ 语句 } else if(条件表达式){ 语句 } else{ 语句 }
            ⅰ. 当执行该语句时，会从上到下依次对条件表达式进行求值判断，直到执行完毕
            ⅱ. 如果值为true，则执行当前语句
            ⅲ. 如果值为false，则继续向下执行
            ⅳ. 如果所有条件都不满足，则执行最后一个else后的语句
            ⅴ. 该语句中，只会有一个代码块被执行，一旦代码块被执行，则直接结束语句
            1. 所以在进行条件语句判断时，要判断严谨
            2. 从最优先条件向下判断
    b. 条件分支语句
    c. 循环语句

```
if (false) 
console.log('111');  // if() 语句控制
console.log('222');  // 不受if() 语句控制

if (false) {
    console.log('111');
    console.log('222');
}

let a = 11;
if (a > 11) {
    console.log('111');
    console.log('222');
}


if (age > 100) {
    console.log('死了');
}else{
    console.log('好好的');
}


age = 1
if (age > 90) {
    console.log('对于90');
}else if(age > 80){
    console.log('对于80');
}else if(age > 70){
    console.log('对于70');
}else if(age > 60){
    console.log('对于60');
}else{
    console.log('小于60');
}



// 会导致死代码
age = 50
if (age > 10) {
    console.log('大于10');
}else if(age > 20){
    console.log('大于20');
}else if(age > 30){
    console.log('大于30');
}else if(age > 50){
    console.log('大于50');
}else{
    console.log('小于10');
}

//可完善条件表达式
age = 52
if (age > 10 && age < 20) {
    console.log('大于10');
}else if(age > 20 && age < 30){
    console.log('大于20');
}else if(age > 30 && age < 50){
    console.log('大于30');
}else if(age > 50){
    console.log('大于50');
}else{
}
```

    从键盘输入小明的期末成绩，
    当成绩等于100 时，奖励宝马一辆
    当成绩大于等于80 并且 小于等于99 时，奖励手机一部
    当成绩大于等于60 并且 小于等于80 时，奖励参考书一部
    其他情况时，什么奖励都没有

```
window.onload = function () {

    let chengji = document.getElementById('chengji');
    let oBtn = document.getElementById('search');

    oBtn.addEventListener('click', function () {
        // console.log(chengji.value);

        let cj = chengji.value;

        if (cj > 100 || cj < 0 || isNaN(cj)) {
            console.log('分数不合法');
        } else {
            if (cj == 100) {
                console.log('奖励宝马一辆');
            } else if (cj >= 80 && cj <= 99) {
                console.log('奖励iPhone15s');
            } else if (cj >= 60 && cj <= 80) {
                console.log('奖励参考书一部');
            } else {
                console.log('什么奖励都没有');
            }
        }
    });
};

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>小明成绩</title>
</head>
<body>
    
    <input type="text" id="chengji" value="">

    <bottom id="search"> 查询 </bottom>


</body>
<script src="biji.js"></script>
</html>
```

## P23:条件分支语句

    条件分支语句也叫 switch语句
    ● 工作原理：首先设置表达式 n（通常是一个变量）。随后表达式的值会与结构中的每个 case 的值做比较。如果存在匹配，则与该 case 关联的代码块会被执行。请使用 break 来阻止代码自动地向下一个 case 运行。
    ● 如果比较结果为true，则从当前case处开始执行代码
    ○ 当前case后的所有代码都会执行，可以使用 break 来阻止代码自动向下一个 case 运行
    ○ 如果比较结果为false，则继续向下比较
    ○ 如果所有的比较结果都为 false，则只执行 default 后的语句

## P24:循环语句
    循环语句 
    ● 通过循环语句可以反复的执行一段代码多次
    1. 初始化表达式
    a. var i = 0;
    2. 条件表达式
    a. while( i<10 )
    3. 更新表达式
    a. i++

    while 循环
    ● 语法
    ● while( 条件表达式 ) {
    ●       语句... 
    ●  }
    while 语句再执行时，
    ● 先对条件表达式进行求值判断
    ○ 如果为true，则执行循环体，循环体执行完毕后，继续对表达式进行判断，如果为true，则继续执行循环体
    ○ 如果为false，则退出循环

    do...while 循环
    ● 在执行时，会先执行循环体，在对条件表达式进行判断
    ● 和 while 循环的区别就是，while循环会先进行条件表达式的判断，在执行循环体。而do...while循环至少会执行依次循环体。
    break关键字和continue
    ● 可以用来退出 swith和循环语句
    ● 不能用来退出 if (){  } 语句
    ● break关键字，会立即终止离他最近的那个循环
    ● continue会跳过当前循环
    ● 可以给for 循环制定 lable (别名) 来制定终止或者跳过离他最近的那个循环

    console.time('test');  // 开启一个名叫test 的计时器
    console.timeEnd('test');  // 结束 test 的计时器

    合理使用 break 和 循环条件，可以大幅提升代码性能 
 
```
// 1000块，年利率 5% 一共 需要多少年 能到 5000块

let mn = 1000;
let i = 0;

while (mn <= 5000) {
    mn = mn * 1.05;
    i++;
}

console.log('一共需要 ' + i + '年')  // 一共需要 33年


let x = 11;

do {
    console.log('我最少会执行依次');
    x++;
} while (x<10);

/**
 * for循环的语法
 *    
 *      for(①初始化表达式; ②条件表达式; ④更新表达式){
 *          ③语句...
 *      }
 *      
 *      执行顺序 
 *          ①：初始化表达式
 *          ②：条件表达式
 *                 如果为true,执行 ③ ，
 *                  如果为false，终止循环
 *          ④：执行更新表达式，完毕后，继续执行②
 */



for (let index = 0; index < array.length; index++) {
    const element = array[index];
    
}



// 死循环
for (;;) {
    alert('Hello')
}
let max=0;
for (let i = 1; i <= 100; i++) {


    if (i%2 != 0) {
        console.log(i);
        max+=i;
    }
    
}


console.log('0-100之间所有奇数的和为 '+max);  //0-100之间所有奇数的和为 2500



// 最外层循环控制输出高度
// 内层循环控制输出长度

for (let index = 0; index < 5; index++) {

    for (let x = 0; x < 5; x++) {
        document.write('*&nbsp;&nbsp;&nbsp;');
    }

    document.write('<br/>')
}

*   *   *   *   *   
*   *   *   *   *   
*   *   *   *   *   
*   *   *   *   *   
*   *   *   *   *   


for (let index = 0; index < 5; index++) {

    for (let x = 0; x < index+1; x++) {
        document.write('*&nbsp;&nbsp;&nbsp;');
    }

    document.write('<br/>')
}

*   
*   *   
*   *   *   
*   *   *   *   
*   *   *   *   *   

// 写法1
for (let index = 0; index < 5; index++) {

    for (let x = 5; x > index; x--) {
        document.write('*&nbsp;&nbsp;&nbsp;');
    }

    document.write('<br/>')
}

// 写法2 
for (let index = 0; index < 5; index++) {

    for (let x = 0; x < 5 - index; x++) {
        document.write('*&nbsp;&nbsp;&nbsp;');
    }

    document.write('<br/>')
}

*   *   *   *   *   j<5(5-0)  				i=0
*   *   *   *   		j<4(5-1)					i=1
*   *   *   				j<3(5-2)					i=2
*   *   						j<2(5-3)					i=3
*   								j<1(5-4) 			  	i=4

// 9*9乘法表

for (let i = 1; i < 10; i++) {
    for (let j = 1; j <= i; j++) {
        document.write(`${j} * ${i}` + '=' + (i * j)+'&nbsp;&nbsp;&nbsp;&nbsp;')
    }
    
    document.write('<br/>')
}

1 * 1=1    
1 * 2=2    2 * 2=4    
1 * 3=3    2 * 3=6    3 * 3=9    
1 * 4=4    2 * 4=8    3 * 4=12    4 * 4=16    
1 * 5=5    2 * 5=10    3 * 5=15    4 * 5=20    5 * 5=25    
1 * 6=6    2 * 6=12    3 * 6=18    4 * 6=24    5 * 6=30    6 * 6=36    
1 * 7=7    2 * 7=14    3 * 7=21    4 * 7=28    5 * 7=35    6 * 7=42    7 * 7=49    
1 * 8=8    2 * 8=16    3 * 8=24    4 * 8=32    5 * 8=40    6 * 8=48    7 * 8=56    8 * 8=64    
1 * 9=9    2 * 9=18    3 * 9=27    4 * 9=36    5 * 9=45    6 * 9=54    7 * 9=63    8 * 9=72    9 * 9=81    
```

## P25:对象

    对象的分类 
    1. 内建对象
    a. 有ES标准中定义的的对象，在任何的ES的实现中都可以使用
    b. 比如：Math Date String Number Boolean Function Object....
    2. 宿主对象
    a. 由JS的运行环境提供的对象，目前来讲主要指 浏览器提供的对象
    b. BOM DOM
    3. 自定义对象
    a. 由开发人员自己创建的对象
    // 创建对象

```
/**
 * 使用new 关键字调用的函数，是构造函数 constructor 
 * 构造函数是专门用来创建对象的函数
 * 
 */


let obj = new Object();


/**
 * 在对象中保存的值为属性
 * 向对象中添加属性
 *  语法：对象.属性 = 属性值
 */


obj.name = '李学峰';
obj.gender = '男';
obj.age = 30;


console.log(obj);  // {}


/**
 * 读取对象中的属性
 *  对象.属性名
 * 
 * 如果读取对象中没有的属性，不会报错而是会返回 undefined
 */
console.log(obj.age);  //30



/**
 * 修改对象的属性
 *  对象.属性名 = 新值
 */


obj.age = 18;


console.log(obj.age);  //18


/**
 * 删除对象
 *  delete 对象.属性名
 */


delete obj.age;


console.log(obj); // { name: '李学峰', gender: '男' }

var obj = {};
obj.name = '李学峰';


/**
 * 使用对象字面量，可以在创建对象时，直接指定对象中的属性
 *  语法： {属性名：属性值,属性名：属性值,...}
 */
var obj2 = {
    name:'fm',
    age:26,
}


console.log(obj2); //{ name: 'fm', age: 26 }

```

    向对象中添加属性
    1. 属性名
    a. 对象的属性名不强制要求遵循标识符的规范，什么乱七八糟的属性名都可以
        ⅰ. obj.var = 'hello'  
        ⅱ. obj.123 = '456';   这种方式会报错
        1. 如果想使用可以 obj['123'] = '456';
        2. 获取的时候也要 console.log(obj['123']) 
    b. 最佳实践，还是尽量遵循标识符的规范
    c. 如果要使用特殊的属性名不能采用 .的方式来操作，需要另一种方式
        ⅰ. 语法： 对象["属性名"] = 属性值
        ⅱ. 读取的时候也要采用这种方式
        ⅲ. 使用[] 这种形式去操作属性，更加灵活，在[] 中可以直接传递一个变量，这样变量值时多少就会读取那个属性
    2. 属性值
    a. JS对象的属性值，可以是任意的数据类型，
```
let obj = new Object();


obj.var = 'hello';


console.log(obj); //{ var: 'hello' }



// obj.123 = '324'; // 报错


obj['123'] = '1777';


console.log(obj); //{ '123': '1777', var: 'hello' }


// 使用[]这种方式更加灵活，可以再[] 传递一个变量，变量的值是多少就会读取那个属性


let n = '123';


console.log(obj[n]); //1777
/**
 * in 运算符
 *  - 该运算符，可以检查一个对象中是否含有指定的属性
 *  - 语法； "属性名" in 对象
 */

let obj = new Object();
obj.var = 'hello';
obj['123'] = '1777';

console.log('123' in obj);  //true 
```
    基本数据类型的值，直接在栈内存中存储
    值与值之间时独立存在的，修改一个变量不会影响其他的变量

    引用数据类型，保存在堆内存中，每创建一个新的对象，就会在堆内存中开辟一个新的空间，
    而变量保存的是对象的内存地址，（对象的引用-指针），如果两个变量保存的是同一个对象的引用
    当一个通过一个变量修改属性时，另一个也会受到影响





## P26:函数

    /**
     * 函数便于维护和在不同地方调用
     * 函数也是一个对象，
     * 函数中可以封装一些功能（代码），在需要时，可以执行这些功能
     */


    // 使用构造函数来创建一个函数对象
    // 可以将要执行的代码以字符串的形式传递给构造函数
    var fun = new Function("console.log('new Function关键字声明函数');");


    // 使用函数声明来创建一个函数
    // var 函数名 = function([形参1,形参2,形参3...,形参N])
    function fun2() {
        console.log('111');
    }


    // 使用函数表达式 来创建一个函数
    // var 函数名 = function([形参1,形参2,形参3...,形参N])
    var fun3 = function () {
        console.log('我是一个匿名函数');
    }


    // 封装到函数中的代码，不会立即执行，
    // 函数中的代码会在函数调用的时候执行
    fun();
    fun2();
    fun3();

    函数中的参数
    1. 在函数中的()中来指定一个或多个形参（形式参数）
    a. 多个参数之间使用,分割，声明形参就相当于在函数内部声明了对应的变量，但并不赋值
    2. 在函数调用时，可以在()中制定实参，（实际参数）
    a. 实参将会赋值给函数中的形参
    3. 调用函数时，解析器不会检查实参的类型，
    a. 所有要注意，是否有可能接收到非法的参数，如果有可能则需要对参数进行类型检查
    b. 函数的实参可以是任意数据类型
    4. 调用函数时，解析器也不会检查实参的数量
    a. 多余的实参不会被赋值
    b. 如果实参的数量少于形参的数量，则没有对应实参的形参将是undefined
    /**
     * 
     * @param {形参1} a 
     * @param {形参2} b 
     */
    function sum(a, b) {
        console.log(a);
        console.log(b); //undefined
        console.log(a + b);
    }



    // 实参 1 33 
    // 多余的将会被忽略
    sum(1,33,true,undefined,null); // 34
    sum(1); // NaN
    返回值
    1. 可以使用 return来设置函数的返回值，可以定义一个变量来接收返回值
    2. return可以返回任意类型的值
    3. 在函数中return后的语句都不会执行
    4. 如果return语句后不跟任何值就相当于 返回 undefined
    a. 如果函数中不写 return 也会返回undefined

    var obj = {
        name: '李学峰',
        age: 30,
        sayName: function () {
            // console.log(obj.name);
            console.log(this.name);
        }
    }


    // 函数也可以作为对象的属性
    //如果一个函数作为一个对象的属性保存，那么我们称这个函数是这个对象的方法
    obj.sayName();
    // 立即执行函数
    (function () {
        console.log('hello');
    })();

    (function (a,b) {
        console.log(a);
        console.log(b);
    })(10,20);

    // 枚举对象中的属性
    // 使用 for ... in 语句
    // 语法： 
    //      for ( var 变量 in 对象 ){
    //          
    //      }
    for (const key in obj2) {
        console.log(key); // 属性名
        console.log(obj2[key]); // 属性值
    }

## P26:作用域（Scope）
    作用域：
    1. 全局作用域 -- 全局执行环境是最外层的一个执行环境（上下文）
    a. 执行环境定义了变量或函数有权访问的其他数据，决定了他们各自的行为。
    b. 每个执行环境都有一个与之关联的变量对象，环境中定义的所有变量和函数都保存在这个对象中
    c. 根据ES 实现所在的宿主环境的不同，表示执行环境的对象也不一样。
    d. 在web浏览器中，全局执行环境被认为是 window 对象, node中为 global对象
        ⅰ. 因此所有全局变量和函数都是作为 window 对象的属性和方法创建的
    e. 某个执行环境中的所有代码执行完毕后，该环境被销毁，保存在其中的所有变量或函数定义也随之销毁
    f. 全局执行环境直到应用程序退出--例如关闭网页或者浏览器---时才会被销毁
    2. 函数作用域（局部作用域）
    a. 函数执行环境或者叫函数执行的上下文
    b. 调用时创建函数作用域，函数执行完毕后，函数作用域销毁
    c. 函数作用域中可以访问到全局作用域中的变量，全局作用域中无法访问到函数作用域中的变量
    d. 在函数作用域中操作一个变量时，它会先在自身作用域中寻找，如果有就直接使用，如果没有就想上一级寻找，一直找到全局作用域，如果没找到则会报错
    e. 在函数中如果想访问全局的同名变量可以使用 window.x 访问
    f. 函数中var 关键字 声明变量也会进行变量提升 ， 函数声明也是
    g. 函数形参会声明变量，相当于var  形参，所以形参的作用域在函数内
    3. 块级作用域
    a. es6 中新增 let const 关键字和 { }
    b. let 关键字声明变量后不能在同一个作用域重复声明 --否则会报错
    c. const 关键字用来声明一个常量
        ⅰ. 声明时必须同时初始化为某个值
        ⅱ. 同一个作用域不能重复声明
        ⅲ. 不能重复赋值

    var 关键字的变量提升
    1. 使用var 关键字声明的变量，会在所有代码执行之前被声明（不会被赋值） 
    a. let const 关键字 不会进行变量提升，会进入暂时性死区

    console.log(a);
    var a = 13; //undefined

    // var 关键字 会做变量提升， 上边的写法，相当于下面 的代码
    var a;
    console.log(a);
    a = 13;
    函数的声明提前
    1. 使用函数声明的形式创建的函数 function 函数(){ }
    a. 他会在所有代码执行前就被创建，所以我们可以在函数声明前就调用函数
    2. 使用函数表达式创建的函数，不会被声明提升，只会进行变量提升，所以以这种方式创建的函数，在它之前调用 会报错  undefined/函数 is not a function 
    fun(); // this is fun  -- 函数调用
    console.log(fun2); // undefined
    fun2(); //fun2 is not a function


    //函数声明的形式
    function fun() {
        console.log('this is fun');
    }

    // 函数表达式的形式
    var fun2 = function () {
        console.log('this is fun2');
    }
    // let 关键字的作用域是块级

    let a = 123;
    console.log(window.a); // undefined 


    var b = 123;
    console.log(window.a); // 123

    // let关键字在同一个作用域内不能声明两次或者多次，（报错）
    // 重复的var 声明会被忽略

## P27:this
    在ECMAScript 5 中，函数内部存在两个特殊的对象， arguments和this。在ES6中又新增了new.target属性
    1. this对象是在运行时基于函数的运行环境绑定的：在全局函数中，this等于window，而在函数被作为某个对象的方法调用时this等于那个对象。
    2. 匿名函数的执行环境具有全局性 因此其this对象通常指向 window
    3. 在箭头函数中，this引用的是定义箭头函数的上下文

    尚硅谷  
    ● 根据函数的调用方式的不同，this会指向不同的对象
    ○ 以函数的形式调用时，this永远都是window
    ○ 以方法的形式调用时，this就是调用方法的那个对象
    function fun() {
        // console.log(arguments);
        console.log(this);  // Window 
        console.log(this.name);
    }

    var name = '是我全局中的name'; //是我全局中的name

    // fun()  // 全局执行环境 this window 

    var obj = {
        name:'fxm'
    }
    obj.sayName = fun;



    obj.sayName(); // fxm   this {name: 'fxm', sayName: ƒ}


---------------------------------------------------------

``` // 创建一个全局name变量
var hh = '全局变量';

function fun() {
    console.log(this.hh);
}

var obj = {
    hh:'xiaomiao',
    sayName:fun
}

var obj2 = {
    hh:'kkkk',
    sayName:fun
}
fun(); // 全局变量

obj.sayName(); // xiaomiao
obj2.sayName(); //kkkk
```
## P28:使用工厂模式创建对象
```
使用工厂模式创建对象，可以大批量创建对象
1. 使用工厂方法创建的对象，使用的构造函数都是Object
  a. 所以创建的对象都是Object这个类型，就导致我们无法区分出多种不同类的对象
// 使用对象字面量创建对象
var obj = {
    name: '李学峰',
    age: 18,
    gender: '男',
    sayName: function () {
        console.log(this.name);
    }
}
var obj2 = {
    name: '封晓淼',
    age: 18,
    gender: '女',
    sayName: function () {
        console.log(this.name);
    }
}
var obj3 = {
    name: '李宝宝',
    age: 3,
    gender: '女',
    sayName: function () {
        console.log(this.name);
    }
}
obj.sayName(); //李学峰
obj2.sayName(); //封晓淼
obj3.sayName(); //李宝宝
```
-------------------------------------------------------------
```
// 使用工厂模式创建对象
function createPerson(name, age, gender) {
    var person = new Object();

    person.name = name;
    person.age = age;
    person.gender = gender;
    person.sayName = function () {
        console.log(this.name);
    }
    return person;
}


var xiaoMing = createPerson('小明',16,'男');
var xiaoHong = createPerson('小红',18,'女');
var niuNai = createPerson('牛奶',3,'男');

console.log(xiaoMing);
xiaoMing.sayName(); //小明
xiaoHong.sayName(); // 小红
niuNai.sayName(); // 牛奶


// 创建一个狗的对象
function createDog(name, age) {
    var dog = new Object();

    dog.name = name;
    dog.age = age;
    dog.sayHello = function () {
        console.log('汪汪~~');
    }
    return dog;
}

var wangcai = createDog('旺财', 3)
console.log(wangcai); //{ name: '旺财', age: 3, sayHello: [Function (anonymous)] }
wangcai.sayHello(); //汪汪~~
```
## P29:构造函数模式
```
构造函数模式  -- 创建自定义的构造函数
1. 创建一个构造函数，专门用来创建制定对象
  a. 构造函数就是一个普通的函数，创建方式和普通函数没有区别
  b. 不同的是构造函数习惯上首字母大写
2. 构造函数和其他普通函数的唯一区别就是调用方式的不同
  a. 普通函数是直接调用，而构造函数需要使用new关键字来调用
3. 构造函数的执行流程
  a. 立即创建一个新的对象
  b. 将新建的对象设置为函数中的this ,在构造函数中可以使用this来引用新建的对象,将构造函数的作用域赋给新对象因此this就指向了这个新对象
  c. 逐行执行函数中的代码
  d. 将新建的对象作为返回值返回
4. 使用同一个构造函数创建的对象，我们成为一类对象，也将一个构造函数成为一个类	
  a. 我们将通过一个构造函数创建的对象，称为是该类的实例
5. this的情况
  a. 当以函数的形式调用时，函数的执行环境 （上下文）是全局时，this指向 window 
  b. 当以一个对象的方法调用时，谁调用方法this就指向谁
  c. 当以构造函数的形式调用时，this就是新创建的那个变量
// 创建人
function Persion(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = function () {
        console.log(this.name);
    };
    this.sayHello = function () {
        console.log('I love you');
    }
}
// 创建狗狗
function Dog(name, age) {
    this.name = name;
    this.age = age;
    this.sayName = function () {
        console.log(this.name);
    };
    this.sayHello = function () {
        console.log('汪汪~~');
    }
}

var lxf = new Persion('李学峰', 30, '男')
var fm = new Persion('封淼', 18, '女')

console.log(lxf);
console.log(fm); //Persion {name: '封淼', age: 18, gender: '女', sayName: ƒ, sayHello: ƒ}
lxf.sayName();  // 李学峰
lxf.sayHello();  // I love you


var wangcai = new Dog('旺财', 3)
var dafu = new Dog('大福', 2)

console.log(wangcai); //Dog {name: '旺财', age: 3, sayName: ƒ, sayHello: ƒ}
wangcai.sayName(); // 旺财
dafu.sayName(); //大福
instanceof 运算符 用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上。--MDN
尚硅谷
● instanceof 运算符可以检查一个对象是否是一个类的实例
  ○ 如果是 返回 true 否则返回 false
● 所有的对象都是Object的后代
  ○ 所以任何对象和Object 做 instanceof 操作 都会返回 true

/**
 * 语法：
 *      对象 instanceof 类
 * */ 
console.log(wangcai instanceof Dog); //true
console.log(wangcai instanceof Persion); //false

console.log(wangcai instanceof Object); //true
console.log(wangcai instanceof Object); //true
P30：构造函数模式+原型模式
构造函数的不足：
● 当我们的方法是在构造函数内部创建的时候, 构造函数每执行一次 就会创建一个新的该方法，也就是说所有实例的 方法都是唯一的
● 这样就导致了构造函数执行一次就会创建一个新的方法，执行1w次就会创建1w个新的方法
● 这完全没有必要，完全可以使所有的对象共享同一个方法
// 构造函数
function Persion(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = function () {
        console.log(this.name);
    };
    this.sayHello = function () {
        console.log('I love you');
    }
};


// 创建对象实例
var per1 = new Persion('李学峰',20,'男'); 
var per2 = new Persion('封淼',18,'女'); 

per1.sayName();// 李学峰
per2.sayName();// 封淼

console.log( per1.sayName == per2.sayName); // false  相互独立的
// 不推荐污染全局作用和不利于多人协作

// 构造函数
function Persion(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = fun;
    this.sayHello = love
};


function fun() {
    console.log(this.name);
};
function love() {
    console.log('I love you');
};
// 创建对象实例
var per1 = new Persion('李学峰', 20, '男'); 
var per2 = new Persion('封淼', 18, '女'); 


per1.sayName(); // 李学峰
per2.sayName(); // 封淼

console.log(per1.sayName == per2.sayName); // true
原型 prototype
● 我们所创建的每一个函数，解析器都会向函数中添加一个属性 prototype ，这个属性对应着一个对象，这个对象就是我们所谓的原型对象，
● 如果函数作为普通函数 调用 prototype 没有任何作用
● 当函数以构造函数的形式调用时，它所创建的对象中都会有一个隐含的属性（__proro__），指向该构造函数的原型对象，我们可以通过__proro__来访问该属性

1. 原型对象就相当于一个公共区域，所有同一个类的实例都可以访问到这个原型对象，我们可以将对象中共有的内容，统一设置到原型对象中，
2. 当我们访问对象的一个属性或方法时，它会先在对象自身中寻找，如果有则直接使用，如果没有则会去原型对象中寻找，如果找到则直接使用，直到找到Object对象的原型，Object对象的原型没有原型，如果在Object原型中依然没有找到，则返回 undefined
function Persion() {
    
};

function MyClass() {
    
};

console.log(Persion.prototype); //{}
console.log(MyClass.prototype); //{}
console.log( Persion.prototype == MyClass.prototype);  //false

MyClass.prototype.a = '123';
MyClass.prototype.b = '456';

var mc = new MyClass();
var mc2 = new MyClass();
console.log(mc.a); // 123
console.log(mc2.a); //123

mc.a = 'hello'

console.log(mc.a); // hello
console.log(mc2.a); //123


console.log(MyClass.prototype); // { a: '123', b: '456' }
console.log(mc.__proto__ == MyClass.prototype); //true
 

// 构造函数+原型
function Persion(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
};

Persion.prototype.sayName = function () {
    console.log(this.name);
}

// 创建对象实例
var per1 = new Persion('李学峰', 20, '男'); // 李学峰
var per2 = new Persion('封淼', 18, '女'); // 封淼


per1.sayName();
per2.sayName();


console.log(per1.sayName == per2.sayName); // true
使用 in 检查对象中是否含有某个属性时，如果对象中没有但是原型中有，也会返回true 
可以使用对象的 hasOwnPrototype() 来检查对象中是否含有该属性
function MyClass() {
};

MyClass.prototype.name = '我是原型中的name';

var mc = new MyClass();
mc.age = 30;
// 使用 in 检查对象中是否 含有某个属性时，如果对象中没有但是原型中有，也会返回true 
console.log('name' in mc); //true

// 使用对象的 hasOwnPrototype() 来检查对象 自身中是否含有该属性
// 该方法只有对象自身中含有属性时，才会返回true
console.log(mc.hasOwnProperty('name'));  //false
console.log(mc.hasOwnProperty('age')); //true


console.log(mc.hasOwnProperty('hasOwnProperty'));//false
console.log(mc.__proto__.hasOwnProperty('hasOwnProperty'));//false
console.log(mc.__proto__.__proto__.hasOwnProperty('hasOwnProperty')); //true  Object
console.log(mc.__proto__.__proto__.__proto__); //null


/**
 * 原型对象也是对象，所以它也有原型
 *      当我们使用一个对象的属性或方法时，会先在自身总寻找
 *      自身中如果没有 ，则直接使用
 *      如果没有则去原型中寻找，如果原型对象中有，则使用
 *      如果没有则去 原型的原型中寻找,直到找到 Object 对象的原型 
 */
console.log( MyClass.prototype);
// {name: '我是原型中的name', constructor: ƒ}
// name: "我是原型中的name"
// constructor: ƒ MyClass()
// [[Prototype]]: Object
console.log( MyClass.prototype.__proto__);
// {constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}constructor: ƒ Object()hasOwnProperty: ƒ hasOwnProperty()isPrototypeOf: ƒ isPrototypeOf()propertyIsEnumerable: ƒ propertyIsEnumerable()toLocaleString: ƒ toLocaleString()toString: ƒ toString()valueOf: ƒ valueOf()__defineGetter__: ƒ __defineGetter__()__defineSetter__: ƒ __defineSetter__()__lookupGetter__: ƒ __lookupGetter__()__lookupSetter__: ƒ __lookupSetter__()__proto__: (...)get __proto__: ƒ __proto__()set __proto__: ƒ __proto__()
function Persion(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
};

// 自己定义一个 
// Persion.prototype.toString = function () {
//     return `Persion { name:${this.name},age:${this.age},gender:${this.gender}, }`
// }

var per = new Persion('李学峰', 18, '男');
var per2 = new Persion('封淼', 18, '女');
console.log(per); //Persion { name: '李学峰', age: 18, gender: '男' }
console.log(per.toString()); //Persion { name:李学峰,age:18,gender:男, }
console.log(per2.toString()); //Persion { name:封淼,age:18,gender:女, }

// 为自己定义时 per.toString() per2.toString() 返回 [object Object]
```
## P31:垃圾回收
    当一个对象没有任何的变量或属性对他进行引用，此时我们将永远无法操作该对象
    此时对象就像是一个垃圾，JS中有自动的垃圾回收机制，会自动将这些垃圾从内从中销毁，我们不需要也不能进行垃圾回收的操作
    我们需要将 不在使用的对象设置为null 即可
## P32:数组
    1. 自定义对象
    2. 宿主对象
    3. 内建对象

    数组
        ● 数组也是一个对象
        ● 它和普通对象的功能类似，也是用来存储一些值，
        ● 不同的是普通对象使用字符串作为属性名
        ● 而数组是使用数字作为索引操作元素
        ● 索引
        ○ 从0开始的整数就是索引
        ● 数组的存储性能比普通对象要好

    // 创建数组对象
    var arr = new Array();

    console.log(arr); // []
    console.log(typeof arr); // object
```
/**
 * 向数组中添加元素
 *      语法：数组[索引] = 值
 */
arr[0] = 10;
arr[1] = 5;
arr[2] = 12;
arr[3] = 412;

console.log(arr);

/**
 * 读取数组中的元素
 *      数组[索引]
 *  
 * 如果读取不存在的索引，它不会报错，而是会返回undefined
 */

console.log(arr[2]);

/**
 * 获取数组的长度
 *      可以使用lenght属性来获取数组的长度（元素的个数）
 *      语法：数组.lenght
 * 
 * tips：
 *      对于连续的数组，使用 lenght 可以获取到数组的长度（元素的个数）
 *      对于非连续的数组，使用 lenght 会获取到数组的最大索引+1
 *      尽量不要创建非连续的数组
 * */ 
console.log(arr.length); //4

arr[100] = 11;
console.log(arr.length); //101

/**
 * 修改lenght
 *      如果修改的lenght大于原长度，则多出部分会空出来
 *      如果修改的lenght 小于原长度，则多出元素会被删除
 */

arr.length = 3;

// 查看 实例 中 __proto__属性，指向原型对象中的属性和方法
console.log(arr.__proto__); //Object(0) []

// 向数组的最后一个位置添加属性
arr[arr.length] = 40;
arr[arr.length] = 410;
arr[arr.length] = 310;

console.log(arr); //[ 10, 5, 12, 40, 410, 310 ]


// 数组字面量方式创建数组
// 数组中的元素可以是任意数据类型
var arr2 = [];
// 直接赋值
var arr3 = [10,12,14];

var arr4 = new Object(10,22,33); // 多个参数时行为和字面量方式创建的数组一致
// 一个参数时，表示创建一个长度为10的数组
var arr5 = new Object(10)

var arr6 = [{name:'猪八戒'},{name:'猴哥'},{name:'老唐'}]

var arr7 = [{ name: '猪八戒' }, 'hello', 33, null, undefined, function () { console.log('lalal'); }]

console.log(arr7);
// [
//     { name: '猪八戒' },
//     'hello',
//     33,
//     null,
//     undefined,
//     [Function(anonymous)]
// ]
console.log(arr7[5]());  // lalal undefined
数组中的方法
forEach() 方法对数组的每个元素执行一次给定的函数。
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach
// 箭头函数
forEach((element) => { /* … */ })
forEach((element, index) => { /* … */ })
forEach((element, index, array) => { /* … */ })


// 回调函数
forEach(callbackFn)
forEach(callbackFn, thisArg)


// 内联回调函数
forEach(function(element) { /* … */ })
forEach(function(element, index) { /* … */ })
forEach(function(element, index, array){ /* … */ })
forEach(function(element, index, array) { /* … */ }, thisArg)

函数传入三个参数：
1.数组当前项的值
2.数组当前项的索引
3.数组对象本身


arr7.forEach(function (element,index,array) {  
//     // console.log(arguments);
//     // console.log('element='+element);
//     // console.log('index='+index);
//     // console.log('array='+array);
});


arr7.forEach((element, index, array) => {
    // console.log(arguments);
    // console.log('element='+element);
    // console.log('index='+index);
    // console.log('array='+array);
});

数组去重，编写一个函数，去除下列数组中的重复元素
var arr = [1,2,3,4,5,2,2,2,5,1,3,3,6,7,7,2];
//数组去重，编写一个函数，去除下列数组中的重复元素,并返回一个新的数组
var arr = [7, 7, 7, 9, 1, 2, 3, 4, 5, 2, 2, 2, 5, 1, 3, 3, 6, 7, 7, 2];


function newArr(arr) {
    let nArr = arr;
    //获取数组中的每一位元素
    for (let index = 0; index < arr.length; index++) {
        const element = arr[index];
        // console.log(element);
        // 然后获取当前元素后的所有元素，要比较的每一位
        for (let k = index + 1; k < arr.length; k++) {
            const element2 = arr[k];
            // console.log('---->'+element);
            // 判断他们是否相等
            if (element == element2) {
                // 如果相等则证明出现了重复的元素，则删除j对应的元素
                nArr.splice(k, 1)
                // Array.prototype.splice.call(arr,k,1)
                // Array.prototype.splice.apply(arr, [k, 1])
                // 当删除了当前的k所在的元素后，后边的元素会自动补位
                // 此时将不会在比价当前索引的这个元素（1,2,3,3,这种连续的情况）
                // 所以需要在比较 k 所在索引位置的元素
                k--
            }
        }
    }
    return nArr;
}

var result = newArr(arr);


console.log(result); //(8) [7, 9, 1, 2, 3, 4, 5, 6]
console.log(arr);   // (8) [7, 9, 1, 2, 3, 4, 5, 6]


//splice()该方法会改变原始数组。

function A() {
}


function B(a) {
    // 添加属性 
    this.a = a;
}

function C(a) {
    // 添加属性，如果存在 参数a
    if (a) {
        this.a = a;
    }
}

A.prototype.a = 1;
B.prototype.a = 1;
C.prototype.a = 1;

console.log(new A()); //{ __proto__:{ a:1 }}
console.log(new B()); //{ a: undefined ,__proto__:{ a: }}
console.log(new C()); //{ __proto__:{ a:1 }}
```

## 33:call和apply
```
call()和aply()
● 这两个方法都是函数对象的方法，需要通过函数对象来调用
● 当对函数调用call()和apply()都会调用函数执行
● 在调用call()和apply()可以将一个对象指定为第一个参数
  ○ 此时这个对象将会成为函数执行的this
● call()方法可以将实参在对象之后，依次传递用,分割
● apply()方法需要将实参封装到一个数组中统一传递

this 
1. 以函数形式调用时，this指向window
2. 以方法的形式调用时，this是调用方法的对象
3. 以构造函数调用时，this 是新创建的对象实例
4. 使用call和apply调用时，this是指定的那个对象

function fun() {
    console.log(this.name);
    // console.log(this);
}
// fun();
// fun.call();
// fun.apply();

var obj1 = {
    name:'lxf'
}
var obj2 = {
    name:'fxm'
}

// fun(); this == window
fun.call(obj1) //lxf  
fun.call(obj2) //fxm
```

## 34：arguments 

## 35:Date对象
    Date 对象用于处理日期和时间。

## 36:Math 对象
```
Math 对象用于执行数学任务。
注释：Math 对象并不像 Date 和 String 那样是对象的类，因此没有构造函数 Math()，像 Math.sin() 这样的函数只是函数，不是某个对象的方法。您无需创建它，通过把 Math 作为对象使用就可以调用其所有属性和方法。
它不是一个构造函数，它属于一个工具类，不要创建对象，它里边封装了数学运算相关的属性和方法
abs()  计算绝对值
cell() 向上取整
floor() 向下取整
round() 把数四舍五入为最接近的整数。
random()  返回 0 ~ 1 之间的随机数。 
// Math.random(); 生成一个0-1的随机数
// Math.round();四舍五入


// 生成0-10间的随机数


// for (let index = 0; index < 100; index++) {
//     let element = Math.random()*10;
//     // 四舍五入
//     element = Math.round(element)
//     console.log(element);
// }


// 生成 x-y的随机数
// for (let index = 0; index < 100; index++) {
//     let element = Math.random()*20;


//     // 四舍五入
//     element = Math.round(element+1)
//     console.log(element);
// }


// 生成一个从 x-y的随机数 包含x和y
function randomNumber(x, y) {
    return Math.round(Math.random() * (y - x)) + x
}

// 生成 5-55之间的随机数
for (let index = 0; index < 100; index++) {
    let result = randomNumber(5, 10)
    console.log(result);
}
```
## 37:包装类
```在js中为我们提供了三个包装类，通过这三个包装类，可以将基本数据类型的数据转换为对象
String()
● 可以将基本数据类型字符串转换为 String对象
Number()
● 可以将基本数据类型的数值转换为 Number对象
Boolean()
● 可以将基本数据类型的布尔值转换为 Boolean对象
注意
我们在实际应用中不会使用基本数据类型的对象
如果使用基本数据类型的对象，在做一些比较式，可能会带来一些不可预期的结果
这三个包装类，解析器会在底层进行使用
比如：
  ○ var n = 123;
  ○ let result = n.toString();  // 这里解析器会临时 把 n 转成对象 ，所以他能调用 toString()方法
  ○ console.log(result);'123'
  ○ console.log(typeof result); //string
● 方法和属性只能添加给对象，不能添加个基本数据类型
  ○ 当我们对一些基本数据类型的值去调用属性和方法时
    ■ 解析器会临时使用包装类将其转换为对象，然后再调用对象的属性和方法
    ■ 调用完成以后，在将其装换为基本数据类型
```
## 38:字符串的方法
```
在底层字符串是以字符数组的形式保存的
let str = 'lxf';
['l','x','f']
console.log(str.length); //3
console.log(str[1]); //x

字符串常用方法
charAt() 返回在指定位置的字符。 
charCodeAt() 返回在指定的位置的字符的 Unicode 编码。 
concat() 连接字符串。 
indexOf() 检索字符串。 
lastIndexOf() 从后向前搜索字符串。 
slice() 提取字符串的片断，并在新的字符串中返回被提取的部分。 
split() 把字符串分割为字符串数组。 
substr() 从起始索引号提取字符串中指定数目的字符。 
substring() 提取字符串中两个指定的索引号之间的字符。 
toLowerCase() 把字符串转换为小写。 
toUpperCase() 把字符串转换为大写。
配合正则使用
match()找到一个或多个正则表达式的匹配。 
replace() 替换与正则表达式匹配的子串。 
search() 检索与正则表达式相匹配的值。

正则表达式
语法：var 变量 = new RegExp('正则表达式'，'匹配模式')

/**
 * 13910358567
 * 
 * 1-第一位以1开头
 * 2-第二位以3开头
 * 之后无限制
 */
var phoneNum = '13410358567';


var reg = /^1([3-9])(\d{9,9})$/;


var result = reg.test(phoneNum);


console.log(result); //true
// 检查字符串中是否有 .  任意字符-查找单个字符，除了换行和行结束符。 
var str = '1111asd12sa.asdas.asdas.qqwq.sss.as';
var strReg = /\./g;
var result = strReg.test(str);


console.log(result);

//在构造函数中，由于它的参数是一个字符串，而\是字符串的转义字符
	// 如果要使用\ 则需要使用\\来代替

strReg('\\.')
// 去除字符串的前后多余空格
var str = '        l x  f      ';


// 看看对象原型上有哪些方法
// console.log(String.prototype);
// 方式一
// str = str.trim();
// console.log(str);


// * 匹配任何包含零个或多个 n 的字符串。
// + 匹配任何包含至少一个 n 的字符串。s

var strReg = /(^\s*|\s*$)/g;
console.log(str.replace(strReg,''));
// 检测邮件的正则表达式
var email = 'xli20689.ranxing@gmail.com.ccc';
/**
 * 分析邮箱的规则
 * 
 * xli20689                                     .ranxing                @    gmail      .       com   .cn
 * 
 * 开头可以是任意数字、字母、_ 开头 最少3位    可有可无部分任意字母数字_   @    任意字母数字       任意字母2-5位    任意字母2-5位
 * 
 * (\w{3,})                                     (\.\w+)*            (@)     ([A-z0-9])+  (\.)   ([A-z]{2,})+
 * 
 */

email = 'xli20689@gmail.aa';
let emailReg = /^(\w{3,})(\.\w+)*@([A-z0-9])+(\.[A-z]{2,})+$/;
let result = emailReg.test(email);
console.log(result);

企业级的程序里的校验正则
^\\s*\\w+(?:\\.{0,1}[\\w-]+)*@[a-zA-Z0-9]+(?:[-.][a-zA-Z0-9]+)*\\.[a-zA-Z]+\\s*$
合法E-mail地址： 
 1. 必须包含一个并且只有一个符号“@” 
 2. 第一个字符不得是“@”或者“.” 
 3. 不允许出现“@.”或者.@ 
 4. 结尾不得是字符“@”或者“.” 
 5. 允许“@”前的字符中出现“＋” 
 6. 不允许“＋”在最前面，或者“＋@” 
^(\w+((-\w+)|(\.\w+))*)\+\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z0-9]+$ 
```
## 39:DOM
```什么是 DOM？
DOM 是 W3C（万维网联盟）的标准。
DOM 定义了访问 HTML 和 XML 文档的标准：
“W3C 文档对象模型 （DOM） 是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式。”
W3C DOM 标准被分为 3 个不同的部分：
● 核心 DOM - 针对任何结构化文档的标准模型
● XML DOM - 针对 XML 文档的标准模型
● HTML DOM - 针对 HTML 文档的标准模型
编者注：DOM 是 Document Object Model（文档对象模型）的缩写。
什么是 XML DOM？
XML DOM 定义了所有 XML 元素的对象和属性，以及访问它们的方法。
如果您需要学习 XML DOM，请访问我们的 XML DOM 教程。
什么是 HTML DOM？
HTML DOM 是：
● HTML 的标准对象模型
● HTML 的标准编程接口
● W3C 标准
HTML DOM 定义了所有 HTML 元素的对象和属性，以及访问它们的方法。
换言之，HTML DOM 是关于如何获取、修改、添加或删除 HTML 元素的标准。

// <bottom id="search"> 查询 </bottom>

let oBtn = document.getElementById('search')
console.log(oBtn.innerHTML); // 可通过节点的 innerHTML 属性来访问文本节点的值。
oBtn.innerHTML = 'hello'  // 修改文本节点的值
一些 DOM 对象方法
这里提供一些您将在本教程中学到的常用方法：
方法	描述
getElementById()	返回带有指定 ID 的元素。
getElementsByTagName()	返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。
getElementsByClassName()	返回包含带有指定类名的所有元素的节点列表。
getElementsByName()	通过name属性获取一组元素节点对象 
appendChild()	把新的子节点添加到指定节点。
removeChild()	删除子节点。
replaceChild()	替换子节点。
insertBefore()	在指定的子节点前面插入新的子节点。
createAttribute()	创建属性节点。
createElement()	创建元素节点。
createTextNode()	创建文本节点。
getAttribute()	返回指定的属性值。
setAttribute()	把指定属性设置或修改为指定的值。
HTML DOM 属性
属性是节点（HTML 元素）的值，您能够获取或设置。

innerHTML属性
● 获取元素内容的最简单方法是使用 innerHTML 属性。
nodeName 属性
nodeValue 属性
nodeType 属性
HTML DOM 事件对象
Event 对象
Event 对象代表事件的状态，比如事件在其中发生的元素、键盘按键的状态、鼠标的位置、鼠标按钮的状态。
事件通常与函数结合使用，函数不会在事件发生前被执行！
切换图片练习
// 切换图片
window.onload = function () {
    let imgArr = [
        './img/1.jpeg',
        './img/2.jpeg',
        './img/3.jpeg',
        './img/4.jpeg',
        './img/5.jpg',
        './img/6.jpeg',
    ];

    // 获取按钮
    let oBtnPrve = document.getElementById('btn_prve');
    let oBtnNext = document.getElementById('btn_next');
    // 获取图片
    let imgElement = document.getElementsByTagName('img')[0];
    // 当前展示的图的索引
    let iNow = 0;
    // 初始化图片地址为数组第一位
    imgElement.src = imgArr[iNow];
    // 初始化描述文字
    document.getElementById('miaoshu').innerHTML = `总数为${imgArr.length},当前为第${iNow + 1}张`


    oBtnPrve.onclick = function () {
        // alert('上一张')
        // imgElement.src = '';
        iNow--;
        if (iNow < 0) {
            iNow = imgArr.length - 1;
        }
        // 更新展示和描述
        imgElement.src = imgArr[iNow];
        document.getElementById('miaoshu').innerHTML = `总数为${imgArr.length},当前为第${iNow + 1}张`
    };


    oBtnNext.onclick = function () {
        // alert('下一张');
        // imgElement.src = '';
        iNow++;
        if (iNow > imgArr.length - 1) {
            iNow = 0;
        }
        // 更新展示和描述
        imgElement.src = imgArr[iNow];
        document.getElementById('miaoshu').innerHTML = `总数为${imgArr.length},当前为第${iNow + 1}张`
    };
}

// HTML部分
  
 <div id="imgPic">
      <p id="miaoshu"></p>
  
      <img src="https://img2.baidu.com/it/u=1395980100,2999837177&fm=253&fmt=auto&app=120&f=JPEG?w=1200&h=675" alt="风景">

      <button id="btn_prve">上一张</button>
      <button id="btn_next">下一张</button>
  </div>
更多DOM/BOM/JS对象文档 
https://www.w3school.com.cn/jsref/obj_window.asp
https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelectorAll

https://developer.mozilla.org/zh-CN/docs/Web/API/Window/getComputedStyle
```

获取元素样式
===
```var imgPic = document.querySelector('#imgPic');
imgPic.style 这种方式只能获取元素的行内样式，和设置行内样式 imgPic.style.widht='200px'

currentStyle
● 语法： 元素.currentStyle.样式名 
● 属性时ie 独有的，不考虑使用

Window.getComputedStyle()  获取元素样式，样式表里的样式  ie9+
Window.getComputedStyle()方法返回一个对象，该对象在应用活动样式表并解析这些值可能包含的任何基本计算后报告元素的所有 CSS 属性的值。私有的 CSS 属性值可以通过对象提供的 API 或通过简单地使用 CSS 属性名称进行索引来访问。
console.log(window.getComputedStyle(imgPic,null).width); 也可以直接.样式名方式获取
function getTheStyle(){
    	let elem = document.getElementById("elem-container");
    	let theCSSprop = window.getComputedStyle(elem,null).getPropertyValue("height");
    	document.getElementById("output").innerHTML = theCSSprop;
   }
 getTheStyle();

currentStyle和getComputedStyle() 读取到和样式都是只读的，不能修改，如果修改必须通过 style属性或者setProperty()， 相对来说 元素.style.属性名 = value的方式更便捷
事件对象：
● 当事件的响应函数被触发时，浏览器每次都会将一个事件对象作为实参传递进响应函数
● e , event
● https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent/clientX
```
```事件对象的兼容性处理
event =  event || window.event

https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent/pageX
event.clientXevent.clientY   它提供事件发生时的应用客户端的可视区域坐标 ,ie8中 +滚动距离
event.pageXevent.pageY  返回的相对于整个文档的坐标  ，不兼容ie8 

1. chrome 中有认为滚动距离是，document.body.scrollTop，
2. ie8和火狐中认为滚动距离是，document.documentElement.scrollTop   documentElement= html
兼容写法：var st = document.body.scrollTop || document.documentElement.scrollTop;

取消冒泡的两种方式
https://developer.mozilla.org/zh-CN/docs/Web/API/Event/stopPropagation
https://developer.mozilla.org/zh-CN/docs/Web/API/Event/cancelBubble
```
```
事件委派
● 冒泡的应用
● 值将事件统一绑定给元素的共同的祖先元素，这样后代元素中的事件触发时，会一直冒泡到祖先元素从而通过祖先元素的相应函数来处理事件。
● 事件委派，利用了冒泡。通过委派可以减少事件绑定的次数，提高程序的性能
var u1 = document.getElementById('u1');

var reg = /^link$/;
// target 返回触发此事件的元素（事件的目标节点）。 
u1.onclick = function (event) {
    event = event || window.event;

    console.log(event.target); // className ie8不支持 
    if (reg.test(event.target.className)) {
        // console.log('111');
        alert('触发')
    }
}



<ul id="u1">
    <li><a href="javascript:;">1</a></li>
    <li><a href="javascript:;">1</a></li>
    <li><a href="javascript:;">1</a></li>
    <li><a href="javascript:;">1</a></li>
    <li><a href="javascript:;">1</a></li>
    <li><a href="javascript:;">1</a></li>
</ul>
https://developer.mozilla.org/zh-CN/docs/Web/API/EventTarget/addEventListener

事件的传播 分为捕获和冒泡
ie8+才有，了解内容
一般都是冒泡的方式触发事件，如果想在捕获的时候就触发事件 在addEventListener()方法中第三个时参数设置为true
addEventListener('click', function () { },true);
// 这种绑定函数的模式，后边的相应函数会覆盖前边的相应函数
u1.onclick = function () {
    console.log('1111');
}
u1.onclick = function () {
    console.log('2222');
}


//如何绑定多个,按顺序执行，正序执行
u1.addEventListener('click', function () {
    console.log('333');
},false);
u1.addEventListener('click', function () {
    console.log('444');
},false)

//addEventListener ie不支持

//ie中 5到10 使用 attachEvent();  区别 是用 onclick , 倒序执行
u1.attachEvent('onclick', function () {
    console.log('555');
});
u1.attachEvent('onclick', function () {
    console.log('666');
});
//addEventListener()中this，是邦迪事件的对象
//attachEvent() 中的 this， 是window


/**
 * 
 * @param {事件对象} oELe 
 * @param {事件类型} eType 
 * @param {回调函数} callback 
 */
function bingTypeEvents(oELe, eType, callback) {
    if (oELe.addEventListener) {
        oELe.addEventListener(eType, callback, false);
        // console.log(this);
    } else {
        oELe.attachEvent('on' + eType + '', function () {
            // 在匿名函数中 调用 改变 this ，指向调用函数的对象
            callback.call(oELe,null);
        });
        // console.log(this);
    }
}


bingTypeEvents(u1, 'click', function () {
    console.log('1');
});
bingTypeEvents(u1, 'click', function () {
    console.log('2');
});
bingTypeEvents(u1, 'click', function () {
    console.log('3');
    alert(this)
});
```