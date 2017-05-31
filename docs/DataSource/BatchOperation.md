# 批量数据操作
通过批量数据操作， 我们可以直接生成一条sql语句对数据进行批量删除，更新，插入，而不用先把数据读取到服务端内存再进行操作， 从而可以大幅度提升操作性能。

注意：
批量操作因为 不经过内存，所以不会触发实体的服务端数据操作相关事件，如插入时/后，更新时/后，删除时/后，保存时/后， 也不会触发实体属性的值改变时间， 并且不会产生数据修改日志。

### 批量删除

语法：
query.BatchDelete();

示例：
- 批量删除去年的日志信息
```csharp
ApplicationData.LogSet.Where(w=>w.CreateTime.Year==DateTime.Now.Year-1).BatchDelete();
```

### 批量更新

语法：
query.BatchUpdate(updateLambda);

示例：
- 批量更新客户待拜访日期为空的客户，设置其待拜访日期为7天后，并且设置状态为带拜访
```csharp
ApplicationData.CustomerSet.Where(w=>w.NextVisitDate==null).BatchUpdate(item=>{
	item.NextVisitDate=DateTime.Today.AddDays(7),
	item.Status="待拜访"
})
```
- 批量把业务员为01的客户划转给业务员02
```csharp
var newSalesman=ApplicationData.EmployeeSet.Where(w=>w.No=="01");//得到业务员02的实体对象
ApplicationData.CustomerSet.Wheere(w=>w.SalesMan.No=="01").BatchUpdate(item=>item.SalesMan==newSalesman);//批量更新
```
### 批量插入
query.BatchInsert(insertLambda);

示例：
- 批量把昨天的日志数据移动到历史日志表
```csharp
var logQuery=ApplicationData.LogSet.Where(w=>w.CreateTime.Date==DateTime.Date.AddDays(-1));
logQuery.BatchInsert(s=>new ApplicationData.HistoryLog(){
	CreateTime=s.CreateTime
	Content=s.Content
});//批量复制到HistoryLog表
logQuery.BatchDelete();//批量删除
```

