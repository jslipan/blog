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
  - ANSI　C 是美国国家标准协会（ANSI）于1983年发布的C语言标准
  - 1989年，此标准被采纳为国际 ISO/IEC 9899：1990
  - ISO C 标准现旨在提供应用程序的可移植性，使其能适应于不同的操作系统，而不仅仅是 UNIX 操作系统

- POSIX
  - 1986年，IEEE 制定了 IEEE　P1003标准，这套标准被称为 POSIX（Potable Operating System Interface)
  - POSIX定义了一整套的应用程序接口，包括系统调用、库函数、公共命令
  - POSIX标准希望在源代码级别保证应用程序可移植性

### Minix

因为 AT&T (通用电气)的政策改变，在 Version 7 Unix 推出之后，发布新的使用条款，将 UNIX 源代码私有化，在大学中不再能使用 UNIX 源代码。Andrew S. Tanenbaum (塔能鲍姆)教授为了能在课堂上教授学生操作系统运作的实务细节，决定在不使用任何 AT&T 的源代码前提下，自行开发与 UNIX 兼容的操作系统，以避免版权上的争议。他以小型 UNIX（mini-UNIX）之意，将它称为 MINIX。

### Linux

因为Minix只是教学使用，因此功能并不强，因此 Torvalds 利用 GNU 的 bash 当做开发环境，gcc当做编译工具，编写了 Linux 内核-v0.02，但是一开始Linux并不能兼容Unix，即Unix上跑的应用程序不能在Linux上跑，即应用程序与内核之间的接口不一致，因为 Unix 是遵循 POSIX 规范的，因此 Torvalds修改了 Linux，并遵循 POSIX（Portable Operating System Interface，他规范了应用程序与内核的接口规范）； 一开始Linux只适用于386，后来经过全世界的网友的帮助，最终能够兼容多种硬件。

## Minix没有火起来的原因

> Minix 的创始人说，MINIX 3没有统治世界是源于他在1992年犯下的一个错误，当时他认为 BSD 必然会一统天下，因为它是一个更稳定和更成熟的系统，其它操作系统难以与之竞争。因此他的MINIX的重心集中在教育上。四名 BSD 开发者已经成立了一家公司销售 BSD 系统，他们甚至还有一个有趣的电话号码1-800-ITS-UNIX。然而他们正因为这个电话号码而惹火上身。美国电话电报公司因电话号码而提起诉讼。官司打了三年才解决。在此期间，BSD 陷于停滞，而Linux 则借此一飞冲天。他的错误在于没有意识官司竟然持续了如此长的时间，以及BSD会因此受到削弱。如果美国电话电报公司没有起诉，Linux 永远不会流行起来，BSD将统治世界

## Linux环境准备

### Linux的发行版本介绍

Linux内核(kernel)版本主要有4个系列，分别为Linuxkernel 2.2、Linuxkernel 2.4、Linux、kernel 2.6, Linux kernel3.x, inux kernel4.x, 更多更新的内核版本请浏览https://www.kernel.org/

Linux的发行商包括 Slackware、Redhat、 Debian、 Fedora、 Turbolinux、 Mandrake、SUSE、 CentOS、 Ubuntu、 红旗、麒麟．…·

其中几个重要的发行版本。

1）Red Hat: Red Hat Linux9.0的内核为2.4.20。在版本9.0之后，RedHat不再遵循GPL协议，成为收费产品（但仍开源），发展的新版本依次为RedHat 3.xRedHat 4.x、RedHa5.x、Red Hat 6.x、 Red Hat 7.x。

2）Fedora: 为Red Hat的一个分支，仍遵循GPL协议，可以认为是 Red Hat预发布版。

3）CentOS (Community Enterprise Operating System) : Red Hat的另一个重要分支，以 Red Hat 所发布的源代码重建符合GPL许可协议的Linux系统，即将Red Hat Linux 源代码的商标 LOGO 以及非自由软件部分去除后再编译而成的版本，目前 CentOS 已被 Red Hat 公司收购，但仍开源免费。CentOS Linux是国内互联网公司使用最多的Linux系统版本。

