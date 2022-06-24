##### 第一章：基础

###### 1. 基础命令

- npm i typescript -g 全局安装
- tsc --init 初始化,会生成tsconfig.json文件
    - 可在文件中修改出口文件、编译为es几等
    - 注意：因为是json文件，需使用双引号，单引号将报错
    - 如修改“target:es2016”改为“target:es5”则会将js文件已es5的语法进行编辑输出
- tsc xxx.ts 将xxx.ts文件编译为js文件
- 修改tsconfig.json中的'outDir'即文件输出目录时，如果无效的话，将监视打开：vscode终端->运行任务->显示所有任务->下拉找到’tsc监视‘点击即可；此后修改ts文件后保存时对应的js文件会自动更新，相当于热更新
- 如果不想打开终端，也可以使用命令：tsc -p tsconfig.json --watch 监听当前目录的变化，依据tsconfig.json文件去编译，其实手动运行终端的操作就是执行了这条命令
- 如果ts文件已更新但对应的js文件未更新，可使用命令“tsc xxx.ts”更新对应的js

###### 2. 原始数据类型

- 像number、string、boolean、symbol、null、undefined等必须为小写
    - 如：let a: number = 1
    - let str: string; str = 'kobe'
- 一些新的语法需在tsconfig.json中进行配置才可使用
    - 如 let sym: symbol = Symbol() 就会报错，因为Symbol比较新需目标库 lib支持
    - 在配置文件中修改“lib:[]”,可改为“lib:['ESNext']”  即支持最新的语法
- void一般只用在函数无返回值的情形下
    - function fn(): void {}
    - 如果要定义fn未undefined，则函数内部必须return undefined
      - 如：function fn(): undefined {return undefined}
- 如果不写类型，ts是可以推断出类型的

###### 3.非原始数据类型

- object: 除number、string、boolean、undefined、null、symbol的引用数据类型，即只可用来定义函数、数组和对象
- Object: 和{}一样，代表所有拥有toString、hasOwnProperty方法的类型，也就是包含原始类型和非原始类型，范围比object更广
- 严格模式下，undefined和null不能作为Object类型的值
- 在一个项目中，ts会把整个项目作为环境，如果在ts文件1中声明了变量str,那么在ts文件2中就不可再声明变量str，如果想使用，则在ts文件1中加上`export{}`即将这个文件导出为空对象，这样可绕过检测
- 一般定义对象时用object，因为它包含的范围窄，更容易区分类型

###### 4.数组类型

- ```typescript
    // 方式1 泛型，即类型参数化
    let arr1: Array<number> = [1,2,3] //限制数组中值的类型
    // 方式2
    let arr2: number[] = [1,2,3]
    // 方式3 又叫元组
    let arrVal: [number,number] = [1,2] // 限制数组中每一个值的类型
    arrVal.push(3)
    // 此时可以push,但无法访问到push后的值 因为在定义时就已经通过两个“number”限制了它的长度和数据类型
    console.log(arrVal[2]) // 报错
    ```


- ```typescript
    // 联合类型 其实就是“或”
    let num: 1 | '2' = 1 // num只能为1或'2'
    let arr1: Array<number | string> = [1, '2'] // 数组arr1中的元素只能为number或string
    let arr2: number | string[] = ['1','2'] // arr2只能为number或为元素为string的数组
    let arr3: (number | string)[] = [1,'2'] // 数组arr3中的元素只能为number或string
    // 交叉类型
    let obj: {name: string} & {age: number} = {name: 'kobe',age: 18,height: 198} // 必须包含name和age两个属性且属性的类型要符合要求
    ```

###### 5. any和unknown

- any: 不建议使用

    - let a: any = 1

- unknown

    - 代表不确定变量类型，和any区别：unknown会进行类型检查

    - ```typescript
        // ts会进行静态编译
        let x = 1
        let y = '2'
        let unk1: unknown
        if (typeof x === 'number') {
        	unk1 = x
        } else {
        	unk1 = y
        }
        unk1.toFixed(2) // 此处报错 因为typeof只是检测了x的类型，而unk的类型仍是未知，而tofixed方法只能number类型才可使用，此行代码不能确定unk1的类型，故会报错
        
        let unk2: unknown
        unk2 = 2
        unk.toFixed(2) // 此处依然报错 因为赋值是js在运行时执行 而在js运行前ts就已经进行了校验
        
        // 使用typeof缩小unknown的范围则不会报错 因为检测后已经确定了unk的类型才会继续执行括号内的代码
        if (typeof unk === 'number') {
            unk.toFixed(2)
         } else if(typeof unk === 'string') {
           unk.charAt(1)
         }
        ```

