# ES6
> 来源：阮一峰大神的[es6入门](http://es6.ruanyifeng.com)

## let和const命令
1. let

> let实际上为JavaScript新增了块级作用域。

* “暂时性死区”:在代码块内，使用let命令声明变量之前，变量不可用，会抛出一个ReferenceError。

2. const

> const声明一个只读的常量。一旦声明，常量的值就不能改变。这意味着，const一旦声明变量，就必须立即初始化。

* 对于复合类型的变量，变量名不指向数据，而是指向数据所在的地址。 
* 可以使用Object.freeze方法 将对象冻结。

3. 共性
* let和const命令都绑定了当前的块级作用域，变量不提升，存在暂时性死区，无法重复声明。
* let命令、const命令、class命令声明的全局变量，不属于顶层对象的属性。


## 变量的解构赋值
> 按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构。

解构不成功，变量的值就等于undefined。
不完全解构，即等号左边的模式，只匹配一部分的等号右边的数组。这种情况下，解构依然可以成功。

* 适用于var命令，let命令和const命令
* 解构赋值允许指定默认值。
* 解构赋值允许指定默认值，如果一个数组成员不严格等于undefined，默认值是不会生效的
* 默认值可以引用解构赋值的其他变量，但该变量必须已经声明。

### 默认值
* 如果默认值是一个表达式，那么这个表达式是惰性求值的，即只有在用到的时候，才会求值。
* 默认值可以引用解构赋值的其他变量(引用的是赋值之后的其他变量)，但该变量必须已经声明。

1. 数组的解构赋值  
* 如果等号的右边不是数组，或者严格地说，不是可遍历的结构，那么将会报错。
* 只要某种数据结构具有Iterator接口，都可以采用数组形式的解构赋值。
* ES6内部使用严格相等运算符（===），判断一个位置是否有值。所以，如果一个数组成员不严格等于undefined，默认值是不会生效的。

对于Set结构，也可以使用数组的解构赋值。
        
        let [x, y, z] = new Set(["a", "b", "c"]);
        x // "a"

2. 对象的解构赋值  

对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。

* 对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。真正被赋值的是后者，而不是前者。
* 变量没有对应的同名属性，导致取不到值，最后等于undefined。
* 默认值生效的条件是，对象的属性值严格等于undefined。

对象的解构赋值是下面形式的简写

        var { foo: foo, bar: bar } = { foo: "aaa", bar: "bbb" };
如果变量名与属性名不一致，必须写成下面这样
        
        var { foo: baz } = { foo: 'aaa', bar: 'bbb' };

3. 字符串的解构赋值

字符串可以解构赋值是因为字符串被转换成了一个类似数组的对象。  
类似数组的对象都有一个length属性，因此还可以对这个属性解构赋值。

4. 数值和布尔值的解构赋值

5. 函数参数的解构赋值

### 作用
* 交换变量的值
* 从函数返回多个值
* 函数参数的定义
* 提取JSON数据
* 函数参数的默认值
* 遍历Map结构
* 输入模块的指定方法

## 字符串的扩展
1. 字符串是否包含
includes()：返回布尔值，表示是否找到了参数字符串。  
startsWith()：返回布尔值，表示参数字符串是否在源字符串的头部。  
endsWith()：返回布尔值，表示参数字符串是否在源字符串的尾部。  

2. repeat方法  
返回一个新字符串，表示将原字符串重复n次。

3. 字符串补全长度  
ES7推出了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。padStart用于头部补全，padEnd用于尾部补全。

4. 模板字符串
* 模板字符串的空格和换行，都是被保留，如果不想要这个换行，可以使用trim方法消除它。
* 模板字符串中嵌入变量，需要将变量名写在${}之中。大括号内部可以放入任意的JavaScript表达式，可以进行运算，以及引用对象属性。如果大括号内部是一个字符串，将会原样输出。
* 模板字符串之中还能调用函数。
* 模板字符串甚至还能嵌套。

## 正则的扩展

## 数值的扩展

## 数组的扩展
* Array.from：用于将两类对象转为真正的数组：类似数组的对象（array-like object）和可遍历（iterable）的对象（包括ES6新增的数据结构Set和Map）

