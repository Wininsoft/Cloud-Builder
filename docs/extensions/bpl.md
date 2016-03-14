# BPL语言引擎扩展

### 什么时BPL语言引擎扩展？

通过BPL语言引擎扩展， 可以在BPL语言引擎执行以下代码点时执行自定义的代码，并可以返回自定义的结果
- 字段值设置前
- 字段值设置后
- 属性值设置前
- 属性值设置后
- 方法调用前
- 方法调用后

典型的应用场景包括编写自定义的BPL类，然后通过语言引擎捕捉到类的方法调用代码点，进而执行本地代码（C#-服务端，javascript-客户端）。

语言引擎同时支持C#和javascript， 可根据业务场景来考虑实现C#还是javascript，或者两者同时实现， 如：
- 后台退款申请确认后， 需要在服务端执行C#代码进行微信/支付宝退款操作， 需要实现C#的BPL扩展
- 用户输入客户名称以后，自动生成客户名称的拼音简码， 如果要马上生成，那么需要实现javascript BPL扩展， 也可以在数据插入/更新时生成，则需要实现C# BPL扩展

### C#语言引擎扩展
以判断输入是否符合中国身份中验证规则为例：

- 新增.Net 4.6.1 的dll项目
- 添加文件IdentifierUtil.bpl文件并作为签入资源，文件内容如下：
```cs
class IdentifierUtil
{
    static bool IsValid(){}
}
```

- 添加IdentifierUtilInterceptor.cs文件，结构如下：
```cs
 [Export(typeof(IObjectInterceptor))]
    class ChineseHelperInterceptor : IObjectInterceptor
    {
        public TypeDeclaration GetType(CompileService compileService, Type type)
        {
            return null;
        }

        public TypeDeclaration GetType(CompileService compileService, object obj)
        {
            return null;
        }

        public Type GetClrType(TypeDeclaration typeDeclaration)
        {
            return null;
        }

        //BPL执行方法前调用
        public bool BeforeMethodCalled(VariableScope scope, object obj, TypeMethodDeclaration methodInfo, object[] parameters, out object returnValue)
        {
            //如果当前执行的方法类型名称是IdentifierUtil
            if (methodInfo.Parent.FullName == "IdentifierUtil")
            {
                //如果当前执行的方法名称是Isvalid
                if (methodInfo.Name == "Isvalid")
                {
                    string identifer=parameters[0];//获取第一个参数的值，为字符串
                    returnValue = true;//设置返回值
                    //返回true表示扩展已经处理了方法调用，reutnrValue的值将作为BPL方法执行的返回值，方法执行结束，不会再触发AfterMethodCalled
                    return true;
                }
            }
            returnValue = null;
            return false;
        }

        //BPL执行方法后调用
        public bool AfterMethodCalled(VariableScope scope, object obj, TypeMethodDeclaration methodInfo, object[] parameters, ref object returnValue)
        {
            return false;
        }

        //BPL获取属性值前调用
        public bool BeforeGetPropertyValue(VariableScope scope, object obj, TypePropertyDeclaration propertyInfo, object[] index, out object returnValue)
        {
            returnValue = null;
            return false;
        }
        
        //BPL获取属性值后调用
        public bool AfterGetPropertyValue(VariableScope scope, object obj, TypePropertyDeclaration propertyInfo, object[] index, ref object returnValue)
        {
            return false;
        }
        
        //BPL设置属性值前调用
        public void SetPropertyValue(VariableScope scope, object obj, TypePropertyDeclaration propertyInfo, object value, object[] index)
        {

        }

        //BPL获取字段值前调用
        public bool BeforeGetFieldValue(VariableScope scope, object obj, TypeFieldDeclaration fieldInfo, out object returnValue)
        {
            returnValue = null;
            return false;
        }

        //BPL获取字段值后调用
        public bool AfterGetFieldValue(VariableScope scope, object obj, TypeFieldDeclaration fieldInfo, ref object returnValue)
        {
            return false;
        }
    }
```
- 把编译好的dll打包到ext扩展包中， 发布后服务端会检测到ext包中的dll，自动进行加载

### javascript BPL扩展

- 新建IdentifierUtil.js文件，内容如下：
```js
var IdentifierUtilInterceptor = (function () {
    function IdentifierUtilInterceptor() {
    }
    IdentifierUtilInterceptor.prototype.getType = function (compileService, obj) {
        return null;
    };
    //BPL方法执行前调用
    IdentifierUtilInterceptor.prototype.beforeMethodCalled = function (callStack, methodInfo, obj, parameters, returnValue) {
        if (methodInfo.declaringType.fullName == "System.Uri") {
            if (methodInfo.name == "EscapeDataString") {
                returnValue.value = encodeURIComponent(parameters[0]);
                returnValue.processed = true;
            }
            else if (methodInfo.name == "EscapeUriString") {
                returnValue.value = encodeURI(parameters[0]);
                returnValue.processed = true;
            }
        }
    };
    //BPL方法执行后调用
    IdentifierUtilInterceptor.prototype.afterMethodCalled = function (callStack, methodInfo, obj, parameters, returnValue) {
    };
    //BPL获取字段值前调用
    IdentifierUtilInterceptor.prototype.beforeGetFieldValue = function (fieldInfo, obj, returnValue) {
    };
    //BPL获取字段值后调用
    IdentifierUtilInterceptor.prototype.afterGetFieldValue = function (fieldInfo, obj, returnValue) {
    };
    //BPL设置字段值前调用
    IdentifierUtilInterceptor.prototype.beforeSetFieldValue = function (fieldInfo, obj, returnValue) {
    };
    //BPL设置字段值后调用
    IdentifierUtilInterceptor.prototype.afterSetFieldValue = function (fieldInfo, obj, returnValue) {
    };
    //BPL获取属性值前调用
    IdentifierUtilInterceptor.prototype.beforeGetPropertyValue = function (callStack, propertyInfo, obj, indexParameters, returnValue) {
    };
    //BPL获取属性值后调用
    IdentifierUtilInterceptor.prototype.afterGetPropertyValue = function (callStack, propertyInfo, obj, indexParameters, returnValue) {
    };
    //BPL设置属性值前调用
    IdentifierUtilInterceptor.prototype.beforeSetPropertyValue = function (callStack, propertyInfo, obj, indexParameters, returnValue) {
    };
    //BPL设置属性值后调用
    IdentifierUtilInterceptor.prototype.afterSetPropertyValue = function (callStack, propertyInfo, obj, indexParameters, returnValue) {
    };
    return UriInterceptor;
}());
//注册BPL语言引擎扩展
Wininsoft.CloudBuilder.BPL.CompileService.registerObjectInterceptor(new IdentifierUtilInterceptor());
```

- 在extension.json文件的resources节点添加'IdentifierUtil.js'引用
