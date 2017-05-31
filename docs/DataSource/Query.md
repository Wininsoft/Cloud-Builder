# 查询

通过查询语句，平台会把查询语句翻译成sql语句发送给 底层数据源进行执行，然后返回强类型的查询结果。

### 查询整个表的全部数据

语法：
[数据源].[表]Set，其中[数据源]为数据源的名称，[表]为表的名称。
示例：
```csharp
ApplicationData.CustomerSet
```
表示查询ApplicationData数据源Customer表的全部数据
生成的sql语句参考：
select * from [Customer]

### 过滤

语法：
查询.Where(lambda)， 其中 lambda表示要对查询进行过滤的布尔类型lambda表达式

示例：
```csharp
ApplicationData.CustomerSet.Where(w=>w.Type=="Personal")
```
查询Type字段的值等于Personnal的客户
生成的sql语句参考：
select * from [Customer] as [it] where [it].[Type]=='Personal'

```csharp
ApplicationData.CustomerSet.Where(w=.w.Type=="Personal"&&w.NextVisitDate==DateTime.Today)
```
查询Type字段值等于Personal，并且NextVisitDate值等于金泰你的客户
生成的sql语句参考：
select * from [Customer] as [it] where [it].[Type]=='Personal' and w [it]NextVisitDate==convert(getdate() as date)

### 排序

语法：
- 查询.OrderBy(lambdad)，升序
- 查询.OrderByDescending(lambdad)，降序
- 查询.ThenBy(lambdad)，附加升序
- 查询.ThenByDescending(lambdad)，附加降序

其中升序/附加升序，降序/附加降序的区别是， 如果查询已经有排序， 则升序/降序会覆盖掉查询中原有的排序，而附加升序/降序不会，而是在原有查询排序基础上进一步排序

示例：
```csharp
ApplicationData.CustomerSet.OrderBy(o=>o.CreateTime)
```
按照创建时间对客户进行升序
生成的sql语句参考：
select * from [Customer] as [it] order by [it].[CreateTime]

```csharp
ApplicationData.CustomerSet.OrderByDescending(o=>o.CreateTime)
```
按照创建时间对客户进行降序
生成的sql语句参考：
select * from [Customer] as [it] order by [it].[CreateTime] desc

```csharp
ApplicationData.SalesOrderSet.OrderBy(o=>o.Customer).ThenByDescending(o=>o.Amount)
```
对销售订单先按照客户升序，然后按照金额进行降序
生成的sql语句参考：
select * from [Customer] as [it] order by [it].[Customer], [it].[Amount] desc

### 分页

语法：
- 查询.Take(int pageSize); 获取给定条数的数据
- 查询.Skip(int startIndex); 从给定行号开始获取数据

示例：
```csharp
ApplicationData.OrderSet.OrderByDescending(o=>o.Amount).Take(20)
```
获取销售订单金额最大的20条数据

示例：
```csharp
ApplicationData.OrderSet.OrderByDescending(o=>o.Amount).Skip(20)
```
获取销售订单按照金额降序后的第20条开始的数据

```csharp
ApplicationData.OrderSet.OrderByDescending(o=>o.Amount).Skip(100).Take(20)
```
获取销售订单金额最大的第100到120条数

### 分组

语法：query.GroupBy(groupByLambda);

示例：
```csharp
ApplicationData.CustomerSet.GroupBy(g=>g.Type);
```
按照Type对客户进行分组

生成的sql参考：
select [it].[Type] from [Customer] [it] group by [it].[Type]

```csharp
ApplicationData.GroupBy(g=>new{
  g.Type,
  g.CreateTimeYear
})
```
生成的sql参考：
select [it].[Type], year([it].[CreateTime]) from [Customer] [it] group by [it].[Type], year([it].[CreateTime])

### 选择返回结果

语法：query.Select(selectLambda);

示例：
```csharp
ApplicationData.CustomerSet.Select(s=>new{
  s.Name,
  s.Type
})
```
生成sql参考：
select [it].[Name], [it].[Type] from [Customer] [it]


### 获取结果数

语法：query.Count()

示例：
```csharp
ApplicationData.CustomerSet.Count()
```
生成sql参考：
select count(*) from [Customer] [it]
