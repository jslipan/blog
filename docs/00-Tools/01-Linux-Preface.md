## 学习链接

- [IBM-面向 Linux 程序员和系统管理员的技术资源](https://www.ibm.com/developerworks/cn/linux/)
- [鸟哥的 Linux 私房菜](http://linux.vbird.org/new_linux.php)
- [命令大全（commandlinefu）](https://www.commandlinefu.com/commands/browse)
- [Linux命令搜索引擎](https://wangchujiang.com/linux-command/)

## 服务器概述

服务器是提供计算和存储服务的设备。由于服务器需要响应服务请求，并进行处理，因此一般来说，服务器应具备承担服务及保障服务的能力。服务器的构成包括电源、处理器、硬盘、内存、系统总线等。服务器的尺寸一般用高度 U 表示（1U = 1.75in = 44.45mm）以 Dell 机架式服务器为例,R2X0到R6X0基本都是 1U 的, R7X0 或 R8X0 是 2U 的, R9X0 是 4U 的。

### Raid卡

Raid 磁盘冗余阵列, Raid 的实现有软 Raid (即软件实现)和硬 Raid (即硬件实现),二者主要区别就是,硬件Raid的实现性能、冗余都更好、更高。不过，在企业真正的重要服务器里，Raid 几乎是不被采用的。

Raid卡的好处： 
- 可以将所有硬盘整合到一起（扩充容量）
- 可以使得数据更加安全（数据冗余）
- 可以获得更高得效率（读写性能）

互联网公司的服务器一般都是购买独立 Raid 卡，Raid 卡上也是有缓存的，具体说明如下：
- 冗余好到坏： Raid1  Raid10  Raid5  Raid0
- 性能从好到坏：Raid0  Raid10  Raid5  Raid1
- 成本从低到高：Raid0  Raid5  Raid1  Raid10

## 操作系统发展史

### Unix

1965年之前的时候，电脑并不像现在一样普遍，它可不是一般人能碰的起的，除非是军事或者学院的研究机构，而且当时大型主机至多能提供30台终端（30个键盘、显示器)，连接

为了解决数量不够用的问题

1965年左后由贝尔实验室、麻省理工学院 以及通用电气共同发起了Multics项目，想让大型主机支持300台终端

1969年前后这个项目进度缓慢，资金短缺，贝尔实验室退出了研究

1969年从这个项目中退出的Ken Thompson当时在实验室无聊时，为了让一台空闲的电脑上能够运行“星际旅行”游行，在8月份左右趁着其妻子探亲的时间，用了1个月的时间 编写出了 Unix操作系统的原型

1970年，美国贝尔实验室的 Ken Thompson，以 BCPL语言 为基础，设计出很简单且很接近硬件的 B语言（取BCPL的首字母），并且他用B语言写了第一个UNIX操作系统。

因为B语言的跨平台性较差，为了能够在其他的电脑上也能够运行这个非常棒的Unix操作系统，Dennis Ritchie和Ken Thompson 从B语言的基础上准备研究一个更好的语言

1972年，美国贝尔实验室的 Dennis Ritchie在B语言的基础上最终设计出了一种新的语言，他取了BCPL的第二个字母作为这种语言的名字，这就是C语言

1973年初，C语言的主体完成。Thompson和Ritchie迫不及待地开始用它完全重写了现在大名鼎鼎的Unix操作系统

由于UNIX是由工程师所主导开发的，而且使用者也大多是工程师，因此造成了UNIX系统接口（库函数与API）较难被一般使用者接受

UNIX的两大流派：AT&T贝尔实验室（现今的SCO UNIX），加州大学伯克利分校计算机系统研究小组的BSD UNIX

80年代UNIX版本的剧增以及各种UNIX版本之间的差别不断扩大导致了以美国政府为代表许多用户要求对其标准化，以增强各种应用程序在这些UNIX操作系统之间的可移植性

重要的UNIX标准包括： ANSI C、 IEE POSIX等

- ANSI C
    - ANSI　C是美国国家标准协会（ANSI）于1983年发布的C语言标准
    - 1989年，此标准被采纳为国际ISO/IEC 9899：1990
    - ISO C标准现旨在提供应用程序的可移植性，使其能适应于不同的操作系统，而不仅仅是UNIX操作系统


- POSIX
    - 1986年， IEEE制定了IEEE　P1003标准，这套标准被称为POSIX（Potable Operating System Interface)
    - POSIX定义了一整套的应用程序接口，包括系统调用、库函数、公共命令
    - POSIX标准希望在源代码级别保证应用程序可移植性


### Minix

因为AT&T(通用电气)的政策改变，在Version 7 Unix推出之后，发布新的使用条款，将UNIX源代码私有化，在大学中不再能使用UNIX源代码。Andrew S. Tanenbaum(塔能鲍姆)教授为了能在课堂上教授学生操作系统运作的实务细节，决定在不使用任何AT&T的源代码前提下，自行开发与UNIX兼容的操作系统，以避免版权上的争议。他以小型UNIX（mini-UNIX）之意，将它称为MINIX。

### Linux

因为Minix只是教学使用，因此功能并不强，因此Torvalds利用GNU的bash当做开发环境，gcc当做编译工具，编写了Linux内核-v0.02，但是一开始Linux并不能兼容Unix，即Unix上跑的应用程序不能在Linux上跑，即应用程序与内核之间的接口不一致，因为Unix是遵循POSIX规范的，因此Torvalds修改了Linux，并遵循POSIX（Portable Operating System Interface，他规范了应用程序与内核的接口规范）； 一开始Linux只适用于386，后来经过全世界的网友的帮助，最终能够兼容多种硬件。

## Minix没有火起来的原因

> Minix的创始人说，MINIX 3没有统治世界是源于他在1992年犯下的一个错误，当时他认为BSD必然会一统天下，因为它是一个更稳定和更成熟的系统，其它操作系统难以与之竞争。因此他的MINIX的重心集中在教育上。四名BSD开发者已经成立了一家公司销售BSD系统，他们甚至还有一个有趣的电话号码1-800-ITS-UNIX。然而他们正因为这个电话号码而惹火上身。美国电话电报公司因电话号码而提起诉讼。官司打了三年才解决。在此期间，BSD陷于停滞，而Linux则借此一飞冲天。他的错误在于没有意识官司竟然持续了如此长的时间，以及BSD会因此受到削弱。如果美国电话电报公司没有起诉，Linux永远不会流行起来，BSD将统治世界


## Linux环境准备

### Linux的发行版本介绍

Linux内核(kernel)版本主要有4个系列，分别为Linuxkernel 2.2、Linuxkernel 2.4、Linux、kernel 2.6, Linux kernel3.x, inux kernel4.x, 更多更新的内核版本请浏览https://www.kernel.org/。

Linux的发行商包括 Slackware、Redhat、 Debian、 Fedora、 Turbolinux、 Mandrake、SUSE、 CentOS、 Ubuntu、 红旗、麒麟．…·

其中几个重要的发行版本。

1）Red Hat: Red Hat Linux9.0的内核为2.4.20。在版本9.0之后，RedHat不再遵循GPL协议，成为收费产品（但仍开源），发展的新版本依次为RedHat 3.xRedHat 4.x、RedHa5.x、Red Hat 6.x、 Red Hat 7.x。

2）Fedora: 为Red Hat的一个分支，仍遵循GPL协议，可以认为是 Red Hat预发布版。

3）CentOS (Community Enterprise Operating System) : Red Hat的另一个重要分支，以Red Hat所发布的源代码重建符合GPL许可协议的Linux系统，即将Red Hat Linux源代码的商标LOGO以及非自由软件部分去除后再编译而成的版本，目前CentOS已被Red Hat公司收购，但仍开源免费。CentOS Linux是国内互联网公司使用最多的Linux系统版本。

### Linux版本场景选择

如果你是一个Linux爱好者，想个桌面系统，并且既不想使用盗版，又不想花太多钱购买商业系统软件，那么可以选择Ubuntu桌面系统。如果你需要服务器端的Linux系统，想要使用一个比较稳定的服务器系统，或者说你的目标就是进入企业从事Linux运维工作，那么建议你选择CentOS或Red Hat。在这两者当中又应首选CentOS, 因为目前市场的趋势就是这样的，CentOS社区非常活跃。如果是对系统稳定性安全性有更高的要求，或者是有特殊使用偏好的用户，可以考虑Debian或FreeBSD。如果是特别痴迷千新技术体验和追求最新的软件版本，那么可以选择 Fedora, 但要容忍Fedora潜在的新技术软件的Bug和系统稳定性的问题。如果喜欢更好的中文环境支持，可以选择麒麟Linux……


### 常用虚拟机软件

|虚拟机软件|特点及选择建议|
|:---:|:---:|
|VMware Workstation|工作站版虚拟软件，简单、易用，适合用于搭建学习环境|
|KVM/Xen Linux的虚拟化|服务器级虚拟化软件，适合企业虚拟化应用，复杂、不适合用于搭建学习|
|Virtual PC|MAC平台可以用|
|Virtual Box|开源的虚拟机软件|

### 虚拟机选择网络类型

VMware虚拟机常见的网络类型有bridged(桥接)、NAT(地址转换)、host-only(仅主机)3种。

- NAT(地址转换)
  - NAT(Network Address Translation), 网络地址转换，NAT模式是比较简单的实现虚拟机上网的方式，简单的理解就是，NAT模式虚拟机就是通过宿主机（物理电脑）进行上网和交换数据的
  - 在NAT模式下，虚拟机的网卡连接到宿主机的VMnet8上。此时系统的VMware NAT Service服务就充当路由器，负责将虚拟机发到VMnet8的包进行地址转换之后再发到实际的网络上，再将实际网络上返回的包进行地址转换后通过VMnet8发送给虚拟机。VMware DHCP Service负责为虚拟机分配IP地址。
  - NAT网络特别适合于家庭里电脑直接连接网线的情况，当然办公室的局域网环境也是适合的，优势是不会与其他物理主机IP发生冲突，且在没有路由的环境下也可以通过SSH、NAT连接虚拟机学习，换了网络环境虚拟机IP等不影响。

- Bridged(桥接模式)
  - 桥接模式可以简单地理解为通过物理主机网卡架设了一座桥，从而连入到实际的网络中。因此，虚拟机可以被分配与物理主机相同网段的独立IP，所有网络功能与网络中的真实机器几乎完全一样。桥接模式下的虚拟机和网内真实的计算机所处的位置是一样的。
  - 在bridged模式下，电脑设备创建的虚拟机就像一台真正的计算机一样，它会直接连接到实际的网络上，逻辑上上网与宿主机没有联系。
  - Bridged网络类型适合的场景：特别适合局域网环境，优势是虚拟机像一台真正的主机一样，缺点是会与其他物理主机IP发生冲突，并且在与宿主机交换数据时，都会经过实际的路由器，在不考虑NAT模式的时候，就选这个桥接模式，桥接模式下更换了网络环境之后，所有虚拟机的IP都会受影响。

- Host-only(仅主机)
  - 在Host-only模式下，虚拟机的网卡会连接到宿主机的VMnet1上，但宿主系统并不会为虚拟机提供任何路由器，因此虚拟机只能与宿主机进行通讯，不能连接到实际的网络中，即无法上网。

## 基本配置

### 查看系统版本
```bash
[jslipan@localhost ~]$ uname -m    //print the machine hardware name
x86_64

[jslipan@localhost ~]$ uname -a
Linux localhost.localdomain 3.10.0-862.el7.x86_64 #1 SMP Fri Apr 20 16:44:24 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

[jslipan@localhost ~]$ ls -d /lib64
/lib64
```

### 修改更新源
```bash
curl -s -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
curl -s -o /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

yum -y update

// 更改为中国上海，立即生效
timedatectl set-timezone Aisa/Shanghai
// 使用远程时间服务器同步本机系统时钟
yum -y install ntp
timedatectl set-ntp yes
```

### systemd初始化进程

Linux操作系统开机过程：从BIOS开始，然后进入Boot Loader, 再加载系统内核，然后内核进行初始化，最后启动初始化进程。初始化进程作为Linux系统的第一个进程，它需要完成Linux系统中相关的初始化工作，为用户提供合适的工作环境。红帽RHEL 7系统替换了初始化进程服务System V init，正式采用全新的systemd初始化进程服务。

**systemctl管理服务区别**
| System V init | Systemctl | 作用 |
|:---:|:---:|:---:|
| service foo start| systmectl start foo.service | 启动服务 |
| service foo restart | systemctl restart foo.service | 重启服务 |
| service foo stop | systemctl stop foo.service | 停止服务 |
| service foo reload | systemctl reload foo.service | 重新加载配置文件(不终止服务) |
| service foo status | systemctl status foo.service | 查看服务器状态 |

**systemctl设置服务区别**
| System V init | Systemctl | 作用 |
|:---:|:---:|:---:|
| chkconfig foo on | systemctl enable foo.service | 开机自动启动 |
| chkconfig foo off | systemctl disable foo.service | 开机不自动启动 |
| chkconfig foo | systemctl is-enabled foo.service | 查看特定服务是否为开机自动启动 |
| chkconfig --list | systemctl list-uint-files --type=service | 查看各个级别下的启动与禁用情况 |
