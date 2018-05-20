### REST – Content Negotiation

一般情况下，资源可以有多种表示，最主要的原因是因为它可能由不同的客户端请求不一样的表现层。客户端请求一个合适的资源表现层就被称为内容协商（content negotiation）。

> HTTP规定了集中内容协商机制——当可以获取多种资源的表述层时，为给定的响应选择最佳的资源表述层的方法。
>
> ——[RFC 2616](https://www.w3.org/Protocols/rfc2616/rfc2616-sec12.html) 

### Server-driven Vs Agent-driven Content Negotiation

如果是由服务端通过算法来为一个响应选取最佳资源表现层的话，那么这就被称为服务端驱动内容协商。如果由客户端或代理人来进行选取，则被称为代理人驱动内容协商。

事实上，你不会找到很多服务端驱动内容协商的例子，因为如果使用这种方法的话，你需要对客户端期望的内容形式做太多的假设。有关客户端上下文以及客户端如何处理资源表现层是（服务端）几乎不可能确定的。这种实现方法除了会让服务端变得复杂以外，同样也是没必要的。

所以大多数的REST API实现基于客户端驱动的内容协商。客户端驱动的内容协商依赖于HTTP请求头的使用或者资源的URI。

1. **Content negotiation using HTTP headers**
   在服务端，收到的请求可能会包含一个实体。为了确定这个实体的类型，服务端使用HTTP请求头中的`Content-Type`字段。有关这个字段的一些常用值可能为`text/plain`, `application/xml`, `text/html`, `application/json`, `image/gif`, 以及 `image/jpeg`。

   ```
   Content-Type: application/json
   ```

   同样，可以使用HTTP头`ACCEPT`来确定客户端期望哪种资源表现层。它的取值与上面所提到的`Content-Type`字段是一样的。

   ```
   Accept: application/json
   ```

   一般情况下，如果客户端没有在请求中指定`Content-Type`，服务端可以发送任何预先设定的默认的表现层类型。

   > 通过`Accept`头来实现内容协商是最广泛使用的同时也是最推荐的方法。

   