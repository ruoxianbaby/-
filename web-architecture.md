# 网站架构设计
:kissing_closed_eyes: 欢迎阅读本文档，本文档用于说明开发初级的方向
## 技術栈选型
|应用场景         |技术名        |说明         |
|:--------------|:------------ |:-----------|
|后台语言         |[php](http://www.php.net/manual/zh/)          |             |
|后台框架         |[yii2](http://www.yiichina.com/doc/guide/2.0)         |强大的、能快速开发项目的高性能php框架 |
|前端语言         |[ECMAScript2015](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_6_support_in_Mozilla)          ||
|前端框架         |[vue](https://cn.vuejs.org/)          |当前最流行的JavaScript渐进式框架|
|ui框架1          |[iView](https://www.iviewui.com/)        |talkingdata开源的基于vue的ui组件|
|ui框架2          |[Element-ui](http://element-cn.eleme.io/#/en-US)       |饿了么的开源基于vue的ui组件|
|ui框架3          |[bootstrap](https://v3.bootcss.com/)    |Twitter推出的一个用于前端开发的开源工具包|
|前端自动化工具    |[webpack](https://doc.webpack-china.org/)       |健壮的前端资源模块打包器|
|代码管理    |[git](https://git-scm.com/book/zh/v2) |强大的版本管理工具|
## yii的强大之处  
> yii 过于强大，项目初期的设计什么的完全不需要，直接写业务代码就好。yii的学习成本还是有一点的。

[feature](http://www.yiichina.com/features)
> gii快速生成代码，ActiveRecord，身份验证，权限控制
## 权限分级
共4级权限，排序从大到小
- 系统管理员   *sysadmin*
- 超级管理员   *superadmin*
- 管理员   *root*
- 座席     *1008*
## 前后台的分离
> 1.超级管理员界面，使用gii生成绝大部分的业务逻辑和前端html代码(*yii2自带bootstrap ui组件*)，开发人员只做少量业务逻辑修改。

> 2.用户界面，采用当前流行的中后台设计风格。

前后分离
> yii2的一个项目下，yii框架管理前端路由和组件。前后台通讯完全使用XMLHttpRequest，技术实现Ajax或者axios。通过请求api项目下的数据接口，获得数据。api项目主要功能：验证信息、提供交互数据、一般计算。

## 组件化开发
> 高度复用代码，去除冗余功能实现，可复用组件采用组件方式引入项目，如搭积木一样实现完整页面。

## 开发规范
> 正常的面向对象的php开发规范。[php开发规范](http://psr.phphub.org/)（尽量做到就行）

例如:
- 类的命名 必须 遵循 StudlyCaps 大写开头的驼峰命名规范
- 类中的私有变量 必须 用下划线作为首字母
- 方法名称 必须 符合 camelCase 式的小写开头驼峰命名规范

## Demo
elment-ui [在线预览](http://106.14.107.99:233/vue-admin/)  
bootstrap[在线预览](http://106.14.107.99:88/index.php?r=site%2Fsignup)
## 开发文档
开发文档[点击查看](https://github.com/ruoxianbaby/shanghai-yantong-documents/blob/master/yt-web-developer-document.md)
## 结语
> php是世界上最好的语言。--鲁迅

yantong developer group  
2018/04/22