### Linux版本场景选择

如果你是一个 Linux 爱好者，想个桌面系统，并且既不想使用盗版，又不想花太多钱购买商业系统软件，那么可以选择Ubuntu桌面系统。如果你需要服务器端的Linux 系统，想要使用一个比较稳定的服务器系统，或者说你的目标就是进入企业从事 Linux 运维工作，那么建议你选择 CentOS 或 Red Hat。在这两者当中又应首选 CentOS, 因为目前市场的趋势就是这样的，CentOS 社区非常活跃。如果是对系统稳定性安全性有更高的要求，或者是有特殊使用偏好的用户，可以考虑 Debian 或 FreeBSD。如果是特别痴迷千新技术体验和追求最新的软件版本，那么可以选择 Fedora, 但要容忍 Fedora 潜在的新技术软件的Bug和系统稳定性的问题。如果喜欢更好的中文环境支持，可以选择麒麟 Linux……

### Linux系统启动流程（重要）

**CentOS 6**
打开计算机电源，计算机首先会加载BIOS信息，进而对 CPU 信息、设备启动顺序信息、硬盘信息、内存信息、时钟信息等进行自检。当正确检查完所有硬件信息后，计算机就会根据 BOIS 里的设置读取相应的启动系统里的硬件设备，如果预先设定了从硬盘启动加载系统，那么 BOIS 就会读取硬盘的 MBR（即0磁道0柱面1扇区的前446字节），接下来才开始加载内核文件，然后交由 Linux 来控制系统运行。

MBR 全称为 Master Boot Record，即主引导记录，它位于磁盘上的0磁道0柱面1扇区，整个大小512字节，MBR 里面存放了系统预启动信息、分区表信息及分区标志等。

在 MBR 的512字节中，第一部分为引导记录区，占有前446字节大小，其作用是找到标志为活动的分区，并将活动分区的引导记录读入内存。

第二部分为分区表，占有后面剩下全部的66字节大小，用于记录磁盘的分区信息，这其中，前64字节是磁盘分区表信息，后2字节是分区的结束标志。

计算机读取 BIOS 所指定的磁盘 MBR 信息之后，就会将其读入到内存中。被读入到内存中执行的其实就是 Boot Loader（引导加载程序），对应于 Linux 系统，就是加载 Grub 信息。

引导加载程序（Boot Loader）是计算机在加载操作系统内核之前运行的一段小程序。这段小程序可以初始化硬件设备、建立内存空间的映射图，从而将系统的软硬件环境加载到一个适合的状态，以便为最终调用操作系统内核做好准备。引导加载程序读取 grub.conf 文件配置信息，然后根据对应的配置信息来启动不同的操作系统。

加载完内核的相关文件以后，系统第一个运行的程序为 /sbin/init，因此，init 进程对应的进程号永远为1，相当于是所有 Linux 进程的祖先

此时 init 程序会读取 /etc/inittab 文件，并根据此文件来进行初始化工作， /etc/inittab 文件主要作用就是设定了 Linux 以什么样的运行级别启动，其设定被配置是"id:3:initdefault"，其中的3就是表明 Linux 需要运行在3级别上。

CentOS6 以前的版本，init 进程会根据 inittab 的设置加载 /etc/rc.d/rc.sysinit，并进行初始化。例如：设置主机名、设置欢迎信息、激活udev 和 selinux、加载 /etc/fstab（挂载磁盘设备等）、设置系统时钟、读取 /etc/sysctl.conf 设置内核参数、激活 lvm 及 software raid 设备、加载额外设备的驱动程序、各种清理操作（如清理日志）等。

CentOS6 以后，init 进程不再读取 inittab 加载 /etc/rc.d/rc.sysinit，而是读取 /etc/init/rcS.conf 文件加载 /etc/rc.d/rc.sysinit,并对系统进行初始化系统设置。

init 进程加载内核相关模块，CentOS5 下是读取 /etc/modules.d 目录下对的文件来加载内核模块，而在 CentOS 6 下则是加载 /etc/sysconfig/modules/ 下的内核模块。