###### 6.never类型

- 表示永远不会发生值的类型
- never是所有类型的子类型

###### 7.interface类型

- 作用：用来自定义类型的

- ```typescript
    // 接口类型的变量首字符最好大写
    // 定义接口类型 给对象用
    interface ObjItf{
      name: string,
      age: number
    }
    let obj: ObjItf
    obj = {
      name: 'kobe',
      age: 12
    }
    // 定义接口类型 给数组用
    interface ArrItf{
      [idx: number]: number | string // 即索引为number，索引值为number或string
    }
    let arr: ArrItf = [1,2,'3']
    // 定义接口类型 给函数用
    interface FnItf{
      // 形参及类型 返回值类型
      (p: number, a: string): void
    }
    let fn: FnItf = (p: number, a: string) => {}
    fn(1, '2')
    ```

- 接口特性

    - ```typescript
        // 继承
        interface NameItf{
          name: string
        }
        interface AgeItf{
          age: number
        }
        interface PersonItf extends NameItf,AgeItf {
          height: number
        }
        let p: PersonItf
        p = {
          name: 'kobe',
          age: 18,
          height: 198
          // p的三个属性少一个都会报错 因为继承的必写
        }
        ```

    - ```typescript
        // 缺省
        // 数据在定义的时候可以不写
        interface NameItf{
          name: string
        }
        interface AgeItf{
          age?: number
        }
        interface PersonItf extends NameItf,AgeItf {
          height: number
        }
        let p: PersonItf
        p = {
          name: 'kobe',
          height: 198
          // 属性age由于缺省可以不定义
        }
        ```

    - ```typescript
        // 同名
        // 同名会将属性合并 下方的obj两个属性都要有
        interface AItf{
          a: number
        }
        interface AItf{
          b: string
        }
        let obj: AItf = {
          a: 1,
          b: '2'
        }
        ```

    - ```typescript
        // 只读
        interface RItf{
          readonly name: string
        }
        let p: RItf = {
          name: 'kobe'
        }
        p.name = 'curry' // 报错 因为只读
        ```

###### 8.类型别名 type

- 其实就是给一个变量定义一个类型，然后用它来限制别的变量类型

- ```typescript
    type StrType = string | number
    let str: StrType = '1'
    str = 10
    type ObjType = {
      a: number,
      b: string
    } 
    let obj: ObjType = {
      a: 1,
      b: '2'
    }
    // 类型别名可用来保存接口上某个属性类型
    type AType = ObjType['a']
    let a: AType = 1
    // 不可重复定义类型别名
    type NumType = string | number
    type NumType = boolean // 报错，重复定义
    ```

###### 9.ts函数

- ```typescript
    // 小括号后的number用来限制返回值类型
    function fn(a: number, b: number): number {
      return a + b
    }
    //  函数无返回值 可用void限制
    function fns(): void {}
    ```

- 接口定义函数类型

    - ```typescript
        interface FnItf {
          (p: string): number // 变量需为字符串，但变量的值要为number
        }
        let fn: FnItf = (p: string) => {
          return 1 // 注：必须有返回值且类型为number，否则报错
        }
        fn('s')
        ```

- 类型别名定义函数类型

    - ```typescript
        type FnType = (p: string) => void
        let fn: FnType = (p: string): void => {}
        fn('s')
        ```

###### 10.promise的写法

- ```typescript
    // 先定义好接口数据类型，即要和resolve传的实参类型一致，为then时使用的res的属性做准备
    interface ResItf{
      code: number,
      data: {a: number, b: string}[],
      message: string
    }
    // 如果不在此处限制好p，then时使用res会报类型未限制
    let p: Promise<ResItf> = new Promise((resolve, reject) => {
      resolve({
        code: 1,
        data: [{a: 1, b: '2'}],
        message: 'success'
      })
    })
    p.then(res => {
      if (res.code === 1) {
        res.data.forEach(item => item.a = 2)
      }
    })
    ```

