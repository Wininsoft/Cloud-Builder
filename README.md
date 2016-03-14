# Cloud Builder

### 什么是Cloud Builder？

Cloud Builder是完整的云RAD开发工具，用于快速定制企业级信息化系统， 典型的应用包括ERP，OA，CRM，以及类似业务形态的业务系统。

大家可以通过入门视频对Cloud Builder做一个总体的了解：
http://i.youku.com/u/UMzQwOTczMDMwNA==?qq-pf-to=pcqq.discussion

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
- 任意窗口可拖拽（类似Visual Studio开发工具）

### Cloud Builder部署包
- 部署服务端
  - 目前基于IIS+.Net 4.6.1
  - 计划今年年中支持linux，技术方案包括：.Net Core，Mono或Nodejs， 目前倾向于用Mono移植，等.Net Core足够稳定再迁移到上面，这样最节约成本。 Nodejs作为备选方案，主要原因是Nodejs目前更倾向于IO密集型应用而不是CPU密集型应用， 会对平台造成一定的限制。
  - 客户通过浏览器访问运行环境系统，支持
    - IE 10+ （请注意我们是从IE10+开始支持的， 考虑到IE9不支持flexbox，会对平台功能性做比较大的限制）
    - Chrome 30+
    - Firefox 20+
    - Safari 6+
- App客户端
  - Android，iOS客户端
  - 基于ionic 1.2.4+cordova，准备升级到ionic 2.0
  - 通用的客户端， 在第一次登陆系统时需先配置服务器的地址

### 功能路线图
- 1.0.x版（2016-03月）
  - 1.0.x版我们主要精力会放在日常bug修复，功能细节完善优化
  - 集成文件浏览器
  - 支持以界面为向导的开发方式，不需要先建数据源再建界面
  - PDF报表引擎中文输出支持
  - 移动客户端Android，iOS上架应用市场
  - 属性编辑器多个对象一起编辑支持
  - 扩展支持
  
- 1.1版本（2016年-4月）
  - 业务级多语言支持（注意：平台本身已经支持多语言）
  - 运行时审批流程管理
  - 多语言资源
    - 繁体中文
    - 法语
    - 我们的资源有限， 其它语言资源需要开源后由社区进行完善
    
- 1.2版本（2016年6月）
  - linux支持
    - 初步的计划是先迁移到Mono，等.Net Core第二版出来再迁移到上面
    - 备用方案为Nodejs
    - Nodejs vs .Net
      - Nodejs带来统一的语言堆栈，不仅对Cloud Builder开发者，也对扩展开发者来说更加简单，只需要考虑js一种场景
      - Nodejs适合IO密集型应用而不是CPU密集型操作（单线程模式，多进程可以解决掉部分问题但总体来说可以这样进行概括），会对平添后续发展产生比较大的限制，这是为什么把Nodejs作为备用优先考虑.Net的最大因素
      - Nodejs拥有无与伦比的开源社区，.Net还是个婴儿刚起步， 目前完全无法相提并论

- 1.3版本
  - 业务市场
  - 插件市场
  - 支持App开发

### 试用Cloud Builder
目前Cloud Builder还没有向公众开放， 目前只开放给我们内部的合作伙伴测试试用， 我们将在下半年向所有用户进行开放，如果您目前迫切希望体验Cloud Builder， 请联系我们，我们将给您提供邀请码进行注册。

体验地址：
http://180.153.108.102

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
  - 
- 后端
  - 基于Asp.Net MVC 5.4
  - Signalr 2：应用内即时通讯
  - Antlr V4：BPL语法树解析
  - Entity Framework：Cloud IDE服务端数据库访问层
  - Newtonsoft Json：Json操作类库
  - CsvHelper：csv导入导出
  - NPoi:：xls导入导出
  - EPPlus：xlsx导入导出

### 目标&计划

Cloud Builder目前刚发布1.0版本， 这对我们来说是一个全新的起点。
我们希望通过我们以及社区的努力，把Cloud Builder打造成全球顶级，最流行的云开发工具，让大家把更多的时间专注于业务开发上而不是基础的底层架构。

目前Cloud Builder还未进行开源， 但开源是我们计划中的一部分，这对我们来说非常重要， 在开源之前我们还有很多工作要做， 更多的单元测试，文档……

我们计划分步对Cloud Builder进行开源
- 今年第四季度对Cloud Builder部署包进行完全开源

我们希望让更多的开发者加入进来， 共同来实现这一伟大的目标！

### 我们如何盈利？

我们提供免费和收费2种策略：
- 免费：适用于在Cloud Builder上开发的项目是公开的，别人可以搜索到并复制做二次定制
- 收费：适用于内部不公开的项目，别人不能搜索到该项目， 我们将收取少量的费用，为我们持续的Cloud Builder开发提供资金支持

### 感谢的话

- 首先把微不足道的成就归给耶和华上帝我们的神。
- 感谢微软的LightSwitch， Cloud Builder很大一部分灵感来自于LightSwitch， 虽然微软现在基本上已经放弃LightSwitch，但我们完整的继承了它的核心思想， 并且做了质的改进， 让改进版的‘LightSwitch’在各方面都做了极大的加强， 可以完全适用于大型项目。
- 感谢在杭州启擎公司当平台架构师近2年的经历， 让我可以全职全身心的投入到Cloud Builder的前身启擎快速研发平台中来， 这对Cloud Builder的开发提供了宝贵的经验。
