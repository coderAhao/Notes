# CSS

#### 第一章:CSS基础

##### 第1节:浏览器支持情况 

###### 1.IE 

- 内核类型:Trident  私有前缀:-ms 

###### 2.Chrome/Safari 

- 内核:Webkit  前缀:-webkit 

###### 3. Firefox 

- 内核:Gecko  前缀:-moz 

###### 4. Opera 

- 内核:Blink 前缀:-o

##### 第2节:样式规则

###### 1. 格式:选择器{属性:属性值;} 

1. 选择器区分大小写,属性和值不区分,但通常都采用小写 

2. 多个属性之间用分号隔开 

3. 若属性值由多个单词组成且中间包含空格,则需对它加双引号 

4. 为提高代码可读性,通常会对CSS加上注释 

5. 对样式代码进行排版,即所谓的格式化CSS代码

##### 第3节:引入样式表

###### 1.行内式(内联样式):

1. 通过行内style属性设置 

###### 2.内嵌式:

1. 写在头部head标记中,并用style标记定义 

2.  虽可放在文档任何位置,但由于代码自上而下解析,故最好放置在头部

###### 3.链入式

1.  属性:rel="stylesheet" href=""

2. 优点:
   -  一个样式表可被多个HTML引用,一个HTML也可引用多个样式表
   - HTML和CSS的分离实现了结构和表现的完全分离

#### 第二章:文本样式属性

##### 第1节:字体样式属性

######  1.font-style:字体风格

1. normal默认/italic斜体/oblique斜体 
2. 使用斜体时通常用italic

######  2.font-variant:

1. normal/small-caps字体比默认值小一号且小写英文变为大写

######  3.font-weight:字体粗细

1. normal默认值/bold粗体/bolder更粗/lighter更细/100-900由细到粗(需为100倍数)400等同normal 700等同bold

######  4.font-size:字号大小

1. rem 根元素(即浏览器默认 16px)字体大小
   -  即相对于html元素的字体大小来说的

2. 相对长度单位: em（此元素父元素大小的倍数）/px像素/百分比 
   -  即em先继承当前元素字体大小，若没有设置则继承父元素的字体大小,
   - 如父元素fz为10px 则1em为10px

3. 绝对长度单位:in英寸/cm/mm/pt点

######  5.font-family:字体样式

1. 可同时指定多个字体,中间以逗号分隔,若浏览器不支持第一个则会依次往下找

2. 中文字体需加引号,英文不需,但英文必须写在中文之前 

3. 若英文字体包含空格或特殊符号则此时需加引号

######  6.font:综合设置属性

1. 依次为:font-style、 font-variant 、font-weight、 font-size/line-height 、font-family 

2. font-size和font-family必须有,否则属性无效,且书写顺序不可错

######  7.line-height:行高 

1. normal/数字/百分比/px/em 
2. 行高分为三部分,上间距、字高和下间距

######  8.@font-face:自定义字体(新增属性)

1. font-family:字体名称 
2. src:字体路径

######  9.direction:文本方向 

1. ltr文本左对齐 
2. rtl文本右对齐

######  10.unicode-bidi:文字方向

1. normal/embed/bidi-override 配合direction使用

######  11.word-wrap:长单词和url自动换行

1. normal:单词或url不被打断,溢出也不换行 

2. break-word:自动换行不溢出,单词不允许被打断，即某个单词后有空间但不足以排满下个单词,则下个单词会进行换行排布

######  12.word-break:非中日韩文本换行规则

1. normal:单词不被打断

2. break-all:允许单词被打断

3. break-keep:不被打断,碰到连字符或半角空格会自动换行

   

##### 第2节:文本外观属性

######  1.color:文本颜色

1. 预定义颜色值:red/green... 

2. 十六进制:#0-F 当三个分量的数字都相同时可缩写,如#FFAA55可写为#FA5

3. rgb(0,0,250)/rgb(0%,0%,100%) 使用百分比即使为0,%也不可省 ，还有rgba(0,0,0,.5)

4. HSL(H,S,L)（色调,饱和度,亮度），HSLA同rgba增加了透明度

######  2.透明度

1. opacity:0-1之间的值,值越小越透明 (整个标签里连带内容的透明度全都改变)

2. rgba()：元素(即整个容器)的透明度进行改变,但里面的内容不会更改

######  3.letter-spacing:字符间距

1. normal/px/em/-px/-em 英文每个字母/中文每个文字被隔开

######  4.word-spacing:单词间距

1. 用法同letter-spacing
2. 连写的中文等同于一个单词

######  5.line-height:行高(即行间距)

1. normal/数字/百分比/px/em 

2. 其中只有px为固定值其他均为相对值

3. 行高继承:body{font:12px/1.5 Microsoft yahei}
   -  父元素设置了字体大小及行高后,子元素若设置了font-size,则行高为1.5×fz，否则继承父元素为12×1.5 
   - 优势:子元素可根据自身文字大小自动调整行高。

4. 字体不同默认行高则不同,故需重置行高

5. 由于继承特性行高写时最好用数字表示

######  6.text-transform:文本转换

1. none默认/capitalize首字母大写/uppercase全部字符转为大写/lowercase

######  7.text-decoration:文本装饰

1. none/underline下划线/overline上划线/line-through删除线/blink文本闪烁(现仅火狐和opera支持) 

2. 可同时用多个属性,空格隔开

######  8.text-align:水平对齐方式

1. left默认/right/center/justify(两端对齐) 
2. 仅适用于块级元素,对行内无效

######  9.text-indent:首行缩进

1. em/px/%/负值 
2. 建议用em 
3. 仅适用于块级元素,对行内无效

######  10.text-shadow:阴影效果

1. h(水平距离,可为负值) v(垂直距离) blur(模糊半径) red(模糊色) 

2. 例:p{text-shadow:h v blur red} 

3. 使用多个阴影效果时,中间需要逗号隔开

######  11.text-stroke:文字描边

1. px color 两个参数,描边大小和颜色

2. 此属性需浏览器私有前缀,如:-webkit-text-stroke

######  12.text-fill-color 文字填充颜色

1. 同上也需私有前缀才行

######  13.text-overflow:处理溢出文本

1. clip:修剪溢出文本 
2. ellipsis:省略号表示被修剪掉的溢出文本 

3. 单行文本省略：

   -  white-space:nowrap(强制文本不换行);

   -  overflow:hidden(溢出隐藏);

   -  text-overflow:ellipsis(显示省略标)

4. 多行文本省略:

   -  display:-webkit-box(弹性伸缩盒显示); 

   -  -webkit-box-orient:vertical(设置或检索伸缩盒对象子元素的排列方式); 

   -  -webkit-line-clamp:number(文本第几行显示省略);
   - overflow:hidden; 

   - text-overflow:ellipsis

   - 由于兼容性问题推荐后台人员做此效果

######  14.white-space:空白元素处理方式

1. normal:超出范围自动换行,多空格合并为一 

2. pre:空白保留,原格式 

