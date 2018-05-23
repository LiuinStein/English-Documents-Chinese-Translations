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