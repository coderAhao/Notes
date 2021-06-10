#### 第一章：JS基础

##### 1.1 初识JavaScript

1. 对网页而言,HTML、CSS、JavaScript分别代表了结构、样式和行为。

2. 结构是骨架,样式是外观,行为是交互逻辑。

3. 非脚本语言一般需要编译、链接生成独立的可执行文件后才能运行

4. 脚本语言只需经过编写-运行 即不需编译成二进制，以文本形式存在,只依赖于解释器不能独立运行,在被调用时自动进行解释或编译。如JS、python、PHP（缺点:执行效率不如编译型语言快）

5. JS作用:动态改变网页内容(HTML)、样式(CSS) 验证表单数据及响应事件

##### 1.2 浏览器

1. 浏览器内核分为两部分,排版引擎和JavaScript引擎 

    - 前者负责解析和处理网页内容,如HTML和CSS

    - 后者解析JavaScript语言,通过执行代码实现网页交互

2. 排版引擎:

    - 微软两个浏览器: IE:Trident和Microsoft Edge:EdgeHTML

    - Mozilla FireFox:Gecko  

    - Safari:WebKit

    - Chrome/Opera:Blink

3. JavaScript引擎:

    - IE:Chakra

    - FireFox:SpiderMokey/Rhino

    - Safari:JavaScriptCore

    - Chrome:V8

4. JS编译：

    - 传统方式为JS被编译为字节码-->二进制代码 

    - 但V8引擎跳过字节码，直接编译为二进制代码(故Google比其他浏览器加载速度快)

##### 1.3 其他

1. JavaScript引入方式:

    - 行内式:作为HTML标签属性值使用

    - 嵌入式:写在script标签中

    - 外链式:通过单独的文件引用

2. 常用输出语句：

    - alert() 弹出框

    - console.log() 控制台输出内容  

    - document.write() 文档页面输出内容

3. JS严格遵循大小写

4. 在一个HTML文档中使用多个script标签嵌入JS语句时,标签里的内容相互关联 

 

------

#### 第二章：基本语法

##### 2.1 变量

1. 标识符:开发中,自定义符号来标记名称并赋予特殊用途,如变量名、函数名等。

2. 变量命名规范：

    - 以字母、数字、下划线或美元符号组成,不得包含空格、标点、运算符等符号

    - 不得以数字开头  

    - 不能是系统关键字  

    - 区分大小写  

    - 命名最好有意义

3. 命名方式：

    - 多个单词时:

        - 下划线法
        - 驼峰法（首个单词首字母小写,其后单词首字母均大写）

        - 帕斯卡法（所有单词首字母均大写）

    - 下划线通常用于变量命名，驼峰法用于函数命名

    - 变量声明关键字“var” ，同时声明多个变量需用逗号分隔开

    - ES6使用const关键字定义常量,常量通常均用大写字母表示且在声明时就必须赋值

##### 2.2 数据类型

- 基本数据类型(深拷贝) 

    -  Boolean:true(1)/false(0) 必须小写
    -  String:字符型
    -  Number:数值/NaN(即not a number)(注:NaN≠NaN,因为NaN被操作时可能是Boolean、Number、Null等)
    -  Null:null 空型 表示一个不存在或无效的对象或地址,它已定义并初始化为null (注:通过将变量值设为null来清空变量)
    -  Undefined:undefined 变量已被声明但未被初始化(注意与Null的区别)
    -   这些类型在内存中占用固定大小空间,值保存在栈空间中,按值访问
    -   
- 引用数据类型(浅拷贝)
    - 对象 数组 函数 
    - 引用类型保存对象多少不固定,即在内存中空间不固定,但内存地址固定,存储在堆内存中,存储的是内存地址 变量复制时,基本类型复制的是值本身,系统会再为其分配内存空间;而引用类型复制的是地址
- 常用转义字符： 换行\n 回车\r 退格\b 反斜杠\\ 双引号\“
- 数据类型检测: 
    - 用法:typeof string 
    - 其返回值可有 “undefined 、boolean、number、string、object、function
    - 测试数据类型时,null和Array都会返回object,因为他们都属于特殊的对象
-  数据类型转换：利用相关函数进行数据类型转换

    -   布尔型：Boolean() 将非空字符串和非零数值转换为true,其他转换为false

    -   数值型：

        - Number([value])  value为Boolean转换为0或1；null为0；undefined为NaN；空为0；以0开头的忽略前导0；纯数字字符串转为数字；其他字符转为NaN
        - parseInt(nub,几进制)
        - parseFloat()  parseFloat只解析十进制
        - parseInt和parseFloat只会将纯数字字符串转为对应数字、将以数字开头字符串转成开头数字，其余均会转成NaN

        -  isNaN() 判断数据是否为数值类型，当不是数值类型时会先将其转化再进行判断；只有给定值为undefined、NaN和Object时才返回true

    -  字符型：

        - String([num]) 可将任意类型转化为字符串
        - arr.toString([进制]) 默认进制为10;只有null和undefined无法转化；还可将数组转为字符串

        - 字符串的比较

            - 数值字符串和数值比较时,字符串会自动转化为数值再进行比较
            - 两个都为数字字符串则比较首个数字 
            - 字母字符串会转换成对应的ASCII码进行比较
- 去除空格
    - str.trim() 去除str左右两边的空格,通常用于输入表单的验证

##### 2.3 表达式

- 可以是各种类型的数据、变量和运算符的集合

##### 2.4 运算符

- 算数运算符

    - 加+ 减- 乘* 除/ 求余% 幂运算** 自增++ 自减-- 

    - 正负得负 如:+(-2)为-2 负负得正 正正得正 负正得负

    - 求余正负取决于被模数 

    - number和string用“+”操作时会将number转为字符串进行拼接 
        - 如:b=a+1+2  b结果为a12,因为先a+1再a1+2 
        - b=a+(1+2) 结果为a3
    -   number和string用“-”操作时会将string转换为number

-  字符串运算符 

    -  赋值运算符：可为变量连等赋值 

    -  比较运算符：

        - “==”和“!=”只比较数据值； 

        - “===”和“！==”则既比较值也比较数据类型

    -  逻辑运算符： 
        - && 与 
        - || 或 
        - ！非 
        - “与”和“或”可短路运算

    -  三元(条件)运算符： 
        - 条件？语句1：语句2  条件为真执行问号后的语句1否则执行冒号后的语句2

    -  位运算

    -  关系操作符: < > <= >= 操作数值会返回布尔值

##### 2.5 流程控制语句

-  顺序结构：自上而下  
-  选择结构：
    - 单分支if；双分支if else；多分支if..else if..else
    - switch：switch(表达式){case num:; break; ... default:;}

-  循环结构：while、do..while和for 
    -  for(语句1;语句2;语句3){被执行的代码块}
        - 语句1在循环前开始执行；
        - 然后执行语句2,若语句2为true则执行代码块否则结束循环；
        - 语句3在代码块执行后执行,语句1和3均可省略(其实省略后需把它加进代码块),语句2不可省,否则会死循环

-  跳转语句

    - break：跳出当前最近的循环体,执行循环体后的语句

    - continue：结束本次循环,开始当前循环体的新循环

    - 此外break和continue还可跳转到指定的标签语句处(标签语句需在使用前定义)
    
        

------

#### 第三章：Array数组

##### 3.1 基本操作

- 创建数组方式：

    - var a=new Array(val1,val2) 直接实例化对象
        -  此种方式不可有空位置的元素,但创建时可指定数组长度 
        - 若只有一个参数则是指定数组的长度

    - var a=[val1,val2] 
        - 此种方式可包含有空位置的元素
    - length属性可获取和修改数组长度

- 访问与遍历

    - arr[index] 通过下标(即索引)访问
    -  for (var index in arr) 通过for...in遍历 ，index保存的是下标

    -  for (var key of arr) 通过for...of遍历 ，key保存的是键值

- 元素的添加、修改与删除

    -  Array[index]='' 直接通过下标的方式添加与修改 

    -  [a,b,c]=[num1,num2,num3] 解构赋值 将右侧依次赋给左侧 (ES6特性) 
        - 注还可用于交换两值 如[a,b]=[b,a]
    - delete Array[index] 通过delete关键字删除(注:只删除了值,位置依然留有)

- 数组排序

    - 冒泡排序

        - 按要求从小到大或从大到小排序,不断比较数组相邻两个元素的值,较小或较大元素前移 

        - 原理：比较轮数为数组长减一,每轮比较次数为数组长度减当前轮数 

        - 核心:[arr[j],arr[j+1]]=[arr[j+1],arr[j]]

        - ```javascript
            let arr = [1, 3, 7, 5, 8];
            for(let i =1; i < arr.length; ++i) { 									// 控制需要比较的轮数
              for(let j = 0; j < arr.length - i; ++i) {					 // 控制参与比较的元素
                if (arr[j] > arr[j + 1]) {															// 比较相邻的两个元素
                  [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]]
                }
              }
            }
            ```

            

    - 插入排序

        - 构建有序数组进行元素存储,即将待排序数组第一个元素视为有序数组,其后的元素视为无序数组,依次将其中元素插入有序数组中 

        -  原理:比较轮数为数组长减一(即无序数组长),每轮比较次数为构建的有序数组长度 

        - 核心:(var j=i;j>0;j--)

        - ```javascript
            let arr = [1, 3, 7, 5, 8];
            for(let i = 1; i < arr.length; ++i) { 							// 遍历无序数组下标
              for(let j = i; j > 0 ; --j) {					 									 // 遍历并比较一个无序数组元素与所有有序数组元素
                if (arr[j - 1] > arr[j]) {															// 比较相邻的两个元素
                  [arr[j - 1], arr[j]] = [arr[j], arr[j - 1]]
                }
              }
            }
            ```

            

