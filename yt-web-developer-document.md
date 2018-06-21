# 言通-开发者文档

## 开发周期
> 两个月内，完成呼叫中心的核心功能

## 开发进度控制
> 从公共模块和权限管理开始做起  
采用并行开发，原则上，谁开发，谁维护，谁负责。

代码质量，代码规范 优先级较高  
以类为单位，每个模块必须清晰、明确、降低耦合，不可冗杂、相互依赖。
## 数据库远程连接
测试环境ip：106.14.107.99  
端口：3306  
账号：developer  
密码：123456  
库名称: u_crm_db_dev  
## 项目仓库地址
```bash
git clone ssh://developer_name@139.224.24.169:6900/home/code-repertory/callcenter/dev.git callcenter
```
## yii初始化
回到根目录下，打开终端，运行
```
php init  // 一路yes，就行
```
解压项目根目录下的vendor.zip到项目根目录
### db文件  
[click download](https://share.weiyun.com/5QpxwHh) ,把sql db文件解压缩放到mysql的data目录下,mysql版本需要5.6以上 

## 模块划分
按照权限，分为五大模块，五大模块并行开发，互不影响  
所有项目的入口文件这在```/frontend/web/```下，这样解决了跨域的问题。
```
┎━━ frontend      # 预留模块
根    ┗━━ web
┃         ┡━━ index.php       # 指向項目根目錄的frontend文件夾
目         ┡━━ api_backend.php # 指向項目根目錄的api_backend文件夾
┃         ┡━━ backend.php     # 指向項目根目錄的backend文件夾
錄         ┡━━ sysadmin.php    # 指向項目根目錄的sysadmin文件夾
┃         ┡━━ superadmin.php  # 指向項目根目錄的superadmin文件夾
┃         ┡━━ staff.php       # 指向項目根目錄的staff文件夾
┃         ┡━━ api_staff.php   # 指向項目根目錄的api_staff文件夾
┃         ┕━━ agent.php       # 指向項目根目錄的agent文件夾
┞━━ api_backend    # 以root權限登入的數據接口
┞━━ backend        # 以root權限登入的界面,管理员
┞━━ sysadmin       # 以sysadmin權限登入的界面，页面用gii制作
┞━━ agent          # 以agent權限登入的界面，原crm，页面用gii制作
┞━━ api_staff      # 以staff權限登入的數據接口，坐席
┞━━ staff          # 以staff權限登入的界面，坐席
┕━━ superadmin     # 以superadmin權限登入的界面，页面用gii制作

```
**入口**(老网站)  
root：ip/login.php  
sysadmin：ip/control_login.php  
agent:ip/crm_login.php  
**说明**：代理和superadmin 同级，功能一样，只不过代理管理的机构更多一点。  
sysadmin 和 superadmin 也同级，只不过sysadmin权限更大，并管理全部机构。  
代理 和 superadmin 可以做到同一个模块里  
------修改  
agent 与 sysadmin superadmin。仅仅判断 agent 还是sysadmin。  
坐席管理机器人和机器人设置的页面用共root的页面，仅判断是以什么身份登入的。  
<<<<<<
## 常量的定义
在```/common/config/const.php``` 中定义  
这么定义的：
```php
define('FRONTEND', dirname(dirname(__DIR__)) . '/frontend'); // 绝对路径，指向`/var/www/callcenter/frontend`
define('STATIC_FRONTEND', '/static/frontend'); // 相对于web目录下的路径，指向/fronted/web下的 `./static/frontend`
# code...
```
也有别称,在```/common/config/bootstrap.php```中定义，定义如下：
```php
Yii::setAlias('@frontend', dirname(dirname(__DIR__)) . '/frontend');
# code...
```
载入常量文件，都在```/frontend/web/```下的各项目的入口文件完成。同样也可以在对应项目下的```config/```下定义并引入这个项目独有的常量。

## controller运行前
所有controler，更改继承本项目下的```\app\controllers\CommonController```,例如
```php
use app\controllers\CommonController;

class IndexController extends CommonController
{  
  # 使用 beforeaction 或 init 方法代替 construct
  public function beforeaction()
  {
     # code...
  }
}
```
为啥这么干，因为 同项目下的所有controller都需要做很多相同的事情，比如验证登陆，加载相同组件等。  
在```/common/models/```中同样可以写一些静态方法，或者用于继承的对象。
## 公共静态方法
在`common/models/Yt.php`中，使用，直接`use common\models\Yt; Yt::checkUser();`即可。
## 组件
注册、引用组件：  
公共组件的数据输入初始化，应该在`CommonController`里完成，调用则分别在不同的控制器里面。

## 静态文件  
按照项目名称，全部存放在```/frontend/web/static/```下面
例如，要取得```/frontend/web/static/backend/lib/jquery.js```,则在代码中
```html
<script src="<?=STATIC_BACKEND?>/lib/jquery.js"></script>
```  
## 前端说明  

## 页面的JavaScript代码  
写项目的时候样式和js可以写在html内，测试完后需分离，javascript需要用webpack，编译、压缩。（html看情况做压缩）。
## webpack的使用
安装```nodejs + npm```  
仓库地址：  
```git
git clone ssh://developer_name@139.224.24.169:6900/home/code-repertory/web-frontend-tool/yt-frontend.git
```
安装
```bash
cd yt-frontend
npm i --registry=https://registry.npm.taobao.org
```
项目结构
```bash
build                # 输出 编译后的代码
src                  # 输入 源代码
package.json         # 说明
package-lock.json    # 依赖
webpack.config.js    # 配置
```
使用
```bash
npm run build
```






完结撒花。  
:cherry_blossom:  &emsp;  :grapes:   &emsp;  :cherry_blossom: &emsp;     :cherry_blossom: &emsp; :cherry_blossom: &emsp; :cherry_blossom:  
:cherry_blossom:  &emsp;  :cherry_blossom:  &emsp;  :cherry_blossom:  &emsp;  :cherry_blossom: &emsp; :cherry_blossom:  &emsp;  :cherry_blossom:  
:cherry_blossom:   &emsp;    :cherry_blossom:  &emsp;   :cherries:  &emsp;    :cherry_blossom:    &emsp;  :cherry_blossom:  &emsp;   :cherry_blossom:  

 
  
