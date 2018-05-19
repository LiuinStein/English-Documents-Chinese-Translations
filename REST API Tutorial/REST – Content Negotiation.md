### REST – Content Negotiation

一般情况下，资源可以有多种表示，最主要的原因是因为它可能由不同的客户端请求不一样的表现层。客户端请求一个合适的资源表现层就被称为内容协商（content negotiation）。

> HTTP规定了集中内容协商机制——当可以获取多种资源的表述层时，为给定的响应选择最佳的资源表述层的方法。
>
> ——[RFC 2616](https://www.w3.org/Protocols/rfc2616/rfc2616-sec12.html) 

### Server-driven Vs Agent-driven Content Negotiation

