# 主界面扩展

### 什么是主界面扩展？

通过主界面扩展， 用户可以选中项目根节点， 在属性编辑器中会列出所有注册的主界面， 可以进行切换。


### 实现步骤

#### 1，注册

在扩展包的js文件中需要调用以下代码，对扩展进行注册：
Wininsoft.CloudBuilder.Presentation.Shell.ShellModel.registerShell(name, description);

- name：主界面名称
- description：主界面描述

#### 2，实现主界面
在注册时所用的名称，我们需要用knockoutjs注册一个相同名称的component， component所传递的参数为Wininsoft.Presentation.Shell.ShellModel对象