##### 3.2 数组普通方法

- 栈和队列

    - push()/unshift 在数组 末尾/开头添加1或多个元素,并返回数组的新长度

    - pop()/shift() 从数组 末尾/开头移除一个元素,并返回移除的元素

- 检索方法

    - includes() 确定数组中是否含有某元素,返回值true/false 

        - 用法：`arrayName.includes(val,index)`

        - 若index大于数组长度,则直接返回false
        - 若index小于0,则从数组长加index位置开始检索，若还小于0则检索整个数组

    - Array.isArray(arrayName) 确定传递的值是否是一个Array, 返回值true/false

    - indexOf() (从指定下标开始)检索到第一个匹配值,返回值index/-1 

        - 用法：`arrayName.indexOf(val,[index])`

        - 若index大于数组长度,则直接返回-1
        - 若index小于0,则从数组长加index位置开始检索;若还小于0则检索整个数组

    - lastIndexOf() (从指定下标开始)逆向检索到第一个匹配值,返回值index/-1 

        - 用法：arrayName.indexOf(val,[index])

        - 若index大于等于数组长度,则检索整个数组;
        - 若index小于0,则从数组长加index位置开始逆向检索;若还小于0则返回-1

- **数组**转字符串

    - join('-') 转时可添加任意连接符,若不添加则默认以逗号连接 用法:str.join()

    - toString() 用法:arr.toString()

        

- 其他方法

    - arr.reverse() 数组中的元素逆序

    - arr.sort() 数组中的元素按ASCII码从小到大排序
        -  arr.sort(fun) 可自定义给排序规则

    - arr.fill(val,[start],[end]) 将数组中(指定下标)元素用val填充(其实就是替换)

    - arr.concat(数组/元素) 将数组/元素和arr合并为一个新的数组，原数组不改变

    - arr.splice(index,num,val...)对一个数组在指定下标范围内删除/添加元素，原数组被改变

        - 从index开始,切num个数据(num为0则表示添加),添加元素val(val可为多个元素) 
        - 若只有index则从此删完 

        - 若index大于等于数组长则从末尾开始;
        - 若index小于0则从数组长加index开始;若还小于0则从头部开始

    - arr.slice(start,end) 从一个数组指定下标范围内切取元素拷贝到新数组中,不改变原数组 

        - 从下标start开始切到end(不包含end)
        - 省略end则表示切到尾部 
        - 若只有start且为负则从尾部开始 

        - 当提取的参数为负值时

            ```javascript
            let str="12345678"
            str.slice(1,-3)   // str长度为8,-3+8=5,则提取str中[1,5）的数据
            str.slice(6,-3)   // -3+8=5,,此时[6,5) 6大于5,提取为空
            str.slice(-6,-3)  // -6+8=2,-3+8=5 则提取str中[2,5)的数据
            ```

##### 3.3 迭代方法

- forEach()

    - `arrName.forEach(function(value,index,arrName){......})`

    - 数组arr中的每一个元素依次执行函数 
    - 形参为三个可选的默认参数
    - value当前值、index当前索引、arrName数组本身

- filter()

    - `arrName.filter(function(value, index, arrName){return ...})`

    - filter会新建一个数组,数组arrName中的元素依次执行函数,将符合条件的元素筛选出放入新数组中

    - ```javascript
        let arr = [1, 2, 3];
        let newArr = arr.filter(function (value, index, arr) {
          return value >= 2;
        })
        console.log(newArr); // [2,3]
        ```

- some()

    - `arrName.some(function(value, index, arrName){return ...})`

    - 查找数组中是否有符合条件的元素,如果查找到就返回true,否则返回false;查找到首个满足条件的元素便会终止

    - return的结果是true代表已找到所需元素,无需再遍历,否则会遍历完整个数组

    - ```javascript
        let arr = [1,2,3];
        let boo = arr.some(function (value,index,arr) {
          return value == 3;
        })
        console.log(boo); // true
        ```

- every()

    - `arrName.every(function(value, index, arrName){return ...})`
    - 与some()方法结果相反，遍历数组中的每一项,只有所有项都符合要求才返回true，有一项不满足则返回false



------

#### 第四章：函数

#####  4.1 函数基本概念

- 声明和调用
    - 函数内部定义变量应: 定义-赋值-输出 ,否则会出现逻辑错误

        - 如输出-赋值-定义 函数遇到输出会先执行定义再回来输出,此时还未赋值故报错

    - 使用关键字function声明,必须是小写;

    - 函数本身不会自动运行,只有调用时才会执行;可以先调用后声明(不在同一个script中仍可调用)

    - 函数调用方法

        - 普通函数: fun()/fun.call()

        - 对象方法: obj.fun()

        - 构造函数: new Fun()

        - 绑定事件函数: btn.onclick=fun(){}

        - 定时器函数: setInterval(fun(){},times)

        - 立即执行函数: (fun(){})()

- 变量作用域

    - 全局变量：函数体外声明或函数体内省略“var”声明，整个文档都可使用

        - 优点:变量少,减少形参和实参传递带来的时间消耗 

        - 缺点:代码可读性低,可被多个函数使用,值可能随时发生变化,不利于程序查错和调试
    - 局部变量：函数体内使用“var”声明 只在函数体内有效
    - 块级变量：使用“let”声明,仅在其后“{}”内有效,常用在“if、for、while语句中”
    - 函数的参数都是按值传递的
    - 函数内部可使用全局变量；外部不可使用局部变量；函数执行完后夲作用域内局部变量会销毁

- 函数内部属性

    - arguments对象: 当不确定形参个数时可将函数中的所有参数存储在arguments中,相当于一个数组
    - 例：arguments[0]表示函数第一个参数
        - 可通过arguments动态添加参数和length属性检测函数实参个数
    
- 函数内this指向

    - this一般指当前作用域下的对象

    - 普通函数:this指向window

    - 对象方法:this指向该方法所属对象

    - 构造函数:this指向实例对象，原型对象里的方法也指向实例对象（即函数被new来调用,那么函数内部的this是new关键字新创建的上级对象；）

    - 绑定事件函数:this指向绑定事件对象

    - 定时器函数和立即执行函数:this均指向window

- return语句

    - 外层必须有函数包括,如if语句虽然包括“return”,但if外层仍需有函数包括,否则会发生语法错误
    - 如果函数中包含if语句,if中又包含return,则if下面的代码不会再执行,即“return”可让函数停止运行
    - 当函数遇到第一个return后将终止后面的代码,会跳出函数

- 所有的函数都是Function的实例,如同所有的对象都是Object的实例,此外函数也是对象

    - 如同原型链基础:

        - 构造函数Function通过“.prototype”指向原型对象(通过.constructor反指回构造函数)

        - 构造函数可生成函数对象实例,而对象实例又可通过`__proto__`指向原型对象

- 内存管理

    - 内存生命周期：

        - 内存分配:当申明变量、函数、对象时系统会自动为其分配内存

        - 内存使用:即读写内存,也就是使用变量、函数等

        - 内存回收:使用完毕垃圾回收机制自动回收不再使用的内存

    - 局部变量(临时变量)存在栈内存,全局变量存在堆内存

    - 没引用时调用函数,栈空间会分配一小块内存给它,函数里的变量储存在栈空间里,调用完毕栈空间会释放掉

- 垃圾回收算法

    - 核心思想是如何判断内存已不再使用 

    - JS内存管理注意事项：

        -  避免不必要的全局变量:当变量被定义在全局作用域中,默认情况下不会被销毁回收,会存在于堆内存中直至页面关闭。

        -  及时解除不再使用的变量将其赋值为null，浏览器会每隔一段时间检查回收内存

        -  合理使用函数,函数中局部变量执行结束后会自动释放内存

##### 4.2 全局函数(在这仅指JS中系统已封装好的函数)

- 全局函数和属性可用于所有内建的JS对象，全局函数又叫顶层函数或系统函数。

- isNaN(x) 检查参数是否是非数值

    - x为非数字则返回true否则false；NaN即 not a number

    - 常用其检测parseInt()/Float()的解析结果,以判断它们表示的是否是合法数字

- String() 把对象值转换为字符串

- Number() 把对象值转换为数字

- eval() 解析某个字符串并执行其中的代码,该方法只接受字符串为参数

- escape() 编码字符串(返回已编码的string副本)
    -   该方法不对ASCII字母和数字(a-z A-Z 0-9)及“+ - * / @ . _”共69个字符编码,主要防止特殊字符造成计算错误 

- unescape() 对"escape()"编码的字符串进行解码      

- encodeURI() 把字符串编码为URI,其中有82个字符不对其编码,防止特殊字符造成URI传递错误 

- decodeURI() 解码某个编码的URI

##### 4.3 改变函数内部this指向的方法

- call()

    - 作用:调用函数以及改变函数中this的指向

    - 如: fun.call(funName,实参,实参) 即调用了fun函数并且fun中的this指向funName

    - call()方法只是调用了父构造函数,this指向发生改变,不是真正的继承,它只能使用父构造函数中的属性,原型对象中的属性和方法子类依然拿不到

    - ```javascript
        function fun(x,y) {
          console.log("武");
          console.log(x + y);
        }
        let person = {name: 'xiao'};
        fun.call(person,1,2);
        ```

        

- apply()

    - 使用方法和call()方法相同,只是传参时参数为数组不为单个参数

    - 主要应用:借助数学内置对象求最大/小值

    - ```javascript
        let arr = [1,2,3];
        let newArr = Math.max.apply(Math,arr);
        console.log(newArr); // 3
        ```



