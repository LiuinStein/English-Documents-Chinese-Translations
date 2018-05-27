### REST API Security Essentials

安全永远不是事后才考虑的。它必须是任何开发项目以及REST API的组成部分。有多种方法来保卫RESTful API，例如[basic auth](http://howtodoinjava.com/resteasy/jax-rs-resteasy-basic-authentication-and-authorization-tutorial/), [OAuth](https://oauth.net/)等等。但是要记住一件事就是RESTful API必需是无状态的，所以请求的认证和授权必须不能依赖cookie或者session。相反，每个API请求必须带有一些授权信息，服务端每次收到请求后都要去验证这些信息。