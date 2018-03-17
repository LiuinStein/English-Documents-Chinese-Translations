### What is REST

REST是**RE**presentational **S**tate **T**ransfer（表述性状态传递）的缩写，是2000年由Roy Fielding在他[论文](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)中提出的一种适用于分布式超媒体系统（distributed hypermedia systems）的体系结构。

像任何其他架构风格一样，REST也有它自己的[6个指导性约束](https://restfulapi.net/rest-architectural-constraints/)，如果接口需要被称为RESTful，则必须满足这些约束。这些原则列在下面。

### Guiding Principles of REST

1. 客户端服务器模式（**Client–server**）：通过将用户界面问题与数据存储问题分离开来，我们可以提升跨多个平台的用户界面的可移植性，并通过简化服务器组件来提高可伸缩性。

2. 无状态（**Stateless**）：从客户端到服务器的每个请求都必须包含处理请求所需的所有信息，并且不能利用服务器存储任何的上下文，因此，会话状态需要完全保留在客户端上。

3. 可缓存（**Cacheable**）：缓存约束要求对请求响应中的数据隐式或明确标记为可缓存或不可缓存。如果响应是可缓存的，则客户端缓存有权重用该响应数据以用于以后等效的请求。

4. 统一接口（**Uniform interface**）：通过将一般的软件工程原理应用于组件接口，使得整个系统的体系结构得到简化，交互性得到提高。为了获得统一接口，需要多个体系结构的约束来共同指导组件的行为。REST定义了4个接口约定：

   * 资源标识符（identification of resources）

   * 通过资源的表述来操纵资源（manipulation of resources through representations）

     > 译者注：
     >
     > 在某一特定的时间点处资源的状态称之为资源的表述（resource representation）
     >
     > The state of resource at any particular timestamp is known as **resource representation**. 

   * 自我描述的信息（self-descriptive messages）

   * 以超媒体作为应用状态的驱动（hypermedia as the engine of application state）

5. 分层系统（**Layered system**）：分层系统由多个受约束且功能不同的组件进行的层级划分而组成，每个组件均不能被那些与他正在交互的组件之外的组件“看到”

6. 按需求编写代码【非必需】（**Code on demand (optional)**）：REST允许客户端通过从服务器下载和执行以applet或script形式的代码来扩展客户端的功能，这个设计允许通过减少需要预先实现的功能的数量来简化客户端。

### Resource

对于REST来说，对信息最关键的抽象就是资源（resource），任何可以被命名的信息均可以作为一个资源：一份文档或图像，一个临时的服务，其他资源的集合，一个非虚拟的物体（例如，一个人）等等。REST使用资源标识符（**resource identifier**）来区分组件间进行交互的特定的资源。

在某一特定的时间点处资源的状态称之为资源的表述（resource representation），一个表述通常包含数据，描述数据的元数据（metadata）以及可以帮助客户端转换到下一期望状态的超媒体链接。

> 译者注：
>
> 此处将timestamp译为时间点，timestamp主要指UNIX时间戳，UNIX时间戳是指从1970年1月1日（UTC/GMT的午夜）开始所经过的秒数

