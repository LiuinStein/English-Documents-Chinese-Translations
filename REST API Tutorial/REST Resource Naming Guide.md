### REST Resource Naming Guide

在REST中，主要的数据表现层称之为**资源**。使用一个健壮以及坚持使用同一个REST资源命名策略将是一个长期的最佳的设计决策。

> 在REST中，对于信息最关键的抽象即为资源。任何信息都可以被称为一个资源：一份文档或图像，一个临时的服务（例如：今天洛杉矶的天气），一个其他资源的集合，一个非虚拟化的物体（例如一个人）等等。换句话来说，任何可能成为作者超文本引用目标的概念都必须符合资源的定义。一个资源在概念上可映射为一组实体，而不是与任何特定时间点相映射的对应实体。
>
> --[Roy Fielding的博士论文](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2_1_1) 

任何资源都可以是单个或者多个（一个集合）。就比如，对银行系统来说，一群顾客就是一个集合资源，一个顾客就是一个单个的资源。我们可以使用URI `/customers ` 来标识一群顾客，同样可以使用URI `/customers/{customerId} ` 来标识一个顾客。

一个资源同样可以包含子资源。例如，同样对银行系统来说，一个顾客（资源）可能含有多个银行账户（子资源），这些账户可以通过URN `/customers/{customerId}/accounts `来标识。同样，在这个子资源`accounts`下的一个单个的资源`account`可以标识为`/customers/{customerId}/accounts/{accountId} `

REST API使用[统一资源标识符 URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)来寻址资源。REST API设计者应当使用URI来向其客户端开发者传达REST API的资源模型。只有当一个资源有良好的命名时，一个API才能直观易用。反之，这些API将会变得难用且难以理解。

有关统一接口（*uniform interface*）的约束可以通过按照标准和惯例使用的URI和HTTP动词组合来解决。

> 译者注：
>
> HTTP动词（HTTP verb）指的是诸如GET, POST, DELETE, PUT这样的HTTP请求方式。 
>
> 有关统一接口的约束请参考本目录下的文章*REST Architectural Constraints*

下面是有关如何为你的API命名资源URI的几点提示。

### REST Resource Naming Best Practices

#### Use nouns to represent resources

RESTful API应当引用为一个资源，也就是一个事物（名词）而不是一个动作（动词），因为名词可以拥有属性而动词不行——同样资源也应当有属性。下面列举一些资源的例子：

* 系统中的用户
* 用户账号
* 网络设备等等

他们的资源URI可以被设计为：

```
http://api.example.com/device-management/managed-devices 
http://api.example.com/device-management/managed-devices/{device-id} 
http://api.example.com/user-management/users/
http://api.example.com/user-management/users/{id}
```

为了更清楚起见，让我们把**资源的原型（resource archetypes）**分为4个不同的类型（document 文档，collection 集合，store 存储，controller 控制器），**你应该始终将一个资源对应一种原型，然后遵循它的命名约定**。由于一致性的缘故，抵制设计不止一种原型的混合资源的诱惑。 

1. **属性** （document）
   资源属性是一个单一的概念，它类似于一个对象实例或一条数据库记录。在REST中，你可以将其视为一个资源集合中的单个资源。一个属性的状态表现层通常包含具有值的字段以及指向其他相关资源的链接。
   使用“单数”名称来表示资源属性原型。 

   ```
   http://api.example.com/device-management/managed-devices/{device-id}
   http://api.example.com/user-management/users/{id}
   http://api.example.com/user-management/users/admin
   ```
   > 译者注：
   >
   > 这里的属性英文原文写的是document，字面上翻译为文档或者文件
   >
   > 但是在这里它并不是指的传统意义上的那个文档，程序文档或代码文档。
   >
   > 依据上下文语境，**这里的document指的应该是一个资源的具体属性，它有可能是一个对象实例或者一条数据库记录**，而这个属性必需以“单数”名词的形式表现在URI里面。
   >
   > 翻阅了很多资料，都没有很好的解释方法，[Collins](https://www.collinsdictionary.com/us/dictionary/english/document)词典也没有给出有关document这个单词更好的衍生意义来，故在此将其意译为“属性”
   >
   > 如果有更好的翻译方法，请提交Issue或pull request

2. **集合**
   一个集合的资源是一个由服务器管理的资源的目录。客户端可能会向其添加新的资源。然而，它取决于要创建新资源的集合