- bind()

    - 作用:不调用函数,只改变原函数this指向并返回新函数

    - 如: `let newfun = fun.bind(objName,实参,实参)`

    - ```javascript
        let obj = {age:18};
        function fun(a,b) {
          console.log(this);
          console.log(a + b);
        }
        let fu = fun.bind(obj, 1, 2);
        fu(); 	// obj  3
        ```

    - 应用:某些函数不需立即调用但调用时又需改变函数内this指向

    - 例:禁用某个按钮,一定时间后启用

    - ```javascript
        btn.onclick = function () {
          this.disabled = true;
          setTimeout(function () {
            this.disabled = false;  // 定时器中的this指向window,bind调用时通过bind改变this指向
          }.bind(this),2000)
        }
        ```

        

- 每个函数都包含两个非继承而来的方法 apply()和call(),这两个方法都是在特定的作用域中调用函数,实际上等于设置函数体内this对象的值 ,本质上都一样,只是传参形式不同 ;这两种方法常用来扩充函数运行的作用域即改变函数中this的指向而非单纯传参


##### 4.4 匿名函数与闭包

- 匿名函数

    - 指没有函数名称的函数，可有效避免全局变量污染及函数名的冲突
    - 函数表达式：将声明的函数赋值给一个变量,通过变量完成函数调用和传参

    - 匿名函数定义和调用方法：

        - 赋值给一个变量“fn”,利用“fn()”调用

        - 自调用“(函数)(实参)” 传递实参并立即执行此函数

        - 将函数赋值给一个指定事件,比如“onclick” 

-  闭包

    - 有权限访问另一个函数作用域中变量的函数，本质上闭包是连接函数内外部的桥梁

    - 用途：通过闭包可以访问局部变量;可以让这些变量的值始终保存在内存中 ;延伸变量作用范围
    
    - 优点：避免了使用全局变量,命名冲突 

    - 缺点：闭包里作用域返回的局部变量资源不会被立刻销毁回收,可使变量一直保存在内存中，会占用更多内存；过度使用会降低程序处理速度，造成性能降低

    - 案例：使用闭包点击li显示其索引
    
        - 核心:写一个立即执行的匿名闭包函数
    
    - 创建方式：在一个函数中嵌套另一个函数
    
        ```javascript
        function fun() {
            let a = 10;
            return function fn() {
              console.log(a);
            }
          }
          let f = fun(); // 此时 f=fn(){console.log(a)}
          f(); // 10   另:由于形成了闭包,函数f若不调用则a会一直存在不被销毁
        
        // 外部要想访问到a,访问方式：1.fun()()  2.var str=fun(); str()
        // 方式1每次调用fun时会执行函数里的所有内容,从上到下依次执行,即a每次都会初始化 
        // 方式2每次调用时只是调用的嵌套函数,a只会初始化一次,嵌套函数用到a时只会向上搜索
        // 方式1和2调用的区别如下
        ```
        
        ```javascript
        // 方式1：
        function fun() {
          let a=100;
          console.log('调用一次弹一次');
          return function(){
        		a++;
         		console.log(a);
           }
        }
        fun()(); 	// 101
        fun()(); 	// 101
        // 每次调用时整个函数从头开始运行,a每次都被初始化,会弹出两次“调用一次弹一次” 故调用两次a均为101 
        /*------------------------------------------------*/
          // 方式2:
        function fun() {
           let a=100;
           console.log('只弹一次');
           return function(){
        			a++;
        			console.log(a);
           }
        }
        let b=fun(); // 此时函数fun已运行,a已被初始化且由于return此时b=function(){a++;console.log(a);}
        b(); //101
        b(); //102
        b=null; // 不再使用将其赋值为null,避免占用内存
        // 赋值b时函数fun则会运行,a会被初始化且“只弹一次”会弹出,b等于函数fun运行后的return结果,调用b时调用的是里面的匿名函数,故a会累加,第一次101,第二次102
        ```

 

##### 4.5 循环函数中的匿名函数和闭包

- 循环函数中的匿名函数

    ```javascript
    function fun() {
    	var arr=[];
      for(var i=0; i<5; i++) {
    		arr[i] = function() {
    			return '元素' + i;
    		}
    	}
    	return arr;
    }
    var bn = fun();
    console.log(bn); // 5个函数
    console.log(bn.length); // 结果为“5”
    console.log(bn[0],bn[1],bn[2],bn[3],bn[4]); // 5个匿名函数
    console.log(bn[0]()); // “元素5”
     // 因为闭包内的函数没有立即执行，循环结束后得到的只是5个匿名函数，此时“i”由于循环结束变为了“5”，当再调用时调用的已经是匿名函数了，匿名函数的值为“元素i”,此时i已经变为了“5”
    ```

    ```javascript
    function fun() {
      var arr = [];
      for(var i = 0; i < 5; i++) {
    		arr[i] = function() {
    			return '元素'+i;
    		}();
    	}
    	return arr;
    }
    var bn = fun();
    console.log(bn); // 此时会得到数组“元素0-4”
     // 因为在每次执行循环时函数都立即执行,函数参数按值传递,会及时的将值return出去
    ```

    

- 循环函数中的闭包

    ```javascript
    // 1. 不传参不立即执行
    function fun(){
       var arr = [];
       for(var i = 0; i < 5; i++){
    			arr[i] = function() {
     				return function(){
      				return '元素'+i;
     				}
    			}
     	}
      return arr;
    }
    var bn=fun();
    console.log(bn[0]()); 		// 结果依然为一个匿名函数
    console.log(bn[0]()()); 	//“元素5”
     // 注意:bn是一个集合,不可写成bn(),而是bn[0-4]()
    ```

    ```javascript
    // 2. 传参并立即执行
    function fun(){
      var arr=[];
      for(var i = 0; i < 5; i++){
     		arr[i] = function(n) {
    			return function() {
    				return '元素'+n;
    			}
    		}(i);
     	}
      return arr;
    }
    var bn = fun();
    for(var i=0; i < 5; i++){
       console.log(bn[i]); // “function(){return '元素'+i}”
       console.log(bn[i]()) // 数组“元素0-4”
    }
    // 注意:此时的“n”只是一个形参 在“i”传参并立即执行时,由于函数按值传递,第一次循环时“i”为0,拷贝0赋值给形参“n”,第二次循环时“i”为1,拷贝1赋值给形参“n”,即在每次调用匿名函数时都会传入变量“i”,并将变量“i”的当前值传给形参“n”,即每次调用匿名函数都会在其内部创建一个局部变量“n”并赋值,这就是闭包可将局部变量保存在内存中
    ```

    

#####  4.6 闭包中的this

- 匿名函数的执行具有全局性,this通常指向window

- 访问闭包中的变量：

    - 使用call()或apply()方法对象冒充强制改变this指向

        ```javascript
        var name='window';
        var obj={
           name:'myobj',
           get: function() {
          		// 若在此处添加this 则this作用域在匿名函数内 this指向obj 因为匿名函数是obj的对象
          		return function(){
           			return this.name; //此处this的作用域仅在闭包内 指向get 因为是get的方法 
          		}
           }
        }
        console.log(obj.get()()) // 结果为“window”
        console.log(obj.get().call(obj)) // 结果为“myobj” call()即将闭包函数中的this指向obj
        // 结果1在window作用域内调用obj的get方法,obj的“name”属性在get方法上面并未被初始化,故指向window的name属性
        // 结果2使用了对象冒充相当于在obj作用域内调用get方法，故指向obj的name属性
        ```

        

    - 将this赋值给变量,通过闭包访问这个变量 

        ```javascript
        var name='window';
        var obj={
          name:'myobj',
          get: function() {
            var that = this;
            return function(){
              return that.name; 
            }
          }
        }
        console.log(obj.get()()) // 结果为“myobj”
        // 调用get方法会将“that=this”初始化,由于this关键字,一层一层向上一级作用域寻找
        ```

        

##### 4.7 模仿块级作用域

- 块级作用域
    - 又叫私有作用域,但JS没有块级作用域的概念,这意味着块语句(比如for语句)中定义的变量不会因为离开块(离开for)失效。

    - 块级作用域：使用let声明的变量,只在{}中有效,常用于for循环中等

-  如何模仿块级作用域

    - 写一个匿名函数并让其立即执行,外部访问不到函数内部的变量即(function)()

    - 优点

        - 只要是在匿名函数中定义的变量均会在函数执行结束时销毁（最重要的一点）

        - 尽可能少向全局作用域中添加变量和函数,避免了命名冲突

        - 使用块级作用域不会扰乱全局 

        - 在全局作用域中使用块级作用域减少闭包带来的内存消耗

-  私有变量

    - 在任何函数中定义的变量都是私有变量,因为不能在函数外部访问

    - 它包括局部变量、函数的参数、在函数内部定义的其他函数

    - JS没有私有属性概念,所有的属性都是公用的

- 特权方法

    - 内部创建一个闭包,闭包可以访问私有变量,因此创建用于访问私有变量的公用方法称作特权方法

        ```javascript
        function people(){
        	var name = '张三';
        	this.getName=function(){
        		return name;
        	}
        }
        var p1 = new people();   // 注意需用new 
        console.log(p1.getName());
        ```

        

- 静态私有变量
    -  创建步骤

        - 创建私有作用域 
        - 定义私有变量或函数 
        - 定义构造函数或特权方法

        ```javascript
        (function() {             			   // 创建私有作用域 
        		var name = '张三';     		// 定义私有变量
        		User = function(){};  	// 定义构造函数 注意此时User为全局变量 
        		User.prototype.getName = function(){
        				return name;
        			}
        		User.prototype.setName = function(value){
        				name = value
        			}
        })()
        var p1 = new User();
        console.log(p1.getName());  	// “张三” 
        p1.setName('李四');
        console.log(p1.getName());  	// “李四” 
        ```

        

    - 这种方式创建的变量使用原型实现共享,此时的User可被多个实例共享,但也由于共享导致实例没有自己的私有变量

##### 4.8 箭头函数与回调函数

