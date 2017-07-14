# 自定义登陆界面


###  Web节点下添加一个html文件

如添加Login.html，然后选中根节点，  选择登陆界面为刚才添加的Login.html，这样登陆的时候就用这个文件进行呈现


### 登陆页面变量替换

- @{ApplicationName}：应用的显示名称
- @{ErrorMessage}：如果登陆错误，则获取登陆的错误消息
- @{UserName}：如果登录错误，则获取登陆用户名
- @{AppVersion}：获取应用版本号
- @{EnableCaptcha}：获取是否启用验证码


### 登陆页面提交

提交地址为： /应用名称/Account/Login

其中'应用名称'为应用发布的地址，如果发布到根路径下，Default，或发布地址直接是/Account/Login

需要传递的参数如下：
- userName：用户名
- password：密码
- captcha：验证码，只有在启用验证码的时候需要用到

