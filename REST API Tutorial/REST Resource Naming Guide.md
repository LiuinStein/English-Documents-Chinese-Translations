### REST Resource Naming Guide

在REST中，主要的数据表述称之为**资源**。使用一个健壮以及坚持使用同一个REST资源命名策略将是一个长期的最佳的设计决策。

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