3. nowrap:强制文本不换行,直至遇到br标签 多个空格合并为一 

4. pre-wrap:超出范围自动换行,多个空格符不会合并 

5. pre-line:超出范围自动换行,多个空格符合并为一

######  15.overflow-x:溢出处理 

1. 内容溢出则左右裁剪 (强制使其不换行,配合white-space:nowrap有滚动效果)

2. visible溢出也不裁剪/ hidden裁剪/scroll提供滚动条/auto若溢出则提供滚动条

######  16.overflow-y:

1. 同x,对上下裁剪(不需要配合white-space)

######  17.overflow:

1. 用法同上,设置时同时对x、y起效

######  18.user-select:文本是否可被选中

1. none(不可被选中)/text(可被选中)/element(可以选择文本,但选择范围受元素边界的约束)/all(当所有内容作为一个整体时可以被选择,如果双击或者在上下文上点击子元素,那么被选择的部分将是以该子元素向上回溯的最高祖先元素)





##### 第3节:vertical-align对齐方式

######  1. 设置元素垂直对齐方式（只针对行内或行内块元素,主要用于图片、表单和文字对齐)

1. baseline(默认):与父元素基线对齐

2. middle:与父元素中线对齐

3. top:元素顶端与行中最高元素顶端对齐

4. bottom:元素顶端与行中最低元素底端对齐

5. px/百分比

6. text-top:元素顶端与父元素字体顶端对齐

7. text-bottom元素顶端与父元素字体底端对齐

8. super/sub:与文本上/下标对齐    



##### 第4节:image

######  1.常见图片格式：

1. jpg对色彩信息保留较好，常用于产品类图片 
2. png体积较小可用于图标

######  2.PS切图：

1. 图层切图:
   - 找到所在图层,右击-导出;
   - 很多情况下需要将多个图层合并为一个再将其切出(合并后无法拆分,记得备份)

2. 切片切图:用切片选中后,单击 文件-导出-存储为web-png/jpg等格式-保存

   -  注:在保存路径时注意将最下方的“所有切片”改为“选中的切片”

   -  此外在切透明图片时将背景层关掉,再切为png格式,就可切出透明图

3. 插件切图:cutterman

4. 图片底侧默认会有空白缝隙,原因是行内块元素会和文字基线对齐 ，解决方法:

   -  修改对齐方式 “verticial-align:middle/top/bottom”等(推荐使用) 

   -  块级元素不存在基线对齐问题,故可将图片“display:block”

5. 精灵技术 

   -  目的:为有效减少服务器接收和发送请求次数,提高页面加载速度 

   -  借助“background-position”来实现 ，一般情况下都是负值

#### 第三章:高级特性

##### 第1节

######  1.层叠性:引用不同样式里的不同属性

######  2.继承性: 

1. 可继承属性:外观样式,如文字、颜色 

2. 不可继承的属性:布局属性,如边框/外边距/内边距/背景/定位/布局/元素宽高

######  3.优先级-权重:

1. 权重值:
   - 通配符:0 
   - 标记:1 
   - class:10 
   - id:100 
   - 行间样式:1000 
   - !important:无穷大(Infinity)

2. 继承或通配符(即*)： 0,0,0,0 
3. 标签、伪元素 ：0,0,0,1
4. 类、伪类、属性 ：0,0,1,0  
5. id： 0,1,0,0 
6. 行内 ：1,0,0,0   

7. !important无穷

8. 权重会叠加,到一定程度会进位。权重值用四个数字表示：0,0,0,0相当于十进制的0000,当权重进行叠加时,比如十个li标签,那么此时它的权重值为0,0,0,10 其实将其理解为256进制就很好理解了,当256个li权重值相加时就会进位变为 0,0,0,256 即0,0,1,0 此时256个li标签的权重值就等于一个class标签权重

9. 注:CSS权重进制在IE6为256,后来扩大到了65536,而现代浏览器则采用更大的数量

10. 特殊情况:继承样式权重为0;行内样式优先;权重相同时遵循就近原则,即比较靠近元素;!important写在元素值之后分号之前

#### 第四章:选择器

##### 第1节:基础选择器

