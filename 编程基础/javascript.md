# Javascript

## 1. 内置对象

### JS的对象分为内置对象和自定义对象

### 1.1 顶层函数（全局函数）

| 返回值类型 | 函数名称                   | 说明                                                         |
| ---------- | -------------------------- | ------------------------------------------------------------ |
| String     | decodeURI(String)          | 解码某个编码的URI                                            |
| String     | decodeURIComponent(String) | 解码一个编码的URI组件                                        |
| String     | encodeURI(String)          | 把字符串编码为URI                                            |
| String     | encodeURIComponent(String) | 把字符串编码为URI组件                                        |
| String     | escape(String)             | 对字符串进行编码                                             |
| String     | unescape(String)           | 对由escape()编码的字符串进行解码                             |
| String     | eval(String)               | 计算js字符串，并将其作为脚本执行                             |
| boolean    | isFinite(value)            | 检查某个值是否是无穷大的数，是则返回true，不是则返回false    |
| boolean    | isNaN(value)               | 检查某个值是否是非数字，是数字返回false，否则返回true        |
| int        | Number(Object)             | 把对象的值转换成数字，Boolean的false为0，true为1；字符串需要连续的数字，否则返回false；如果是Date对象，那么返回1970年1月1日到今天的毫秒数 |
| flaot      | parseFloat(String)         | 解析字符串并返回一个浮点数，该函数指定字符串中的首个字符是否是数字。如果是就对字符串进行解析，直达字符串的末端为止，然后返回该数字，而不是作为字符串。如"34 56"和"34good"的返回值都是34.如果字符串的第一个字符不能被转换成数字，那么parseFloat()会返回NaN |
| int        | parseInt(String, radix)    | 解析一个字符串并返回一个整数。当参数radix的值为0，或没有设置该值时，parseInt会根据字符串来判断数字的基数。0x-十六进制； 0-八进制； 1~9-十进制 |
| String     | String(Object)             | 把对象的值转换为字符串，与字符串对象的toString()方法值一样   |



### 1.2 JS内置对象Date

描述： 创建Date实例用来处理日期和时间。Date对象基于1970年1月1日起的毫秒数。

```js
var now = new Date();
console.log(now.valueOf()); // 获取距1970年1月1日的毫秒数
// Date构造函数的参数
1. new Date(1498099000356)
2. 日期格式字符串 new Date("2020-12-1");
3. 年月日 new Date(2020,12,1)
```

获取日期的毫秒格式：

```js
var now = new Date();
console.log(now.valueOf());

var now = Date.now();

var now = +new Date();
```

日期格式化方法：

```js
toString() // 转换成字符串
valueOf() // 获取毫秒数
// 下面格式化日期的方法，在不同的浏览器可能变现不一致，一般不用
toDateString()
toTimeString()
toLocaleDateString()
toLocaleTimeString()
```

获取日期指定部分

```js
1. getFullYear() // 返回四位数的年份
2. getMonth() // 返回日期中的月份，返回值0-11
3. getDate() // 返回月份中的天数
4. getDay() // 返回星期，返回值0-6
5. getHours() // 返回小时
6. getMinutes() // 返回分钟
7. getSeconds() // 返回秒
8. getTime() // 返回表示日期的毫秒数
```

设置年月日时间

```js
1. setFullYear(year) // 设置四位数的年份
2. setMonth(month) // 设置日期中的月份，从0开始，0表示1月份
3. setDate(day) // 设置日期
4. setHours() // 设置小时
5. setMinutes() // 设置分钟
6. setSeconds() // 设置秒
7. setTime() // 以毫秒设置日期，会改变整个日期
```





### 1.3 JS内置对象String

**字符串不可变：**

```javascript
var str = "abc";
str = "hello";
// 当重新给str赋值的时候，常量"abc"并不会被修改，依然还在内存里。
// 重新给字符串赋值，会重新再内存中开辟空间，这个特点就是字符串的不可变
// 由于字符串不可变，在大量拼接字符串的时候会有效率问题
```

**创建字符串对象：**

```js
var str = new String("hello world");
console.log(str.length); // 获取字符串的个数
```

**注意：字符串的所有方法，都不会修改字符串本身（字符串时不可变的），操作完成后会返回一个新的字符串**

```javascript
// 1. 字符串方法
charAt() // 获取指定位置出的字符
charCodeAt() // 获取指定位置处字符的ASCII编码
str[0]  // html5、IE8+支持  和  charAt()等效

// 2. 字符串操作方法
concat() // 拼接字符串，等效于+
slice() // 从start未知开始，截取到end位置
substring() // 从start未知开始，截取到end位置
substr() // 从start位置开始，截取length个字符

// 3. 位置方法
indexOf() // 返回指定内容在元字符串中的位置
lastIndexOf() // 从后往前找，执照第一个匹配上的位置

// 4. 去除空白
trim() // 只能取出字符串前后的空白

// 5. 大小写转换方法
to(Locale)UpperCase() // 转换成大写
to(Locale)LowerCase() // 转换成小写

// 6. 其他
search() 
replace()
split()
formCharCode() // String.fromCharCode(101,102,103) 将ASCII码转换成字符串
```



### 1.4 JS内置对象Math

