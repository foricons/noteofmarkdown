# JavaScript  

## JS的编写的位置  
```html  
<!-- 1.可以编写到标签的指定属性中   -->
<button onclick="alert('hello');">我是按钮</button>  
<a href="javascript:alert('aaa');">超链接</a>  

<script type="text/javascript">  
// 2.可以编写到script标签中  
//编写js代码  
</script>  

<!-- 3.可以将代码编写到外部的js文件中，然后通过标签将其引入 （script标签一旦用于引入外部文件了，就不能在编写代码了，即使编写了浏览器也会忽略  ,如果需要则可以在创建一个新的script标签用于编写内部代码 ）   -->
<script type="text/javascript" src="文件路径"></script>  
```
## 输出语句  
```javascript  
alert("要输出的内容");  // 该语句会在浏览器窗口中弹出一个警告框 
document.write("要输出的内容");  // 该内容将会被写到body标签中，并在页面中显示  
console.log("要输出的内容");  // 该内容会被写到开发者工具的控制台中  
``` 

## 字面量和变量  
### 变量  
规范：  
1.标识符中可以含有字母、数字、_、$  
2.标识符不能以数字开头  
3.标识符不能是JS中的关键字和保留字  
4.标识符一般采用驼峰命名法  

# 数据类型  

## 六种数据类型  

 5个基本数据类型 
 String 字符串  
 Number 数值  
 Boolean 布尔值  
 Null 空值  
 Undefined 未定义  

 object
 Object 对象  

### 2.Number 数值  
 **JS中所有的整数和浮点数都是Number类型**  （包括NaN 和 Infinity）
最大能表示的值：Number.MAX_VALUE=	1.7976931348623157e+308  

 特殊的数字：能赋值给变量  
	Infinity 正无穷 a = Infinity ,能赋值  
	-Infinity 负无穷  
	NaN 非法数字（Not A Number）  
 其他进制的数字的表示：  
0b 开头表示二进制，但是不是所有的浏览器都支持  
0 开头表示八进制  
0x 开头表示十六进制   

### 4.Null 空值  
 空值专门用来表示为空的对象，Null类型的值只有一个  
 null  
 使用typeof检查一个Null类型的值时会返回"object"  

###  5.Undefined 未定义  ： **如果声明一个变量但是没有为变量赋值此时变量的值就是undefined**  

## 类型转换  
### 方式一（强制类型转换）
 **调用被转换数据的toString()方法**  （不适用于null和undefined）

 ### 方式二（强制类型转换）
 **调用String() Number() Boolean()函数**
1. String =>String

2. Number => 
 字符串 > 数字    
	 如果字符串是一个合法的数字，则直接转换为对应的数字  
	 如果字符串是一个非法的数字，则转换为NaN  
	 如果是一个空串或纯空格的字符串，则转换为0  
 布尔值 > 数字     
	 true转换为1  
	 false转换为0  
 空值 > 数字     
	 null转换为0  
 未定义 > 数字    
	 undefined 转换为NaN  

3. Boolean =>
 字符串 > 布尔  
	 除了空串其余全是true  
	  
 数值 > 布尔  
	 除了0和NaN其余的全是true  
	  
 null、undefined > 布尔  
	 都是false  
	  
 对象 > 布尔  
	 都是true  

 ### 方式三（隐式的类型转换）: 

 1. 为任意的数据类型 +""**  =>String
 2. 为任意的数据类型做两次非运算，即可将其转换为布尔值** 
```javascript  
var a = "hello";  
a = !!a; //true  
```
 3. 使用一元的+来进行隐式的类型转换    
 例子：  
```javascript  
var a = "123";  
a = +a;  
```
### 方式四（Number的强制类型转换）：  
 调用parseInt()或parseFloat()   这两个函数专门用来将一个字符串转换为数字的  

如果对非String使用parseInt()或parseFloat()，它会**先将其转换为String**然后在操作 parseInt()  
 可以将**一个字符串中的有效的整数位**提取出来，并转换为Number    
 例子：  
 ```javascript  
var a = "123.456px";  
a = parseInt(a); //123  
 ```
 如果需要可以在parseInt()中指定一个第二个参数，来指定进制parseFloat()可以将一个**字符串中的有效的小数位**提取出来，并转换为Number    
 例子：  
```javascript  
var a = "123.456px";  
a = parseFloat(a); //123.456  
```

# 基础语法  

**===**  
	 **全等**，判断左右两个值是否全等，它和相等类似，只不过它不会进行自动的类型转换，  
		如果两个值的类型不同，则直接返回false  
		  
!==  
	 **不全等**，和不等类似，但是它不会进行自动的类型转换，如果两个值的类型不同，它会直接返回true  
	  
特殊的值：  
	 null和undefined  
		 由于undefined衍生自null，所以**null == undefined** 会返回true。  
			但是 null === undefined 会返回false。  
**NaN**  
	 NaN不与任何值相等，报告它自身 NaN == NaN //false  
	  
 判断一个值是否是NaN  
	 使用isNaN()函数  

## 对象的分类：  
创建对象  
 
```javascript
	 var obj = new Object(); // 方式一：
	 var obj = {}; //方式二： 
var obj = {  
    属性名:属性值,  
    属性名:属性值,  
    属性名:属性值,  
    属性名:属性值  //如果属性名是特殊的，需要带引号
}
```
**向对象中添加属性**  
 语法：  	对象.属性名 = 属性值;  	**对象["属性名"] = 属性值;**	//这种方式能够使用特殊的属性名  
 **对象的属性名没有任何要求，不需要遵守标识符的规范，但是在开发中，尽量按照标识符的要求去写。**  
属性值也可以任意的数据类型。  
 
读取对象中的属性  :	对象.属性名  /	对象["属性名"] //"属性名"可以使字符串常量，也可以是字符串变量  
 如果读取一个对象中没有的属性，它不会报错，而是返回一个undefined  

删除对象中的属性*: delete 对象.属性名  / delete 对象["属性名"]  

## 遍历  

1. **使用in检查对象中是否含有指定属性**  
 语法："属性名" in 对象  :	 如果在对象中含有该属性，则返回true  ;		如果没有则返回false  
```javascript  
const car = { make: 'Honda', model: 'Accord', year: 1998 };
console.log('make' in car);
// expected output: true
```

2. 循环遍历对象自身的和继承的可枚举属性(不含Symbol属性).  
```javascript  
var obj = {'0':'a','1':'b','2':'c'};    
for(var i in obj) {  //i中存储的是obj属性的name
     console.log(i,":",obj[i]);  
}  
```


