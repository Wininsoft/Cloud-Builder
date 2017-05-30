# Cloud Builder

### 什么是Cloud Builder？

Cloud Builder是完整的云RAD开发工具，用于快速定制企业级信息化系统及移动App， 典型的应用包括ERP，OA，CRM，BI以及类似业务形态的业务系统。

大家可以通过入门视频对Cloud Builder做一个总体的了解：
http://i.youku.com/u/UMzQwOTczMDMwNA==?qq-pf-to=pcqq.discussion
http://www.cloudbuilder.cc/video

Cloud Builder分为2部分：
- Cloud Builder IDE
- Cloud Builder部署包

### Cloud Builder IDE
Cloud Builder IDE基于Asp.Net MVC 5.4+html5+TypeScript， 对开发者来说可以直接用浏览器打开进行在线项目的开发。

### 功能集

- 数据源
  - 一个项目可以添加多个数据源
  - 数据源目前支持5种数据库
    - Sql Server
    - Mysql
    - Oracle
    - SQLite
    - Postgresql
  - 表设计器
    - 主键：支持复合主键
    - 表关联：一对一，一对多，多对多
    - 索引管理
    - 数据类型：内置数据类型提供了相比传统物理数据库更为高级的数据类型，如Email，Html，更加符合实际业务需要， 可通过扩展系统扩充
  - 枚举类型
- 界面设计器
- BPL语言引擎
  - BPL是Business Process Language的缩写，实现了C# 90%的语法， 以及其他的一些自定义的语法
  - BCL：Base Class Library， 类似于Net的BCL， 我们实现了最为基础的核心类库
  - 同时在Javascript以及.Net运行时下实现完整的语言引擎&核心库
  - 代码编辑器，提供语法高亮，上下文感知的智能提示
  - 断点调试，支持远程调试
- 菜单树管理
- 流程设计器
- 报表设计器
- 系统参数
- 扩展权限
- 多语言资源
- 扩展系统
  - 扩展系统的目的是让任何开发者都参与到Cloud Builder的开发中来，我们提供了诸多的扩展点
  - 主界面扩展
  - 数据类型扩展
  - 验证扩展
  - 格式化扩展
  - 界面模板扩展
  - 报表模板扩展
  - 控件类型扩展
  - BPL语言引擎扩展
- 团队管理
- 源码管理
- 计划任务
- 发布
  - 在线发布
  - 离线发布
  - 发布方案

### Cloud Builder部署包
- 部署服务端
  - 目前基于IIS+.Net 4.6.2
  - 计划今年年中支持linux，技术方案包括：.Net Core，Mono或Nodejs， 目前倾向于用Mono移植，等.Net Core足够稳定再迁移到上面，这样最节约成本。 Nodejs作为备选方案，主要原因是Nodejs目前更倾向于IO密集型应用而不是CPU密集型应用， 会对平台造成一定的限制。
  - 客户通过浏览器访问运行环境系统，支持
    - IE 11
    - Chrome 30+
    - Firefox 20+
    - Safari 6+
- App客户端
  - Android，Cloud Builder首页版本发布新闻中的附件中下载
  - iOS客户端，可在App Store搜索微英业务平台下载
  - 基于ionic 3.2+cordova 6.3.1
  - 通用的客户端， 在第一次登陆系统时需先配置服务器的地址
  - 可打包个性化的App，自定义的Icon，名称，应用包名称等

### 试用Cloud Builder
QQ群：387158200

体验地址：
http://www.cloudbuilder.com

### 技术堆栈

- 前端
  - 基于Html5+Javascript
  - [TypeScript](https://github.com/Microsoft/TypeScript)
  - [Cordova](http://cordova.apache.org/)：App混合式框架
  - [Ionic](https://github.com/driftyco/ionic)：App UI框架
  - [Knockoutjs](http://knockoutjs.com/)：数据绑定引擎
  - [pegjs](http://pegjs.org/)：BPL语法树解析
  - [jQuery](http://www.jquery.com/)
  - [jQuery UI]()
  - [fancytree](https://github.com/mar10/fancytree)：树形控件
  - jQuery Form
  - q.js：Promise实现
  - jQuery.print：dom元素打印
  - Filemanager：文件管理器
  - free-jqGrid：数据表格控件
  - dockspawn：窗口停靠控件
  - [CodeMirror](http://codemirror.net/)：代码编辑器
  - [ckeditor](http://ckeditor.com/)：html编辑器
  - jui_dropdown
  - [fullcalendar](https://github.com/fullcalendar/fullcalendar)：日历控件
  - jquery.bxslider：轮播控件
  - modernizr
  - waitMe.js
  - [plotly](https://github.com/plotly/plotly.js)：图表控件库
  - moment.js
  - justgage
  - [ResizeSensor](https://github.com/marcj/css-element-queries)：跟踪dom元素大小变更
  - jQuery contextmenu：上下文菜单控件
  - monaco:html，js，css代码编辑器 
- 后端
  - 基于Asp.Net MVC 5.4
  - Signalr 2：应用内即时通讯
  - Antlr V4：BPL语法树解析
  - Entity Framework：Cloud IDE服务端数据库访问层
  - Newtonsoft Json：Json操作类库
  - CsvHelper：csv导入导出
  - NPoi:：xls导入导出
  - EPPlus：xlsx导入导出

### 竞争对手

- Justep
- K2
- LightSwith

需要注意的是我们是针对企业级信息系统以及App的RAD平台，并不跟通用的开发工具如Visual Studio，Eclipse等有任何竞争关系。

### 目标&计划

Cloud Builder目前刚发布1.0版本， 这对我们来说是一个全新的起点。
我们希望通过我们以及社区的努力，把Cloud Builder打造成全球顶级，最流行的云开发工具，让大家把更多的时间专注于业务开发上而不是基础的底层架构。

我们希望让更多的开发者加入进来， 共同来实现这一伟大的目标！

### Cloud Builder IDE是否开源?
目前我们还没有这方面的打算，我们认为Cloud Builder IDE和Cloud Builder部署包类似于Visual Studio和.Net Framework的关系。
对于IDE来说，更重要的是提供扩展机制，让第三方开发者可以通过扩展的方式去满足自己多样化的业务需求。


### 感谢的话

- 首先把微不足道的成就归给耶和华上帝我们的神。
- 感谢我的师傅江千帆， 14年前认识他让我在.Net学习上受益颇多，11年前第一次去外地跟着他在东风汽车实施的经历至今难忘， 11年前介绍我来上海是我走上了平台研发之路。
- 感谢微软的LightSwitch， Cloud Builder很大一部分灵感来自于LightSwitch， 虽然微软现在基本上已经放弃LightSwitch，但我们完整的继承了它的核心思想， 并且做了质的改进， 让改进版的‘LightSwitch’在各方面都做了极大的加强， 可以完全适用于大型项目。
- 感谢在杭州启擎公司当平台架构师近2年的经历， 让我可以全职全身心的投入到Cloud Builder的前身启擎快速研发平台中来， 这对Cloud Builder的开发提供了宝贵的经验。