Math对象不是构造函数，它具有数学常用函数的属性和方法，都是以静态成员的方式提供数学相关的运算。

```javascript
Math.PI // 圆周率
Math.random() // 生成随机数
Math.floor() // 向上取整/向下取整
Math.round() // 取整，四舍五入
Math.abs() // 绝对值
Math.max()  Math.min() // 最大值/最小值
math.sin()  Math.cos() // 正弦/ 余弦
Math.power() Math.sqrt() // 求指数次幂 / 求i平方根
```

随机生成颜色

```js
rgb(Math.floor(Math.random()*255),Math.floor(Math.random()*255),Math.floor(Math.random()*255))
```



### 1.5 JS内置对象Array

数组（Array）是一个有序的数据集合。

1. 数组对象的创建

   ```js
   var arr1 = new Array();
   var arr2 = new Array(size);
   var arr3 = new Array(element1, element2, element3,...);
   var arr4 = [element1, element2,...];
   ```


2. Array.isArray(对象) --> 判断这个对象是不是数组

```js
Array.isArray([])
```

3. Array.concat(数组,数组,数组,.....) 组合成一个新的数组

```js
var arr1 = [1,2,3];
var arr2 = [4,5,6];
console.log(arr1.concat(arr2));
```

4. Array.every(函数) 

是对数组中每一项运行给定函数，如果该函数对每一项返回true，则返回true。every从第一个开始，一旦有一个不符合条件，则不会继续迭代下去。

5. Array.some(函数) 

是对数组中的每一项运行给定的函数，如果该函数对任一项返回true，则返回true。some一直在找符合条件的值，一旦找到，则不会继续迭代下去。

6. Array.filter(函数) 

返回的是数组中每一个元素都符合条件的元素，组成了一个新的元素。

7. Array.push()
8. Array.pop()
9. Array.shift()
10. Array.unshift()
11. Array.forEach()
12. Array.map()
13. Array.indexOf()
14. Array.join("字符串")
15. Array.reverse()
16. Array.sort()
17. Array.slice()
18. Array.splice()



### 1.6 JS内置对象RegExp正则表达式

- 字面量

```js
var reg = /\d+/g;
console.log(reg.test("12345")); // true
```

- 构造函数

```js
var reg2 = new RegExp("\\d+","g");
console.log(reg2.test("12345656"));
```



#### `修饰符`

- i 忽略大小写模式
- m 多行模式
- g 全局模式

























## 2. typeof

七种原始类型（基本类型）：Boolean、Null、Undefined、Number、BigInt、String、Symbol和Object。

基本类型是一种既非对象也无方法的数据。多数情况下，基本类型直接就代表了最底层的语言实现。

```js
var bar = "bar";
bar[0] = "c";
console.log(bar[0]); // b
console.log(bar); // bar
```

| 类型         | 结果           |
| ------------ | -------------- |
| Undefined    | "undefined"    |
| Null         | "object"       |
| Boolean      | "boolean"      |
| Number       | "number"       |
| BigInt       | "bigint"       |
| String       | "string"       |
| Symbol       | "symbol"       |
| 宿主对象     | 取决于具体实现 |
| Function对象 | "function"     |
| 其他任何对象 | "object"       |

```js
var s_obj = new String("123");
console.log(typeof s_obj); // object
console.log(typeof String); // function

// s_obj.__proto__ === String.prototype;
// String.prototype.__proto__ === Object.prototype;
Function.prototype.__proto__ === Object.prototype;
```



## 3. instanceof

通常用typeof来判断基本类型；用instanceof来判断引用类型。

**instanceof运算符是用来检测某个实例对象的原型链上是否存在构造函数的prototype属性。**

>注意构造器Function，他是唯一一个prototype和\__proto\__指向相同的对象。注意Object(),他是由function生成的，所以它的\__proto\__属性指向了function的构造器Function的原型Function.prototype.

```js
console.log(String instanceof String); // false
console.log(String instanceof Object); // true
console.log(Object instanceof Object); // true
console.log(Function instanceof Function); // true
console.log(Function instanceof Object); // true
```

```js
function Foo() {}
function BFoo() {}
Foo.prototype = new BFoo();
console.log(Foo instanceof Function); // true
console.log(Foo instanceof Foo); // false
```











## 4. 类型转换





## 5. new





## 6. this





## 7. 闭包



## 8. 原型与原型链



## 9. 执行上下文



## 10. 执行环境与作用域





## 11. 深浅拷贝

* 深拷贝

  

* 浅拷贝



## 12. 防抖与节流

* 原理掌握

  

* 实践





## 13. 模块化 

* CommonJS

  

* AMD





## 14. 继承

* 原型链继承

  

* 借助构造函数继承

  

* 组合继承

  

* 原型式继承

  

* 寄生式继承

  

* 寄生组合式继承

  

* ES6的class继承









## 15. call、bind、apply

* 原理

  

* 如何手动写一个bind、call函数





## 16. let、const、var





## 17. Promise的原理和实践





## 18. Generator原理和实践



## 19. Async/Await



## 20. Map、Set、FlatMap、FlatSet





## 21. Proxy





## 22. 0.1+0.2 != 0.3



































































