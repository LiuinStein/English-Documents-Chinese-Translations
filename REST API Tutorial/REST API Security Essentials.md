### REST API Security Essentials

安全永远不是事后才考虑的。它必须是任何开发项目以及REST API的组成部分。有多种方法来保卫RESTful API，例如[basic auth](http://howtodoinjava.com/resteasy/jax-rs-resteasy-basic-authentication-and-authorization-tutorial/), [OAuth](https://oauth.net/)等等。但是要记住一件事就是RESTful API必需是无状态的，所以请求的认证和授权必须不能依赖cookie或者session。相反，每个API请求必须带有一些授权信息，服务端每次收到请求后都要去验证这些信息。

### REST Security Design Principles

这篇论文[“The Protection of Information in Computer Systems” by Jerome Saltzer and Michael Schroeder](http://web.mit.edu/Saltzer/www/publications/protection/)提出了8条用于保持计算机系统内信息安全的原则，如下：

1. **最小权限（Least Privilege）：**一个实体应当仅有其操作所需的最小权限。只有当实体需要某个权限的时候才授权给它，当其不需要某个权限的时候要即时撤销权限
2. **安全设置缺省值（Fail-Safe Defaults）:**  一个用户对系统内任意资源的默认访问权限都应为拒绝，除非他们明确被授予某个特定的权限
3. **机制经济（Economy of Mechanism）：**这个设计应当越简单越好。所有的组件接口以及两者之间的交互应当足够简单以便理解
4. **完全居中（Complete Mediation）：** 一个系统应当去验证对其所有资源的访问权限而不是单单依赖于缓存过的权限模型。如果对某一个资源的访问权限已经被撤销，但是并没有被相应的反应到权限模型中，那么系统就会变得不安全
5. **开放设计（Open Design）：**这个原则强调了以公开方式建立一个系统的重要性，比如不使用保密的算法
6. **特权分离（Separation of Privilege）：**不应当单单基于一种情况来对实体授予权限，最好使用基于资源类型的条件组合
7. **最不常用机制（Least Common Mechanism）：** 这个考虑的是在不同的组件之间共享状态的风险。如果其中一个可以破坏共享状态，那么他就可以同时破坏所依赖于它的所有的组建
8. **心理可接受性（Psychological Acceptability）：** 安全机制不应当让资源变得难以获取。简要来说，安全机制不应当影响用户体验



