# 扩展系统

### 什么是扩展？

Cloud Builder本身提供了非常强大的内置功能， 但是我们得承认， 再强大的系统都无法内置业务开发所需要的全部功能， 因此我们引入扩展系统， 让任何开发者都可以轻松参与到对平台的扩展中来。

### 可扩展的点

我们在设计Cloud Builder的时候尽量考虑了平台的可扩展性， 我们支持的扩展点包括：
- 数据类型
- 控件
- 界面模板
- BPL语言引擎
- 服务端数据服务事件
- 数据源扩展
- 报表模板
- [主界面](shell.md)

### 如何使用?
Cloud Builder项目节点下包含Extensions（扩展）节点，在这个节点下可以对扩展包进行添加，删除，更新。

### 扩展包结构
扩展包的后缀是ext， 是标准的zip格式文件， 压缩包下必须包含extension.json文件， 以及任何其它必要的文件。
extension.json的样例如下：

{
  "name": "TopMenuShell",
  "version": "1.0.0.0",
  "description": "主界面菜单显示在顶部",
  "publishDate": "2016-03-14",
  "resources": [ "superfish/css/superfish.css", "superfish/js/hoverIntent.js", "superfish/js/superfish.js", "ShellViewModel.js", "NavigationPane.js", "ChangePasswordModel.js" ]
}

描述如下：
- name：扩展的名称
- version：扩展版本号
- description：扩展的详细描述
- publishDate：发布日期
- resources：包含资源数组，在加载扩展包的时候会按顺序对资源进行加载， 可加载的资源包括css，js文件

### 获取扩展包中文件的url

Wininsoft.CloudBuilder.ExtensionUtil.getResource(extensionName:string, resource:string):string
- extesionName：扩展名称
- resource：扩展包中资源路径

