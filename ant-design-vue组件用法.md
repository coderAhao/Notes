###### cascader级连框

- 默认显示
    -  v-model绑定的数据源需为数组
    - 数组里的数据依次为父子级的id值
    - 具体可看销售管理->产品管理->面料辅料分类列表

###### input输入框

- 只能单个字母或数字输入
    - 绑定的数据格式源columns中已写了“key”值
    - 样式部分使用“template”插槽后，`<a-input>`中又绑定了key值
    - 造成输入框输入一下就会失去焦点
    - 这应该是一个错误的写法造成的意向不到的结果
- 验证码输入框依次聚焦
    - 加入有6个输入框，ref名依次为input1-6
    - 方法聚焦时需写为“this.$refs.input1[0].focus()”,不可写为“this.$refs.input1.focus()”否则方法无效
    - input可能比较特殊，添加了ref属性后，当前input仍有多个子元素

###### select下拉框

- 添加“labelInValue”属性后 change回调函数默认接受的参数为一个对象，对象包含两个属性分别为选中对象的key和label

- 页面刷新时路由携带的参数会变为string类型，若select-option绑定的value为number类型，则刷新后下拉框会显示数字而非中文，故需将参数进行转换

    - 此外若从接口获取数据，则类型也应为Number，反正要保证数据源和绑定的值类型一致

- 可输入过滤时

    - select添加属性“show-search ”和“:filter-option="filterOption"”

    - ```javascript
        // filter-option绑定方法
        filterOption(input, option) {
          return option.componentOptions.children[0].text.toLowerCase().indexOf(input.toLowerCase()) >= 0
        }
        ```

###### form-model

- 三个字段名要一致：即`form-model-item`中的prop、v-model绑定的“form.xxx”字段名和rules规则中某项规则的key
- rules规则中，`trigger`的值也可用“change"，用”blur“某些组件校验时可能会一直校验不通过，如”date-picker“

###### tabs切换

- 激活当前栏用属性“activeKey”  注：属性值为string类型，并不为number类型

###### date-picker

- v-model绑定之后 再加一个属性“valueFormat='YYYY-MM-DD'”可直接双向绑定，无需再写change事件

###### upload

- 上传时走自定义接口（因为有时上传可能需要同时传参）

    - before-upload 绑定一个函数，函数return false 

    - 在change函数中

        - ```javascript
            const params = new FormData()
            params.append('file', file)
            params.append('要传的形参', ‘实参)
            return upload(params).then(res => {}).catch(() => {})
            ```

    - 若要校验文件格式，可在change函数中进行，不满足格式将其return，不让其走接口

- 上传后不展示已上传的文件列表

    - 给当前的upload一个refName，上传成功后将this.$refs.refName.sFileList置为空数组（有时可能是refName[0].sFileList，打印一下当前upload即可）