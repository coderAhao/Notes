

#### 第一章: let和const 

##### 第1节:let声明变量特性

- 不能重复声明变量
-  只在其所在的块级作用域内有效(if/else/for/while的“{}”内都是块级作用域)
-  不存在变量提升(即必须先声明再调用)
-  不影响作用域链(即像全局声明那样只能由内部向外查找) 
-  不可直接在函数“{}”重新声明形参 但可再嵌套一级“{}”在此内声明形参
-  ES5时if/for是无块级作用域的

##### 第2节:const声明常量特性

- 声明时就要赋初值且不可重复声明
-  一般常量使用大写
-  常量的值不可修改
-  块级作用域(即在块内定义的常量只在块内有效)
-  对于数组的值及对象的属性的修改不算对常量的修改,因为其指向的地址仍未变(即const保证的是变量指向的内存地址不得改动)

##### 第3节:其他

-  块级作用域使得立即执行匿名函数不再必要
-  ES6声明变量的方法:var/function/let/const/import/class共6种
-  let/const/class声明的全局变量(即不写在块级作用域内)不再属于顶层对象的属性,即不可通过“window”获取

- 暂时性死区(temporal dead zone TDZ)

    - 只要块级作用域内存在let/const命令,它所声明的变量就绑定这个区域不再受外部影响，即在此区块中未用let声明变量之前其都是不可用的

    - ```javascript
        var tmp = 123;
        {
          //TDZ开始
          tmp = 'abc'; //错误
          let tmp; //TDZ结束
          tmp = 456; 
          console.log(tmp) //456
        } 
        ```

    - 变量提升:变量可以在声明之前进行调用,但调用时其值为“undefined”

    - for循环特别之处:“()”内设置循环变量的那部分是父作用域,“{}”内是单独的子作用域,二者互不影响

        ```javascript
        for (let i = 0; i < 2; i++) {
          let i='abc';
          console.log(i)
        }
        // abc 连输出2次
        ```




------



#### 第二章: 解构赋值

解构赋值:按照一定模式从数组和对象中提取值,然后对变量进行赋值

##### 第1节:数组的解构赋值

- 模式一定要匹配 如:let [a,[b,c]]=[1,[2,3]]

- 解构不成功变量值为undefined,如:let [a,b]=[1] 

- 可指定默认值 若数组等号右边有对应值则默认值无效(即右边为“undefined”则默认值才有效),如:let [x=1,y=x]=[2]

##### 第2节:对象的解构赋值

- 变量名必须和属性名一样才可取值,取值时属性名顺序随意
- 解构赋值时是将属性值赋给了变量而非属性

- 可指定默认值

- 大括号不可写在行首,否则会将其理解为代码块

    ```javascript
    let x; {x}={x:1} // 错误
    let x; ({x}={x:1}) // 写法1 
    let {x}={x:1} // 写法2
    // 大括号前至少有其他符号
    ```

##### 第3节:字符串的解构赋值

- 字符串会被转化为类似数组的对象 `let [a,b,c]="hel"`

- 类似数组的对象都有length属性 `let {length:len}="hello"  console.log(len) //5`

##### 第4节:其他

- 函数参数的解构赋值:形参和实参的形式一样即可

- 用途:交换变量的值;提取JSON数据

    ```javascript
    // 如从函数返回多个值
    function f() {
      return {foo:1,bar:2};
    } 
    let {foo,bar} = f() 
    ```




------



#### 第三章:字符串的扩展

##### 第1节: charAt() 返回字符串给定位置的字符

- string.charAt(num) 返回string第num个位置的字符

##### 第2节: 确定字符串中是否包含另一个字符串

- includes(str,[num])

    - 返回值true/false num为可选参数,从第num个开始匹配到结尾

    - string.includes(str)

- startsWith(str,[num])

    - 参数字符串是否在源字符串头部 返回值及num含义同上

    - string.startsWith(str)

- endsWith(str,[num])
    - num为只匹配前num个字符

##### 第3节: 重复字符串

- str.repeat(num)

    - 返回新字符串,str被重复num次(num为小数则舍去小数位)

    - num为字符串则先转换为数字

##### 第4节: 补全字符串

- padStart()

    - string.padStart(length,[str])

    - length为指定string的新长度,在其头部用str来填充,省略str则空格来补

    - 若length小于原string长度则返回原string

    - 若string原长加上str长大于length,则舍去str多余部分

- padEnd() 用法同上

- 用途:为数值补全指定位数;提示字符串格式

