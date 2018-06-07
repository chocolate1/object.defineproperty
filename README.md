# object.defineproperty
据说object.defineproperty是个很牛逼的方法....so，let's get it
vue.js是通过它实现双向绑定的。俗称属性拦截器。而且专门用来监控对象属性变化的Object.observe方法也被草案发起人撤回了(此方法在node环境中仍能使用)。
可见defineProperty的威力之大。
Object.defineProperty() 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象
语法如下:
Object.definerProperty(obj,pro,descriptor)
参数：
obj
要在其上定义属性的对象。
prop
要定义或修改的属性的名称。
descriptor
将被定义或修改的属性描述符。
返回值：
被传递给函数的对象。
描述：
该方法允许精确添加或修改对象的属性。通过赋值来添加的普通属性会创建在属性枚举期间显示的属性（for...in 或 Object.keys 方法）， 
这些值可以被改变，也可以被删除。这种方法允许这些额外的细节从默认值改变。默认情况下，使用Object.defineProperty()添加的属性值是不可变的。

属性描述符：
对象里目前存在的属性描述符有两种主要形式：数据描述符和存取描述符。数据描述符是一个具有值的属性，该值可能是可写的，也可能不是可写的。
存取描述符是由getter-setter函数对描述的属性。描述符必须是这两种形式之一；不能同时是两者。

数据描述符和存取描述符均具有以下可选键值：
configurable
当且仅当该属性的 configurable 为 true 时，该属性描述符才能够被改变，同时该属性也能从对应的对象上被删除。默认为 false。
enumerable
当且仅当该属性的enumerable为true时，该属性才能够出现在对象的枚举属性中。默认为 false。
数据描述符同时具有以下可选键值：
value
该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 undefined。
writable
当且仅当该属性的writable为true时，value才能被赋值运算符改变。默认为 false。                                                                                                                                                                                                 
存取描述符同时具有以下可选键值：
get
一个给属性提供 getter 的方法，如果没有 getter 则为 undefined。该方法返回值被用作属性值。默认为 undefined。
set
一个给属性提供 setter 的方法，如果没有 setter 则为 undefined。该方法将接受唯一参数，并将该参数的新值分配给该属性。默认为 undefined。

描述符可同时具有的键值
 	configurable	enumerable	value	writable	get	set
数据描述符	Yes	Yes	Yes	Yes	No	No
存取描述符	Yes	Yes	No	No	Yes	Yes
如果一个描述符不具有value,writable,get 和 set 任意一个关键字，那么它将被认为是一个数据描述符。
如果一个描述符同时有(value或writable)和(get或set)关键字，将会产生一个异常。
