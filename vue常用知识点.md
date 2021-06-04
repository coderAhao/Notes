### vue常见知识点-1

##### 1. 防抖debounce

- 原理: 在n秒后执行该事件,如果n秒内又触发该事件则重新计时

- 应用场景：登录、发短信等按钮避免用户点击太快，以致于发送了多次请求

```javascript
// 写法1: 使用箭头函数的this
function debounce(func,wait) {
		let timeout;
		return function (...args) {
  			if(timeout) clearTimeout(timeout);
  			timeout = setTimeout(() => {
		   		 func.apply(this,args)
  			},wait)
		}
}
// 写法2: 使用普通函数的this
function debounce(func,wait) {
  	let timeout;
  	return function () {
    		let content = this;
    		let args = arguments;
    		if(timeout) clearTimeout(timeout);
    		timeout = setTimeout(function() {
      			func.apply(content,args)
    		},wait)
  	}
}
function fu() {
  // doSomeThing
}
const str = debounce(fu,300);
str();
```

##### 2. 节流throttle

- 原理: n秒内该事件只触发一次 

- 应用场景: 滚动加载、加载更多、滚到底部监听、搜索框搜索联想



##### 3. 时间戳过滤器 

```javascript
// 简单版
function dateFormat(dateVal) {
		const dt = new Date(dateVal * 1000);
		const y = dt.getFullYear();
		const m = (dt.getMonth() + 1 + '').padStart(2, '0');
		const d = (dt.getDate() + '').padStart(2, '0');
		const hh = (dt.getHours() + '').padStart(2, '0');
		const mm = (dt.getMinutes() + '').padStart(2, '0');
		const ss = (dt.getSeconds() + '').padStart(2, '0');
		return `${y}-${m}-${d} ${hh}:${mm}:${ss}`
}
```

```javascript
//  一劳永逸版
// fmt格式: “yyyy-MM-dd hh:mm:ss” 也可以有其他格式但字母不得改变 

function formateDate(date, fmt) {
  	date = new Date(date * 1000); // 时间戳是秒但Date函数的参数需为毫秒
 		 if (/(y+)/.test(fmt)) {
    		fmt = fmt.replace(RegExp.$1,(date.getFullYear() + '').substr(4 - RegExp.$1.length));
 		 }
  // 单独将年提取出来,因为年份是4个字,但传过来的字数为1/2/3/4个都可以
  // “/(y+)/” 即看传过来的有几个y
  // “RegExp.$1” 即将匹配到的第一个子字符串“y+”保存起来 (可百度RegExp.$1的含义)
  // “date.getFullYear() + ''” 将年由数字转为字符串(也可使用“string”方法转)
  // “substr(4 - RegExp.$1.length)” 根据传来的格式判断年份需要几位(如2019 --> 19)
  // “fmt.replace()” 将截取好的年份进行替换

 			let o = {
          'M+': date.getMonth() + 1,
          'd+': date.getDate(),
          'h+': date.getHours(),
          'm+': date.getMinutes(),
          's+': date.getSeconds(),
       }
       for (let k in o) {
          if (new RegExp(`(${k})`).test(fmt)) {
            let str = o[k] + '';
            fmt = fmt.replace(RegExp.$1, (RegExp.$1.length !== 1) ? str : str.padStart(2,'0'))
          }
        }
		  // 判断“月日时分秒”是否传过来，如果传过来则再进行补零操作

  		return fmt;
}
```



##### 4.混入mixins

- 其实就是将相同的生命周期函数,methods方法、data数据等抽离到一个js文件中,哪个组件需要引入即可

    ```javascript
    // 抽离js文件写法:
    export const funName = {
     		data() {
      			return {
       					data1: ''
      			}
     		},
     		mounted() {
      		fun() {
      		}
     		}
    }
    // 组件引用时：
     import {funName} from '...'  	// 1.先从JS文件中引入方法
    mixins:[funName]		// 2.和data、methods等同级别创建mixins数组放置引入的数据
    ```

    

##### 5.runtime-only 和 runtime+compiler 的区别

1. 先看vue程序运行过程

    <img src="imgs/vueImg/vue运行过程.jpg" alt="vue运行过程"  />

<img src="imgs/vueImg/runtime-only和complier.jpg"  />

2. parse 解析；ast(abstract syntax tree) 抽象语法树；compiler 编译

3. runtime+complier（运行加编译）方式编译过程：

    - 根据main.js文件可知

    - 先将app进行组件注册
    - 再将组件放进template中
    - template -->（通过parse）ast -->（通过compiler）render --> vdom --> ui

4. runtime-only（只运行）方式编译过程：

    - 使用此种方式需安装 vue-template-compiler
    - ".vue"文件通过vue-loader进行加载，通过vue-template-complier已将app中的template编译为render函数
    - 根据main.js文件可知

    - 直接将app组件进行render函数渲染
    - render --> vdom --> ui   

5. runtime-only：

    - 通过vue-template-complier将本该vue处理的template代替处理，vue在main.js文件里直接使用，因而此种方式性能更高，编译出的代码量更少

    - h 函数的本质是createElement 函数，这个函数的作用就是生成一个 VNode节点，render 函数得到这个 VNode 节点之后，返回给 Vue.js 的 mount 函数，渲染成真实 DOM 节点，并挂载到根节点上

        ```javascript
        //  render的箭头函数还原
        render: function (createElement) {
            return createElement(App);
        }
        // createElement函数可接受组件，也可自行创建标签， 具体用法查看原生JS
        /render函数创建的元素会直接将页面中el指定的容器替换掉
        ```

        