- 注:由于是补全字符串补全,非字符串(如number型)需先转化，如 `a=123; a.toString().padStart(5,'*')`

##### 第5节: 模板字符串

- 使用“`”反引号 模板内的空格和缩进均会保留(后面加“.trim()”方法可消除换行)
- ${} 在“{}”内可写变量名/表达式/函数/对象属性进行引用、调用或计算



------



#### 第四章: 对象

##### 第1节: 属性简洁表示法

- 对象中若属性名和属性值相同可只写一个
- 方法可简写为“f(){}” 原写法“f:function(){}”

##### 第2节: 比较与赋值

- ES5比较值只有“==”和“===” 缺点:前者会自动转换数据类型,后者“NaN不等于NaN”及“+0等于-0”
- Object.is(str,str) 返回值true/false 例：`Object.is(+0,-0) false `   `Object.is(NaN,NaN) true`
- Object.assign(target,source1,source2,...) 将source对象的属性复制到target上
    - 若有同名属性则后者覆盖前者
    - 由于是对象其实是引用而非简单的复制

- 数组会当成对象来处理

    - ```javascript
        Object.assign(['a','b','c'],['d','e']) 
        // [d,e,c]  会将[a,b,c]视为对象{0:a,1:b,2:c} [d,e]视为{0:d,1:e} 将同名属性替换掉
        ```

- 用途:为对象添加属性/方法/克隆对象(目标对象为空即可)/合并对象/为属性指定默认值
    - 注:只能复制源对象(source)自身的属性,继承属性和不可枚举的属性不能被复制

##### 第3节: 遍历对象的属性方法

- for...in 遍历数组或枚举一个对象循环显示(不含Symbol属性)
- Object.keys(obj) 返回一个数组包含对象自身(不含继承)所有可枚举属性(不含Symbol属性)
- Object.getOwnPropertyNames(obj) 返回一个数组包含对象自身的所有属性(不含Symbol属性)
- Object.getOwnPropertySymbols(obj) 返回一个数组包含自身的所有Symbol属性
- Reflect.ownKeys(obj) 返回一个数组包含对象自身的所有属性

------

#### 第五章:函数 

##### 第1节: 函数参数默认值

- 可为函数形参设置默认值,多个形参时不可有同名的,形参不可再次用let/const声明

- 定义了默认值的参数应写在尾部,易看出省略了哪些参数

- 若有默认值的参数未写在尾部,则显式传参“undefined”才可触发其默认值
    - ```javascript
        function f(x,y=2,z) {
          return [x,y,z]
        }
        f(1,,3) // 报错
        f(1,undefined,3) // [1,2,3]
        ```

- 函数length属性返回未指定默认值的形参的个数

- 设置了默认值的形参若未在尾部,则length属性只计算在它之前的形参个数

    - ```javascript
        let aa = (function (a, b=1, c, d=2) {}).length
        console.log(aa) // 1
        ```

        

##### 第2节: rest参数与严格模式

- 形式为“...变量名” 用变量获取函数多余参数,这样就不需要引入arguments对象了
- rest参数中的变量代表一个数组,rest参数为最后一个形参否则报错
- 函数的length属性不包括rest参数
- 函数参数只要使用了默认值、解构赋值或扩展运算符则在函数内部就不能显式设置为严格模式,否则报错,规避这种限制的方法:在全局之中进行设置或把函数写为一个无参并立即执行的函数

##### 第3节: 箭头函数

- 用法1(标准用法): 
    - (p1,p2,...pn) => { statements }
- 用法2: 
    - (p1,p2,...pn) => { return expression;} 
    - (p1,p2,...pn) => expression

- 用法3:
    - (p1) => { statements }
    - p1 => {statements}
    - 只有一个参数可省略“()”

- 用法4:

    - () => {statements}

    - _ => {statements}
    - 无参时箭头前需有“()”或“_”

- 关于this:

    - 函数内的this指向固定化,即指向定义时所在的作用域,而非运行时(普通函数中的this绑定的为运行时的作用域)

    - 不可使用arguments对象,可使rest参数代替

    - 不可以当构造函数(即不可使用new命令,因为箭头函数内部无自己的this而是引用的外层this)

        ```javascript
        // 本质形同闭包引用外部this
        function f() {
            var _this=this;
            function f1() {
              console.log(_this.id)
            }
          }
        ```

    - 另箭头函数无自己的this自然也不可使用call()、apply()、bind()方法去改变this

- 箭头函数经常使用的场景:将其作为另一个函数的参数

##### 第4节: 尾调用

- 管道机制:前一个函数的输出是后一个函数的输入
- 柯里化:将多参数的函数转变成单参数的形式
- 尾调用:某个函数的最后一步是调用另一个函数
    - 只能是在函数内部return另一个函数才是尾调用,若对函数进行了其他操作或仅是调用而未return则均不属于尾调用
    - (关于尾调用优化及尾递归相关知识以后再总结 P125页)



------



#### 第六章: 数组

##### 第一节: 扩展运算符

- 扩展运算符:“...” 将数组转为用逗号分隔的参数序列
- 用法: “...变量” “...Arr[]” “...表达式”均可
- 用途:
    - 可展开数组故不需使用apply方法将数组转为函数的参数
    - 合并数组
    - 与解构赋值结合
    - 将字符串转为真正的数组

- 本质: 背后调用的是遍历器接口,如果对象为部署此接口则无法转换

##### 第二节:Array.from()

- 伪数组:类似数组的对象,本质特征为必须有length属性,即在对象内部必须有“length:num”这个属性

- 可将伪数组和可遍历对象转换为真正的数组

- 用法:Array.from(str,[fun])

    - 参数2为可选参数,作用类似数组的map方法用来对每个元素进行函数操作再将其结果放入数组中return出去

    - ```javascript
        Array.from(arr,x => x*x); // 等同于下面的map
        Array.from(arr.map(x => x*x))
        Array.from([1,2,3],x => x*x) // [1,4,9]
        ```

##### 第3节:Array.of()

- 作用: 将一组值转换为数组,基本上可用来替代Array()或new Array(),并且不存在由于参数不同而导致的重载,它的行为非常统一

- 与Array()方法的区别

    - ```javascript
        Array.of(3) // [3]
        Array.of(1,2,3) // [1,2,3]
        
        Array(3) //[, , ,]
        Array(1,2,3) //[1,2,3]
        ```

##### 第4节: copyWithin()

- 作用: 在当前数组内部将指定位置的成员复制到其他位置(会覆盖原成员),然后返回当前数组(即会修改当前数组)

- 用法:

    - arr.copyWithin(target,[start],[end])

    - target:从此位置开始替换 start:从此位置开始复制(默认为0,负值表倒数) end:此位置前停止复制(默认到尾部,负值表倒数)

    - ```javascript
        [1,2,3,4,5].copyWithin(0,2) // [3,4,5,4,5]
        ```

##### 第5节: fill()

- arr.fill(num,[start],[end]) 将指定值填充/替换到数组里

- num:要填充的值 start:填充的起始位置

- ```javascript
    new Array(3).fill(7) // [7,7,7]
    ['a','b','c'].fill(7,1,2) // ['a',7,'c']
    ```

##### 第6节: 遍历数组

- keys():对键名遍历  values():对键值遍历  entries():对键值对的遍历

- ```javascript
    for (let i of ['a','b'].keys()) {
      console.log(i) // 0 1
      // keys()换成values()结果为 'a' 'b'
      // keys()换成entries()结果为 0 'a' 1 'b'
    }
    ```

##### 第7节: includes()

- arr.includes(str,[start])
- 某个数组是否包含给定的值,返回值true/false
- [start]为可选参数默认为0表示搜索起始位置 若为负值则表示倒数,若还大于数组长则重置其为0



------



#### 第七章: Module(模块)语法

##### 第1节: 严格模式及CommonJS

- 严格模式: ES6默认,无论模块头部加没加“use strict”
- 严格模式的限制:
    - 变量需先声明后调用  函数参数不可有同名属性  不能使用with语句  不能对只读属性赋值
    - 不能删除变量“delete prop”,只能删除属性“delete global[prop]”
    - 不得使用前缀0表示八进制数  不可删除不可删除的属性  eval不会在其外层作用域引入变量
    - eval和argument不能被重新赋值  增加了保留字(比如“protected static interface”)
    - 禁止this指向全局对象(ES6模块中顶层this会指向undefined)

- CommonJS引入模块:

    - ```javascript
        let {f1,f2} = require('fs')
        // 等同于
        let fss = require('fs');
        let f1 = fss.f1;
        let f2 = fss.f2;
        // 实质整体加载了fs模块(即所有方法)生成对象fss,再从fss上读取方法,此方法叫运行时加载(只能在运行时才能得到这个对象),无法在编译时进行静态优化
        
        //导出:
        module.exports={ f1:f1, f2, }  
        ```

- ES6模块:通过export命令显式指定输出代码再通过import命令输入

    - import {f1,f2} from 'fs'
    - 实质从fs模块加载了两个方法而不加载其他方法,这种方式称为编译时加载(也叫静态加载)

- 常见的模块化规范:  CommonJS、AMD、CMD、ES6的Modules

##### 第2节: export命令

- 模块:自动运行在严格模式下且无法退出运行的JS代码,是一个独立的文件,内部变量外部无法获取

    - 优点:防止命名冲突、代码复用、高维护性

- export关键字可向外输出变量、函数或类

- export命令可在模块任意位置但必须处于模块顶层,不能处于块级作用域内

- 输出方式

    - ```javascript
        export let m = 1; // 或let m = 1;  export {m};
        //(注:必须有大括号否则输出的就不是接口而是1)
        export let n = 2; // 或let m = 1;  export {m};
        // 方式1分别暴露
        
        export {m,n};
        // 方式2统一暴露 
        
        export {m as n}; 
        export {m as p};
        // 方式3 起别名(可多次输出)
        
        //输出函数的两种方式
        export function f(){}; 
        export {f}; 
        ```

        

##### 第3节: import命令

- import命令具有提升效果,提升到模块头部并执行(本质:编译阶段执行,即在代码运行前)

    - 是静态执行故引入时不能使用表达式和从变量中引入(因为引入提升)

    - ```javascript
        // 如
        let m='my_module'
        import {f} from m
        ```

- import所处位置同export

- 引入方式(引入时<script type="module">标签需加上type)

    - ```javascript
        import {f1,f2} from './profile'; // 引入方式1 路径可为绝对也可为相对
        import {f1,f2} from 'module'; // 引入方式2 直接引入模块名而不写模块路径,但配置文件中必须写明模块位置
        import {f1 as f} from './profile'; // 引入方式3(起别名)
        ```

- CommonJS模块的require命令和ES6的import命令最好不要写在同一个模块里,因为有可能不会得到预期效果

##### 第4节: export default命令(默认暴露)

- 输出方式:

    - ```javascript
        export default function(){} // 输出匿名函数
        export default function f(){} // 输出具名函数
        export default f // 直接输出
        export default{  f1:"", f2:""} //统一暴露
        ```

- 一个模块只能有一个默认输出

    - 故export default命令只能使用一次

    - 故import在引入此文件时不需加“{}”因为只能对应一个方法

    - 本质:输出一个叫“default”的变量或方法,然后为其命名

    - ```javascript
        export default f;
        // 等同于
        export {f as default};
        
        import f from 'modules';
        // 等同于
        import {default as f} from 'modules';
        ```

        

##### 第5节: export与import的复合写法、整体加载模块

- 如果在一个模块中先输入后输出同一个模块可将import和export写在一起

    - ```javascript
        export {f} from 'modules';
        // 等同于
        import {f} from 'modules';
        export {f}  
        // 整体输出和起别名也可用此写法
        ```

- .整体加载模块

    - 使用*指定一个对象,将所有输出值加载到此对象上
    - 某个模块导出的变量较多,一一引入过于麻烦
    - 如: `import * as obj from './profiles'`  使用时可为“obj.name”

- 模块之间可以继承, 但“export * ”命令会忽略被继承的模块的default方法

##### 第6节:import() 动态加载

- import是静态加载,require是运行时加载(即到底加载哪个模块只有运行时才知道)
- import(specifier)为动态加载 参数specifier指定要加载的模块位置
- import()函数可用在任何地方,即运行到这一句边会加载指定模块,故可放在任何位置(比如块级作用域内,import不可放在块级作用域内)
- 适用场景:按需加载、放在if条件下加载、允许模块路径动态生成

#### 第八章:promise与async await

##### 第1节: promise

- 代码首先是给人看的,其次才是给机器看的
- 解决了回调地狱的问题,但其链式写法也并不优雅



##### Iterator迭代器

- Iterator是一种接口,为各种不同的数据结构提供统一的访问机制,任何数据只有部署了此接口均可完成遍历操作

- ES6创建了新的遍历命令for...of循环,Iterator主要供for...of消费

- 原生具备Itterator接口的数据:Array Arguments Set Map String TypedArray NodeList

##### Symbol

- 数据类型:USONB 即undefined String Symbol Object Null Number Boolean
- 特点:值是唯一的,用来解决命名冲突问题
- 不能与自身及其他数据进行运算(可将Symbol看作是身份证,身份证不可运算和叠加)
- 定义的对象属性不可使用for...in遍历循环,但可使用Reflect.ownKeys获取对象的所有键名