- 箭头函数

    - 箭头前为传递的参数,箭头后为函数体

    - 用法

        - 标准用法: `(p1,p2,...pn) => { statements }`

        - `(p1,p2,...pn) => { return expression;}` 或 `(p1,p2,...pn) => expression`
            - 函数体只有一条语句可省略“{}”且函数体只有一条返回值语句时可同时省略“{}”和“return”关键字

        -  `(p1) => { statements }` 或 `p1 => {statements}`
            - 只有一个参数可省略“()”

        -   `() => {statements}` 或 `_ => {statements}`
            - 无参时箭头前需有“()”或“_”

    -  箭头函数不绑定this,即this指向函数定义位置的上下文,也就是创建时的this是谁,则运行时的this就是谁
    - 如函数中定义了箭头函数,则箭头函数中的this指向函数中的那个this对象,即this指向的是上一级作用域下的this

- 剩余参数

    - 实参大于形参个数时,形参args代表一个数组接收剩余参数(可和解构综合使用)

    - 如:`fun(a,b,...args){}` 箭头函数中不能使用arguments,得用args

- 回调函数

    - 函数A作为参数传递给函数B并在B内调用A,此时称A为回调函数 

    - 匿名函数常用作函数的参数传递实现回调

        ```javascript
        function cal(num1,num2,fn) {
        		return fn(num1,num2);
        }
        console.log(
          cal(45,55,function (a,b) {
        		return a+b;
        	})
        );
        console.log(
          cal(45,55,function (a,b) {
        		return a*b;
        	})
        )
        ```

    - 通过在函数体中设置回调函数,可根据调用时传递不同的参数在函数体特定位置实现不同功能,相当于在函数体内根据用户需求完成了不同功能的定制

    - JS内置回调函数方法:
        -  find() every() some() forEach() map() reduce() reduceRight()等 

##### 4.9 函数嵌套与递归 

- 嵌套函数

    - 在一个函数内部存在另一个函数的声明

    - 作用域链：对于嵌套函数来说,内层函数只能在外层函数作用域内执行,在内层函数执行的过程中,若需要引入某个变量，首先在当前作用域中寻找,若未找到则继续向上一层级的作用域寻找,直到全局作用域,这种链式的关系称为作用域链

-  递归函数

    - 一个函数在内部可以调用本身,那么这个函数就是递归函数

    - 递归作用和循环效果一样,但递归容易发生栈溢出错误(stack overflow),故需加退出条件return

    - 属嵌套函数调用中的特殊调用(注:需设置出口,否则变为死循环)

    - 递归函数在遍历维数不固定的多维数组时合适,但它占用的内存和资源较多同时难以实现和维护,谨慎使用
    
        ```javascript
        // 典型的递归函数: 阶乘
        function fun(n) {
          if (n == 1) {
          		return 1; 	//递归出口
          }
          return n * fun(n-1);
        }
        console.log(fun(3));  // 6
        
        //  斐波那契数列:
        //  第一二项值为1,从第三项开始,当前项值等于前两项之和 如: 1 1 2 3 5 8 13...
        //  随意输入第n项,就可求得n所对应的值
        function fun(i) {
          if (i == 1 || i == 2) {
            return 1;
          }
          return fun(i - 1) + fun(i - 2);
        }
        console.log(fun(7));  // 13
        ```



------

#### 第五章：对象

##### 5.1 概述

- 字面量:在源代码中一眼就能知道其数据值和类型的量 ,如:123(数值型) `[123]`(数组) )

- 对象:由属性和方法组成,属性的实质是变量,方法的实质是函数

- Object:对象 在JS中所有的对象都继承自object

- 面向对象

    - 把事务划分为多个对象,以对象功能来划分并解决问题

    - 特征

        - 封装性:隐藏内部细节,只对外开放接口(即对象的方法),无论内部多复杂用户只需知道接口如何用即可 
            - 优势:无论对象内部如何复杂如何修改,只要接口不变就不会影响使用

        - 继承性:一个对象继承另一个对象的成员,从而在不改变另一个对象的前提下进行扩展
            - 优势:可以在保持接口兼容的前提下对功能进行扩展,且增强了代码的复用性,为程序修改和补充提供便利

        - 多态性:同一个操作作用于不同对象会产生不同的执行结果
            - 多态实现往往离不开继承,因为当多个对象继承了同一个对象后获得相同方法,然后根据不同需求改变同名方法执行结果
        
    - 优点:灵活、代码可复用、易于维护和开发,基于三大特性设计出的系统耦合度较低
    
    - 缺点:性能比面向过程低
    
    - 思维特点
    
        - 抽取对象的共用属性和行为封装成类
    
        - 对类进行实例化,获取类的对象
    
- 面向过程

    - 定义:依据分析好的步骤,按照步骤解决问题

    - 优点:性能高适合跟硬件紧密联系的东西,例如单片机的编程

    - 缺点:不如面向对象易于维护、复用和扩展

##### 5.2 自定义对象:

- 创建对象的方法:

    - `var A=new Object(); A.name='逍遥';` 
        - 通过new关键字,此种方式创建过程叫做实例化,得到的对象称为构造函数的实例

    - `var A={}; A.name='逍遥';` 
        - 创建空对象再对其添加成员

    -  `var A={name:'逍遥',age:18}` 
        - 直接创建

-  访问对象方式

    - objName.key
    - objName['key']

    - JS中对象具有动态特征,如果一个对象无成员可手动赋值属性或方法来添加成员

    - 对象没有赋值的属性,该属性值为undefined

-  遍历对象成员

    - for...in语法 (此语法可遍历数组和对象)
    - value in objName  判断某对象是否有某个成员,返回值true/false

    - delete objName.key "delete"可以删除对象

##### 5.3 自定义构造函数

- 基本模式 
    - 缺点：
        - 创建多个对象就会比较繁琐
        - 实例与原型之间看不出联系 

- 工厂模式(函数)

    - 即在一个函数内部创建一个对象,每次创建新对象时只需调用此函数并传入相关参数即可

    - 注:在函数内部需将创建的对象return出去,即完工后的出口 

    - 缺点:

        - 创建的实例无内在联系,不能反映出是同一个原型对象的实例
        - 创建对象时未使用new关键字
        - 资源浪费,每生成一个实例都会增加一个重复的内容

    - ```javascript
        function create(name,weapon) {
        		var per = new Object();
        		per.na = name;
        		per.wea = weapon;
        		per.run = function () {
        				return this.na + '的武器是' + this.wea;
        		}
        		return per;  	// 此步看做出厂,必须有
        }
        var p1 = create('孙悟空','金箍棒');
        console.log(p1.run()); 	//“孙悟空的武器是金箍棒”
        ```

        

- 构造函数

    - 特殊的函数主要用来初始化对象,即为对象成员变量赋初值,与new一起使用，一般将对象中共用的属性和方法放抽取到这个函数中

    - new在执行时的过程:
        - 创建空对象
        - 让this指向这个空对象
        - 执行构造函数中的代码给对象添加属性及方法
        - 返回这个新对象(故构造函数中不需要再手写return)

    -  构造函数成员

        - 实例成员:在函数内部通过“this”添加的属性或方法，只能通过实例化的对象来访问

        - 静态成员:直接通过构造函数名添加的属性或方法，只能通过构造函数名来访问

    - 缺点：函数内部创建方法时,方法为函数,每一个实例化的对象都会为其创建一个新的地址存放函数,浪费内存

    - instanceof 验证实例对象与原型对象之间的关系, 用法：A instanceof B 返回值true/false

    - ```javascript
        function create(name,weapon) {
        		this.na = name;		// 实例成员 只能通过“p1.name”来访问name
        		this.wea = weapon;
        		this.run = function() {
        				return this.na + '的武器是' + this.wea;
        		}
        }
        create.sex = man; // 静态成员 只能通过create来访问sex
        var p1= new create('孙悟空','金箍棒');
        console.log(p1.run());  	//“孙悟空的武器是金箍棒”
        var p2=new Object();
        create.call(p2,'妖怪','葫芦');			// call()和apply()方法做对象冒充 两种方法本质类似,只是传参方式不同而已
        // create.apply(p2,['妖怪','葫芦']);
        console.log(p2.run());  	//“妖怪的武器是葫芦”
        ```
        
        

- prototype原型模式

    - JS规定每一个构造函数都有一个prototype属性指向另一个对象,这个对象的所有属性和方法会被构造函数的实例继承,因此可以将那些不变的属性和方法直接定义在prototype对象上

    -  此方式定义,实例化对象时prototype对象就可以被引用而非拷贝,节省资源

    - ```javascript
        // 创建方式1
        function create(){};
        create.prototype.na='喽啰';   	// 此时创建的原型字面量直接指向构造函数create() 
        create.prototype.wea='大刀';
        create.prototype.run=function(){
        	return this.na+'的武器是'+this.wea;
        }
        /*-------------------------------------------------------------*/
        // 创建方式2
        function create(){};
        create.prototype = {
        	 constructor: create, // 强制指向create()不加此行代码也可,就是和方式1指向不同 当需该指向则加 
        		na: '喽啰',  // 此时创建的字面量指向创建对象create.prototype而非create(),故添加constructor 
        		wea: '大刀',
        		run: function() {
        			return this.na + '的武器是' + this.wea;
        		}
        } 
        var p1=new create();
        console.log(p1.run());  // “喽啰的武器是大刀”
        ```

    - 说白了原型模式就是多了一个prototype属性，将共用的属性及值封装到prototype中,用时直接调用即可

    - isPrototypeOf属性用来判断某个prototype对象和实例的关系 

        - 用法：create.prototype.isPrototypeOf(p1)

    - hasOwnProperty属性用来判断某个实例是否有自己的prototype 

        - 用法：p1.hasProperty.('na') 
        - 如果p1的'na'属性是继承自prototype,而非自已的本地属性则返回false

    - in运算符判断某个实例是否有某个属性,不管它是自己的本地属性还是继承的prototype 
        - 用法：'na' in p1

    - 缺点:

        - 构造函数不能传参,使用原型不能通过给构造函数传参来初始化实例属性

        - 方法(即内部创建的函数)和对象均可被共享,但对象一般很少被多个实例共享,实例一般有自己的对象