## 函数（Function）	  

**函数也是一个对象，也具有普通对象的功能（能有属性）**  
函数中可以封装一些代码，在需要的时候可以去调用函数来执行这些代码  
使用typeof检查一个函数时会返回function  
创建函数  
1. 函数声明 
```javascript
function 函数名([形参1,形参2...形参N]){  
语句...  
}  
```
2. 函数表达式
```javascript
var 函数名 = function([形参1,形参2...形参N]){  
语句...  
};  
```
调用函数  : 语法：函数对象([实参1,实参2...实参N]);  :	fun() sum() alert() Number() parseInt()  

**立即执行函数**  
函数定义完，立即被调用，这种函数叫做立即执行函数  
立即执行函数往往只会执行一次
```javascript
(function(a,b){  
    console.log("a = "+a);  
    console.log("b = "+b);  
})(123,456); 
```  
**如果实参的数量大于形参，多余实参将不会赋值，**  
**如果实参的数量小于形参，则没有对应实参的形参将会赋值undefined**  
**如果return后不跟值，或者是不写return则函数默认返回undefined。**  

**方法（method）**  
 可以将一个函数设置为一个对象的属性，  
	当一个对象的属性是一个函数时，  
		我们称这个函数是该对象的方法。  
 对象.方法名();  
 函数名()  

## 作用域  
1. **全局作用域中有一个全局对象window，window对象由浏览器提供，可以在页面中直接使用，它代表的是整个的浏览器的窗口。在全局作用域中创建的变量都会作为window对象的属性保存**  

2. **变量的声明提前**  
	 在全局作用域中，使用**var关键字声明的变量会在所有的代码执行之前被声明，但是不会赋值。**  
		所以我们可以在变量声明前使用变量。但是不使用var关键字声明的变量不会被声明提前。  
	 在函数作用域中，也具有该特性，使用var关键字声明的变量会在函数所有的代码执行前被声明，  
		如果没有使用var关键字声明变量，则变量会变成全局变量  
		  
3. **函数的声明提前**  
	 在全局作用域中，使用**函数声明创建的函数（function fun(){}）,会在所有的代码执行之前被创建**，  

## this（上下文对象）
指向当前对象  

this的不同的情况：  
1.以函数的形式调用时，this是window  
2.以方法的形式调用时，this就是调用方法的对象  
3.以构造函数的形式调用时，this就是新创建的对象  
this（调用函数的那个对象）  
 this是函数的上下文对象，根据函数的调用方式不同会执向不同的对象  
	1.以函数的形式调用时，this是window  
	2.以方法的形式调用时，this是调用方法的对象  
	3.以构造函数的形式调用时，this是新建的那个对象  
	4.使用call和apply调用时，this是指定的那个对象  
	5.在全局作用域中this代表window  

## 构造函数  

构造函数是专门用来创建对象的函数  
**一个构造函数我们也可以称为一个类**  

例子：  

```javascript  
function Person(name , age , gender){  
    this.name = name;  
    this.age = age;  
    this.gender = gender;  
    this.sayName = function(){  
        alert(this.name);  
    };  
}  
var per=new Person("123",18,"nan");
per.sayName();
``` 
**instanceof 用来检查一个对象是否是一个类的实例**  
 语法：对象 instanceof 构造函数  
	 如果该对象时构造函数的实例，则返回true，否则返回false  
	 **Object是所有对象的祖先，所以任何对象和Object做instanceof都会返回true**  
	 `boolean isPerInstanceOfPerson=per instanceof Person//判断per是否是Person的实例`	  

## 原型（prototype）  

 创建一个函数以后，**解析器都会默认在函数中添加一个数prototype**  
	prototype属性指向的是一个对象，这个对象我们称为原型对象。  
 当函数作为构造函数使用，**它所创建的对象中都会有一个隐含的属性执行该原型对象。**  

```javascript  
这个隐含的属性可以通过对象.__proto__来访问。  
```

**原型对象就相当于一个公共的区域，凡是通过同一个构造函数创建的对象他们通常都可以访问到相同的原型对象。**  
	我们可以将对象中共有的属性和方法统一添加到原型对象中，  
		这样我们只需要添加一次，就可以使所有的对象都可以使用。  
 当我们去访问对象的一个属性或调用对象的一个方法时，它会先自身中寻找，  
	如果在自身中找到了，则直接使用。  
	如果没有找到，则去原型对象中寻找，如果找到了则使用，  
	**如果没有找到，则去原型的原型中寻找，**依此类推。直到找到Object的原型为止，Object的原型的原型为null，  
	如果依然没有找到则返回undefined  
 **hasOwnProperty()**  
	 这个方法可以用来检查**对象自身中**是否含有某个属性  
	 语法：对象.hasOwnProperty("属性名")  

## toString方法  

当我们直接在页面中打印一个对象时，事件上是输出的对象的toString()方法的返回值  

如果我们希望在输出对象时不输出[object Object]，可以为对象添加一个toString()方法	  

```javascript  
//修改Person原型的toString  
Person.prototype.toString = function(){  
	return "Person[name="+this.name+",age="+this.age+",gender="+this.gender+"]";  
};  
```

  

## 垃圾回收（GC）  
将不再使用的对象设置null即可  

# 数组（Array）  
## 数组的操作：  

 创建数组  

```javascript  
var arr = new Array();  
var arr = [];  
//创建数组时直接添加元素 
var arr = [123,"hello",true,null];  
var arr=new Array(10,20,30);
```

向数组中添加元素  :数组对象[索引] = 值;  
```javascript  
arr[0] = 123;  
arr[1] = "hello";  
``` 
获取长度：数组.length  
	length获取到的是数组的最大索引+1  
	对于连续的数组，length获取到的就是数组中元素的个数  
修改数组的长度  数组.length = 新长度  
	如果修改后的length大于原长度，则多出的部分会空出来  
	如果修改后的length小于原长度，则原数组中多出的元素会被删除  
向数组的最后添加元素  
	数组[数组.length] = 值;  
		  