1. 标记/类/ID/通配符(*)/标签指定式(即交集,p.class或p#id)/后代(空格分隔)/并集(逗号分隔)选择器

##### 第2节:属性选择器

1. E为标记,att为属性,value为属性值 

2. E[att]:选择具有att属性,无论属性值为何种的E标记 

2. E[att=value]:选择att属性为value的E标记 

3. E[att1] [att2]:根据多个属性选择元素

4. E[att^=value]:选择att属性为以value开头的E标记 

5. E[att$=value]:选择att属性为以value结尾的E标记

6. E[att*=value]:选择att属性为包含value字符串的E标记

7. E[att~=value]:选择att有多个属性值,且其中之一为value的E标记

8. E[att|=value]:选择att属性为以value开头并用"-"连接的E标记

##### 第3节:关系选择器

1. 后代选择器:以空格分隔,所有后代均被选上

2. “>” 子代选择器 (由于继承特性,后代与其同名的则会继承其样式)

3. “+” 临近兄弟选择器 如：E+F， 同一个父元素且紧跟在E之后的第一个F会被选中

4. “~” 普通兄弟选择器 如：E~F ...且在E之后的所有F...

##### 第4节:伪元素选择器 

1. 伪元素主要是用来创建一些不存在原有dom结构树中的元素,不改变文档内容,不出现在DOM中,不可复制,仅在CSS渲染层加入,属于行内元素

2. 写法: E:/E:: 为规范写法,采用双冒号

   -  E::first-letter 选中E元素的第一个字符

   -  E::first-line 选中E元素的第一行

   -  E::selection 被光标选中的E元素

   -  E::before{content:"文字内容"/url()} 配合content,在E元素内部第一个子元素前插入插入文字或图片

   -  E::after ......

##### 第5节:结构化伪类选择器

1. 伪类表示已存在的某个元素处于某种状态,但是通过dom树又无法表示这种状态,就可以通过伪类来为其添加样式

   - :root 匹配文档根元素（相当于选中整个文档）

   - E:not(F) 选择E结构下除F之外的所有元素

   - E:only-child 选择父元素仅有一个子元素且为E的元素

   - E:first-child 父元素有一或多种子元素,但第一个子元素需为E (即只选中第一个且必须为E)

   - E:last-child ......

   - E:nth-child(n) 选择某个父元素下第n个E元素 (n可为odd奇数 even偶数 2n/n+1等表达式)

   - E:nth-last-child(n) ......

   - E:only-of-type 父元素下有一或多种元素,但E类型的只有一个

   - E:first-of-type 父元素下有一或多种元素,E类型也有多个,但只选中第一个E (即只选中同种类型的第一个)

   - E:last-of-type ......
   - E:nth-of-type(n) ......

   - E:nth-last-of-type(n) ......
   - E:empty 匹配任何子元素或文本内容为空(连空格都不能有)的E元素

##### 第6节:链接(UI)伪类

1. a:link 未被访问时的超链接

2. a:visited 被访问后

3. a:hover 鼠标悬停或划过时

4. a:active 鼠标单击时

5. 书写时以上四种最好按此顺序进行,否则可能无效果

6. E:focus 拥有键盘输入焦点的E元素

7. input:checked/enabled/disabled 被选中/启用/禁用的input元素

8. :not(E){} 选择除E以外的元素添加样式

9. cursor(鼠标形状 ):pointer手 /move移动 /not-allowed禁止 ...



#### 第五章:盒模型

##### 第1节:基础

1. div最大意义:配合float,实现网页布局,即DIV+CSS网页布局 

2. 盒子总宽:width+左右padding+左右border+左右margin

3. 盒子总高:height+上下......

4. div默认宽度等同屏幕宽,需添加宽度才能给它加左右外边距

##### 第2节:样式属性

######  1.边框属性:

1. border-width:px 

2. border-style:none/solid/dashed...

3. border-color:颜色值/rgb/十六进制 

4. border:width style color (综合属性,顺序随意) 

5. border-radius: h(水平半径)/v(垂直半径) (注:此为四个角的综合属性,可分别设置四个角的大小) 

6. border-image: 

   -  border-image-source(图像来源路径): url()

   -  border-image-slice(边框背景图分割方式): 数值或百分比,不能带px(复合数值,大小代表往里进像素大小)

   -  border-image-width(边框宽度): px

   -  border-image-outset(边框背景图的扩展): px (边背景向盒子外部延伸距离)

   -  border-image-repeat(边框图像平铺方式): 

   -   stretch(默认,拉伸)/repeat(重复铺满)/round(调整图片进行铺满);值可复合两个,如stretch round即x向拉伸y向铺满,调整顺序效果不同

7. border-image(复合属性):  source slice/width/outset repeat 
   -   用法有注意的地方,如url() 30 /30px /40px  round,即分割方式、宽度与扩展之间需用“/”分开 

######  2.边距

1. padding:上右下左 

2. margin:上右下左

3. box-shadow:盒阴影

   - 值:h v r r color inset/outset 

   - 水平阴影 垂直阴影 模糊半径 扩展半径 颜色 内/外阴影(默认)

   - 当左右偏移值为0时,写上outset或inset图片无变化,如果不写图片则会有外/内发光效果

4. box-sizing :盒子宽度

   - content-box(默认值):padding和border参数值不包含在width height中

   - border-box:padding和border参数值包含在width height中

5. outline:边框的轮廓

   - 位于边框外围,突出元素作用

   - outline-width/outline-style/outline-color

   - outline:复合属性,用法同border

   - outline-offset:轮廓线距边框距离

6. offset及client

   - offsetLeft:到最近的已定位的父元素左侧的距离(即到父元素左padding的距离)

   - offsetWidth: 控件自身宽度,即width+左右padding+border

   - offsetTop:到最近的已定位的父元素顶部的距离
   - clientWidth: 控件自身宽度,即width+左右padding

##### 第3节:背景属性

1. background-color(颜色):transparent(默认透明色)

2. background-image(背景图像):url()

3. 背景与图像透明度:

   - rgba(r,g,b,alpha) alpha介于0(完全透明)和1(完全不透明) (仅元素盒子透明度变化,里面的内容不变化)

   - opacity:0~1 (元素和里面内容的透明度均会发生变化)

4. background-repeat(图像平铺方式):repeat-x/repeat-y/repeat/no-repeat

5. background-position(图像位置):

   - px px 

   - left/center/right/ top/center/bottom

   - x% y%  (图像上%比位置与元素上%比位置对应)

6. background-attachment(图像固定):scroll(随页面元素滚动)/fixed(固定)

7. background-size(图像大小):

   - px px/% %

   - cover 图像完全覆盖背景,图像宽高比会被改变

   - contain 图像以原比例放大,使宽或高和背景重合,不一定能完全覆盖背景

8. background-origin(背景定位方式):

   - padding-box 相对于内边距定位 

   - border-box 相对于边框定位 

   - content-box 相对于内容定位

9. background-clip(背景裁剪区域):

   - padding-box 从内边距往外裁剪 

   - border-box 从边框往外裁剪 

   - content-box 从内容区域往外裁剪

10. background(复合属性):将以上属性一起写出,顺序随意,不需要的属性可不写

11. 添加多重背景:通过image repeat position size等来实现叠加

12. clip: 设置元素形状 

    - 元素被裁剪入这个形状中(只有设置了position:absolute/fixed才会有效果)。

    - clip:rect(top,right,bottom,left) 

    -   注意： top 图片上边缘距到所要裁剪上边处;bottom 图片上边缘到需要裁剪下边处 ;left图片左边缘到需要裁剪左边处 ;right 图片***左边缘***到需要裁剪右边处

#### 第六章:浮动与定位

##### 第1节:浮动

######  1.传统网页布局三大方式:

1. 标准流(标签按照规定好的默认方式排列)、浮动、定位

######  2.浮动:

1. 元素脱离文档流的控制移动到父元素指定位置

2. 特性:只要添加浮动属性,元素就会具有行内块元素的特点 

   -  行内元素添加了浮动,不需进行display转换就可给宽高

   -  如果块级盒子没有设置宽度,则默认和父元素一样宽;但当添加浮动后,其宽度由里面的内容撑开

   -  浮动的盒子只会影响它后面的标准流;当一个标准流后面的盒子浮动后,浮动的盒子会贴在它后面而不会浮在其左右,因为标准流会独占一行

   -  一个盒子浮动,理论上其余的兄弟盒子也要浮动

3. float(浮动属性):left/right/none

4. clear(清除浮动):left/right/both 不允许元素左/右/两侧有浮动元素

   - 清除原因:父级盒子不方便给高度,当所有的子盒子都浮动后,父元素高度会为0,下面的标准流盒就会顶上来

   - 清除浮动的本质:清除浮动元素脱离标准流造成的影响

5. 清除浮动方法:

   - 在结构父元素结尾处添加空p/div/hr等标记,再对标记应用“clear:both”  缺点:如果布局复杂会添加较多无用标记

   - 在父元素样式表里添加“overflow:hidden/auto/scroll”,浏览器自动检查浮动区域高度 缺点:超出部分被隐藏

   - 利用伪元素在样式表里给父元素添加空元素“after{content:"";display:block;clear:both}” 为了兼容IE6、7,父元素还需添加“{*zoom:1;}”

   - 双伪元素清除浮动“.clearfix:before,.clearfix:after{content:"",display:table} .clearfix:after{clear:both;} .clearfix{*zoom:1}”

##### 第2节:overflow(溢出)

1. visible:溢出的元素不被修剪

2. hidden:溢出的内容被修剪

3. auto:当内容溢出时会增加滚动条

4. scroll:无论内容是否溢出均会增加滚动条

##### 第3节:定位模式position

1. static:静态定位(默认,无法通过边偏移改变位置)

2. relative:相对定位 (原位置被保留且会相对自身原位进行偏移 注:对象不可层叠)

3. absolute:绝对定位 
   - 原位置不被保留且依据最近的已经定位的父元素进行定位,若父元素均未定位则以body进行定位（对象可层叠）

4. fixed:固定定位 (脱离标准文档流控制,以浏览器窗口进行定位)

5. sticky:粘性定位 (导航盒子随滚动条滚动到距离窗口上沿某一距离便固定不动)
   - 可认为是相对和绝对的混合定位,需添加left/right/top/bottom 才有效 
   - 兼容性较差,IE不支持

6. z-index:层叠等级 (仅对定位元素有效,默认值为0,值越大图层越靠上)

7. 实操中,父元素设置relative但不对其进行偏移,子元素设置absolute,这样父元素不会失位且保证子元素依据父元素进行定位 (即子绝父相)

8. 子元素仅设置绝对定位而不设置边偏移,元素位置虽不变但不再占用文档流空间且会与后续元素重叠

9. 绝对定位盒子居中技巧: 先“left:50%”至父元素中心再“margin-left:自身宽度/2”

10. 定位特殊性:

    - 行内元素添加ab/fix定位,则可直接设置宽高,即不需再display转换

    - 块级元素添加ab/fix定位若不给宽高则宽高由内容撑开

11. 浮动、绝对、固定等脱标的元素不会触发外边距合并问题

12. 浮动元素只会压住下面的标准流盒子而不会压住盒子里的文字及图片 ；绝对和固定定位的元素则会压住所有内容

13. 边偏移含义:定位后子元素相对父元素边线的距离

    - left/right/bottom/top 

    - left和right冲突则以left为准
    - top和bottom冲突以top为准

14. 设置了定位position:absolute和浮动float属性后,其属性会自动转换为inline-block



##### 第4节:元素类型与转换

######  1.类型

1. 块元素(标记)

   -  特点:独占一或多行,可对其设置宽高、对齐等属性,用于网页布局和页面搭建

   -  常见的有:h1~h6 p div ul ol li等(注:p嵌套块级元素则会被截断)

2. 行内元素(标记)

   -  特点:会和它前后的其他行内元素在同一行,不独占区域且依靠自身字体、图片大小支撑结构

   -  不可设置宽高、对齐等属性,可定义左右margin,但上下无效,用于控制页面中文本样式

   -  常见的有：strong、b、em、i、del、s 、ins、u、a、span 

   -   (注:a标签内不可再嵌套a)

   -   特殊元素:img、input td可对其设置宽高和对齐等属性 (可被称为行内块元素)

   -  行内元素通常嵌套在块元素中,但块元素不可嵌套在行内元素中

   -  行内块元素或文本类元素包含文本,外面的文字就会和里面的文字底对齐,若无文本则和元素底对齐

######  2.display(转换):

1. inline: 转换为行内元素,大小自适应,不换行

2. block:转换为块元素,同时还有显示元素的意思

3. inline-block:转换为行内块元素,可对其设置宽高和对齐等属性,但不会独占一行

4. none:此元素将被隐藏,不显示也不占用页面空间,相当于不存在

######  3.visibility(显示与隐藏):

1. visible:元素可视

2. hidden:隐藏后其位置被保留



##### 第5节:元素居中方法

######  1.垂直居中

1. 盒子边缘至父中间后再偏置自身一半 (如先left：50% 再margin-left:负自身width/2)

2. 父元素设置“display:table”子元素设置“display:table-cell;vertical-align:middle”

3. 计算margin值

4. 元素设置“display:inline-block;vertical-align:middle”

5. 使用弹性盒“display:flex; align-items:center”

######  2.水平居中 

1. 盒子边缘至父中间后再偏置自身一半

2. 父元素设置“display:inline-block;text-align:center”

3. 计算margin值

4. margin:0 auto （盒子需设置宽度）

5. 绝对定位后left/top各50%,再translate(-50% -50%)

6. 父元素设置“display:flex; justify-content:center”



#### 第七章:transform与动画

##### 第1节:过渡（通常指针移到元素上触发此效果）

1. transition-property:none/all/property(需过渡的css属性名称)

2. transition-duration: 过渡效果花费的时间,单位秒

3. transition-timing-function: ease/linear/ease-in/ease-out/ease-in-out/cubic-bezier(n,n,n,n) 慢速开始,加快,慢速结束(默认值)/匀速/淡入(慢速开始,逐渐加快)/淡出/淡入淡出/贝塞尔

4. transition-delay: 过渡效果何时开始

5. transition: property  duration  timing-function  delay (复合属性,顺序不可错)

##### 第2节:2D变形 transform:

1. translate(x,y) 

   - 以元素中心为基点进行平移 (移动时不会影响其他元素,相当于相对定位 对行内元素无效)

   -  参数若为百分数则移动其自身宽高的百分比

2. scale(x,y) 以元素中心为基点进行x,y向的缩放 (负值效果为先翻转再缩放)

3. skew(x,y) 以元素中心为基点围绕x,y轴进行倾斜 

4. translate、scale省略y则默认x=y,skew省略y则默认y为0

5. 综合写法：translate() scale() 注意书写顺序不同则效果不同

6. matrix(ax,bx,by,ay,cx,cy)
   -  a、b、c分别代表缩放、倾斜、平移 
   - 三种效果合在一个值里

7. rotate(angle) 以元素中心为基点进行旋转 (正顺负逆)  
   - 旋转角度为当前状态相对于最初时的角度,并非旋转了多少度,别混淆了

8. transform-origin:x y 
   - 改变变换的基准点(可用left/top或%表示)

##### 第3节:3D转换transform:

1. translate3d(x,y,z)/translateX(x)/translateY(y)/translateZ(z)
   - 物动眼定 值越大看到的放大倍数越大

2. scale3d(x,y,z)/scaleX(x)/scaleY(y)/scaleZ(z)

3. rotate3d(x,y,z,angle)/rotateX(angle)/rotateY(angle)/rotateZ(angle) 
   - 如rotate3d(1,1,1,45deg)即沿着从原点到坐标(1,1,1)的矢量旋转45deg 
   - 旋转方向:左手螺旋定则 大拇指指向X/Y轴正向四指弯曲方向即为旋转方向，向里为正

4. perspective:px 

   - 为3d转换定义透视图 ，值可取800~1200px之间,需加此元素才能进行3d转换

   - 值越小,即眼睛越靠近物体(眼动物定)看到的放大倍数越大(即看到的投影图)

   - 注:需要将此属性添加至所需元素的父元素上

5. transform-style:flat关闭(默认)/preserve-3d开启  
   -   当一个盒子的子元素开启了3D效果,若此盒子再开启3D效果,则子元素会默认被关闭(将此属性添加至父盒子上,使子元素重新打开)

##### 第4节:动画

1. 先使用关键帧“@keyframes animationname{ from{} to{}/%{} %{} }”创建动画 

2. animation-name:none/keyframename(即用@keyframes创建的动画名字)

3. animation-duration: 动画持续时间

4. animation-timing-function:ease/linear/steps/ease-in/ease-out/ease-in-out/cubic-bezier(n,n,n,n)
   - 值'steps()'可做打字机效果 即将规定时间分为几步

5. animation-delay:动画延时

6. animation-iteration-count:number/infinite(无限循环) 动画播放次数

7. animation-direction：normal/alternate(顺逆交替) 动画是否在下一周期逆向播放

8. animation:复合属性,将以上六种依次写上 name和duration为必写

9. animation-fill-mode:none/forwards/backwards/both 动画时间之外的状态

   - forwards:动画显示在第一帧之前的状态,动画完成后保持在最后一帧

   - backwards:动画显示在第一帧,动画完成后保持在第一帧状态

10. animation-play-state:running/paused 动画运行状态 (即事件触发控制动画是暂停或运行)



#### 第八章:音视频

##### 第1节:支持条件

1. 编解码器:音视频原始数据较大,传输时需对其进行编解码
   - 视频: H.264/Theora/VP8 
   - 音频: AAC/MP3/Ogg

2. 视频格式 

   - Ogg:带有Theora视频编码和Vorbis音频解码的Ogg文件 

   - MPEG4(MP4):带有H.264视频编码和AAC音频编码的MPEG4文件

   - WebM:带有VP8视频编码和Vorbis音频编码的文件

3. 音频格式:Vorbis/MP3/Wav

##### 第2节:常见属性

1. 音视频共有:

   - src:"src"；controls:"controls"；autoplay:"autoplay"；loop:"loop"

   - preload:"preload"；poster:"url"视频播放前预览图像 
   - 注:引入src使用相对路径无效

2. 其他:

   - paused:true/false 设置或返回当前音视频是否暂停

   - currentSrc 设置或返回当前音视频的url

   - currentTime 设置或返回当前音视频的播放位置

   - defaultMuted 设置或返回音视频是否默认静音(非改变当前)

   - muted:true/false 设置或返回当前音视频是否静音

   - volume 设置或返回当前音视频的音量(值介于0到1之间)

   - defaultPlaybackRate 设置音视频默认播放速度

   - playbackRate 设置当前音视频播放速度

   - duration 设置或返回音视频总长度

3. 解决兼容性:
   - video/audio标签内嵌套多个"source"标签,标签内指定"src"和"type"属性，如"type=video/mp4" 注:此时需去掉video内的src属性

##### 第3节:方法和事件

1. 方法

   - load() 播放前预加载,也可用于重新加载

   - play() 播放，将paused属性变为false 

   - pause()暂停 ，将paused属性变为true

   - canPlayType() 测试浏览器是否支持指定的媒体类型

2. 接口事件

   -   play 当执行play()时触发 

   -   playing 正在播放时触发

   -   pause 当执行了pause时触发

   -   timeupdate 当播放位置被改变时触发 
     - 用法:videoname.ontimeupdate=functionname 
     - 注:函数名称后不能有括号,否则事件不能触发

   -   ended 播放结束停止播放时触发

   -   waiting 等待加载下一帧时触发

   -   ratechange 当前播放速率改变时触发

   -   volumechange 音量改变时触发

   -   durationchange 当播放时长改变时触发

#### 第九章:表单

##### 第1节:表单属性及方法

 1. 属性:id/name/action/method/target/length /autocomplete/novalidate

    - name:指定表单名称

    - action:url 表单提交到服务器的地址
    - method: 提交方法 
      - get:一段传输,保密性差,数据量有限
      - post:分段传输,保密性好,无数据量限制
    - autocomplete:on/off 记录输入框的输入记录 
    - novalidate:true/false 取消对表单提交时的检查

2. 用法及方法

   -  用法:formname.id

   -   formname.elements 表单中所有控件的集合

   -   formname.elements[index] 访问表单中的某个控件

3. 常见访问方式:

   -   document.getElementById('')

   -   document.getElementsByTagName('form')[index]

   -   document.forms[index]

   -   document.forms[name]

##### 第2节:表格

1. 三要素
   -   table定义表格 
   - tr:行 
   - td:单元格
   - 
   
2. table对象集合：

   -   rows:返回包含表格中所有行的数组 
     - 用法:tableObject.rows

   -   cells:返回包含表格中每行中所有单元格的数组 
     - 用法:tableObject.rows[i].cells

3. table属性：

   - border:边框距 
   - cowspan:合并列 
   - rowspan:合并行 
   - th(thead)/tfoot/tbody 表格的表头、脚、体 （规范写法应包含） 
   - cellpadding:内容到单元格边距
   - cellspacing:单元格之间的边距 
   - border-collapse:separate(分开,默认)/collapse 表格边框合并为单一边框
   - border-spacing:设置分隔单元格边框的距离
     -    此时border-collapse属性值为collapse,否则不需spacing属性
   - caption-side:top/bottom 表格标题的位置
   - empty-cells:hide(前提border-collapse应为separate)/show 空单元格是否显示
   - table-layout:auto(注意:td即表格宽度不能设置,否则二者冲突;table需给定宽度)/fixed 表格宽度是否随内容变化 

4. 方法:

   -   createCaption() 为表格创建一个caption元素

   -   createFHead() 

   -   createTFoot() 

   -   deleteCaption()

   -   deleteTHead()

   -   deleteTFoot()

   -   insertRow(index) 在下标为index处新建一行(下标从0开始) 若省略参数则默认在末尾添加

   -   deleteRow(index) 必须指定参数否则无效 

   -   insertCell(index) 在指定行index处插入一个空的单元格

   -   deleteCell(index) 

5. 多列:

   - column-width: 列宽 auto(默认值) 
     -    其实为页面被缩放时列的最小宽度,即列宽不能比此数再小,否则列数依次进行减少, 

   - column-count: 元素被分割的列数 auto(默认值)

   - columns: 列宽和列数的简写属性

   - column-rule:列分割线 

     - 用法同border,为以下三个简写属性

     -    column-rule-width 
     - column-rule-style 
     - column-rule-color

   - column-span: 元素横跨列数 默认值为1,可设置为all 

   - column-gap: 列之间的间隔

   - column-fill: 如何填充列 

##### 第3节:input元素及属性

1. type: 

   -   text(单行文本框)/password/radio/checkbox/button/submit/reset/image(图片式提交按钮)/hidden(隐藏域)/file/email/url/range/search/color/(date,month,week...)/tel/number(附加min max step value)

   -   checkbox(添加name和value属性且name值相同value值不同)

   -   radio(需添加name和value属性且name属性为同一个值)

2. name/value/size(控件宽度)

3. readonly:readonly 只读

4. disabled:disabled 禁用该控件

5. checked:checked 默认被选中

6. maxlength: 允许输入的最多字符

7. autocomplete:on/off 记录输入框的输入记录(input需有name,否则无效)

8. autofocus:autofocus 自动获取焦点

9. form:formname 该控件属于哪个表单

10. list:listname 和datalist配合使用

11. multiple:multiple 选择多个值（常用于type=file/email 选取多个文件/邮箱）

12. min、max、step:输入框所允许的最小/大值及间隔

13. placeholder: 提示信息,输入框获取焦点时提示信息则消失

14. required:required 填写内容为空则无法提交

##### 第4节:其他表单元素

1. button:
   - 在表单中使用input创建按钮,其他地方使用button创建按钮
   - 因为在表单中使用button不同浏览器会提交不同值

2. text单行文本框

   -  方法:

     -   blur()文本域上移开焦点

     -   focus()

     -   select()

     -   例:inputname.focus()

3. textarea:多行文本框

   - cols:每行字符数 

   - rows:行数 

   - style="resize:none"文本框大小不可拖曳改变

4. select:下拉列表 (嵌套option使用)

   - 属性:length/multiple/size/selectedIndex

     - length: 设为0可将所有删除

     -  size:下拉菜单可见选项数 

     -  multiple:multiple 多选功能

   - 嵌套option:

     -  optgroup(需有label属性):给option分组,嵌套option
     -  option: selected='selected' 默认被选中
     
   - 创建option方法:

     -  new Option(text,value,true,true) 
     - 后面两个true表示默认被选中和有效

   - 方法：

     -  selectname.add(obj,index) 
       - index省略则添加在末尾,否则添加在index处

     -  selectname.remove(index) 

     -  focus()
     - selectname.options 所有option的集合

5. datalist:下拉菜单(嵌套option效果同select)

   - 和input配合使用,id值需和input的list属性绑定

   - value值若和标签值不同,google浏览器中会将value值和标签值都显示出来,firefox则只显示标签值

6. label元素: 用来为input元素定义标注并与之关联

   - 用法: 

     -  for属性绑定input的id值

     -  label标签中嵌套input 

   - optgroup中添加可为下拉菜单添加标签分组

7. progress:进度条

   - max:规定当前进度最大值 

   - value:设定默认显示值

   - form:规定所属的一个或多个表单

8. meter:度量条 

   -  max默认值为1  min默认值为0 

   -  low视作最低的标准  high视作最高标准(高和低区别在于度量条颜色不同而已) optimum最佳标准

   -  value定义度量值 

   -  form所属一个或多个表单

9. details: 隐藏某些内容,当点击显示符号时将内容显示出

   - 属性open  将内容直接显示出,当点击时才隐藏

   - 子标签summay:为details添加标题

10. fieldset: 将表单内的元素进行分组,加个边框
   - legend:对分组的元素加个标题(fieldset下加它,和fieldset为同一级)

##### 第5节:表单重写

1. 只适用于提交按钮(input或button都行)

2. form表头中的action为提交的url地址,input中的formaction将重写action地址,即点击时跳转到此url

3. input中的type属性应为submit  

   -   formenctype重写enctype属性
-   formmethod重写method属性
   -   formtarget重写target属性
-   formnovalidate重写novalidate属性

##### 第6节:事件

1. form事件句柄

   - onsubmit 提交表单之前调用 (即在提交表单之前调用函数,如果函数结果满足要求则提交表单,否则不提交) 

   -   onreset 重置表单元素之前调用

   -   注:提交按钮需“type=submit”

   -   例:

     ```javascript
     <form action="#" onsubmit='return cofi()'>
        姓名<input type="text"> 
        <input type="submit" value="提交">
      </form>
      <script>
         function cofi() {
           if (confirm('确认提交？')) {} 
         }
       </script>
     ```

2. 事件:复制、粘贴

   -   oncopy 用户复制时触发此事件 
     -    inputname.oncopy=fun(){ ... return false} 函数中“return false”则会禁止复制

   -   onpaste 粘贴

   -   oncut 剪切

   -   oncontextmenu 整个文档 函数中“return false”则会禁止右键查看源代码

   -   例:

       

     ```javascript
     <form action="#" name="form1">
     
        <input type="text" name="copystr" value="禁止复制和粘贴">
     
        <input type="text" name="pastestr">
     
     </form>
     
     <script>
        var copystr=document.form1.copy;
     
        copystr.oncopy=function () {
     
          alert('确定复制？');
        }
     </script>
     ```
     
     

##### 第7节:注意事项

1. form为块元素,input默认有边框效果,通常需将其padding、margin、border重置为0;文本框和密码框通常会设置2-3像素的内边距,使输入内容不紧贴输入框。

2. form属性:将表单外的东西与表单关联,表单头内给表单添加id,表单外的东西加 form=“id” 进行关联

#### 第十章:布局

根据内容是百分比还是固定尺寸可以划分为流体定位布局/固定定位布局

##### 第1节:流体布局

1. 优点:能自适应用户设置,对用户更友好;页面周围空白区域在所有分辨率和浏览器下均相同,视觉上更美观

2. 缺点:设计者难控制用户所见，可能忽略掉一些错误,因为其在特定分辨率下好看；视频以及设置了宽度的内容需要多种宽度以适应不同分辨率的用户

##### 第2节:固定布局

1. 优点:设计宽度易控制;在所有浏览器中宽度一样,不设置min-width和max-width来防止因内容缩放引起的布局混乱

2. 缺点:分辨率较高的用户两边留白,分辨率过小则需加滚动条

##### 第3节:伸缩布局

1. 父元素添加“display:flex” ，子元素添加“flex:份数”,还可指定“min/max-width”使其在一定宽度便不再伸缩

2. 布局方向:“flex-direction:column(列)/row(行)”

   -   水平方向:父元素添加justcify-content:flex-start(子元素左对齐)/flex-end(右)/(center居中)/space-between(两边贴近两端,中间的均分空白区域,空白留在各个元素之间;注：子元素此时不加“flex:1”)/space-around(空白留在各个元素两边,相当于给每个盒子添加了margin)

   -   垂直方向:父元素添加align-items:flex-start(上对齐)/flex-end(底)/center(居中)/stretch(在子元素不给高度的前提下,子元素高度继承父元素)

   -   是否换行:flex-wrap:nowrap(默认值不换行 即固定宽高的子元素充满父盒子后再增加一个子元素,原子元素宽高无效盒子仍被充满,新加子元素不换行)/wrap(换行)

   -   多行垂直居中对齐(父元素必须“display:flex,flex-direction:row,flex-wrap:wrap”): align-content:stretch/center/flex-start/flex-end/space-between/space-around(注:此属性是针对多行,以上几个是针对单行)

3. 子项目排列顺序order:number(默认为0 可为负数值越小越靠前)

   

#### 第十一章:canvas

属性: id width height仅此三个

##### 第1节:路径方法

1. strokeStyle 设置颜色、渐变或模式

2. lineWidth 设置线宽(直接给数值即可无需加px)

3. moveTo() 定义路径起点

4. lineTo() 添加一个新点(即为前面一条线的终点)

5. stroke() 开始绘制已定义的路径

6. beginPath() 画完一个图形后，接着画其他的

7. closePath() 最后一个点直接和第一个点相连形成封闭图形

##### 第2节:矩形

######  1.画矩形的两种方法:

1. 

   - c.strokeStyle=''
   - c.rect(x,y,width,height)

   -  c.stroke();

2. 

   -   c.strokeStyle=''

   -   c.strokeRect(x,y,width,height)

######  2.填充矩形两种方法:

1. 

   - c.fillstyle=''

   -   c.rect(x,y,width,height)

   -   c.fill()

2. 

   -   c.fillstyle=''

   -   c.fillRect(x,y,width,height)

##### 第3节:画圆弧

- arc(x,y,r,起始角度,结束角度,ture/false) 
- 角度需用 Math.PI表示,ture/false表示 逆/顺时针

##### 第4节:填充文字

1. font="px 字体";

2. strokeText("文字",x,y) 此为镂空文字（lineWidth设置笔画宽）

3. fillText("文字",x,y) 实心文字

##### 第5节:渐变

1. ###### 线性渐变

   -   createLinearGradient(x1,y1,x2,y2)颜色渐变的起始坐标和终点坐标

   -   addColorStop(0,"颜色值")

   -  addColorStop(中间值,"颜色值") 这个可不要

   -  addColorStop(1,"颜色值") 
     - 用法:定义一个变量A=createLinearGradient(x1,y1,x2,y2)  
     - 画布.fillStyle=A
   - linear-gradient(x角度(deg) color,color)

   -  linear-gradient(to right/left.. , color,color) 

   - linear-gradient(x角度(deg) color px/%,color px/%)
     -  (控制颜色渐变的百分比时，最后一个应为100%)

   -  repeating-linear-gradient(同上需要的数值)重复线性渐变

2. ###### 径向渐变

   -   用法同上 具体用法及含义百度

   -  createRadialGradient(x1,y1,r1,x2,y2,r2)颜色渐变的起始坐标、半径和终点坐标、半径

   -  radial-gradient(color color)

   -  radial-gradient(ellipse/circle 半径(即颜色在多大的范围内进行渐变) at 圆心位置 , color,color)
     -  圆心位置可用 x% y%/px px/关键字表示(closest-side圆心到距离最近的边 farthest-side 远的边 closest-corner最近的角 farthest-corner最远的角)(椭圆的话，半径值为两个)

   -  repeating-radial-gradient(同上需要的数值) 

##### 第6节:阴影

1. shadowOffsetX= 设置阴影水平偏移距离

2.  shadowOffsetY=

3. shadowBlur=   模糊系数

4.  shadowColor=  阴影颜色

##### 第7节:其他

1. canvas宽高设置在行间和style中有区别:
   -   canvas默认宽高为300X150,在style中设置会将画布拉伸到指定大小画布中图形会变形
   -  在行间设置时则不会

2. 样条结束点的样式: lineCap=butter/round/square 平直/圆形/正方形线帽

3. 交线拐角样式: lineJoin=miter/bevel/round  尖角/斜角/圆角

4. 斜接长度:两条线交汇处内角和外角之间的距离 

   -   miterLimit=x 设置斜接长度 注:只有“lineJoin=miter”时才有效

   -   当斜接长度超过x时,此时边角效果为bevel

5. 清空画布: clearRect(x,y,w,h) 清除指定矩形区域内元素

6. 绘制与两直线相切的圆弧arcTo(x1,y1,x2,y2,r) 用法:以moveTo(x0,y0)为起点形成两直线

 

#### 第十二章:其他特性

##### 第1节:CSS书写顺序

1. 布局定位属性：display/position/float/clear/visibility/overflow

2. 自身属性：width/height/margin/padding/border/background 

3. 文本属性：color/font/text-decoration/text-align/vertical-align/white-space/break-word

4. 其他属性:content/cursor/border-radius/box-shadow/text-shadow/background:linear-gradient...

##### 第2节:BFC(Block Formatting Context)

1. bfc是一个独立的渲染区域只有块级元素参与,它规定了内部元素如何布局与外部无关

   -   说白了bfc就是一个封闭的区域

   -   触发bfc后,bfc内部元素即使浮动也不会影响外部,同理外部也影响不到内部

2. 触发BFC的属性:

   -   块级元素具有bfc条件,属性display:block(此为块元素的默认值无需给块添加)/list-item/table 使元素具有条件(注:仅是具有bfc条件,还不能触发，以下属性才可触发)

   -   position为absoluted或fixed

   -   display为inline-block/table-cell/table-caption/flex/inline-flex

   -   float属性不为none

   -   overflow不为visible,可为hidden/auto/scroll

3. 特性

   -   内部盒子从顶端垂直排列

   -   内部盒子margin会合并,即两个盒子都有margin则会取其最大的一个

   -   BFC盒子不与浮动盒子产生交集,只会紧贴其边缘
     -    即前一个盒子虽然float,但触发了BFC的盒子不会浮动到其下面只会紧贴其边缘

   - 计算BFC高度时，自然也会检测浮动盒子高度

4. 用途

   -   清除子元素浮动 
     - 常见用法：父元素设置“overflow：hidden”

   -   解决外边距重叠合并问题:
     -    在一个总BFC内两个子元素产生外边距合并，此时给其中一个再嵌套一个父元素盒子，使其处于不同辈分。这样两个盒子就不再处于同一个BFC下了。
     - 注：再嵌套的父盒子需加“overflow：hidden”

   -   解决盒子塌陷问题

   -   解决文字会环绕在浮动元素周围的问题 

   -   制作右侧自适应盒子（其特性3）

##### 第3节:外边距合并(margin塌陷)

1. 父子之间

   -   子元素设置的margin-top值比父元素的margin-top值大时,会造成父元素以子元素margin-top值进行定位,且子元素设置的margin-top无效

   -   触发盒子的bfc,即解决margin塌陷问题,给父元素加上以下其一元素：

     -    position:absolute 

     -    display:inline-block 

     -    float:left/right

     -    overflow:hidden  

     -    border-top:   

     -    padding-top:

     -    此方法会引起新的问题,并不是实际解决而是弥补,视情况选择方法

2. 兄弟之间

   -   两个相邻的div设置margin-left和margin-right,margin会累加;设置margin-top和margin-bottom,margin则会取其中一最大值

   -   在一个总BFC内两个子元素产生外边距合并，此时给其中一个再嵌套一个父元素盒子，使其处于不同辈分。这样两个盒子就不再处于同一个BFC下了。(注：再嵌套的父盒子需加“overflow：hidden”)

##### 第4节:高度塌陷

1. 由于父元素中的子元素设置了浮动属性造成父元素高度塌陷(即父元素高度为零)

   -  解决办法:

   - 1.在子元素末尾添加一个块级元素且清除其左右浮动

   - 2.利用伪元素配合content属性在父元素中添加元素 样式如下 

     -   parent:after{content:'';display:block;clear:both}

     -   伪元素是行级元素，要设置宽高将其改为块级元素,只有块级元素才能清除浮动

##### 第5节:大纲规范算法

1. section标签中至少包含一个h1~h6

2. 如果是页面布局且不是header、footer之类的专属区域,都应该使用div

3. body 、nav、 section都是需要有标题才规范 header div 则不需要

4. nav无标题也合理,但最好添加然后display将其隐藏就不会破坏布局

##### 第6节:其他规则

1. CSS3滤镜: filter:函数()

   -   filter:blur(5px) 模糊

   -   filter:contrast(200%) 对比度...

2. calc函数:
   -   calc(100% +-/* px) 
   - 即设置盒子宽度时可用此函数使子盒子始终小于父盒子一定的数值(百分比和四则运算符和px之间均需空格隔开)

3. @规则：

   - @charSet 设置样式表的编码 如“@charSet 'utf-8';”

   -   @import 导入其他样式文件 ，如在HTML中只link一个index.css,而index中可导入“@import 'reset.css'”

   -   @media  媒体查询,查询用户使用的何种设备以及设备的大小

   -   @font-face 自定义字体

4. base标签:

   -   一个页面中只能用一个base标签,标签放在head中

   -   base作用:为a标签设置基础样式

   -   用法:如`<base target="_blank" href="http://www.baidu."> `
     -    则页面内的所有a标签都不必再写target属性,且写“href”时只需写“baidu.”后面的地址即可

5. 实用工具:

   -   “W3C统一验证工具” 可验证CSS代码是否合格

   -   “站长之家-css格式化” 可解压缩CSS代码

   -   制作facvion图标：png图片通过比特虫转为ico格式放在项目根目录下，通过`<link rel="shortcut icon">`引入

6. 网站TDK三大标签SEO优化:

   -   SEO(search Engine Optimization):搜索引擎优化，利用引擎规则提高网站排名方式

   -   T即title 网站名-网站介绍

   -   D即description 如`<meta name="description" content="网站主要做啥">`

   -   K即keywords 如`<meta name="keywords" content="网站主要产品逗号分隔产品">`



##### 第7节:小技巧

1. 做三角形:

   -   四个三角形均分一个盒子：盒子宽高设置为0，单独设置四个边框，边框宽度为所需宽度

   -   只显示1/2/3个三角形：将对应的上/下/左/右border宽设为0 (特殊状况 只显示一个时：需保留上下/左右，并将另一个颜色改为透明即可) 

   -   例：“border-left:50px solid transparent;border-right:50px solid red”

   -   另一种做法:盒子宽高设为零,“border:50px solid transparent; border-left/right...”
     -    即先将四个边框颜色改为透明,要哪个显示哪个即可

2. 常见布局:

   -   浮动的li标签右边框和下一li左边框不重合 方法：“margin-left:-1px”使其重合

   -   鼠标经过li时显示其边框 

     -   若li无相对定位“li:hover{position:relative;border:...}”解决当前li右边框被下一li左边框覆盖

     -   若li有相对定位“li:hover{z-index:1;border:...}”提高当前li的层级

3. 解决相邻两元素因换行产生空格问题：如`<span>文本1</span><span>文本2</sapn>`

     "文本1"和“文本2”之间会有空格,空格大小由文字高度决定。因此将span的父元素font-size设置为0，再单独为span设置文字高度 注意：span同级元素也会受到其父元素字高为0的影响

4. 

   - a链接点击后不跳转“href="javascript:;"”

   -  有“inline-block”的地方通常有“vertical-align:middle”使文字与其他元素居中对齐



#### 第十三章：移动端

##### 1.视口

1. 浏览器显示页面内容的屏幕区域,又可分为布局、视觉和理想视口

2. 布局视口(layout viewport):用于解决早期PC端能在移动端显示的问题,将整个网页全显示,一般元素看上去很小,可通过手动缩放网页

3. 视觉视口(view viewport):用户正在看到的网站的区域(可能看到的只是部分网页)

4. 理想视口(ideal viewport):对设备而言最理想的视口尺寸,即布局视口和设备宽度相同，通过手动写meta视口标签通知浏览器操作

5. vh:视口高度 
   - 100vh即代表整个视口大小 
   - 50vh即为视口的一半

##### 2.meta视口标签:

1. 标准写法:

- ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">
  ```

-  width=device-width 宽度定义为设备宽度
-  initial-scale:初始缩放比,即刚打开时的页面

-  user-scalable:用户是否可缩放 yes/no(或1/0)

##### 3.物理像素比:

- 物理像素:即分辨率

- PC端1px等于1个物理像素,但移动端不一定

- 1px能显示的物理像素点的个数称为物理像素比或屏幕像素比

##### 4.两种开发方式:

-  单独制作移动端页面(主流) 

-  响应式兼容PC端移动端(非主流):通过判断屏幕宽度来改变样式以适应不同终端 
  -   缺点:制作麻烦需花费精力调试兼容性

-  通常情况下网址前加m可打开移动端 通过判断设备,如果是移动设备打开则跳到移动页面

##### 5.特殊样式:

-  盒模型: -webkitbox-sizing:border-box

-  高亮清除: -wenkit-tap-highlight-tcolor:transparent (如一个a链接点击时背景可能会高亮)

-  清除按钮和输入框的默认样式: -webkit-appearance:none

-  禁用页面长按时弹出菜单: -webkit-touch-callout:none (如图片长按时可能会弹出浏览器的菜单选项)

- 移动端浏览器基本以webkit内核为主,因此只需考虑webkit兼容性问题,此外webkit支持H5及CSS3特性

##### 6. 常见布局方式:

1. 单独制作移动端页面时:

- 流式布局(百分比布局):也叫非固定像素布局,盒子宽度设置成百分比来根据屏幕的宽度进行伸缩,不受固定像素限制,内容向两侧填充; max/min-width 用来限制盒子的缩放使内容不被挤变形

- flex弹性布局(强烈推荐)

- less+rem+媒体查询布局

- 混合布局

2. 响应式页面兼容移动端:

-   媒体查询

-   bootstrap

##### 7.适配:

1. 媒体查询: “@media mediatype and/not/only (media feature) {}”

   -  如: @media screen and (max-width: 800px){代码部分}

   - 以“@media”开头

   - “mediatype”为媒体类型: screen(用于电脑、平板、手机)/print(用于打印机和打印预览)/all(用于所有设备)

   - 关键字“and、not、 only”:用于将媒体类型和媒体特性连接到一起作为媒体查询条件

   - 媒体特性“media feature”:width(可见区域宽度)/min-width(页面最小可见区域宽度)/max-width

2. 引入资源:即准备多套css,针对不同的屏幕引用不同的css

   语法: 

   - ```html
     <link rel="stylesheet" href="" media="mediatype and/not/only (media feature)">
     ```

3. rem适配方案

   - 方案1:less+媒体查询+rem

   - 方案2:flexible.js+rem(已被淘宝废弃更新,推荐使用viewport)

- 页面元素的rem值 = 页面元素值(px) / html的font-size字体大小

- pc端打开时不让页面充满可以设置 “html{font-size:50px}”将此项写在设置媒体查询前面