- 构造函数和原型组合模式

    - ```javascript
        function create(name,weapon) {
        		constructor: create;
        		this.na = name;
        		this.wea=weapon;
        }	
        create.prototype = {
        		run: function(){
              return this.na+'的武器是' + this.wea
            }
        }
        //写成这样更好理解 create.prototype.run=function(){return this.na+'的武器是'+this.wea}
        var p1=new create('喽啰',['大刀','长矛']);
        console.log(p1.run()); 	//“喽啰的武器是大刀,长矛”
        ```

    - 和构造函数相比就是把共用属性放在了prototype属性上,调用时引用此属性而不是像构造函数那样复制,节约资源,除此外无差别。

    - 瑕疵: 封装性差了点,因为分成了两个而非一个函数

- 动态原型模式

    - ```javascript
        function create(name,weapon) {
        		this.na = name;
        		this.wea = weapon;
        		console.log('开始初始化');
        		create.prototype.run = function() {
              return this.na + '的武器是' + this.wea
            }
        		console.log('结束初始化');
        }
        var p1 = new create('喽啰','大刀');
        var p2 = new create('小兵','长矛');
        //由于p1和p2均为构造函数,在创建时会进行初始化,因此即使未调用方法,即没有下面的console.log语句仍会弹出两次“开始/结束初始化”
        console.log(p1.run());
        console.log(p2.run());
        
        // 多个对象实例化时此时会出现问题,即在方法调用前后需初始化,但只初始化一次即可,此时这种写法会造成每个实例在创建时都开始进行初始化,即即使未调用方法依然会弹出初始化,解决办法如下
        ```

        ```javascript
        function create(name,weapon){
        		this.na=name;
        		this.wea=weapon;
        		if(this.run != 'function') {
        			  console.log('开始初始化');
        				create.prototype.run = function(){
                  return this.na + '的武器是' + this.wea;
                }
        				console.log('结束初始化');
        		}
        }
        ```

-  工厂模式和构造函数模式每次实例化对象都会给对象创建新的地址,即函数拷贝到每一个实例中,而不是引用地址 造成资源浪费

##### 5.4 继承

- 父类、子类
    - 父类又叫超类、基类
    - 子类的实例可以共享父类的方法
    - 子类可以覆盖或扩展父类的方法
    - 子类和父类都是子类实例的类型

-  继承方式：

    - 对象冒充(又叫构造函数绑定) 

        - 原理:使用对象冒充（call或apply方法,实质是改变this指针指向）继承基类

        - 一个子类可继承多个父类,注意传参顺序及数量

        - 缺点:由于是构造函数,函数传参是按值传递造成资源浪费

        - ```javascript
            function monkey(type,home){
            	this.ty = type;
            	this.ho = home;
            }
            function magic(hp) {
            	this.h = hp;
            }
            function magic_monkey(type,home,hp) {
            	monkey.call(this,type,home);    // 冒充第一个父类的对象
            	magic.call(this,hp);            				// 冒充第二个父类的对象
            	this.skill = '七十二变';
            }
            var wukong=new magic_monkey('猴子','花果山','生命值');
            console.log(wukong.ty);  // “猴子”
            console.log(wukong.ho);  // “花果山”
            console.log(wukong.h);  //  “生命值”
            console.log(wukong.skill);  // “七十二变”
            ```

    - 原型链继承

        - 缺点:只能继承一个父类的prototype属性,因为前者会被后者覆盖

        - ```javascript
            function monkey(){};
            monkey.prototype.ty = '猴子';
            monkey.prototype.ho = '花果山';
            function magic(){};
            // 此处相当于清空了magic的原prototype属性,再将monkey的prototype赋值给magic
            magic.prototype = new monkey();  
            magic.prototype.skill = '七十二变';  // 添加新属性需在清空并赋值后添加,否则仍会被清空
            var wukong = new magic();
            console.log (wukong.ty); // “猴子”
            console.log (wukong.skill);  // “七十二变”
            ```

    - 混合继承

        -  用构造函数继承父类的对象,用原型链继承父类的方法

        - 借用构造函数继承父类型属性核心原理:通过call方法将父类型中的this指向子类型的this,实现子类型继承父类型的属性
        
        - ```javascript
            function Parent(name,age) {
              this.name = name;
              this.age = age;
            }
            Parent.prototype.sing = function () {
              console.log('子构造函数不能只通过call方法拿到父构造函数原型的属性及方法')
            }
            function Son(na,ag,score) {
              Parent.call(this,na,ag)
            }
            // Son.prototype = Parent.prototype; // 不可直接赋值,因为这样为浅拷贝,修改子构造函数原型上的方法父也会改变
            Son.prototype = new Parent(); // 原型链中实例对象可通过“.__proto__”指向原型故子对象原型可间接指向父对象原型
            Son.prototype.constructor = Son;  // 需将Son的constructor再指回Son,因为上一步new时子原型对象中的所有内容被覆盖了 因此赋值时注意等号左边仅仅是个变量还是类似原型对象这种有隐含属性的对象
            Son.prototype.exam =function () {
              console.log('此时给子构造函数原型已实现继承并能追加自己独有的方法');
            } 
            let son = new Son("武",18,99);
            ```
            
            

##### 5.5 内置对象

- String对象

    - `str.length`

    -  `str.charAt(x)`    返回字符串str在x位置的字符 (at即在..位置的意思)

    -  `str.charCodeAt(x)`  返回在x位置的字符的unicode编码 

    -  `str1.concat(str2)`  str1连接str2

    -  `str.slice(n,m)`   提取str中[n,m)之间的字符串 (slice适用于字符串和数组)

    -  `str.substring(n,m)` 效果同slice 当n、m为负值时效果不同 (只适用于字符串不适用于数组)

        -  `str.substring(3,-2)` 只要参数为负值,此时均为0,取值区间变为[0,3) 若两参数均为负则为[0,0)取空

        -  `str.substring(-2,3)` 效果同上

    -  `str.substr(n,m)`   从n开始,提取m个字符
        -  str.substr(-5,3)  从右向左数到第五个字符,从此位置向右取3个字符 若第二个参数为负则取空 (注意:因为第二个参数含义代表取几个字符)

    -  `str.split(x,num)`  str中有x,则以x为分割符将其分割为字符串数组,否则str变为只有它本身的字符串数组 (相当于未分割,只是变为了数组而已 ；number为可选参数,即将字符串分为几个数组 ；若number小于理论,后面的则被去掉)

    -  `str.toLowerCase()`  转为小写

    -  `str.toUppererCase()` 转为大写

    -  `str.replace(str1,str2)` 使用str2替换str中的str1

    -  `str.indexOf(va)`   获取va在str中首次出现的位置

    -  `str.lastIndexOf(va)` 获取va在str中最后出现的位置

    -  注:JS中的字符串是不可变的，string类定义的方法都不能改变字符串的内容,string方法返回的是全新的字符串而非改变原字符串

- Number对象
    - `num.toFixed(n)` 四舍五入保留小数点后n位 (无参数则保留正整数) 

- Math对象

    -  `Math.PI()`

    -  `Math.max(a,b,c..)`  获取最大值 

    -  `Math.min(a,b,c..)` 获取最小值

    -  `Math.abs(x)`  绝对值 

    -  `Math.sqrt(x)` 平方根 

    -  `Math.pow(x,y)` x的y次方

    -  `Math.ceil()` 数值上舍入 (小数舍去个位进一)

    -  `Math.floor()` 数值下舍入 (小数舍去)

    -  `Math.round()` 四舍五入取整 

    -  `Math.random()` 0-1之间的随机数 [0,1)含0不含1 

        -  要返回某一区间的随机数,有规律可循 `return Math.floor(Math.random()*(high-low+1)+low)`

        -  如:(3,13)  `return Math.floor(Math.random()*(13-3+1)+3)`

- Date对象:

    -  创建日期的四种方法

        - `var datename=new Date()` 无参数,返回当前时间

        - `var datename=new Date(milliseconds)` 参数为毫秒,返回自1970年加上毫秒数的总日期

        - `var datename=new Date(year,month,day)` 返回参数中的年月日,时分秒均为0

        - `var datename=new Date(year,month,day,hour,minter,second)` 返回参数中的年月日时分秒

        - 月份是从0开始的,实际输出需month加1

    - 获取时间的几种方法

        - 先创建好 `var datename=new Date()`
        - `date1=datename.toString()` 获取当前时间,以年月日时分秒输出(24小时制符合外国方式)

        - `date1=datename.toDateString()` 获取当前时间的年月日部分

        - `date1=datename.toTimeString()` 获取当前时间的时分秒部分

        - `date1=datename.toLocaleString()` 获取当前时间以年月日时分秒输出(12小时制且符合国人方式)

        - `date1=datename.toLocaleDateString()` 获取当前时间的年月日部分(符合国人方式)

        - `date1=datename.toLocaleTimeString()` 获取当前时间的时分秒部分(符合国人方式)

        - `date1=datename.valueOf()` 当前时间减去1970年的毫秒数

        - `date1=datename.getTime()` 当前时间减去1970年的毫秒数

        - `date1=datename.getFullYear()` 获取当前时间的年

        - `date1=datename.getMonth()` 获取当前时间的月

        - `date1=datename.getDate()` 获取当前时间的日 (1-31)

        - `date1=datename.getDay()` 获取当前时间的周几 (0-6) (注意:需自己写函数表示"周")

        - `date1=datename.getHours()` 获取当前时间的小时 (0-23)

        - `date1=datename.getMinutes()` 获取当前时间的分 (0-59)

        - `date1=datename.getSeconds()` 获取当前时间的秒 (0-59)

        - `date1=datename.getMilliseconds()` 获取当前时间的毫秒 (0-999) (注意"s"小写)

    - 自定义设置时间(设置时语法同上稍有差异)

        - ```javascript
            var datename=new Date();
            datename.setMonth(5);
            date1=datename.getMonth();
            console.log(date1);
            // 先对datename传入参数,再用一个变量去接收,然后输出变量
            ```

        - `datename.setFullYear()` 设置当前时间的年

        - `datename.setMonth()` 设置当前时间的月

        - `datename.setDate()` 设置当前时间的日 (1-31)

        - `datename.setDay()` 设置当前时间的周几 (0-6) (注意:当年月日都设置好后周几已经确定了,此时无法再自定义)

        - `datename.setHours()` 设置当前时间的小时 (0-23)

        - `datename.setMinutes()` 设置当前时间的分 (0-59)

        - `datename.setSeconds()`设置当前时间的秒 (0-59)

        - `datename.setMilliseconds()` 设置当前时间的毫秒 (0-999) (注意"s"小写)
    
