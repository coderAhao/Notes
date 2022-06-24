### uniapp

#### 使用uview中遇到的问题：

###### 离线图标

- 官网“资源”下载离线图标，然后放入项目文件夹中，在“uni_modules/uview-ui/components/u-icon/u-icon.vue”文件中，在style中修改“@font-face”里的src，将引入的阿里云地址改为本地即可

###### 路由跳转

- uni.$u.route('/pages/index/plan/workApply')  页面从右向左滑进来显示
- uni.navigateBack({url: '/pages/index/plan/workApply' }) 页面从左向右滑动进来(视觉上是回退)
- uni.navigateBack({ delta: 1 }) 页面从左向右滑动到上一页

 