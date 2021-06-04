# HTML总结

#### 第一章:初识HTML

##### 第1节:H5概述

######  1.发展历程:

1.  超文本标记语言(Hyper Text Markup Language)第五代

2. 万维网联盟(World Wide Web Consortium, W3C)负责制定

######  2.优势:

1.  解决了跨浏览器问题

2. 新增了多个特性:

   - 新增语义化标签如:header nav section article aside

   - 新的表单控件如:email time url calendar date search
   - 对传统的控件进行升级:增加了placeholder属性

   -   用于绘画的canvas

   -   用于媒介回放的audio和video

   -   对本地存储更好的支持
   -   增加了地理位置、拖曳、摄像头等API

3. 用户优先的原则:

   -   安全机制设计,对不同的API(Application Programming Interface应用程序编程接口)都通用

   -   表现和内容分离

4. 化繁为简的优势:

   -   新的简化的字符集 

   -   新的简化的DOCTYPE 

   -   简单而强大的HTML5 API 

   -   以浏览器原生能力代替复杂的JavaScript代码

##### 第2节:H5基础

######  1.HTML5语法: 

1. 语法不区分大小写   
2. 允许属性值不使用引号 
3. 允许部分属性值省略 

######  2.HTML5标记:

1. 单标记、双标记、注释标记 

######  3.头部相关标记head:

1.   title:网页名字 

2.   meta:定义页面元信息 

   - charset="utf-8"国际化编码  还有gbk和gb2312 

   - name="" content="" name提供搜索内容名称,content对应搜索内容值 ，如 name="keywords" content="html,css,vue"(注意逗号分隔) 

3. unicode 国际编码

   -    UTF-8是unicode的升级版 Universal Character Set/Unicode Transformation Format，是针对Unicode的一种可变长度字符编码

4. link(引用外部标记)标记属性:

   -    href:url 

   -    rel:"stylesheet(CSS样式表)"/"shortcut icon(图标显示)" 

   -    type: text/css或text/javascript 

5. style:内嵌样式标记 
   -    type:text/css或text/javascript 

######  4.文本控制标记: 

1. 标题和段落

   -    标题 ：h1-h6  
   -  h元素拥有确切语义,需慎重选择 
   - 一个页面只能用一个h1，常被用作logo
   - h1:Logo；h2:副标题；h3:版块标题；h4:版块内容标题；h5、h6:版块嵌套中的版块使用

   - 段落标记P 
   - 水平线标记hr 

2. 文本格式化标记: 

   - `<b>` `<strong>`粗体显示 

   - `<i>` `<em>`斜体 
   - `<del>`删除线 
   - `<ins>`下划线 
   - sub/sup下上标
   -  `<q>`双引号
   -  mark文字添加背景颜色 

3. 特殊字符标记:

   -    以"&"开头,以";"结尾 
   -    常用的三个: `&nbsp;`(空格) 
   - `&lt;`(“<” less than缩写) 
   - `&gt;`(“>” great than缩写) 
   - 也可用实体数值表示(&#160、&#60、&#62) 

4. 图像标记:

   -  gif/jpg/png 

   -  属性值: src(图像路径)  title(鼠标悬停显示的文字) alt(图片不显示时替换的文本;搜索引擎也会根据alt内容来分析网页内容) 

   -  相对/绝对路径: 上一级:"../" 

5. 超链接标记`<a>`:

   -  href(hyperText reference):url(链接到的地址) 

   -  暂时未确定链接目标,将url改为"#"表示空链接点击会跳转到页面头部 ;url改为"javascript:;"则不进行任何跳转

   -  target:_self(在当前窗口打开)  _blank(新建窗口打开) 

   -  锚点链接:可快速定位到链接内容 

     - ​    创建步骤：

     - ​    使用`<a href="#idname">`链接文本`<a> `

     - ​    `<p id="idname">`大量文字内容`<p>`



#### 第二章:页面元素及属性

##### 第1节:列表元素

1. ul(unorder list 无序列表) 
   - 需嵌套li,否则无效 
   - type:disc/circle/square 

2. ol(order list 有序列表)
   -  需嵌套li,否则无效 
   - type:123/ABC/iii/III start(从哪开始)/reversed(逆序,默认值为ture) 

3. dl(自定义)
   -  嵌套一个dt(要解释的名词) 
   - dt后跟一或多个dd(对dt名词解释,会有缩进效果) 

4. list-style-type 设置列表项标志的类型

   -  none/disc(默认,实心圆)/circle(空心圆)/square(实心方块)

   -  decimal(数字)/decimal-leading-zero(0开头的数字)/lower-roman(小写罗马数字)/upper-roman(大写)/lower-alpha(小写英文字母)/upper-alpha(大写)...日文韩文等查手册 

5. list-style-position 列表项标志的位置

   - 即当列表某一项文字过长要换行时,换行文字是否和标志对齐

   - inside/outside(默认 文本不和标志对齐) 

6. list-style-image 将图像设置为列表项标志
   -  none/url()  注：需用相对路径,绝对路径无效 

7. list-style 以上三个属性简写

##### 第2节:结构元素

1. header:导航作用 
   - 通常包含页面头部的内容(一个页面可包含多个header) 

2. nav:定义导航链接(通常嵌套ul) 
   - 适用场合:传统导航条 侧边栏 页内导航 翻页操作 

3. article:用于与上下文不相关独立的部分 
   - 定义一篇日志、一条新闻或评论等 
   - 通常内含多个section将其划分 

4. side:附属信息部分 
   - 在article内作为主要内容的附属信息 
   - 在article外附属,常用于侧边栏,其中内容可为链接、广告单元等 

5. section:对内容进行分块
   - 由标题和内容组成 article强调独立性,可看作特殊的section 
   - section强调分段或块 

6. footer:定义页面或区域底部,类似header

##### 第3节:分组元素

1. figure:定义独立的流内容(图像、图表、代码等) 
   - 一般指一个单独的单元 
   - 内容应与主内容相关,若被删除也不会影响文档流 

2. figcaption:为figure组添加标题 

   - 嵌套在figure内,一个figure至多用一个figcaption 

   - 位置:放在figure第一/最后一个子元素位置 

3. hgroup:将多个标题组成标题组 

   - 当一个标题包含副标题/section/article时,通常放在header中 

   -   通常与h1-h6组合使用

##### 第4节:页面交互元素

1. details、summary 

   -   details描述文档某个细节,配合summary使用 

   -   details嵌套summary和文档内容 单击summary中的内容,details中的文档内容会显示 

2. progress:进度条 
   -   max:当前进度的最大值 
   - value:设定的默认值

3. meter:度量条 

   -   max/min:定义最大/小值,默认为1/0 

   -   high/low:定义哪个点被定义为高/低值(区别在于颜色不同) 

   -   optimum:最佳值 value:度量值

##### 第5节:文本层次语义元素(突出文本之间层次关系)

1. time定义时间或日期 

   -   浏览器中不会呈现特殊效果,但机器可读方式对其进行编码,用户将事件添加到日程表中,搜索引擎产生结果更智能 

   -   datetime属性:定义相应时间如14:00或日期如2016-06-08 

   -   pubdate定义文档发布的时间 

2. mark:高亮某些文本,起到突出显示作用 

3. cite:创建引用标记,被包含的文字会以斜体展示

##### 第6节:全局属性

1. draggable:定义元素可否拖动 
   - 值:true/false (需结合JS) 

2. hidden 
   - 值:true/false (结合JS) 

3. spellcheck:主要针对input元素和textarea 
   - 值:true/false 

4. contenteditable:元素内容可否编辑 
   - 值:true/false