- Object.defineProperty()

    - Object.defineProperty(objName,key,description) 定义新属性或修改原属性

    - description写为对象“{}” 里面有四个属性值 

        - “value:” 设置属性“key”的值

        - “writable:true/false” 属性key的值是否可重写,默认false

        - “enumerable:true/false” 属性key能否被枚举(即遍历),默认false

        - “configurable:true/false” 属性key是否可被删除或属性里的特性(指的是writable等而非key的属性值)能否被再次修改,默认false

##### 5.6 字符串与数字转换

- `new String()`  通过new关键字创建字符串对象

- `A.length`    返回A的长度

- `A.toString()`  将数值A转换为字符串

- `A.toString(x)`  将数值A转换为x进制的整数

- `parseInt(A)`   将字符串类型的A转换为整数

    - 被解析的字符串需以数字开头,否则无法解析

    - 在解析过程中遇到非数字,解析就会结束,只解析未遇到非数字前的那部分

- `parseFloat(A)`  将字符串类型的A转换为浮点数

- `Number(A)`    将字符串类型的数值A转换为数值



------

#### 第六章：Web API

##### 6.1 基础概念

- JS由ECMAScript(JS基本语法、数组、函数和对象)、BOM和DOM组成

- API即接口函数， Web API即提供给浏览器(BOM)和页面元素(DOM)的函数

- 文档状态 readyState

    - uninitialized 还未开始载入

    - loading 载入中 

    - interactive 已加载,可以开始交互

    - complete 加载完成

##### 6.2 BOM

- 即 Browser Object Model 浏览器对象模型 

    - 作用：可以用它移动窗口、改变窗口大小、打开、关闭窗口、弹出对话框等 

    - 最大作用：提供了访问html页面的入口，即document对象  

- window对象

    - 调用时可省略“window”直接调用对象和方法

    - 弹框

        - `console.log()` 即`windows.console.log()` 只有确认按钮

        -  `confirm()` 显示提示用户输入的对话框,有确认和取消按钮,返回布尔值1/0

        -  `prompt(语句1,语句2)` 语句1为显示窗口提示信息,语句2为默认输入语句
            -  有确认和取消按钮
            - 确认返回“语句2”或“用户输入的语句”,若传入大于两个参数则后面参数无效
            - 取消则返回null

    - 窗口对象

        - `open(url,name,specs,replace)`

        - 指定url则新窗口打开地址，无url则打开新空白窗口

        - name指定target属性或窗口名称，可选值如下

            - _blank 新窗口加载 
            - _self 当前窗口加载 
            - _parent 父框架加载(效果等同self)

            - _top 替换任何可加载的框架集 
            - name 窗口具体名称 

        - 当有多个open(url,name)时,若name相同则只打开一个,否则都打开

        - specs

            - 设置窗口特征,设置时需用“,”将特征分割开

            - 常用width/height/left/top 
            - 不常用toolbar(显示工具栏)/resizable(大小可调)等

            - 设置specs时需有name属性,否则无效

        - replace(默认false) true替换浏览历史中的当前条目
        - close()关闭窗口

        - moveTo(px,px) 窗口移动到左上角的距离

        - moveBy(px,px) 窗口每次移动的距离

        - resizeBy(px,px) 窗口每次增大或减小(px为负值)的大小

        - resizeTo(px,px) 窗口增大或减小到(px为负值)

        - innerWidth/Height 返回窗口文档显示区的宽度/高度(即分辨率)

    - 定时器:
        - `setInterval(function,time) `

            - 按照指定周期(毫秒计)不断的调用函数 ,其返回值即定时器ID为number

            - 调用方法有两种：
                - (function,time) 直接写函数调用 
                - (str,time) 将函数赋值给变量操纵变量调用 

        -  `setTimeout(function,time)` 
            - 在指定的时间后(毫秒计)调用函数一次,其返回值即定时器ID为number

        -  `clearInterval(str)` 取消定时

        -  `clearTimeout(str)` 取消延时

    - history对象

        - `history.length`  查看浏览器历史记录访问过页面的个数

        - `history.back()` 第一次跳转到此页面的那个url(即相对本页面的上个url),此时返回到上个url 

        - `history.forward()` 此页面第一次跳转到另一个(即下一个)url,此时会再次跳转到那个url 

        - `history.go(number)`  number为正,跳到它的下几页否则为上几页

    - Location(地址栏)对象

        - 属性

            - location.href='xxx'或loaction.href 设置或返回完整的url

            - location.host  设置或返回主机名和当前url的端口号

            - location.hostname 设置或返回当前url的主机名

            - location.port  设置或返回当前url服务器的端口号
            - ......

        - 方法

            - location.assign('url')    加载新的文档

            - location.reload(true/false)  重新加载当前文档

                - 无参数/false 检查文档是否已变,若变则重新下载否则从缓存中加载文档

                - true 无论文档最后更改日期是何时,均会绕过缓存重新下载

            -  location.replace() 以新文档替换当前文档,在history中不生成新的历史记录,而是将当前记录替换掉

    - Screen对象

        - screen.availWidth/Height 返回显示屏宽高(不包含windows任务栏)

        - screen.Width/Height 返回显示屏宽高(包含windows任务栏)

        - screenLeft/Top 返回相对于屏幕窗口的X/Y坐标 (Firefox不支持)

        - screenX/Y 返回相对于屏幕窗口的X/Y坐标 (IE8不支持)
        - .......

    - Navigator(浏览器)对象属性

        - navigator.appCodeName 返回浏览器代码名

        - navigator.appVersion 返回浏览器平台及版本信息

        - navigator.appMinorVersion 返回浏览器次级版本

        - navigator.platform 返回运行浏览器的操作平台
        - ......

##### 6.3 DOM

- 即 Document Object Model 文档对象模型

- 操作HTML元素

    - 获取HTML文档对象的方法：

        - getElementById()  通过ID对象获取 注意：element是单数因为ID唯一 (括号内参数需加'')

        - getElementsByName()  通过name对象获取 注意：elements是复数 获取到的对象是个数组

        - getElementsByTagName() 通过标签对象获取 注意：elements是复数 获取到的对象是个数组

        - getElementsByClassName() 通过类对象获取 注意：IE678不兼容

    -  获取元素内容和标签名称:  

        - Element.innerHTML 设置或返回对应的HTML 

        - Element.innerText 设置或返回对应的去除所有标签及格式的纯文本 

        - Element.textContent 设置或返回对应的保留格式的纯文本 

        - Element.tagName  返回对应的元素标签名

        -  注：当获取某个元素的class名时,需写为.className

    - 元素属性及方法

        - 属性:Element.attributes 返回一个元素的属性集合

        - 方法:

            - Element.setAttribute(name,value) 设置或改变指定属性的值

            - Element.getAttribute(name) 返回指定元素的属性值

            - Element.removeAttribute(name) 删除元素的指定属性

        - classList属性: Element.classList.length 获取元素类名的个数

        -  方法:

            - Element.classList.add() 给元素添加类名,一次添加一个

            - Element.classList.remove() 移除指定类中的CSS样式而非将类删除,即类名仍有但此类的样式为空

            - Element.classList.contains() 判断元素是否包含指定类名,返回值true/false

            - Element.classList.toggle() 切换元素样式(若元素之前无此类则添加,否则删除)

            - Element.classList.item() 获取与索引对应的元素类名

    - 高级选择器

        - document.querySelector('selectors')  selectors可为 id/class/标记/兄弟选择器/后代选择器等css中选择器，查找时返回第一个满足条件的元素

        - document.querySelectorAll('selectors')  查找时返回所有满足条件的元素，返回结果是个集合，但查找结果非实时的，即动态添加的查询不到。

        - document.getElementsByClassName('selectors') 返回文档中所有指定类名的元素的集合

    - 元素样式
        - Element.style.CSSname 
        - CSSname需驼峰式写法,如text-shadow需写成textShadow

- 操作DOM节点

    - 获取DOM节点

        - Element.firstChild 
        - Element.lastChild 

        - Element.nodeName 当前节点名称 
        - Element.nodeValue  当前节点值

        - Element.nextSibling 下一个兄弟节点 
        - Element.previousSibling 上一个兄弟节点

        - Element.parentNode 当前元素的父节点 
        - Element.childNodes 当前元素子节点的集合

    - 节点增删(先创建节点再给节点添加属性,再将节点追加到元素中或从中删除)

        - document.createElement() 创建元素节点

        - document.createTextNode() 创建文本节点

        - document.createAttribute() 创建属性节点

        - Element.appendChild() 当前元素子节点末尾添加节点

        - Element.insertBefore() 插入到指定子节点之前

        - Element.getAttributeNode() 返回当前节点

        - Element.setAttributeNode() 设置或改变当前节点

        - Element.removeChild() 删除元素节点

        - Element.removeAttributeNode() 删除元素属性节点

        ```javascript
        // 如：
        var h=document.createAttribute('align') 
        h.value='center' 
        div.setAttributeNode(h)
        ```

        

