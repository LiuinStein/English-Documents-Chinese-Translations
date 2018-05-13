### Caching REST API Response

[缓存](https://tools.ietf.org/html/rfc7234)是服务端在请求-响应路径中用来存储一份经常访问的数据的副本的功能。当一个用户请求一个资源的表现层时，请求通过缓存或多级缓存（本地缓存、代理缓存、反向代理）走向托管资源的服务。如果任何一级缓存拥有请求路径的资源表现层的新鲜副本的话，那么这份副本将会用来响应这个请求。如果所有缓存都不能满足这个请求，这个请求将一路传送至服务层（源服务器）。

在HTTP请求头中，源服务器说明一个响应是不是可缓存的，如果是的话，由谁来缓存，缓存的有效期是多少。在响应路径中，缓存可以将响应信息做一个副本，当然前提是缓存数据的metadata允许他们这么做。

可以使用如下的方法来使用缓存优化网络来提高整体的服务质量

* 减少带宽
* 降低延迟
* 减轻服务器负载
* 隐藏网络失败

> 译者注：
>
> 此处的减少带宽指的是，减少数据传输量（带宽使用）以提升服务的质量。
>
> 具体做法可参考文章[Bandwidth and Data Transfer](https://www.website.com/beginnerguide/bandwidth/1/2/how-to-reduce-data-transfer.ws)
>
> 摘抄其中一段：
>
> How can I reduce my "bandwidth usage"?
>
> 我怎么样才能降低我的带宽使用呢？
>
> You certainly do not want to reduce the number of visitors. So, the most effective way is to reduce the size of the files on your website.
>
> 首先，你肯定不想降低访问你网站的用户量，所以，最有效的方法就是减少网站文件的大小。
>
> - Build simpler, more efficient websites. Remove any unnecessary text, images or other files. Keep your pages as small as possible.
> - 创建一个简单的网站，删除一切不必要的文字、图片以及其他文件，让你的网站尽可能地简单
> - Optimize your graphics. Use JPEG image format for photos and GIF form for graphics.
> - 优化图像显示，对图片使用JPEG格式，对动画使用GIF格式
> - Refrain from fancy flash presentations, audio or video. This includes any music playing the background.
> - 避免使用flash来做页面效果或者展示视频及音频，同样避免有任何背景音乐
> - Use CSS and call JavaScript externally instead of embedding in every page. This reduces the HTML file size.
> - 从外部CSS和JavaScript，避免将其嵌入至HTML页面中
> - Remove unwanted tags, white space and comments
> - 删除不想要的标签，空格以及注释
> - Limit your Meta tags to those absolutely necessary
> - 限制源标签的大小
> - Consider caching your website, but set an expiry date in the HTTP headers so your visitors' browsers will refresh the content after a certain time (this allows their browser to save a copy of your website, and each time the visitor visits your website, the pages are served from the copy on the browser and not your web server)
> - 对你的网站考虑做缓存，并且在HTTP头部设置一个过期时间

### Caching in REST APIs



