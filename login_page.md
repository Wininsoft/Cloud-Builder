# 自定义登录页

### 在Web节点下创建一个html页面

在这个页面需要有一个form，form下需要包含表单输入项：
- userName：登录名
- password：密码
- returnUrl：返回地址（可选）

表单设置:
- form提交地址：Login
- form提交方式：post

在html页面中可使用以下替换文本，加载界面时会自动替换成实际的文本：
- @{UserName}：用户名，在提交后有错误，会自动记录上次提交的用户名
- @{ErrorMessage}：错误消息，在提交后如果有错误，这个值就是具体错误消息
- @{ApplicationName}：应用显示名称或名称

### 获取应用的logo
../ApplicationService/GetLogo


### 配置登录页

在项目浏览器中选中根节点， 在属性编辑器中可以看到“登录页”设置，选择上一步添加的登录页面。

发布后，应用地址/Account/Login下访问登录页。

### 获取图片资源

- 在项目浏览器的资源节点下添加好资源以后，通过../Resource/Get?id=xxx的方式获取具体的资源