##### 6.4 事件 

- 事件处理

    - 事件流：事件发生时,从元素节点到DOM树根节点之间按特定顺序进行传播的过程

    - 传播顺序

        - 捕获方式:事件流从DOM树根节点到发生事件的元素节点

        - 冒泡方式:事件流从发生事件的元素节点到DOM树根节点 

        - 不是所有事件都能冒泡如：blur、focus、load、unload 不可冒泡

    - 事件监听与移除
        - 监听：DomObj.addEventListener(type,callback,[capture])
            - type为事件类型,如click 
            - callback为要处理的程序函数 
            - [capture]默认false冒泡处理；true则为捕获处理
        - 移除:DomObj.removeEventListener(type,callback)

- 事件对象

    - 获取对象：函数传参e，如 fun(e){} 注:event简写为e

    - 属性和方法

        - e.type 返回当前事件类型

        - e.target 返回触发此事件的元素

        - e.eventPhase 返回事件当前传播阶段， 1表示捕获；2表示处于目标阶段； 3表示冒泡阶段

        - e.stopPropagation() 阻止事件冒泡

        - e.preventDefault() 阻止事件默认行为

- 事件分类

    - 页面事件

        - window.onload 页面载入完毕后触发(注:原为load,加了on)
        - window.unload 页面关闭后触发

        - img.onload=function(){} 监听图片加载完成

    -  焦点事件

        - obj.focus 获得焦点触发事件

        - obj.onblur 失去焦点触发事件

    -  鼠标事件

        - onclick 单击   

        - ondblclick 双击(dbl为double)

        - onmousedown 按下

        - onmouseup 松开

        - onmouseover 移到某元素上

        - onmouseout 从某元素移开 

        - onmousemove 在某元素上移动时

        - onchange 内容发生改变时(多用于select对象) 

    - 位置属性

        - event.clientX 事件被触发时返回鼠标指针水平坐标 (相对于整个可见区域的文档)

        - event.clientY              

        - event.screenX 事件被触发时返回鼠标指针水平坐标 (相对于用户屏幕)

        - event.screenY 

        - event.pageX 位于文档的水平坐标 (不兼容IE6~8) 

        - event.pageY 

    - 键盘事件

        - onkeydown 某个键盘按键被按下

        - onkeyup 某个键盘按键被松开

        - onkeypress 某个键盘按键(ctr/shift/alt/esc等除外)按下并被松开 (经测试,按下未松开时就触发了事件)

        - 优先顺序 down press up

        - 区别：由于event对象包含keycode属性，down和up表示按下的具体的键；press表示按下的字符,即它是区分大小写的,即它保存的是ASCII码

        - onselect 文本被选中

        - onreset 重置按钮被点击

        - onscroll 文档被滚动

        - ......

        - event.keyCode 返回键盘按下的键对应的值

        - event.which 返回键盘按下的字符对应的unicode编码值,即ASCII码

        - event.ctrlKey 事件触发时ctrl键是否被按下,若被按下,返回值为1 (用onkeydown检测)

        - event.shiftKey

        - event.altKey

        - event.button 鼠标左/中/右哪个键被按下，返回值依次为0/1/2，IE里对应返回1/2/4，此事件应用onmousedown



------

#### 第七章：正则表达式

##### 7.1 基础概念

- 正则表达式(Regular Expression,简称RegExp)

    - 一种描述字符串结构的语法规则,是一个特定的格式化模式,用于验证各种字符串是否匹配这个特征,进而实现高级的文本查找、替换、截取等内容操作

    - 正则作用

        - 检索、替换符合某个模式的文本

        - 过滤替换敏感词

        - 从字符串中提取特定部分内容

    - 特点
        - 灵活性、逻辑性和功能性较强

        - 可用极简单的方式达到字符串的复杂控制

        - 实际开发一般都是复制已写好的,但可根据实际情况修改

##### 7.2 几个关于搜索匹配的方法

- search  str.search('i') 找到i则返回i的位置索引,否则返回-1 (注：其只查找首次出现的单个字符)

- match  str.match('string') 找到string则返回string,否则返回null

- replace  str.replace('javascript','js') 前一个字符串被后一个替代 若前一个字符串不存在则返回str

- split  str.split(i,number) 将str用i分割为number个数组,number可选 i会消失

##### 7.3 创建方式

- 使用RegExp对象：`var st=new RegExp(pattern,attributes)` 特殊字符需转义

- 使用字面量(推荐)： `var st=/pattern/attributes` 特殊字符无需转义
    - pattern指表达式的模式或其他正则 
    - attributes指修饰符
- 创建的正则里无论是数字型还是字符型都无需加引号

##### 7.3 字符类别

- 修饰符

    - i  不区分大小写

    - g 全局匹配
    - m 多行匹配

    - u 以Unicode编码执行正则

- 方括号[]:

    - `[abc]`  查找方括号内的任意一个字符

    - `[^abc]`  查找不在方括号内的任何字符（放括号内有“^”则代表取反，别和边界符弄混）

    - `[0-9]`、`[a-z]`、`[A-Z]`、`[A-z]`  查找区间内的字符（“-”为范围连接符）

    - `[a-zA-Z0-9]`  查找大小写字符和0-9

    - `[\u4e00-\u9fa5]`  查找任意一个中文字符

- 元字符

    - "."  匹配除换行符("\n")外的任何字符

    - "\d" 匹配任意一个0-9的数字 
    - "\D" 匹配任意一个非0-9的字符

    - "\w" 匹配任意一个数字、字母或下划线 
    - “\W” 匹配任意一个非数字、字母或下划线
    - "\s" 匹配空白符 \S

    - "\uhhhh" 匹配16进制的unicode码为hhhh的字符 
    - ......

- 限定符

    - "?"  匹配限定符前面的字符0次或1次

    - "*"  匹配限定符前面的字符0次或多次

    - "+"  匹配限定符前面的字符1次或多次

    - "{n}"  匹配限定符前面的字符n次

    - "{n,}" 匹配限定符前面的字符最少n次

    - "{n,m}" 匹配限定符前面的字符最少n次,最多m次

    - 边界(限定)符

        -  ^ 匹配行首的文本

        -  $ 匹配行尾的文本
        - "^str" 匹配以str开头的字符串
        - "str$" 匹配以str结尾的字符串

        -  二者组合则为精确匹配，即文本必须和边界符内的内容完全一致,即使文本重复也不行

    - 零宽断言：

        - 零宽度的子表达式匹配,用于查找子表达式匹配的内容之前或之后是否含有特定的字符集

        - "?=str" 匹配后面紧跟str的字符串

        - "?!str" 匹配后面不是紧跟str的字符串

-  括号字符:()

    - 被“()”括起来的内容被称为正则的子表达式

    - 作用: 改变限定符的作用范围 ；分组

##### 7.4 运算符优先级

- 由高至低

    - “\”  转义符

    - “() []”  括号

    - “* + ？ {n} {n,} {n,m}”  限定符 

    - “^ $ \d 之类的任何字符及元字符”  定位点和序列

    - “|”  或操作

##### 7.5 子表达式

- 子表达式：正则对象包含分组的表达式

- 正则对象的属性和方法：

    - reg为自定义的正则表达式

    - 检测模式修饰符

        - reg.gobal 判断是否设置了修饰符“g”，若有则返回true

        - reg.ignoreCase 判断是否设置了修饰符“i”，若有则返回true

        - reg.multiline 判断是否设置了修饰符“m”，若有则返回true

        - reg.sourse 返回模式匹配(即reg)文本(去掉了修饰符和定界符)

        - reg.lastIndex 返回下一次匹配文本时从哪个字符开始的位置 (需全局匹配的元素才可用此属性,多用于一个字符串多次匹配)

    -  方法

        - test()  判断要检索的字符串内是否有符合要求的正则对象,若有返回true否则返回false 
            - 语法：reg.test(str)

        - exec()  返回匹配的字符串 

            - 语法：reg.exec(str)  

            - exec()有两个方法 exec().index返回匹配的索引；exec().input返回要检索的字符串

    -  exec()与match()的区别：

        - 用法不同 reg.exec(str)和str.match(reg)

        - 正则无子表达式且非全局匹配,两种方式结果相同均返回第一个匹配的字符串

        - 正则无子表达式且全局匹配,exec()匹配到第一个便终止；match()匹配全局,返回多个元素的数组

        - 正则有子表达式且全局匹配,两者均只匹配第一个便终止；但exec()会增加子表达式匹配，match()则忽略子表达式匹配

        - 正则有子表达式且非全局匹配,两者均只匹配第一个便终止，均增加子表达式匹配 

        - 综上：exec()只会匹配到第一个元素便终止,且随有无子表达式增加子表达式匹配；match()全局匹配则忽略子表达式而匹配全局,非全局匹配则随有无子表达式增加子表达式匹配 





------

#### 第八章：Ajax

##### 8.1 概述

- Ajax (Asynchronous JavaScript And XML) 即异步JS和XML技术,它不是一门语言和技术而是由JS、XML、DOM、CSS等多种已有技术组合而成的浏览器端技术,用于实现与服务器交互功能

- 优势

    - 按需获取数据,减少冗余请求和响应对服务器造成的负担

    - 部分工作由服务器端转移到客户端,减轻服务器和宽带负担

    - 无需重载整个页面,通过DOM实现内容更新,用户体验更好

