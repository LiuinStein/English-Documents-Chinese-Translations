### REST Architectural Constraints

REST代表了**Re**presentational **S**tate **T**ransfer（表述性状态传递）,一个由[Roy Fielding](https://en.wikipedia.org/wiki/Roy_Fielding)在2000年创造的名词，是一种通过HTTP用来设计松散耦合应用的设计体系风格，通常被用来开发web service。REST并不强制任何有关如何在底层实现的规则，它仅仅提出了高层设计的方针并且让开发者去思考如何去实现。

在我最近一次的工作中，我为一家电信公司设计了2年的RESTful API、在这篇文章里，我将会分析我的一些从实际开发经验中总结的一些思考。你可能不同意其中的几点，但是这没关系，我乐意以开放的心态来与你讨论这些事。

让我们从标准设计的具体内容开始，来理解Roy Fielding到底想让我们如何去做。然后再来讨论一些我的想法使得你的RESTful API设计更加精益求精。

### Architectural Constraints

REST定义了6个可用于任何web服务（一个真正的RESTful API）的体系约束

1. 统一接口
2. 客户端-服务器模式
3. 无状态
4. 可缓存
5. 分层系统
6. 写满足需求的代码（可选）

#### 统一接口

顾名思义，你**必须**决定对于系统内部资源的API接口，并且将这些接口暴露给API的消费者。每个系统内的资源应当仅有一个对应的逻辑URI，并且提供一个方法来获取相关或附加数据。将一种资源与一个URL地址关联起来总是最好的。

> 译者注：
>
> API的消费者（API consumers）即为使用该API的人。
>
> 将一种资源与一个URL地址关联起来总是最好的，原句为：
>
> > It’s always better to **synonymies a resource with a web page**.
>
> 原句指的是将一种资源与web page做同义替换，但译者认为此处的web page其实指的应当就是一个单独的URL

任何单个资源都不应该太大或者在它的表述（representation）里包含了所有的东西。无论何时相关，一个资源都应当包含一个链接（HATEOAS），指向一个用来获取相关信息的URI。

同时，系统间的资源的表述应当遵循一个特定的准则，例如命名规范，链接格式或数据格式（xml或Json）等。

所有的资源都应当可以通过一个通用的方法来进行访问（例如HTTP GET），并且对其他资源使用一致的方法来进行访问。

> 一个开发者一旦对你的API熟悉了之后，他将能通过类似的方法来获取其他的（对于其他资源的）API。

#### 客户端-服务器模式

