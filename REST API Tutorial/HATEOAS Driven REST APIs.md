### HATEOAS Driven REST APIs

**HATEOAS (Hypermedia as the Engine of Application State 使用超媒体作为应用状态引擎)** 是REST应用程序架构的约束之一，用来保证RESTful体系结构与其他网络应用体系结构之间的独特性。这个术语“**hypermedia**”指的是任何包含一个超链接或者其他媒体形式（诸如图像、电影或者文本）的内容。

这个体系结构允许你在响应体中使用超链接，以便客户端可以通过超链接动态定向到所需要的资源。这在概念上等价于web用户通过点击web页面上的超链接来到达其想要的页面或寻求期望的信息。

例如，下面的是对请求`HTTP GET http://api.domain.com/management/departments/10`的一个JSON响应体：

```json
{
    "departmentId": 10,
    "departmentName": "Administration",
    "locationId": 1700,
    "managerId": 200,
    "links": [
        {
            "href": "10/employees",
            "rel": "employees",
            "type" : "GET"
        }
    ]
}
```

在这个例子中，服务端返回一个包含跳转到职工信息超链接`10/employees`的响应体，客户端可以通过这个超链接来读取这个部门的职工信息。

上述实现方法的优点在于从服务端返回的超链接驱动着这个应用程序的状态。

这里并没有一个通用的实现方法用来在JSON中表示两种资源之间的链接。你同样可以选择下面的形式来通过HTTP响应头来发送一个链接：

```
HTTP/1.1 200 OK
...
Link: <10/employees>; rel="employees"
```

这两者都是合适的解决方案。

### HATEOAS Implementation

在现实世界中，当你访问一个网站的时候，你点击了它的主页。他会现实一个网页的快照以及一些链接到其他网站部分的链接。你点击这些链接，然后你将会获得更多与上下文相关的链接。

与人类浏览网页相似，**一个REST客户端访问初始API URI，然后使用服务端提供的链接来动态寻求可使用的动作以及获取相关资源**。一个客户端并不需要对有关服务以及不同步骤有任何的预先了解。此外，**无需将不同资源的URI地址结构硬编码到客户端内**，这同样允许在无需修改客户端的情况下，服务端随着API的演变而修改URI地址。

> 译者注：
>
> 硬编码就是写死到代码里。

以上API交互必需使用HATEOAS。

每一个REST框架都会提供其自己的HATEOAS实现方法，例如在[这篇文章](https://howtodoinjava.com/resteasy/writing-restful-webservices-with-hateoas-using-jax-rs-and-jaxb-in-java/)内，链接作为资源模型类的一部分，并作为资源状态传递给客户端。

### HATEOAS References

