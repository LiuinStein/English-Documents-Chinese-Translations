## Get Started, Part 1: Orientation and setup 第一部分：基本信息和安装

欢迎！很高兴能见到你来学习Docker。通过本教程你将学到：

* 安装你的Docker环境（本页）
* [建立一个镜像并通过其来运行一个容器]()
* [扩展你的APP到多个容器]()
* [搭建分布式应用集群]()
* [通过添加后端数据库来建立堆栈服务]()
* [将你的APP部署到产品之中]()

### Docker concepts Docker基本概念

Docker是一个针对程序员和系统管理员设计的用于开发、部署、运行应用程序的容器化平台。在Linux下使用容器技术来部署应用程序的过程称之为容器化（containerization）。这并不是一个新兴的概念，其主要应用于更加轻松地部署应用程序。

容器化的应用越来越广泛主要是因为：

* 灵活：即使是很复杂的应用程序都可以被容器化
* 轻量：容器间利用并共享宿主机内核
* 可互换：在运行中即可部署更新和升级
* 便捷：你可以在本地构建容器，在云端部署，在任意地方运行
* 可扩展：你可以增加并自动分发容器副本
* 可堆栈化：可动态垂直堆栈化你的服务

![](https://bucket.shaoqunliu.cn/image/0295.png)

##### Images and containers 镜像和容器

运行一个镜像即可得到一个容器。镜像（image）是一个可执行包，其包括了运行一个应用程序所需要的全部内容--代码、运行时环境、库、环境变量及配置文件。

容器（container）是一个镜像的运行时实例--实际执行时镜像会在内存中变成什么（一个带有状态的镜像或者一个用户进程）。你可以在Linux下执行命令`docker ps`来查看当前正在运行的容器。

##### Containers and virtual machines 容器和虚拟机

容器原生地运行在Linux系统之上，多个容器之间共享一套宿主机内核。容器中运行着一套与宿主机分离的进程，不占用任何其他应用程序的内存，这使得容器更加轻量化。

相比之下，虚拟机运行着一套完整的客户机操作系统，通过一系列虚拟机管理程序（hypervisor）虚拟地访问宿主机资源。通常情况下来说，虚拟机会为应用程序提供一个有较多资源的环境。

![](https://bucket.shaoqunliu.cn/image/0296.png)

### Prepare your Docker environment 配置你的Docker环境

在[相关支持平台](https://docs.docker.com/ee/supported-platforms/)上安装一份[维护版本](https://docs.docker.com/engine/installation/#updates-and-patches)的社区版（Docker Community Edition (CE)）或企业版docker（Enterprise Edition (EE)）

> **Kubernetes整合**
>
> * 在[17.12 Edge (mac45)](https://docs.docker.com/docker-for-mac/edge-release-notes/#docker-community-edition-17120-ce-mac45-2018-01-05)或者[17.12 Stable (mac46)](https://docs.docker.com/docker-for-mac/release-notes/#docker-community-edition-17120-ce-mac46-2018-01-09)更高版本的docker（for mac）上可以安装[Kubernetes on Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/kubernetes/)
> * 在[18.02 Edge (win50)](https://docs.docker.com/docker-for-windows/edge-release-notes/#docker-community-edition-18020-ce-rc1-win50-2018-01-26)及更高版本的docker（for Windows）上可以安装[Kubernetes on Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/kubernetes/)

[安装docker（英文版，此文暂未列入翻译计划）](https://docs.docker.com/install/) 

##### Test Docker version 测试docker版本

1. 使用命令`docker --version`来获取docker版本信息

   ```shell
   docker --version
   
   Docker version 17.12.0-ce, build c97c6d6
   ```

2. 使用命令`docker info`或`docker version`（注意没有`--`）来获取更多有关docker的信息

   ```shell
   docker info
   
   Containers: 0
    Running: 0
    Paused: 0
    Stopped: 0
   Images: 0
   Server Version: 17.12.0-ce
   Storage Driver: overlay2
   ...
   ```

   > 为了避免诱发权限错误，请使用sudo或者将当前用户加入`docker`用户组。[点击查看更多相关信息（英文版，此文暂未列入翻译计划）](https://docs.docker.com/install/linux/linux-postinstall/)
   >
   > 译者注：
   >
   > docker的守护进程会直接绑定Unix套接字（Unix socket）而不是使用TCP端口，默认情况下Unix套接字的所有权归`root`用户所有，其他用户访问均需要使用`sudo`命令，docker的守护进程自始至终都需要以`root`的权限来运行。如果你不想每次都用`sudo`命令的话，你也可以单独创建一个名为`docker`的用户组，然后使用此用户组下的用户运行docker，但要注意的是：`docker`用户组下的用户权限应当等同于`root`用户的权限。

##### Test Docker installation 测试docker安装

1. 通过运行一个简单的docker镜像来检测你的docker是否可以正常工作，[hello-world](https://hub.docker.com/_/hello-world/)

   ```shell
   docker run hello-world
   
   Unable to find image 'hello-world:latest' locally
   latest: Pulling from library/hello-world
   ca4f61b1923c: Pull complete
   Digest: sha256:ca0eeb6fb05351dfc8759c20733c91def84cb8007aa89a5bf606bc8b315b9fc7
   Status: Downloaded newer image for hello-world:latest
   
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   ...
   ```

2. 列出下载到你机器中的`hello-world`镜像

   ```shell
   docker image ls
   ```

3. 列出运行起来的`hello-world`容器（由镜像启动），此容器会在输出信息后退出。在下面的命令中，如果容器仍在运行的话，你将不再需要输入`--all`选项

   ```shell
   docker container ls --all
   
   CONTAINER ID     IMAGE           COMMAND      CREATED            STATUS
   54f4984ed6a8     hello-world     "/hello"     20 seconds ago     Exited (0) 19 seconds ago
   ```

### Recap and cheat sheet 回顾及备忘

```shell
## 列出docker控制台命令
docker
docker container --help

## 显示docker版本及相关信息
docker --version
docker version
docker info

## 运行docker镜像
docker run hello-world

## 列出本机docker镜像
docker image ls

## 列出docker容器 (正在运行的, 全部, 以quiet mode显示所有容器)
docker container ls
docker container ls --all
docker container ls -aq
```

> 译者注：
>
> 在quiet mode下仅显示容器的ID，此处可进一步参考其文档[docker container ls](https://docs.docker.com/engine/reference/commandline/container_ls/)，如果按字面翻译为“静默模式”总感觉不合适，故对此名词未做翻译。

### Conclusion of part one 第一部分总结

容器化使得[CI/CD](https://www.docker.com/solutions/cicd)进程无缝链接。这可以体现在：

* 无系统依赖的应用程序
* 更新可以快速提交至分布式应用程序的任一部分
* 更优化的资源密度

有了docker，扩展你的应用程序就变成了一个不断启动容器的过程，而不是启动繁琐复杂的虚拟机。

> 译者注：
>
> 依据docker官方文档中给出的链接，在此处CI/CD为Continuous Integration and Continuous Deployment，中文即为持续集成和持续部署。
>
> 另有[维基百科相关词条](https://en.wikipedia.org/wiki/CI/CD)给出CI/CD的另一种释义为：
>
> In software engineering, CI/CD or CICD may refer to the combined practices of **continuous integration and continuous delivery**.
>
> 即：持续集成和持续交付
>
> 另：Continuous Delivery（持续交付）和Continuous Deployment（持续部署）为截然不同的两个概念，注意区分！