init 进程执行对应运行运行级别下的脚本，根据系统设定运行级别的不同，系统会运行 rc0.d 到 rc6.d 中相应脚本程序，从而完成相应的初始化工作，以及启动相应的服务。在 CentOS6 以后的版本中，init 进程不再读取 inittab 加载运行级别对应的脚本，而是读取 /etc/init/rc.conf 加载指定运行级别下的脚本

rc.local 就是在系统做好一切初始化工作之后，留给管理员自主设置的一个文件，可以将需要跟随计算机启动的程序启动命令放置到这里。

系统读取 /etc/init/tty.conf（早期也是读取 inittab 进行设置的），设置对应运行级别的终端，启动 mingetty，进入登录前的状态。

1) 开启开机按钮，计算机加载 BIOS 自检
2) 读取 MBR 信息
3) 加载 Grub 菜单（Boot Loader，引导加载程序）
4) 加载 Kernel 内核以及驱动程序
5) 启动 init 进程，读取 inittab 文件
6) init 进程执行 rc.sysinit 初始化系统
7) init 进程加载内核相关模块
8) init 进程执行对应运行级别下的脚本
9) 加载 /etc/rc.local 
10) 启动mingetty，进入登录前的状态

**CentOS 7**

1) 开启开机按钮，计算机加载 BIOS 自检
2) 读取 MBR 信息
3) 加载 Grub 菜单
4) 加载 Kernel 内核以及驱动程序
5）启动 systemd 进程，加载如下文件：

1. 执行 initrd.target (/usr/lib/systemd/system/initrd.target) 包含挂载 /etc/fstab 文件中的文件系统
2. systemd 执行默认的 target 配置，默认的启动文件是 /etc/systemd/system/default.target，根据它的指向可以找到系统要进入的模式
3. systemd 执行 sysinit.target, 初始化系统加载 basic.target 准备启动系统
4. systemd 启动 multi-user.target（生产工作模式）下的服务程序，即开机自启动的程序，程序目录为 /etc/systemd/system 和 /usr/lib/systemd/system.
5. systemd 执行 multi-user.target 下的 /etc/rc.d/rc.local 内容
6. systemd 执行 multi-user.target 下的 getty.target 及登录服务
7. systemd 执行 graphical 所需要的服务（如果安装了图形桌面功能）

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

### 系统软件包安装

```bash
yum group install "Compatibility libraries" "Base" "Development tools"

yum group install "debugging Tools" "Dial-up Networking Support"

yum install psmisc net-tools bash-completion vim-enhanced -y
```

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

### Linux开关机

| 关机 | 说明 |
|:---:|:---:|
| shutdown -h now | 立刻关机 |
| shutdown -h +1 | 1分钟以后关机，1可以是别的数字或时间点，例如，11：00 |
| halt | 立即停止系统，需要人工关闭电源，CentOS 7 下为 systemctl halt |
| init 0 | 切换到运行级别0|
| poweroff | 立即停止系统，CentOS 7下为 systemctl poweroff |

```bash
// 重启
reboot
systemctl reboot
shutdown -r now
shutdown -r +1
init 6
```

## 常用命令

### 文件管理

```bash
cd /home/jslipan    #改变目录
cd -   #返回上次目录
cd ~   #家目录

mkdir  #创建目录 -v详细  -p递归 目录
cp   #复制   -r目录   -v详细  -f强制  -n静默
rm   #删除   -r递归   -f强制  -v详细过程
mv   #移动 eg:  mv /root/file1  /tmp
```

### 权限管理

- 用户账户
  - 普通用户账户：在系统上的任务是进行普通工作
  - 超级用户账户（或管理员账户）：在系统上的任务是对普通用户和整个系统进行管理。

- 组账户(组是用户的集合)
  - 标准组：标准组可以容纳多个用户
  - 私有组：私有组中只有用户自己

- 当一个用户同属于多个组时，将这些组分为
  - 主组（初始组）：用户登录系统时的组。
  - 附加组：登录后可切换的其他组