- 同步和异步请求

    - 同步
        - 提交请求后服务器只能做这一件事,当处理完才可做下一件
        - 使用场景:当前请求结果是下一步请求前提)

    - 异步:浏览器可同时做多件事
    
    - 异步任务包含三种:
    
          回调函数:定时器中的回调、事件中的回调、ajax中的回调

##### 8.2 基本用法流程：

- 创建XMLHttpRequest对象 
    - 语法：`var myAjax=new XMLHttpRequest()`

- 向服务器发送请求：使用open()和send()方法

    - open(method,url,async) 
        - method请求类型 : get/post 
        - url:文件在服务器上位置  
        - async:true(异步 通常为异步)/false(同步)

    - send(string) string仅用于post请求

- 服务器响应

    - XMLHttpRequest三个重要属性
        - onreadystatechange  存储函数(或函数名)每当readyState属性改变时触发此函数

        - readyState  
            - 存有XMLHttpRequest的状态,0到4共5种状态值
            - 0 请求未初始化 
            - 1 服务器已建立连接 
            - 2 请求已接收 
            - 3 请求处理中 
            - 4 请求已完成且响应已就绪

        - status:状态码 如 200/404等 (statusText:状态码对应的文本,如404对应not found)

- 获取响应信息

    - responseText 接收服务器返回字符串形式的响应

    - responseXML 接收服务器返回XML形式的响应并解析

```javascript
var myAjax = new XMLHttpRequest();
myAjax.open('get', 'test.txt', true);
myAjax.send(null);
myAjax.onreadystatechange = function() {
  if(readyState == 4){
    if(myAjax.status == 200) {
      console.log('success')
      console.log(myAjax.responseText)
    }
  }
}
```

##### 8.3 跨域请求

- 域指网络中独立运行的单位 

- 浏览器遵循同源策略才会阻止跨域请求,同源指请求URL中的协议、域名和端口号都相同

-  跨域策略
    - 服务器通过“Access-Control-Allow-Origin”响应头指定特定的URL跨域请求(相当于白名单)
    - 通过JSONP(JSON with Padding): 利用“script、<img>、<iframe>、<link>”的src属性都可跨域
        - JSONP只支持get请求

##### 8.4 数据交换格式

- json

    - json语法是JS对象表示法的语法的子集

    - json实际是个字符串(注:在json中不可写注释,因为它本身就是字符串,即使是注释也会读取)

    - 语法规则
        - 数据在键值对中 
        - 由逗号分隔 
        - 花括号保存对象 
        - 方括号保存数组

    - json值：number(整数或浮点数)/strings(键值对均在双引号中)/boolean/Array/object/null

    - json解析器

        - 只会识别文本并不执行

        - 语法:`var ob=JSON.parse(myjson,参数2)`
            - 参数2为匿名函数可选 
            - 匿名函数需有两个形参,执行时会将json的键和值传入

    - 序列化

        - 与解析相反,将几组对象转换为json数据(即字符串)

        - 语法:`var ob=JSON.stringify(myjson,参数2,参数3)`

            - 参数2可选,用法同上,若不选可写为“null”

            - 也可设置为要过滤的键值,如“['name','age']”会将其他的键值筛选出去再序列化

            - 参数3可选,即如何排版,可写为“数字或字符”，如(“4”或“\*\*”)即在每个键值对的前面加上4个空格或2个“*”

-  XML

    - eXtensible Markup Language可扩展标记语言,与HTML都是标签语言,标签需成对出现且大小写敏感 

    - 主要用于描述和存储数据,可自定义标签

##### 8.5 cookie

- cookie
    - 或称cookies
    - 为辨别用户身份、进行会话(session)跟踪而存储在客户端的数据变量,当浏览器请求页面时浏览器会记录该用户状态,在响应头中通过“Set-Cookie”字段发送数据,浏览器保存此数据,下次再访问同一页面时,服务器先查看cookie,根据cookie资料判断来访者,进而发送内容。
    -  目前大部分浏览器可在客户端生成和读取cookie，但Chrome不支持，需在服务端。

- 创建cookie

    - document.cookie=''; 
    - 可连续创建多个且后面的不会覆盖前面的

    - 参数: “属性及值” 

        - 如：`document.cookie='name=张三'`

        - expires(过期时间) 如：`document.coolie='name=张三;expires='+date`

        -  path

            - 路径：默认为“/”
            - 登录某一网站,该网站的cookie信息可在该网站任一页面查看,若在某一页面设置cookie路径,则该页面的源代码需放置在指定的路径下再打开才能查看cookie 

            - 如：`var str='/D:/demo'; document.cookie='name=张三;path='+str`

        -  domain 设置cookie的有效域名,一般默认值,即绑定当前域名,在本地测试无效,需用服务器测试

        -  secure 
            - 设置传输协议,默认为普通http协议传输,若设置了则为https安全协议传输 
            - 如：`document.cookie='name=张三;secure'`

- 缺点：

    - 内存仅有4K,能保存数据的数量有限,大概保存20-50条信息,不同浏览器有差异

    - 有些信息不适合,比如银行卡号

- cookie是根据域名、路径等参数存储的,不同网站的cookie相互隔离从而保证数据的安全

- cookie函数的封装

    - ```javascript
        // 设置自定义cookie过期时间
        function dday(str) {
          var day = new Date();
          day.setDate(day.getDate() + str);
          return day;
        }
        function setCookie(key, value, str) {
          document.cookie = key + '=' + value + ';expires=' + dday(str);
        }
        setCookie('name','逍遥郎君',10);
        setCookie('age',24,10);
        setCookie('sex','man',10);
        
        // cookie的读取 用到split()函数将字符串分割为数组
        var strings=document.cookie;
        
        //因为cookie每个值冒号后都有一个空格,此split后的空格是为了将其抵消掉,否则cookie字符串被分割后的数组每个前面都有一个空格(第一个除外) 或者在调用函数输入数据时在每个数据前加个空格(不推荐此法) 
        var attstr = strings.split('; ');  // 分号后有个空格
        function getCookie(key) {
          for (var i = 0; i < attstr.length; i++) {
            var att = attstr[i].split('=');
            if (key == att[0]) return att[1];
          }
        }
        console.log(getCookie('name'))
        ```








------

#### 第九章：原型

##### 9.1 原型

- 构造函数原型：prototype

    - JS规定每个构造函数都有一个prototype属性指向另一个对象,这个对象的所有属性和方法都会被构造函数所拥有

    - 故可将那些不变的方法直接定义在prototype对象上,供所有实例共享

    - 原型:就是一个对象，也称prototype为原型对象
    - 作用：共享方法

- 实例对象原型:`__proto__`(前后均为两杠)

    - 实例对象都会有一个属性“`__proto__`”指向构造函数的“prototype”原型对象
    - prototype属于构造函数的显式原型 

    - `__proto__`属于实例对象的隐式原型,二者相等,但它只是内部指向原型对象“prototype”,不可以使用它

    - 对于实例对象的方法,先从实例对象查找,如果没有找到由于“`__proto__`”就会去原型对象上查找

        - ```javascript
            function Person() {}
            Person.prototype.skill = function () {}
            let x = new Person();
            console.log(x.__proto__ == Person.prototype); 	// true
            ```

- constructor构造函数

    - 对象原型(`__proto__`)和构造函数(prototype)原型对象里面都有一个属性constructor,称其为构造函数,因为它指回构造函数本身

    - constructor主要用于记录该对象引用于哪个构造函数,它可让原型对象重新指向原来的构造函数

    - 很多情况下需要手动利用constructor属性指回原来的构造函数

    - ```javascript
        function Person() {}
        Person.prototype.sing = function () {}
        Person.prototype.movie = function () {}
        // 此种写法是在原型的基础上(原型有constructor属性)添加方法
        
        Person.prototype = {
          constructor：Person,
          sing() {},
          movie() {}
        }
        // 此种写法为重写原型,即将原型的属性清空了再添加,故需手动添加上constructor属性
        
        let x = new Person();
        ```

- 利用原型对象扩展内置对象方法

    - 只可使用“.”方法追加,不可使用对象的方式覆盖

    - ```javascript
        Array.prototype.sum = function () {
          let sum = 0;
          for (let i = 0; i < this.length; i++) {
            sum += this[i]
          }
          return sum;
        }
        let arr1 = [1,2,3];
        let arr2 = new Array(1,2,3);
        console.log(arr1.sum()); 	// 6
        console.log(arr2.sum()); 	// 6 
        ```

- 构造函数、原型对象及实例对象之间的关系

    - 构造函数通过“.prototype”指向原型对象“prototype” ，通过new生成实例

    - 原型对象“prototype”通过“.constructor”指向构造函数，原型对象“prototype”等于实例对象“`__proto__`”

    - 实例对象“`__proto__`”等于“prototype”,故也可通过“constructor”指向构造函数

    - 原型对象与实例对象的存储地址不同

##### 9.2 原型链

- 在构造函数、原型对象及实例对象的基础上增加了Object,Object为所有构造函数的祖先

- 原型对象“prototype”也有属性“`__proto__`”且指向Object的原型对象“prototype”

- Object原型对象“prototype”通过“.constructor”指向Object构造函数，通过“.`__pro__`”指向null

- Object构造函数又通过“.prototype”指向Object的原型对象“prototype”

- JS成员查找机制

    - 当访问一个对象的属性或方法时,根据作用域链，如下

    - 先自身查找-->prototype原型-->Object原型对象-->直到null

    - 因此在此链上只要有所需的属性或方法对象就可拿来用,但遵循就近原则 (可看作继承的原理)

- 原型对象中this的指向

    - 构造函数中通过this添加的属性以及构造函数的原型函数(方法)中的this均指向实例对象

    - 即构造函数中的this指向它的调用者

- 关系网

    ![](imgs/JavaScriptImg/原型链关系网.png)

