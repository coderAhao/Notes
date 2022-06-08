##### 1.三维地图

- 某一区域三维地图：
  - npm 安装的echart可能不带地图，需手动下载map将其放到echart中module包里
  - 在阿里网站上可生成区域json文件，百度一下将json文件转为js文件并放到上面map文件夹中
  - 安装echarts-gl并在需要的文件中引入 此插件辅助将二维转为三维
  - 引入区域js文件
    - 注意点：引入的js文件名和js中转化json时的也有个name名，以及配置options时的map值，三者必须一样，否则无效

- 图表添加触发点击事件
  - myChart.on('click', params => {})
  - 此事件需写在myChart.setOption()前，否则无效
  - series区域默认打开了点击事件，该配置区域中发生点击可直接触发
  - 但地图上的点击事件分为数据区域和非数据区域的触发，需写为myChart.getZr().on('click', params => {})，不管是在非数据区域还是数据区域都能触发。但这样获取不到地图上点击部分的名称，可以在emphasis中label里的formatter中加js代码

