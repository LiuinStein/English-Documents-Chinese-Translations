### What is REST

REST是**RE**presentational **S**tate **T**ransfer（表述性状态传递）的缩写，是2000年由Roy Fielding在他[论文](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)中提出的一种适用于分布式超媒体系统（distributed hypermedia systems）的体系结构。

像任何其他架构风格一样，REST也有它自己的[6个指导性约束](https://restfulapi.net/rest-architectural-constraints/)，如果接口需要被称为RESTful，则必须满足这些约束。这些原则列在下面。

### Guiding Principles of REST

1. 客户端服务器模式（**Client–server**）：通过将用户界面问题与数据存储问题分离开来，我们可以提升跨多个平台的用户界面的可移植性，并通过简化服务器组件来提高可伸缩性。
2. 无状态（**Stateless**）：从客户端到服务器的每个请求都必须包含处理请求所需的所有信息，并且不能利用服务器存储任何的上下文，因此，会话状态需要完全保留在客户端上。
3. 可缓存（**Cacheable**）：缓存约束要求对请求响应中的数据隐式或明确标记为可缓存或不可缓存。如果响应是可缓存的，则客户端缓存有权重用该响应数据以用于以后等效的请求。
4. 统一接口（**Uniform interface**）：