上面也说了，账户的实质上就是用户在系统上的标识，这些标识是用文件保存起来的：

- 用户名和 UID 被保存在/etc/passwd文件中，文件权限 (-rw-r--r--)
- 组和GID 被保存在 /etc/group文件中，文件权限(-r--------)
- 用户口令(密码)被保存在 /etc/shadow文件中  ，文件权限(-rw-r--r-- )
- 组口令被保存在 /etc/gshadow文件中 ，文件权限 (-r--------)

也就是说：我们创建的用户，这个用户的信息由不同的文件来保存着。

```bash
# drwx------. 18 jslipan jslipan 4096 11月 16 20:28 .cache
# - -------- ---  ------  ------ ---   ------------  -----
# |    |      |      |       |    |           |        |
# |    |      |      |       |    |           |        +----- 文件名
# |    |      |      |       |    |           +-------------- 最后修改时间
# |    |      |      |       |    +-------------------------- 文件大小，如果是目录4096
# |    |      |      |       +------------------------------- 所属用户组
# |    |      |      +--------------------------------------- 文件拥有者
# |    |      +---------------------------------------------- 如果是文件，表示硬链接的数，如果是目录则表示目录的子目录个数
# |    |
# |    +----------------------------------------------------- 第1-3位确定所有者（该文件的所有者）拥有该文件的权限。 ---User
# |                                                           第4-6位确定所属组（同用户组的）拥有该文件的权限。 ---Group
# |                                                           第7-9位确定其他用户组拥有该文件的权限。 ---Other
# |
# +---------------------------------------------------------- 第0位确定文件类型（d,-,l,c,b）
umask   # 不应该赋予的权限

# 除了上面所说的权限之外，Linux还提供了三种特殊的权限：
- SUID：使用命令的所属用户的权限来运行，而不是命令执行者的权限
- SGID：使用命令的组权限来运行。
- Sticky-bit：目录中的文件只能被文件的所属用户和root用户删除。
```

**用户管理**
useradd
usermod
userdel

**组管理**
groupadd
groupmod
groupdel

**批量管理用户**
成批添加/更新一组账户：newusers
成批更新用户的口令：chpasswd

**组成员管理**
向标准组中添加用户
gpasswd -a <用户账号名> <组账号名>
usermod -G <组账号名> <用户账号名>

从标准组中删除用户
gpasswd -d <用户账号名> <组账号名>


**口令维护(禁用、恢复和删除用户口令)**
设置用户口令：
passwd [<用户账号名>]

禁用用户账户口令
passwd -l <用户账号名>

查看用户账户口令状态
passwd -S <用户账号名>

恢复用户账户口令
passwd -u <用户账号名>

清除用户账户口令
passwd -d <用户账号名>

### 任务调度

crontab   -e编辑   -l查询  -r删除当前用户所有的crontab任务

```bash
/etc/crontab
crontab -e
*/1 * * * * ls -l /etc/ > /tmp//to.txt      # 每小时的每分钟执行 ls -l /etc/ > /tmp/to.txt

# *    *    *    *    *
# -    -    -    -    -
# |    |    |    |    |
# |    |    |    |    +----- 星期中星期几 (0 - 7) (星期天 为0)
# |    |    |    +---------- 月份 (1 - 12) 
# |    |    +--------------- 一个月中的第几天 (1 - 31)
# |    +-------------------- 小时 (0 - 23)
# +------------------------- 分钟 (0 - 59)

# 0 8,12,16 * * * 代表每天的8点0分，12点0分，16点0分都执行一次
# 0 5 * * 1-6  代表在周一到周六的凌晨5点0分执行命令
# 45 22 * * *  在22点45分执行
# 0 17 * * 1  每周一17点0分执行
# 30 6 */10 * * ls  每月的1、11、21、31日是的6：30执行一次ls命令
# 00 03 * * 1-5 find /home "*.xxx" -mtime +4 -exec rm {} \;  
# 每周一至周五3点钟，在目录/home中，查找文件名为*.xxx的文件，并删除4天前的文件
```
