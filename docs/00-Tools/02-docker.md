# 什么是Docker

Docker是基于Go语言实现的开源容器项目。Docker中有三个核心概念：Image、Container、Repository。

- Image： 类似于虚拟机镜像，可以将它理解为一个只读的模板。有领“好人卡”倾向的广大程序猿一定对 镜像 的概念不会陌生。但和 windows 的那种 iso 镜像相比，Docker 中的镜像是分层的，可复用的，而非简单的一堆文件迭在一起（类似于一个压缩包的源码和一个 git 仓库的区别）。
- Container： 容器的存在离不开镜像的支持，他是镜像运行时的一个载体（类似于实例和类的关系）。Dockers 容器类似于一个轻量级的沙箱，Docker 利用容器来运行和隔离应用。依托 Docker 的虚拟化技术，给容器创建了独立的端口、进程、文件等“空间”，Container 就是一个与宿机隔离 “容器”。容器可宿主机之间可以进行 port、volumes、network 等的通信。
- Repository： Docker 的仓库和 git 的仓库比较相似，拥有仓库名、tag。在本地构建完镜像之后，即可通过仓库进行镜像的分发。常用的 Docker hub 有 https://hub.docker.com/ 、 https://cr.console.aliyun.com/ 等。

## 相关命令

