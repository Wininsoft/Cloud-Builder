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


样例：
```
<body style="background-color: #ddd; padding: 0px; margin: 0px;background-image:url(../Resource/Get?id=login_background.png&appVersion@{AppVersion});background-repeat:no-repeat;background-size:cover">
  <form id="formid"  name= "myform" method = 'post'  action = 'Login'>
        <div style="margin-top:25%;display:inline-block;padding-left:55%">
            <div style="color: white; margin-top: 20px">@{ApplicationName}</div>
            <div style="margin-top: 20px">               
                <div style="margin:10px">
                    <span style="color:white">用户</span>
                    <input type="text" id="userName" name="userName" value="@{UserName}" style="height: 18px; margin: 0px; background-color: #FFF8DF; border: 0; width: 150px" />
                </div>
                <div style="margin:10px">
                    <span style="color:white">密码</span>
                    <input type="password" id="password" name="password" onkeydown="if (event.which == 13) { login() }" style="height: 18px; margin: 0px; background-color: #FFF8DF; border: 0; width: 150px" />
                    <a href="#" style="color: white; margin-left: 10px;" onclick="login()">登陆</a>
                </div>
                <div>
                    <span style="color:red">@{ErrorMessage}</span>
                </div>
            </div>
        </div>
    </form>
    <script type="text/javascript">
        function login() {           
            if (document.getElementById('userName').value == null || document.getElementById('userName').value == '') {
                alert('请输入用户名');
                return;
            }
            if (document.getElementById('password').value == null || document.getElementById('password').value == '') {
                alert('请输入密码');
                return;
            }
            document.forms[0].submit();
        }
    </script>
</body>

```
