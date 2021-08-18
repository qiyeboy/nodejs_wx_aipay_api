
# 个人支付免签系统 Api 版

  技术栈 EggJs + MySql + Vue

  项目说明： 支持个人网站、安卓App、微信公众号、PC软件的接入，实时到账您的支付宝/微信余额中，支付宝无需上传收款二维码，支持H5唤醒支付，支持回调通知、支持补单、后台功能简单。
  
  特点：支持回调通知，0手续费实时到账（不经过任何第三方，直接到账微信/支付宝余额），提供无依赖服务端源代码运行在自己服务器上，支持php/java/python等任意开发语言接入，非xp框架HOOK的方式，无需root权限安全无风险。

实现原理： 当收到支付宝、微信、实时收款信息，客户端会实时通知服务器收款金额和方式，服务器收到有效期订单金额后处理订单状态。5分钟订单有效期内有相同金额的订单会随机减免0.01 - 0.10的方式用来区分订单。

  
  ## 支持信息
    2021年08月18日
    支付宝 10.2.28（最新版）
    微信 8.1.0（最新版）
  
  ## 关于demo演示
  
  后台演示地址: http://pay.yio.me/ 账号密码 admin，**api版后台仅保留订单列表和二维码管理功能**。
  
  支付演示地址: http://pay.yio.me/#/goods/DwnNGCW4VLk1CjemIiUqf 
  
  ## 客户端赞助地址
  
  没有客户端无回调通知，其他功能不影响，可以测试后台功能，客户端需要购买后使用。

  客户端赞助地址： http://pay.yio.me/#/goods/74ct1zBzZBW8YGFBKe-Yf 
  
  
## 视频教程
    
   https://pan.baidu.com/s/1czuBjaTIT2hwC215yQ-FlQ

## 文本教程

  1. 安装 node.js mysql 环境，并将此项目所有文件下载到服务器任意目录上面；注：node.js版本 >= 8.9.0 mysql版本 >= 5.5

  2. 下载项目 [点击下载](https://github.com/yioMe/nodejs_wx_aipay_api/archive/master.zip "点击下载")，解压并进入项目根目录,找到 config/config.default.js 文件按照提示修改所需配置保存，然后进入database/config.json 文件修改 development 数据库配置信息； 注： 数据库需要手动创建,字符集utf-8排序规则utf8_general_ci

  3. 在项目根目录中打开命令行， 执行 npm install 安装依赖文件

  4. 在项目根目录中打开命令行， 执行 npx sequelize db:migrate  创建数据表结构； 注： 是npx 不是 npm ;（也可以通过项目文件pay.sql）文件手动导入到数据库
  
  5. 在项目根目录中打开命令行， 执行 npm start 启动应用,默认端口7001； 注： npm stop 停止应用

  6. 访问 http://你的服务器地址:端口号/index.html 注：必须带index.html


## Api文档

  下载本项目后，进入DocApi目录，使用浏览器打开index.html文件即可

  你只需要关注 ↓

  order - 创建支付订单

  无需关注（二次开发需要）↓

  android - 接收推送客户端信息

  android - 验证客户端
  
 ## 客户端配置

  api 地址填写： http(s)://你的服务器地址:端口号/addons/pay/ 注意：必须以反斜杠结尾

  签名密匙填写： config/config.default.js 里的 secretkey 值

  点击保存提示配置成功即可，没有其他设置!
  
 ## 开启微信/支付宝收款通知
 
  微信->钱包->二维码收款->开启收款到账语音提醒  

  注：（如果微信在PC登录了，请在手机微信中关闭手机静音，或退出PC微信）

  支付宝->收钱->开启收款到账语音提醒
  
 ## 注意
 
  1.收款二维码是定额的二维码不是你的微信二维码，二维码收款->设置金额->保存收款二维码（不能修改任何文字信息，否则会无法识别报404）
  
  2.服务器一定要是公网ip，否则支付宝付款时无法找到正确的二维码地址

 ## 疑问

  问：资金多久到账？

  答： 实时到账，直接到账微信/支付宝余额，不经过任何第三方。

  问：会掉单吗？

  答： 保持客户端和服务端网络畅通99.99%不会掉单!

  问：这个服务端是什么意思，客户端是什么意思?

  答: 服务端源码是用来接收客户端推送收款信息，客户端是获取支付宝和微信的收款信息并实时推送到服务器。

  问: 微信公众号可以使用吗?

  答： 可以使用微信，长按二维码即可直接支付；
   
  问: 原生安卓可以使用吗?
  
  答： 可以使用，请使用webView控件中加载html a 标签，接口返回的qr_url内容设置到a标签的href属性，H5页面同理，即可唤醒支付宝支付，H5同理。
  
  问：如何联系到你
  
  答： 邮件 a@yio.me 
  
  ## 使用声明
  本账号发布的项目中涉及的任何脚本/程序，仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断。
  本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。
  yioMe对任何脚本/程序问题概不负责，包括但不限于由任何脚本/程序错误导致的任何损失或损害.
  间接使用脚本/程序的任何用户，包括但不限于建立VPS或在某些行为违反国家/地区法律或相关法规的情况下进行传播, yioMe 对于由此引起的任何隐私泄漏或其他后果概不负责。
  **请勿将此项目的任何内容用于商业或非法目的，否则后果自负。**
  如果任何单位或个人认为该项目的脚本/程序可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关脚本。
  以任何方式查看此项目的人或直接或间接使用项目的任何脚本/程序的使用者都应仔细阅读此声明。yioMe 保留随时更改或补充此免责声明的权利。一旦使用并复制了任何相关脚本/程序或项目，则视为您已接受此免责声明。
  您必须在下载后的24小时内从计算机或手机中完全删除以上内容。

 
