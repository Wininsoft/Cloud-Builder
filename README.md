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


### 目标&计划

Cloud Builder目前刚发布1.0版本， 这对我们来说是一个全新的起点。
我们希望通过我们以及社区的努力，把Cloud Builder打造成全球顶级，最流行的云开发工具，让大家把更多的时间专注于业务开发上而不是基础的底层架构。

目前Cloud Builder还未进行开源， 但开源是我们计划中的一部分，这对我们来说非常重要， 在开源之前我们还有很多工作要做， 更多的单元测试，文档……

我们计划分步对Cloud Builder进行开源
- 今年第四季度对Cloud Builder部署包进行完全开源
- 明年年中对Cloud Builder IDE进行开源

我们希望让更多的开发者加入进来， 共同来实现这一伟大的目标！