## 数组的方法  
[https://www.runoob.com/jsref/jsref-obj-array.html]()

## 遍历数组  

 遍历数组就是将数组中元素都获取到  
 一般情况我们都是使用for循环来遍历数组
```javascript
var arr=[1,2,3,4,5,6];
for(var i=0 ; i<arr.length ; i++){  
    //数组[i]  
}  
//forEach()方法需要一个回调函数作为参数;
//自动传递的三个函数，按顺序分别是当前元素的：value、index、被遍历的对象
arr.forEach(function(value , index , obj){  
  
});  
```
## 函数的属性和方法
call()  
apply()  
 **这两个方法都是函数对象的方法需要通过函数对象来调用**  
 通过两个方法可以直接调用函数，并且**可以通过第一个实参来指定函数中this**  
 不同的是call是直接传递函数的实参而apply需要将实参封装到一个数组中传递 
  
**arguments**  
**arguments是传递的实参的封装**
 **arguments中有一个属性callee表示当前执行的函数对象**  


## Date  
创建对象  
```javascript
// 创建一个当前的时间对象  
 var d = new Date();  

// 创建一个指定的时间对象  
	var f = new Date("月/日/年 时:分:秒");  //严格按照格式顺序
```
方法：  
[https://www.runoob.com/jsref/jsref-tutorial.html]()

## Math			  

Math属于一个工具类，它不需要我们创建对象，它里边封装了属性运算相关的常量和方法  
我们可以直接使用它来进行数学运算相关的操作  
方法：  
[https://www.runoob.com/jsref/jsref-tutorial.html]()

# 常用类和方法  

## 包装类  

在JS中为我们提供了**三个包装类：**  
String() Boolean() Number()  
 通过这三个包装类可以创建基本数据类型的对象  
例子：
```javascript
var num = new Number(2);  
var str = new String("hello");  
var bool = new Boolean(true); 
```
但是在实际应用中千万不要这么干。  

当我们去操作一个基本数据类型的属性和方法时，  
**解析器会临时将其转换为对应的包装类，然后再去操作属性和方法，**  
操作完成以后再将这个临时对象进行销毁。  

## 字符串的相关的方法  

使用ES6中的字符串新方法  

 **String.prototype.padStart(maxLength, fillString='')** 或 **String.prototype.padEnd(maxLength, fillString='')**来填充字符串；  
[https://www.runoob.com/jsref/jsref-tutorial.html]()


### 正则表达相关方法  
[https://www.runoob.com/jsref/jsref-obj-regexp.html]()
 ```javascript
//创建正则表达式
//方法1
 var reg = new RegExp("正则","匹配模式");// 注意：使用构造函数时，由于它的参数是一个字符串，而\是字符串中转义字符，如果要使用\则需要使用\\来代替  
//方法2
 var reg = /正则表达式/匹配模式// （匹配模式可以多个一起写：/gi）  
/*匹配模式：
i	执行对大小写不敏感的匹配。
g	执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）
m	执行多行匹配。
以match为例：默认情况下我们的match只会找到第一个符合要求的内容，找到以后就停止检索；设置正则表达式为全局匹配模式后，就会匹配到所有的内容；可以为一个正则表达式设置多个匹配模式，且顺序无所谓 
*/
//RegExp 对象方法
//1、 exec	检索字符串中指定的值。返回找到的值，并确定其位置。
//2、 test	检索字符串中指定的值。返回 true 或 false。
//3、 toString	返回正则表达式的字符串。
// 支持正则表达式的 String 对象的方法
// search	如果搜索到指定内容，则会返回第一次出现的索引，如果没有搜索到返回1
// match	可以根据正则表达式，从一个字符串中将符合条件的内容提取出来
// replace	替换与正则表达式匹配的子串。
// split	把字符串以正则匹配到的字符分割为字符串数组。
var result=reg.test("strings");
```



# DOM  
Document Object Model  
文档对象模型，通过DOM可以来任意来修改网页中各个内容  
文档  
 文档指的是网页，一个网页就是一个文档  
对象  
 对象指将网页中的每一个节点都转换为对象  
	转换完对象以后，就可以以一种纯面向对象的形式来操作网页了  
模型  
 模型用来表示节点和节点之间的关系，方便操作页面  
节点（Node）  
 节点是构成网页的最基本的单元，网页中的每一个部分都可以称为是一个节点  
 虽然都是节点，但是节点的类型却是不同的  
 常用的节点  
	 文档节点 （Document），代表整个网页  
	 元素节点（Element），代表网页中的标签  
	 属性节点（Attribute），代表标签中的属性  
	 文本节点（Text），代表网页中的文本内容  
	  

## DOM操作  

 DOM查询  
 在网页中浏览器已经为我们提供了**document对象**，  
	**它代表的是整个网页，它是window对象的属性，可以在页面中直接使用。**  
 document查询方法：  
	 根据元素的id属性查询一个元素节点对象：  
		 document.getElementById("id属性值");  
	 根据元素的name属性值查询一组元素节点对象:  
		 document.getElementsByName("name属性值");  
	 根据标签名来查询一组元素节点对象：  
		 document.getElementsByTagName("标签名");  
		  
 元素的属性：  
	 **读取元素的属性：**  
		语法：元素.属性名  
		例子：ele.name    
			  ele.id    
			  ele.value   
			  ele.className  
			注意：class属性不能采用这种方式，  
			**读取class属性时需要使用 元素.classNam**e	   

修改元素的属性：  
	语法：元素.属性名 = 属性值  
	  
 innerHTML  
	 使用该属性可以获取或设置元素内部的HTML代码  

## 事件（Event）  

 事件指的是用户和浏览器之间的交互行为。比如：点击按钮、关闭窗口、鼠标移动。。。  
 我们可以为事件来绑定回调函数来响应事件。  
 绑定事件的方式：  
	1.可以在标签的事件属性中设置相应的JS代码  
		例子：  

```javascript  
<button onclick="js代码。。。">按钮</button>  
```

2.可以通过为对象的指定事件属性设置回调函数的形式来处理事件  
	例子：  

```javascript  
<button id="btn">按钮</button>  
<script>  
    var btn = document.getElementById("btn");  
    btn.onclick = function(){  
  
    };  
</script>  
```

文档的加载  
 浏览器在加载一个页面时，是按照自上向下的顺序加载的，加载一行执行一行。  
 如果将js代码编写到页面的上边，当代码执行时，页面中的DOM对象还没有加载，  
	此时将会无法正常获取到DOM对象，导致DOM操作失败。  
 解决方式一：  
	 可以将js代码编写到body的下边  
	  

```javascript  
<body>  
		<button id="btn">按钮</button>  
  
		<script>  
			var btn = document.getElementById("btn");  
			btn.onclick = function(){  
		  
			};  
	</script>  
</body>  
```

 解决方式二：  
	 将js代码编写到window.onload = function(){}中  
	 window.onload 对应的回调函数会在整个页面加载完毕以后才执行，  
		所以可以确保代码执行时，DOM对象已经加载完毕了		  

```javascript  
<script>  
    window.onload = function(){  
        var btn = document.getElementById("btn");  
        btn.onclick = function(){  
        };  
    };  
</script>	    
```

## DOM查询  

通过具体的元素节点来查询  
元素.getElementsByTagName()  
通过标签名查询当前元素的指定后代元素  

**子节点包括便签元素中的文本，子元素自包含标签元素**  

元素.childNodes  
 获取当前元素的**所有子节点**  
 **会获取到空白的文本子节点**  

childNodes属性会获取包括文本节点在呢的所有节点  
  根据DOM标签标签间空白也会当成文本节点  
  注意：在IE8及以下的浏览器中，不会将空白文本当成子节点，  
	所以该属性在IE8中会返回4个子元素而其他浏览器是9个  

元素.children  
 获取当前元素的**所有子元素**  

元素.firstChild  
 获取当前元素的**第一个子节点**，会获取到空白的文本子节点  

元素.lastChild  
 获取当前元素的**最后一个子节点**  

元素.parentNode  
 获取当前元素的父元素  

元素.previousSibling  
 获取当前元素的前一个兄弟节点  

previousElementSibling获取前一个兄弟元素，IE8及以下不支持  

元素.nextSibling  
 获取当前元素的后一个兄弟节点  

firstElementChild获取当前元素的第一个子元素  
 firstElementChild不支持IE8及以下的浏览器，  
	如果需要兼容他们尽量不要使用  

innerHTML和innerText  
这两个属性并没有在DOM标准定义，但是大部分浏览器都支持这两个属性  
两个属性作用类似，都可以获取到标签内部的内容，  
**不同是innerHTML会获取到html标签，而innerText会自动去除标签**  
如果使用这两个属性来设置标签内部的内容时，没有任何区别的	  

**读取标签内部的文本内容**  

</h1>h1中的文本内容</h1>  

元素.firstChild.nodeValue  

## document对象的其他的属性和方法  

document.all  
 **获取页面中的所有元素**，相当于document.getElementsByTagName("*");  

document.documentElement  
 **获取页面中html根元素**  

document.body  
 获取页面中的body元素  

document.getElementsByClassName()  
 **根据元素的class属性值查询一组元素节点对象**  
 这个方法不支持IE8及以下的浏览器  

document.querySelector()  
 **根据CSS选择器去页面中查询一个元素**  
 如果匹配到的元素有多个，则它会返回查询到的第一个元素	  

document.querySelectorAll()	  
 根据CSS选择器去页面中查询一组元素  
 会将匹配到所有元素封装到一个数组中返回，即使只匹配到一个  

##  DOM修改  

document.createElement("TagName")  
	可以用于创建一个元素节点对象，  
	它需要一个标签名作为参数，将会根据该标签名创建元素节点对象，  
	并将创建好的对象作为返回值返回  
document.createTextNode("textContent")  
可以根据文本内容创建一个文本节点对象  

**父节点.appendChild(子节点)**  
  向父节点中添加指定的子节点  
**父节点.insertBefore(新节点,旧节点)**  
 将一个新的节点插入到旧节点的前边  
父节点.replaceChild(新节点,旧节点)  
 使用一个新的节点去替换旧节点  

**父节点.removeChild(子节点)**  
 删除指定的子节点  
  推荐方式：**子节点.parentNode.removeChild(子节点)**  

**以上方法，实际就是改变了相应元素（标签）的innerHTML的值。**  

```javascript  
myClick("btn07",function(){  
    //向city中添加广州  
    var city = document.getElementById("city");  
  
    /*  
	* 使用innerHTML也可以完成DOM的增删改的相关操作  
	* 一般我们会两种方式结合使用  
	*/  
    //city.innerHTML += "<li>广州</li>";  
  
    //创建一个li  
    var li = document.createElement("li");  
    //向li中设置文本  
    li.innerHTML = "广州";  
    //将li添加到city中  
    city.appendChild(li);  
  
});  
```

## DOM对CSS的操作  

### 读取和修改内联样式  

使用style属性来操作元素的内联样式  
	读取内联样式：  
	语法：元素.style.样式名  
例子：  
	元素.style.width  
	元素.style.height  
	注意：**如果样式名中带有-，则需要将样式名修改为驼峰命名法将-去掉，然后后的字母改大写**  
	比如：backgroundcolor > backgroundColor  
	borderwidth > borderWidth  
修改内联样式：  
语法：元素.style.样式名 = 样式值  
 **通过style修改和读取的样式都是内联样式**，由于内联样式的优先级比较高，  
	所以我们通过JS来修改的样式，往往会立即生效，  
	**但是如果样式中设置了!important，则内联样式将不会生效。**  
	  

### 读取元素的当前样式  

正常浏览器  
 **使用getComputedStyle()**  
 这个方法是window对象的方法，可以返回一个对象，这个对象中保存着当前元素生效样式  
 参数：  
	1.要获取样式的元素  
	2.可以传递一个伪元素，一般传null  
 例子：  
	获取元素的宽度  
		getComputedStyle(box , null)["width"];  
 通过该方法读取到样式都是只读的不能修改  

IE8  
 **使用currentStyle**  
 语法：  
	元素.currentStyle.样式名  
 例子：  
	box.currentStyle["width"]  
 通过这个属性读取到的样式是只读的不能修改  

**实现兼容性**  

//对象.属性不存在，不会报错，如果直接寻找对象，（当前作用域到全局作用域）找不到会报错  

```javascript  
/*  
* 定义一个函数，用来获取指定元素的当前的样式  
* 参数：  
* 		obj 要获取样式的元素  
* 		name 要获取的样式名  
*/  
function getStyle(obj , name){  
//对象.属性不存在，不会报错，如果直接寻找对象，（当前作用域到全局作用域）找不到会报错  
    if(window.getComputedStyle){  
        //正常浏览器的方式，具有getComputedStyle()方法  
        return getComputedStyle(obj , null)[name];  
    }else{  
        //IE8的方式，没有getComputedStyle()方法  
        return obj.currentStyle[name];  
    }  
    //return window.getComputedStyle?getComputedStyle(obj , null)[name]:obj.currentStyle[name];			  
}  
```

### 其他的样式相关的属性  

注意：以下样式都是只读的,未指明偏移量都是相对于当前窗口左上角  

clientHeight  
 元素的可见高度，包括元素的内容区和内边距的高度  
clientWidth  
 元素的可见宽度，包括元素的内容区和内边距的宽度  
offsetHeight  
 整个元素的高度，包括内容区、内边距、边框  
offfsetWidth  
 整个元素的宽度，包括内容区、内边距、边框  
offsetParent  
 当前元素的定位父元素  
 离他最近的开启了定位的祖先元素，如果所有的元素都没有开启定位，则返回body  
offsetLeft  
offsetTop  
 当前元素和定位父元素之间的偏移量  
 offsetLeft水平偏移量  offsetTop垂直偏移量  

scrollHeight  
scrollWidth  
 获取元素滚动区域的高度和宽度  

scrollTop  
scrollLeft  
 获取元素垂直和水平滚动条滚动的距离  

判断滚动条是否滚动到底  
 垂直滚动条  
	scrollHeight -scrollTop = clientHeight  
	  
 水平滚动	  
	scrollWidth -scrollLeft = clientWidth	  

  

# 事件（Event）  

## 事件对象  

当响应函数被调用时，浏览器每次都会将一个事件对象作为实参传递进响应函数中，这个事件对象中封装了当前事件的相关信息，比如：鼠标的坐标，键盘的按键，鼠标的按键，滚轮的方向。。  

可以在响应函数中定义一个形参，来使用事件对象，但是在IE8以下浏览器中事件对象没有做完实参传递，而是作为window对象的属性保存  

例子：  
```javascript  
元素.事件 = function(event){  
    event = event || window.event;  
};  
  
元素.事件 = function(e){  
	e = e || event;  
	  
};  
```

**获取到鼠标的坐标**  
  clientX和clientY  
	用于获取鼠标在当前的可见窗口的坐标  
  div的偏移量，是相对于整个页面的  

  pageX和pageY 可以获取鼠标相对于当前页面的坐标  
	但是这个两个属性在IE8中不支持，所以如果需要兼容IE8，则不要使用  
var left = event.clientX;  
var　top = event.clientY;  

  

 ## 事件的冒泡（Bubble）  

 事件的冒泡指的是事件向上传导，当后代元素上的事件被触发时，将会导致其祖先元素上的同类事件也会触发。  
 事件的冒泡大部分情况下都是有益的，如果需要取消冒泡，则需要使用事件对象来取消  
 **可以将事件对象的cancelBubble设置为true，即可取消冒泡**  
   例子：  

```javascript  
元素.事件 = function(event){  
    event = event || window.event;  
    event.cancelBubble = true;  
};  
```

  

## 事件的委派  

 指将事件统一绑定给元素的共同的祖先元素，这样当后代元素上的事件触发时，会一直冒泡到祖先元素，从而通过祖先元素的响应函数来处理事件。  

事件委派是利用了冒泡，通过委派可以减少事件绑定的次数，提高程序的性能		  

我们希望，只绑定一次事件，即可应用到多个的元素上，即使元素是后添加的  
我们可以尝试将其绑定给元素的共同的祖先元素  

 **target** : event中的target表示的触发事件的对象  

## 事件的绑定  

addEventListener()  
 通过这个方法也可以为元素绑定响应函数  
参数：  
	1.事件的字符串，不要on  
	2.回调函数，当事件触发时该函数会被调用  
	3.是否在捕获阶段触发事件，需要一个布尔值，一般都传false  

使用addEventListener()可以同时为一个元素的相同事件同时绑定多个响应函数，  
这样当事件被触发时，响应函数将会按照函数的绑定顺序执行  

这个方法不支持IE8及以下的浏览器  

```javascript  
btn01.addEventListener("click",function(){  
	alert(1);  
},false);  
  
btn01.addEventListener("click",function(){  
	alert(2);  
},false);					  
```

attachEvent()  

 在IE8中可以使用attachEvent()来绑定事件  
参数：  
	1.事件的字符串，要on  
	2.回调函数  

这个方法也可以同时为一个事件绑定多个处理函数，  
	不同的是它是后绑定先执行，执行顺序和addEventListener()相反  

```javascript  
btn01.attachEvent("onclick",function(){  
alert(1);  
});  
  
btn01.attachEvent("onclick",function(){  
alert(2);  
});	  
```

```javascript  
//定义一个函数，用来为指定元素绑定响应函数  
/*  
			 * addEventListener()中的this，是绑定事件的对象  
			 * attachEvent()中的this，是window  
			 *  需要统一两个方法this  
			 */  
/*  
			 * 参数：  
			 * 	obj 要绑定事件的对象  
			 * 	eventStr 事件的字符串(不要on)  
			 *  callback 回调函数  
			 */  
function bind(obj , eventStr , callback){  
    if(obj.addEventListener){  
        //大部分浏览器兼容的方式  
        obj.addEventListener(eventStr , callback , false);  
    }else{  
        /*  
					 * this是谁由调用方式决定  
					 * callback.call(obj)  
					 */  
        //IE8及以下  
        obj.attachEvent("on"+eventStr , function(){  
            //在匿名函数中调用回调函数  
            callback.call(obj);  
        });  
    }  
}  
```

## 事件的传播  

 关于事件的传播网景公司和微软公司有不同的理解  
 微软公司认为事件应该是由内向外传播，也就是当事件触发时，应该先触发当前元素上的事件，  
	然后再向当前元素的祖先元素上传播，也就说事件应该在冒泡阶段执行。  
 网景公司认为事件应该是由外向内传播的，也就是当前事件触发时，应该先触发当前元素的最外层的祖先元素的事件，  
	然后在向内传播给后代元素  
 W3C综合了两个公司的方案，将事件传播分成了三个阶段  
	1.捕获阶段  
		 在捕获阶段时从最外层的祖先元素，向目标元素进行事件的捕获，但是默认此时不会触发事件  
	2.目标阶段  
		 事件捕获到目标元素，捕获结束开始在目标元素上触发事件  
	3.冒泡阶段  
		 事件从目标元素向他的祖先元素传递，依次触发祖先元素上的事件  

 如果希望在捕获阶段就触发事件，可以将addEventListener()的第三个参数设置为true  
	一般情况下我们不会希望在捕获阶段触发事件，所以这个参数一般都是false  

 IE8及以下的浏览器中没有捕获阶段  

## 常用事件  

### 鼠标事件  

拖拽事件  

```javascript  
<!DOCTYPE html>  
    <html>  
    <head>  
    <meta charset="UTF-8">  
        <title></title>  
<style type="text/css">  
  
    #box1{  
width: 100px;  
height: 100px;  
background-color: red;  
position: absolute;  
}  
  
#box2{  
width: 100px;  
height: 100px;  
background-color: yellow;  
position: absolute;  
  
left: 200px;  
top: 200px;  
}  
  
    </style>  
  
<script type="text/javascript">  
  
    window.onload = function(){  
    /*  
				 * 拖拽box1元素  
				 *  - 拖拽的流程  
				 * 		1.当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown  
				 * 		2.当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove  
				 * 		3.当鼠标松开时，被拖拽元素固定在当前位置	onmouseup  
				 */  
  
    //获取box1  
    var box1 = document.getElementById("box1");  
    var box2 = document.getElementById("box2");  
    var img1 = document.getElementById("img1");  
  
    //开启box1的拖拽  
    drag(box1);  
    //开启box2的  
    drag(box2);  
  
    drag(img1);  
  
};  
  
/*  
			 * 提取一个专门用来设置拖拽的函数  
			 * 参数：开启拖拽的元素  
			 */  
function drag(obj){  
    //当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown  
    obj.onmousedown = function(event){  
  
        //设置box1捕获所有鼠标按下的事件  
        /*  
					 * setCapture()  
					 * 	- 只有IE支持，但是在火狐中调用时不会报错，  
					 * 		而如果使用chrome调用，会报错  
					 */  
        /*if(box1.setCapture){  
						box1.setCapture();  
					}*/  
        obj.setCapture && obj.setCapture();  
  
  
        event = event || window.event;  
        //div的偏移量 鼠标.clentX - 元素.offsetLeft  
        //div的偏移量 鼠标.clentY - 元素.offsetTop  
        var ol = event.clientX - obj.offsetLeft;  
        var ot = event.clientY - obj.offsetTop;  
  
  
        //为document绑定一个onmousemove事件  
        document.onmousemove = function(event){  
            event = event || window.event;  
            //当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove  
            //获取鼠标的坐标  
            var left = event.clientX - ol;  
            var top = event.clientY - ot;  
  
            //修改box1的位置  
            obj.style.left = left+"px";  
            obj.style.top = top+"px";  
  
        };  
  
        //为document绑定一个鼠标松开事件  
        document.onmouseup = function(){  
            //当鼠标松开时，被拖拽元素固定在当前位置	onmouseup  
            //取消document的onmousemove事件  
            document.onmousemove = null;  
            //取消document的onmouseup事件  
            document.onmouseup = null;  
            //当鼠标松开时，取消对事件的捕获  
            obj.releaseCapture && obj.releaseCapture();  
        };  
  
 /*  
* 当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，  
* 	此时会导致拖拽功能的异常，这个是浏览器提供的默认行为，  
* 	如果不希望发生这个行为，则可以通过return false来取消默认行为  
*   
* 但是这招对IE8不起作用  
*/  
        return false;  
    };  
}  
  
  
</script>  
</head>  
<body>  
  
    我是一段文字  
  
<div id="box1"></div>  
  
<div id="box2"></div>  
  
<img src="img/an.jpg" id="img1" style="position: absolute;"/>  
    </body>  
</html>  
```

  

滚轮事件：  

onwheel都支持  

```javascript		  
<!DOCTYPE html>  
    <html>  
    <head>  
    <meta charset="UTF-8">  
        <title></title>  
<style type="text/css">  
  
    #box1{  
width: 100px;  
height: 100px;  
background-color: red;  
}  
  
    </style>  
<script type="text/javascript">  
  
    window.onload = function(){  
  
  
    //获取id为box1的div  
    var box1 = document.getElementById("box1");  
  
    //为box1绑定一个鼠标滚轮滚动的事件  
    /*  
				 * onmousewheel鼠标滚轮滚动的事件，会在滚轮滚动时触发，  
				 * 	但是火狐不支持该属性  
				 *   
				 * 在火狐中需要使用 DOMMouseScroll 来绑定滚动事件  
				 * 	注意该事件需要通过addEventListener()函数来绑定  
				 */  
  
  
    box1.onmousewheel = function(event){  
  
        event = event || window.event;  
  
  
        //event.wheelDelta 可以获取鼠标滚轮滚动的方向  
        //向上滚 120   向下滚 -120  
        //wheelDelta这个值我们不看大小，只看正负  
  
        //alert(event.wheelDelta);  
  
        //wheelDelta这个属性火狐中不支持  
        //在火狐中使用event.detail来获取滚动的方向  
        //向上滚 -3  向下滚 3  
        //alert(event.detail);  
  
  
        /*  
					 * 当鼠标滚轮向下滚动时，box1变长  
					 * 	当滚轮向上滚动时，box1变短  
					 */  
        //判断鼠标滚轮滚动的方向  
        if(event.wheelDelta > 0 || event.detail < 0){  
            //向上滚，box1变短  
            box1.style.height = box1.clientHeight - 10 + "px";  
  
        }else{  
            //向下滚，box1变长  
            box1.style.height = box1.clientHeight + 10 + "px";  
        }  
  
        /*  
					 * 使用addEventListener()方法绑定响应函数，取消默认行为时不能使用return false  
					 * 需要使用event来取消默认行为event.preventDefault();  
					 * 但是IE8不支持event.preventDefault();这个玩意，如果直接调用会报错  
					 */  
        event.preventDefault && event.preventDefault();  
  
  
        /*  
					 * 当滚轮滚动时，如果浏览器有滚动条，滚动条会随之滚动，  
					 * 这是浏览器的默认行为，如果不希望发生，则可以取消默认行为  
					 */  
        return false;  
  
  
  
  
    };  
  
    //为火狐绑定滚轮事件  
    bind(box1,"DOMMouseScroll",box1.onmousewheel);  
  
  
};  
  
  
function bind(obj , eventStr , callback){  
    if(obj.addEventListener){  
        //大部分浏览器兼容的方式  
        obj.addEventListener(eventStr , callback , false);  
    }else{  
        /*  
					 * this是谁由调用方式决定  
					 * callback.call(obj)  
					 */  
        //IE8及以下  
        obj.attachEvent("on"+eventStr , function(){  
            //在匿名函数中调用回调函数  
            callback.call(obj);  
        });  
    }  
}  
  
</script>  
</head>  
<body style="height: 2000px;">  
  
    <div id="box1"></div>  
  
</body>  
</html>  
  
```

### 键盘事件  

键盘事件：  
onkeydown  
 按键被按下  
 对于onkeydown来说如果一直按着某个按键不松手，则事件会一直触发  
 当onkeydown连续触发时，第一次和第二次之间会间隔稍微长一点，其他的会非常的快，这种设计是为了防止误操作的发生。  
onkeyup  
 按键被松开  

键盘事件一般都会绑定给一些可以获取到焦点的对象或者是document  

keyCode  

可以通过keyCode来获取按键的编码  
通过它可以判断哪个按键被按下  
除了keyCode，事件对象中还提供了几个属性  
altKey  
ctrlKey  
shiftKey  
这个三个用来判断alt ctrl 和 shift是否被按下  
如果按下则返回true，否则返回false  

```javascript  
//console.log(event.keyCode);  
  
//判断一个y是否被按下  
//判断y和ctrl是否同时被按下  
if(event.keyCode === 89 && event.ctrlKey){  
	console.log("ctrl和y都被按下了");  
}  
```

```javascript  
input.onkeydown = function(event) {  
    event = event || window.event;  
    //数字 48 - 57  
    //使文本框中不能输入数字  
    if(event.keyCode >= 48 && event.keyCode <= 57) {  
        //在文本框中输入内容，属于onkeydown的默认行为  
        //如果在onkeydown中取消了默认行为，则输入的内容，不会出现在文本框中  
        return false;  
    }  
};  
  
```

# BOM  

浏览器对象模型(browser object model)  
BOM可以使我们通过JS来操作浏览器  
在BOM中为我们提供了一组对象，用来完成对浏览器的操作  
BOM对象  
Window  
 代表的是整个浏览器的窗口，同时window也是网页中的全局对象  
Navigator  
 代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器  
Location  
 代表当前浏览器的地址栏信息，通过Location可以获取地址栏信息，或者操作浏览器跳转页面  
History  
 代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录  
	由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页  
	而且该操作只在当次访问时有效  
Screen  
 代表用户的屏幕的信息，通过该对象可以获取到用户的显示器的相关的信息  

这些BOM对象在浏览器中都是作为window对象的属性保存的，  
可以通过window对象来使用，也可以直接使用  

## Navigator  

 代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器  
 由于历史原因，Navigator对象中的大部分属性都已经不能帮助我们识别浏览器了  
 一般我们只会使用userAgent来判断浏览器的信息，  
	userAgent是一个字符串，这个字符串中包含有用来描述浏览器信息的内容，  
	不同的浏览器会有不同的userAgent  

火狐的userAgent  
Mozilla5.0 (Windows NT 6.1; WOW64; rv:50.0) Gecko20100101 Firefox50.0  

Chrome的userAgent  
Mozilla5.0 (Windows NT 6.1; Win64; x64) AppleWebKit537.36 (KHTML, like Gecko) Chrome52.0.2743.82 Safari537.36  

IE8  
Mozilla4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)  

IE9  
Mozilla5.0 (compatible; MSIE 9.0; Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)  

IE10  
Mozilla5.0 (compatible; MSIE 10.0; Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)  

IE11  
Mozilla5.0 (Windows NT 6.1; WOW64; Trident7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E; rv:11.0) like Gecko  
 在IE11中已经将微软和IE相关的标识都已经去除了，所以我们基本已经不能通过UserAgent来识别一个浏览器是否是IE了  

```javascript  
alert(navigator.appName);  
  
var ua = navigator.userAgent;  
  
console.log(ua);  
  
if(firefoxi.test(ua)){  
alert("你是火狐！！！");  
}else if(chromei.test(ua)){  
alert("你是Chrome");  
}else if(msiei.test(ua)){  
alert("你是IE浏览器~~~");  
}else if("ActiveXObject" in window){  
alert("你是IE11，枪毙了你~~~");  
}  
```

## History  

 对象可以用来操作浏览器向前或向后翻页	  
length  
 属性，可以获取到当成访问的链接数量  
back()  
 可以用来回退到上一个页面，作用和浏览器的回退按钮一样	  
forward()  
 可以跳转下一个页面，作用和浏览器的前进按钮一样	  
go()  
 可以用来跳转到指定的页面  
 它需要一个整数作为参数  
	1:表示向前跳转一个页面 相当于forward()  
	2:表示向前跳转两个页面  
	-1:表示向后跳转一个页面  
	-2:表示向后跳转两个页面  

## Location  

 该对象中封装了浏览器的地址栏的信息	  
如果直接打印location，则可以获取到地址栏的信息（当前页面的完整路径）  
alert(location);  
如果直接将location属性修改为一个完整的路径，或相对路径  
则我们页面会自动跳转到该路径，并且会生成相应的历史记录  
location = "http:www.baidu.com";  
location = "01.BOM.html";  
assign()  
 用来跳转到其他的页面，作用和直接修改location一样	  
reload()  
 用于重新加载当前页面，作用和刷新按钮一样  
 如果在方法中传递一个true，作为参数，则会强制清空缓存刷新页面  
location.reload(true);	  
replace()  
 可以使用一个新的页面替换当前页面，调用完毕也会跳转页面  
	不会生成历史记录，不能使用回退按钮回退  

## window  

###  定时器  

**setInterval()**  
 定时调用  
 可以将一个函数，每隔一段时间执行一次  
 参数：  
	1.回调函数，该函数会每隔一段时间被调用一次  
	2.每次调用间隔的时间，单位是毫秒  

 返回值：  
	返回一个Number类型的数据  
	这个数字用来作为定时器的唯一标识  
**clearInterval()可以用来关闭一个定时器**  
方法中需要一个定时器的标识作为参数，这样将关闭标识对应的定时器   

clearInterval()可以接收任意参数，  
	如果参数是一个有效的定时器的标识，则停止对应的定时器  
	如果参数不是一个有效的标识，则什么也不做  

```javascript  
var num = 1;  
var timer = setInterval(function() {  
	count.innerHTML = num++;  
	if(num == 11) {  
		//关闭定时器  
		clearInterval(timer);  
	}  
}, 1000);  
```

### 延时调用  

**setTimeout**  

延时调用一个函数不马上执行，而是隔一段时间以后在执行，而且只会执行一次  
延时调用和定时调用的区别，定时调用会执行多次，而延时调用只会执行一次  
延时调用和定时调用实际上是可以互相代替的，在开发中可以根据自己需要去选择  

var timer = setTimeout(function(){  
console.log(num++);  
},3000);  

使用clearTimeout()来关闭一个延时调用  
clearTimeout(timer);  

#类的操作  

**直接修改元素的类css：**  

通过style属性来修改元素的样式，每修改一个样式，浏览器就需要重新渲染一次页面。 这样的执行的性能是比较差的，而且这种形式当我们要修改多个样式时，也不太方便 我希望一行代码，可以同时修改多个样式  

我们可以通过修改元素的class属性来间接的修改样式.这样一来，我们只需要修改一次，即可同时修改多个样式，浏览器只需要重新渲染页面一次，性能比较好，  
并且这种方式，可以使表现和行为进一步的分离  

```javascript  
box.className += " b2";	//注意有空格，添加class属性  
```

```javascript  
//定义一个函数，用来向一个元素中添加指定的class属性值  
/*  
 * 参数:  
 * 	obj 要添加class属性的元素  
 *  cn 要添加的class值  
 * 	  
 */  
function addClass(obj, cn) {  
	if (!hasClass(obj, cn)) {  
		obj.className += " " + cn;  
	}  
}  
/*  
 * 判断一个元素中是否含有指定的class属性值  
 * 	如果有该class，则返回true，没有则返回false  
 * 	  
 */  
function hasClass(obj, cn) {  
	var reg = new RegExp("\\b" + cn + "\\b");  
	return reg.test(obj.className);  
}  
/*  
 * 删除一个元素中的指定的class属性  
 */  
function removeClass(obj, cn) {  
	//创建一个正则表达式  
	var reg = new RegExp("\\b" + cn + "\\b");  
	//删除class  
	obj.className = obj.className.replace(reg, "");  
}  
/*  
 * toggleClass可以用来切换一个类  
 * 	如果元素中具有该类，则删除  
 * 	如果元素中没有该类，则添加  
 */  
function toggleClass(obj , cn){	  
	//判断obj中是否含有cn  
	if(hasClass(obj , cn)){  
		//有，则删除  
		removeClass(obj , cn);  
	}else{  
		//没有，则添加  
		addClass(obj , cn);  
	}  
}  
```

# JSON  

 **JavaScript Object Notation** JS对象表示法

## JSON 格式

1. 复合类型的值只能是数组或对象，不能是函数、正则表达式对象、日期对象。
2. 原始类型的值只有四种：字符串、数值（必须以十进制表示）、布尔值和`null`（不能使用`NaN`, `Infinity`, `-Infinity`和`undefined`）。
3. 字符串**必须使用双引号表示**，不能使用单引号。
4. 对象的键名必须放在双引号里面。
5. 数组或对象最后一个成员的后面，不能加逗号。

  

JS中的对象只有JS自己认识，其他的语言都不认识  
**JSON就是一个特殊格式的字符串**，这个字符串可以被任意的语言所识别，  
并且可以转换为任意语言中的对象，JSON在开发中主要用来数据的交互  
 JSON和JS对象的格式一样，只不过**JSON字符串中的属性名必须加双引号**  
	其他的和JS语法一致  
JSON分类：  
	1.对象 {}  
	2.数组 []  

JSON中允许的值：  
	1.字符串  
	2.数值  
	3.布尔值  
	4.null  
	5.对象  
	6.数组  

举例：  

```javascript  
var arr = '[1,2,3,"hello",true]';  
			  
var obj2 = '{"arr":[1,2,3]}';  
  
var arr2 ='[{"name":"孙悟空","age":18,"gender":"男"},{"name":"孙悟空","age":18,"gender":"男"}]';  
```

JSON工具类  

json > js对象  
JSON.parse()  
 可以将以JSON字符串转换为js对象  
 它需要一个JSON字符串作为参数，会将该字符串转换为JS对象并返回  

var o = JSON.parse(json);  
var o2 = JSON.parse(arr);  

var obj3 = {name:"猪八戒" , age:28 , gender:"男"};  

JS对象 > JSON  
JSON.stringify()                -ify/fy，表示"使……化。  
 可以将一个JS对象转换为JSON字符串  
 需要一个js对象作为参数，会返回一个JSON字符串  

var str = JSON.stringify(obj3);  
console.log(str);  

JSON这个对象在IE7及以下的浏览器中不支持，所以在这些浏览器中调用时会报错  



  

  

  

  

  

  


​		  

# other  

## localStorage  

只读的`localStorage` 属性允许你访问一个[`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document) 源（origin）的对象 [`Storage`](https://developer.mozilla.org/zh-CN/docs/Web/API/Storage)；其存储的数据能在跨浏览器会话保留。`localStorage` 类似 [`sessionStorage`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/sessionStorage)，但其区别在于：存储在 `localStorage` 的数据可以长期保留；而当页面会话结束——也就是说，当页面被关闭时，存储在 `sessionStorage` 的数据会被清除 。  

## eval()  

eval()  
 这个函数可以用来执行一段字符串形式的JS代码，并将执行结果返回  
 如果使用eval()执行的字符串中含有{},它会将{}当成是代码块  
	如果不希望将其当成代码块解析，则需要在字符串前后各加一个()  

 eval()这个函数的功能很强大，可以直接执行一个字符串中的js代码，  
	但是在开发中尽量不要使用，首先它的执行性能比较差，然后它还具有安全隐患  
		  

	var str = '{"name":"孙悟空","age":18,"gender":"男"}';  
	var obj = eval("("+str+")");  
编码  

```html  
<!DOCTYPE html>  
<html>  
	<head>  
		<meta charset="UTF-8">  
		<title></title>  
		<script type="text/javascript">  
			  
			/*  
			 * 在字符串中使用转义字符输入Unicode编码  
			 * 	\u四位编码  
			 */  
			console.log("\u2620");	  
		</script>  
	</head>  
	<body>		  
		<!--在网页中使用Unicode编码  
			&#编码; 这里的编码需要的是10进制  
		-->  
		<h1 style="font-size: 200px;">&#9760;</h1>  
		<h1 style="font-size: 200px;">&#9856;</h1>		  
	</body>  
</html>  
  
```

confirm()用于弹出一个带有确认和取消按钮的提示框  
需要一个字符串作为参数，该字符串将会作为提示文字显示出来  
如果用户点击确认则会返回true，如果点击取消则返回false  
var flag = confirm("确认删除"+name+"吗?");  

## # 原生js  

## 原生js实现复制内容到剪切板  

```js  
copy() {  
    const input = document.createElement("input");  
    document.body.appendChild(input);  
    input.setAttribute("value",this.solution.code);  
    input.select();  
    if (document.execCommand("copy")) {  
        document.execCommand("copy");  
        // console.log("复制成功");  
    }  
    document.body.removeChild(input);  
}  
```