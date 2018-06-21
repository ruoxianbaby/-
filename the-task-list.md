# 任务分配
```dir
 api_backend    # 以root權限登入的數據接口
 backend        # 以root權限登入的界面
 sysadmin       # 以sysadmin權限登入的界面，页面用gii制作
 agent          # 以agent權限登入的界面，原crm，页面用gii制作
 api_staff      # 以staff權限登入的數據接口，坐席
 staff          # 以staff權限登入的界面，坐席
 superadmin     # 以superadmin權限登入的界面，页面用gii制作
 ```
 sysadmin、agent 可以同一项目下  
 superadmin 管理多个root，可以先不做  
 
 ## 注意
 #### 业务修改
 坐席改为6位，前3位公司号，后三位坐席号
 #### gii的model
 所有gii生成的model，全部放在`common\models\`下面，不得做任何形式的修改。  
 如果要使用在对应应用下的models新建文件夹 新建文件去继承这个model，文件里面任意修改  
 #### 新系统
 不去兼容老网站，数据库可以自己去修改
 
 #### 任务分配
 ~~ai机器人部分：方超、明泳霖、李洪飞、文浩 
 呼叫中心部分：close、张轩、俞其明  
 使用gii制作的项目：明泳霖、李洪飞、文浩  
 公共模块：closed、张轩、李洪飞~~  
 - ai机器人: 赵梅 黄国歌 王洪飞  
 - 呼叫中心: 张轩 郑含笑 徐进杰  
 - 坐席: 高忠泽 赵梅 黄国歌   
 - 权限: 徐进杰  
 - 小部件 系统设置 短信: 高忠泽 李洪飞  
 - 公共模块方法: 徐进杰 高忠泽  
 - 系统管理 代理 gii: 李洪飞  
 - 前端: 张轩 孙仙玉
 #### git提交权限不足
 ```bash
 cd /home/code-repertory/callcenter/
 chmod 0777 -R dev.git
 ```
# 任务列表
## 2018-05-02（周任务）
- 通读一遍官方文档（前端vue，后端yii2）  
- 看一遍编程规范  
- 熟悉开发环境
- 了解当前网站的功能、业务
## 2018-05-07（周任务）
- 学会使用git 提交代码
- 深入了解业务和功能
- 做出几个模块的登陆功能  
- 写公共模块  
**具体**    
**说明** `Yii::$app->session()`是不能跨应用交流的，跨应用session，在`common/models/Yt.php`里实现了  
参数一致性：登陆session都放在`Yii::$app->session['loginInfo']`里面具体的是怎样的数组，再讨论
```
closed： api_backend 的登陆 和 去动态实现菜单
文浩：sysadmin的登陆和左侧 头部 菜单，使用组件和布局去实现 
space：common/models/Yt.php里写静态方法，实现 checkLoginStatus  getUserInfo checkLoginType 
等公共方法，参数为调用应用的session，都有返回值，根据session判断
男儿： api_staff 的登陆 和 菜单

```

# 2018-06-04
按照分配的任务,每天每人至少一次commit. 有效的核心代码原则上不得少于50行. 质量过差的代码,扣效绩.