###### 11.this指向

- 指向window

    - ```typescript
        // 此处定义的接口类型Window和全局window重名，但接口类型允许重名，故此处相当于扩展全局Window
        interface Window{
          myName: string
        }
        // ts中函数第一个形参的位置注明this指向
        function Person(this: Window, name: string) {
          this.myName = name
        }
        window.Person('kobe') // 注此处的window代表全局
        ```


###### 12.泛型

- 泛型可以理解为类型的形参
    - ```typescript
        function fn(n: number | boolean): number | boolean {
          return n
        }
        fn(100)
        // 第一个number和boolean定义的是形参类型，第二个则是定义返回值类型
        // 这样写比较麻烦，可以用一个变量来代替
        
        function Fn<T>(n: T): T {
          return n
        }
        Fn<number>(100)
        Fn<string>('100')
        // T仅是一个标识符，可用别的任意字符来代替
        
        function Fns<T, G>(n: T, m: G): T {
          return n
        }
        Fns<number, string>(100, '100')
        ```

- 泛型约束 通过extends关键字

    - ```typescript
        type StrType = string | number
        function fn<T extends StrType>(n: T): T {
          return n
        }
        fn(1)
        ```

###### 13.抽象类和接口

- 抽象类

    - 使用关键字abstract定义一个类，它的作用是用来制定一个类的规范，让普通类按这个规范去继承

    - ```typescript
        // 以后继承Person的类必须得有name属性和getName方法
        abstract class Person {
          abstract name: string
          abstract getName(): string
          getAge() {
            return 18
          }
        }
        
        // 普通类继承时 必须有抽象类定义的name属性和方法，具体的属性值和方法由普通类决定，抽象类只是规定有而不做具体的描述
        class Male extends Person {
          name: string = 'kobe'
          getName() {
            return this.name
          }
        }
        
        // 抽象类中的非抽象方法普通类可直接继承 即下面的getAge
        let m1 = new Male()
        console.log(m1.getName()) // kobe
        console.log(m1.getAge()) // 18
        
        // 抽象类不可进行实例化
        // let m2 = new Person() // 报错
        ```

- 接口

    - 就是定义好一个接口类型用来给类使用

    - 用法其实和上面的抽象类的继承差不多

    - 使用关键字implement来继承

    - ```typescript
        // 书写接口给类使用
        interface PerItf {
          name: string
          age: number
          getName: () => void
        }
        class Male implements PerItf {
          name: string = "kobe"
          age: number = 18
          getName() {
            return this.name
          }
        }
        let m = new Male()
        ```

###### 14.工具类型 Partial和Required

- Partial

    - 作用：根据接口定义好的类型，有选择性的定义对象要有的属性

    - ```typescript
        interface PItf {
          name: string,
          sex: string,
          age: number
        }
        let obj: Partial<PItf> = {
          name: '',
          age: undefined
        }
        // 将鼠标放到 Partial 上会出现下面一行解释说明
        // type Partial<T> = { [P in keyof T]?: T[P] | undefined }
        // T代表PItf, P为键，代表name、age，且键可缺省；T[P]则是键值  因此上面意思为对象obj的键可缺省或键值为undefined
        ```

- Required

    - 作用：和Partial恰好相反，所定义的对象必须要有接口定义的所有属性

    - ```typescript
        interface PItf {
          name: string,
          sex: string,
          age: number
        }
        let obj: Required<PItf> = {
          name: '',
          sex: 'male',
          age: 18
        }
        // 将鼠标放到 Partial 上会出现下面一行解释说明
        // type Partial<T> = { [P in keyof T]-?: T[P] }
        ```

###### 15.提取变量或对象的类型 typeof

- typeof的另一个作用

- ```typescript
    let str = "123"
    type StrType = typeof str
    let s: StrType = "abc"
    
    let obj = {
      name: 'kobe',
      age: 18
    }
    type OType = typeof obj
    let o: OType = {
      name: 'curry',
      age: 20
    }
    ```

    















