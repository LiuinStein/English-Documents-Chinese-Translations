### REST Architectural Constraints

REST代表了**Re**presentational **S**tate **T**ransfer（表述性状态传递）,一个由[Roy Fielding](https://en.wikipedia.org/wiki/Roy_Fielding)在2000年创造的名词，是一种通过HTTP用来设计松散耦合应用的设计体系风格，通常被用来开发web service。REST并不强制任何有关如何在底层实现的规则，它仅仅提出了高层设计的方针并且让开发者去思考如何去实现。

在我最近一次的工作中，我为一家电信公司设计了2年的RESTful API、在这篇文章里，我将会分析我的一些从实际开发经验中总结的一些思考。你可能不同意其中的几点，但是这没关系，我乐意以开放的心态来与你讨论这些事。

让我们从标准设计的具体内容开始，来理解Roy Fielding到底想让我们如何去做。然后再来讨论一些我的想法使得你的RESTful API设计更加精益求精。

### Architectural Constraints