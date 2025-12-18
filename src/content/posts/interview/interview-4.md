---
title: 面试题以及答案总结
published: 2025-08-26
description: "面试题以及答案总结"
image: ""
tags: []
category: "interview"
draft: true
lang: "zh-CN"
---

## 一、单项选择题

1、如下哪一个命令可以帮助你知道 shell 命令的用法（ A ）
A. man B.pwd C. help D. more

2、Linux 分区类型默认的是：（ B ）
A. vfat B. ext2/ext3 C. swap D. dos

3、在大多数 Linux 发行版本中，以下哪个属于块设备 （ B ）
A. 串行口 B. 硬盘 C. 虚拟终端 D. 打印机

4、下面哪个命令行可用来马上重新启动正在运行的 Linux 系统？（ D ）
A. restart --delay=0 B. reboot -w  
C. halt -p D. shutdown -r now

5、在 Linux 系统，默认的 shell 是什么（ A ）
A.bash B.ash C.csh D.gnush

6、下面哪条命令可用来确保文件“myfile”存在（ B ）  
A. cp myfile /dev/null B. touch myfile  
C. create myfile D. mkfile myfile

7、 LILO 的配置文件是：（ B ）
A. /etc/conf B. /etc/lilo.conf
C. /proc/kcore D. /usr/local/

8、用“useradd jerry”命令添加一个用户，这个用户的主目录是什么（ A ）
A./home/jerry B./bin/jerry
C./var/jerry D./etc/jerry

9、Linux 文件权限一共 10 位长度，分成四段，第三段表示的内容是（ D ）
A.文件类型 B.文件所有者的权限
C.文件所有者所在组的权限 D.其他用户的权限

10、某文件的组外成员的权限为只读；所有者有全部权限；组内的权限为读与写，则该文件的权限为（ D ）
A.467 B.674 C.476 D.764

11、不是 shell 具有的功能和特点的是 （ A ）
A.管道 B.输入输出重定向  
C.执行后台进程 D.处理程序命令

12、如何从当前系统中卸载一个已装载的文件系统（ A ）
A. umount B. dismount
C. mount –u D. 从 /etc/fstab 中删除这个文件系统项

13、你用 vi 编辑器编写了一个脚本文件 shell.sh，你想将改文件名称修改为 shell2.sh，下列命令（ B ）可以实现。
A. cp shell.sh shell2.sh B. mv shell.sh shell2.sh
C. ls shell.sh >shell2.sh D. ll shell.sh>shell2.sh

14、在/home/stud1/wang 目录下有一文件 file，使用 （ D ）可实现在后台执行命令，此命令将 file 文件中的内容输出到 file.copy 文件中。
A. cat file >file.copy B. cat file file.copy
C. &cat file file.copy D. &cat file >file.copy

15、字符设备文件类型的标志是 （ B ）
A. p B. c C. s D. l

16、删除文件命令为（ D ）
A. mkdir B. rmdir C.mv D. rm

17、（ B ）命令可更改一个文件的权限设置？
A. attrib B. chmod C. change D. file

18、用命令 ls -al 显示出文件 ff 的描述如下所示，由此可知文件 ff 的类型为（ A ）。

```
-rwxr-xr-- 1 root root 599 Cec 10 17:12 ff
```

A. 普通文件 B. 硬链接 C. 目录 D. 符号链接

19、系统中有用户 user1 和 user2，同属于 users 组。在 user1 用户目录下有一文件 file1，它拥有 644 的权限，如果 user2 用户想修改 user1 用户目录下的 file1 文件，应拥有（ B ）权限。
A. 744 B. 664 C. 646 D. 746

20、在指令系统的各种寻址方式中，获取操作数最快的方式是（ 1 -B ）；若操作数的地址包含在指令中，则属于（ 2-A ）方式。
（1） A、直接寻址 B、立即寻址 C、寄存器寻址 D、间接寻址
（2） A、直接寻址 B、立即寻址 C、寄存器寻址 D、间接寻址

21、在 CPU 和物理内存之间进行地址转换时，（ B ）将地址从虚拟（逻辑）地址空间映射到物理地址空间。
A、TCB B、MMU C、CACHE D、DMA

22、Linux 将存储设备和输入/输出设备均看做文件来操作，（C）不是以文件的形式出现。
A. 目录 B. 软链接
C. i 节点表 D. 网络适配器

23、关于文件系统的安装和卸载，下面描述正确的是（A）。
A. 如果光盘未经卸载，光驱是打不开的
B. 安装文件系统的安装点只能是/mnt 下
C. 不管光驱中是否有光盘，系统都可以安装 CD-ROM 设备
D. mount /dev/fd0 /floppy 此命令中目录/floppy 是自动生成的

24、为了查看 Linux 启动信息，可以用（B）命令
A. cat /etc/lilo.conf B.dmesg  
C. cat/proc/cpuinfo D.lilo

25、用下列（A）命令查看 Linux 使用了多少内存
A.cat /proc/meminfo B. cat /bin/meminfo
C.vi /proc/meminfo D.vi /user/local/meminfo

26、下列（D）设备是字符设备。
A. hdc B. fd0 C. hda1 D. tty1

27、下列说法正确的是（D）
A. ln -s a.txt b.txt，作用是制作文件 b.txt 的符号链接，其名称为 a.txt
B. df 命令可以查看当前目录占用磁盘空间的大小
C. comm 命令打印两个文本文件中的相同的内容
D. rm 命令可以用来删除目录

28、有如下的命令：$dd if=f1 of=f2。其中 if=f1 表示（A）
A. 以 f1 作为源文件，代替标准输入
B. 以 f1 作为目标文件，代替标准输出
C. 当条件满足 f1 的时候，执行真正的拷贝
D. 拷贝的过程中，不转化文件

29、为了查找出当前用户运行的所有进程的信息，我们可以使用（B）命令：
A. ps -a B. ps -u C. ls -a D. ls –l

30、为保证在启动服务器时自动启动 DHCP 进程，应对（ B ）文件进行编辑。
A、 /etc/rc.d/rc.inet2 B、/etc/rc.d/rc.inet1
C、/etc/dhcpd.conf D、/etc/rc.d/rc.S

31、（ D ）设备是字符设备。
A、hdc B、fd0 C、hda1 D、tty1

32、文件 exer1 的访问权限为 rw-r--r--，现要增加所有用户的执行权限和同组用户的写权限，下列命令正确的是（ A ）。
A 、chmod a+x g+w exer1 B 、chmod 765 exer1
C 、chmod o+x exer1 D 、chmod g+w exer1

33、删除当前目录 abc 以及下面的所有子目录和文件，并不要求提示任何确认信息的命令是（B）
A. del abc*.* B. rm –rf abc C. rmdirabc D. rm –r abc _._

34、如果忘记了 ls 命令的用法，可以采用（ C ）命令获得帮助
a. ？ls b.help ls c.man ls d.get ls

35、在安装开始前，用光盘启动系统，想要进入字符界面安装，需要输入的命令是（ C ）
a.linux doc b.linux c.linux text d.linux note

36、要给文件 file1 加上其他人可执行属性的命令是（ C ）
a.chmod a+x b.chown a+x c.chmod o+x d.chown o+x

37、怎样新建一个新文件：（ A ）
a.touch hello.c b.mk hello.c c.rm hello.c d.new hello.c

38、在 bash 命令中，当用（ B ）参数时，表示 bash 是交互的。
A、－c B、－i C、－s D、－d

39、重定向的符号“>"表示：（ C ）
A、输出追加 B、输入追加 C、输出重定向，原来的文件会被改写 D、管道

40、linux 系统能够直接读取的分区类型是（ D ）
a.ntfs b.fat16 c.fat32 d.ext3

41、下列提法中，属于 ifconfig 命令作用范围的是（ B ）。
A、编译源程序 B、配置网卡的 IP 地址  
C、配置系统内核 D、加载网卡到内核中

43、一般可以用（ C ）实现自动编译。
A、gcc B、gdb \* C、make D、 vi

44、处理机主要由处理器、存储器和总线组成，总线包括（ D ）。
A、数据总线、串行总线、逻辑总线、物理总线  
B、并行总线、地址总线、逻辑总线、物理总线  
C、并行总线、串行总线、全双工总线
D、数据总线、地址总线、控制总线

45、假设当前目录下有文件 Makefile，下面是其内容：

```
pr1: prog.o subr.o
gcc –o pr1 prog.o subr.o
prog.o: prog.c prog.h
gcc –c –l prog.o prog.c
subr.o: subr.c
gcc –c –o subr.o subr.c
clear:
rm –f pr1*.o
```

现在执行命令 make clear，实际执行的命令是（ A ）：
A. rm –f pr1\*.o
B. gcc –c –l prog.o prog.c
C. gcc –c –o subr.o subr.c
D. 都执行

46、Linux 将存储设备和输入/输出设备均看做文件来操作，下列选项（C）不是以文件的形式出现。
A. 目录 B. 软链接
C. i 节点表 D. 网络适配器

47、有如下的命令：$dd if=f1 of=f2。其中 if=f1 表示（ A ）
A. 以 f1 作为源文件，代替标准输入
B. 以 f1 作为目标文件，代替标准输出
C. 当条件满足 f1 的时候，执行真正的拷贝
D. 拷贝的过程中，不转化文件

48. 文件之间可以建立两种链接关系：软链接和硬链接，硬链接的特点是（C）
    A. 等同于文件复制操作
    B. 类似于文件复制，但新的链接文件并不占用文件磁盘存储空间
    C. 删除源文件，将使其他链接文件失效
    D. 可以对目录文件名建立硬链接

49. 下面哪一个选项不是 linux 系统的进程类型（D）
    A. 交互进程
    B. 批处理进程
    C. 守护进程
    D. 就绪进程

50、下面（ B ）特性不符合嵌入式操作系统特点。
A、实时性 B、不可定制  
C、微型化 D、易移植

51、下面关于 C 语言程序的描述，正确的是（　 C 　）。
A、总是从第一个定义的函数开始执行  
B、要调用的函数必须在 main()函数中定义  
C、总是从 main()函数开始执行
D、main()函数必须放在程序的开始

52、在 FTP 协议中，控制连接是由（ B ）主动建立的。
A、服务器端 B、客户端  
C、操作系统 D、服务提供商

53、以下叙述中，不符合 RISC 指令系统特点的（ B ）。
A、指令长度固定，指令种类少  
B、寻址方式种类丰富，指令功能尽量增强  
C、设置大量通用寄存器，访问存储器指令简单  
D、选取使用频率较高的一些简单指令

54、当我们与某远程网络连接不上时，就需要跟踪路由查看，以便了解在网络的什么位置出现了问题，满足该目的的命令是（ C ）。
A、ping B、ifconfig
C、traceroute D、netstat

55. 下列哪种文件系统的写入是 LINUX 所不能完全支持的：D
    A. FAT B. UFS C. JFS D. NTFS

56. LINUX 支持网络文件系统 NFS,下列哪个命令实现了将位于 192.168.1.4 机器上的 /opt/sirnfs 目录挂载到本机/mnt/sirnfs 下： A
    A．mount -t nfs 192.168.1.4:/opt/sirnfs/mnt/sirnfs
    B．mount -t nfs /mnt/sirnfs192.168.1.4:/opt/sirnfs
    C．mount nfs –t 192.168.1.4:/opt/sirnfs/mnt/sirnfs
    D．mount nfs –t /mnt/sirnfs192.168.1.4:/opt/sirnfs

57、同 CISC 相比，下面哪一项不属于 RISC 处理器的特征\_ D
A、采用固定长度的指令格式，指令规整、简单、基本寻址方式有 2 ～ 3 种。
B、减少指令数和寻址方式，使控制部件简化，加快执行速度。
C、数据处理指令只对寄存器进行操作，只有加载/存储指令可以访问存储器，以提高指令的执行效率，同时简化处理器的设计。
D、RISC 处理器都采用哈佛结构

58、在下列 ARM 处理器的各种模式中，**D\_**模式有自己独立的 R8-R14 寄存器。
A、系统模式(System)、
B、终止模式(Abort)
C、中断模式(IRQ)
D、快中断模式(FIQ)

59、按照 ARM 过程调用标准（APCS），栈指针使用\_B\_\_\_寄存器，
A、R0 B、R13 C、R14 D、R15

60、在 ARM 体系结构中，\_C**_寄存器作为连接寄存器，当进入子程序时或者处理器响应异常的时候，用来保存 PC 的返回值；\_C_**寄存器作为处理器的程序计数器指针。
A、R0，R14 B、R13，R15 C、R14，R15 D、R14，R0

61、在 ARM 体系结构中，要从主动用户模式（User）切换到超级用户模式（Supervisor），应采用何种方法？C
A、直接修改 CPU 状态寄存器（CPSR）对应的模式
B、先修改程序状态备份寄存器（SPSR）到对应的模式，再更新 CPU 状态
C、使用软件中断指令（SWI）
D、让处理器执行未定义指令

62、下面关于 MMU 和 Linux 描述错误的是：C
A、MMU 是内存管理单元 Memory Management Unit 的缩写
B、uClinux 可以运行在有 MMU 的处理器上
C、Linux 内核功能强大，内存管理功能丰富，即使在没有 MMU 的处理器上，也可以通过软件实现地址映射。
D、Linux 系统正是利用 MMU，才能使得各个进程有独立的寻址空间

63、DNS 域名系统主要负责主机名和（ A ）之间的解析。
A、IP 地址 B、MAC 地址
C、网络地址 D、主机别名

64、在 vi 编辑器中的命令模式下，重复上一次对编辑的文本进行的操作，可使用（ C ）命令。
A、上箭头 B、下箭头 C、<.> D、<\*>

65、进程有三种状态：（ C ）。
A 、准备态、执行态和退出态 B 、精确态、模糊态和随机态
C 、运行态、就绪态和等待态 D 、手工态、自动态和自由态

66、下列变量名中有效的 shell 变量名是（ C ）。
A、-1-time B、\_2$3  
C、bo_chuang_1 D、2009file

67、文件系统的主要功能是（ A ）。
A、实现对文件的按名存取 B、实现虚拟存储  
C、 提高外存的读写速度 D、用于保存系统文档

68、在 ARM Linux 体系中，用来处理外设中断的异常模式是**C\_\_**
A、软件中断（SWI） B、未定义的指令异常
C、中断请求（IRQ） D、快速中断请求（FIQ）

69、在 Linux 系统中，驱动程序注册中断处理程序的函数是\_B\_\_\_\_
A、trap_init B、request_irq
C、enable_irq D、register_irq

70、在 ARM Linux 系统中，中断处理程序进入 C 代码以后，ARM 的处于**A**工作模式
A、超级用户（SVC） B、中断(IRQ)
C、快速中断（IRQ） D、和进入中断之前的状态有关系

71、在 ARM 体系构建的嵌入式系统中，由电平模式触发的中断，其对应的中断标准应该在何时被清除？A
A、当中断处理程序结束以后，才可以清除
B、进入相应的中断处理程序，即可以清除
C、产生 IRQ 中断的时候，处理器自动清除
D、任何时候都可以清除

72、在操作系统中，Spooling 技术是用一类物理设备模拟另一类物理设备的技术，实现这种技术的功能模块称做（ B ）。
A、可林斯系统 B、斯普林系统
C、图灵机系统 D、 虚拟存储系统

73、通过修改下面文件哪个文件 ，可以设定开机时候自动安装的文件系统（C ）
A. /etc/mta B. /etc/fastboot
C. /etc/fstab D. /etc/inetd.conf

74、下面关于 Shell 的说法，不正确的是： （D）
A. 操作系统的外壳
B. 用户与 Linux 内核之间的接口程序
C. 一个命令语言解释器
D. 一种和 C 类似的程序语言

75、init 可执行文件通常存放在（ C ）目录中。
A．/etc B．/boot
C．/sbin D．/root

76、假设 root 用户执行“init 0”命令，系统将会（ B ）。
A．暂停 B．关机 C．重新启动 D．初始化

77、嵌入式系统应用软件一般在宿主机上开发，在目标机上运行，因此需要一个（ B ）环境。
A、交互操作系统 B、交叉编译  
C、交互平台 D、分布式计算

78、已知有变量 data1 定义如下：C

```c
union data
{ int i;
  char ch;
  float f;
} data1;
```

则变量 data1 所占的内存存储空间可表示为。
A、sizeof(int) B、sizeof(char)
C、sizeof(float) D、sizeof(int)+sizeof(char)+sizeof(float)

79、软件开发模型给出了软件开发活动各阶段之间的关系，（ D ）不是软件开发模型。
A、瀑布模型 B、螺旋模型  
C、原型模型 D、程序模型

80、实时操作系统（RTOS）内核与应用程序之间的接口称为（ C ）。
A、输入/输出接口 B、文件系统  
C、API D、图形用户接口

81、在操作系统中，除赋初值外，对信号量仅能操作的两种原语是（ C ）。
A、存操作、取操作 B、读操作、写操作  
C、P 操作、V 操作 D、输入操作、输出操作

82、在下列 ARM 处理器的各种模式中，只有**A\_**模式不可以自由地改变处理器的工作模式。
A、用户模式（User） B、系统模式(System)
C、终止模式(Abort) D、中断模式(IRQ)

83、32 位体系结构的 ARM 处理器有\_B**\_种不同的处理器工作模式，和**B\_\_个主要用来标识 CPU 的工作状态和程序的运行状态的状态寄存器。
A、7、7 B、7、6 C、6、6 D、6、7

84、已知 Linux 系统中的唯一一块硬盘是第一个 IDE 接口的 master 设备，该硬盘按顺序有 3 个主分区和一个扩展分区,这个扩展分区又划分了 3 个逻辑分区，则该硬盘上的第二个逻辑分区在 Linux 中的设备名称是（ D ）
A. /dev/hda2 B. /dev/hda3
C. /dev/hda5 D. /dev/hda6

85、为了查看 Linux 启动信息，可以用：（ B ）
A、cat /etc/lilo.conf B、dmesg C、 cat/proc/cpuinfo D、lilo

86、某文件的组外成员的权限为只写；所有者有读写权限；组内的权限为只读，则该文件的权限为（ B ）
A 467 B 642 C 476 D 764

87、下面哪个命令行可用来马上重新启动正在运行的 Linux 系统？（ D ）
A. restart --delay=0 B. reboot -w  
C. halt -p D. shutdown -r now

88、在 bash 命令中，当用（ B ）参数时，表示 bash 是交互的。
A、－c B、－i C、－s D、－d

89、重定向的符号“>>"表示：（ A ）
A、输出追加 B、输入追加 C、输出重定向，原来的文件被改写 D、管道

90、Linux 文件权限一共 10 位长度，分成四段，第一段表示的内容是（ A ）
A 文件类型 B 文件所有者的权限
C 文件所有者所在组的权限 D 其他用户的权限

91、（ B ）命令可更改一个文件的权限设置？
A. attrib B. chmod C. change D. file

92、你用 vi 编辑器编写了一个脚本文件 shell.sh，你想将该文件名称修改为 shell2.sh，下列命令（ B ）可以实现。
A. cp shell.sh shell2.sh
B. mv shell.sh shell2.sh
C. ls shell.sh >shell2.sh
D. ll shell.sh >shell2.sh

93、在使用 GCC 编译器的过程中，以下（B）选项可用来指定生成的目标文件名
A．-c B．-o C．-S D．-E

94、假设当前目录下有文件 Makefile，下面是其内容：

```
pr1: prog.o subr.o
gcc –o pr1 prog.o subr.o
prog.o: prog.c prog.h
gcc –c –l prog.o prog.c
subr.o: subr.c
gcc –c –o subr.o subr.c
clear:
rm –f pr1*.o
```

现在执行命令 make subr.o，实际执行的命令是（C）：
A. gcc –o pr1 prog.o subr.o
B. gcc –c –l prog.o prog.c
C. gcc –c –o subr.o subr.c
D. 都执行

95、为了使用生成的目标文件能够用于 gdb 调试，在编译时 GCC 应使用（C）选项。
A．-c B．-w C．-g D．-o

96、存盘并退出 vi 的指令是（ D ）。
A、q B、q! C、w D、wq

97. 下列关于/etc/fstab 文件描述，正确的是（ D ）。
    A. fstab 文件只能描述属于 linux 的文件系统
    B. CD_ROM 和软盘必须是自动加载的
    C. fstab 文件中描述的文件系统不能被卸载
    D 启动时按 fstab 文件描述内容加载文件系统

98. ARM 嵌入式系统中，PC 指向的是正在（C ）的指令地址。  
    A 执行 B 译码 C 取指 D 都不是

99. ARM 系统处理 16-bit 数据时，对应的数据类型是（ B ）。  
    A Byte B Halfword C Word D 三者都不是

100.  实时系统是指( B )
      A 响应快的系统 B 时间约束的系统 C 单任务系统 D 内核小的系统

101.  下面属于 blob 运行过程第一阶段的是（C）  
      A 外围的硬件初始化（串口，USB 等）；
      B 根据用户选择，进入命令行模块或启动 kernel。
      C 寄存器的初始化
      D 堆栈的初始化
      答案：C 第一阶段的代码在 start.s 中定义，大小为 1KB，它包括从系统上电后在 0x00000000 地址开始执行的部分。这部分代码运行在 Flash 中，它包括对 S3C44B0 的一些寄存器的初始化和将 Blob 第二阶段代码从 Flash 拷贝到 SDRAM 中。

102.下列几种流行的嵌入式 GUI 中，没有采用分层设计的一种是： B
A.MiniGUI B. Qt/Embedded C. Nano-XWindow D. OpenGUI

103. Qt/Embedded 的底层图形引擎基于一下哪种接口技术： A
     A．framebuffer B．GAL C．IAL D．GFX

104.在 Linux 使用 GCC 编译器时有如下命令:Gcc–g test.c –o test，其中参数-g 的作用是(D)
A .生成目标文件 test.o B.生成汇编文件 test.s C .进行预编译 D .包含调试信息

105. LINUX 支持网络文件系统 NFS,下列哪个命令实现了将位于 192.168.1.4 机器上的 /opt/sirnfs 目录挂载到本机/mnt/sirnfs 下： A
     A．mount -t nfs 192.168.1.4:/opt/sirnfs/mnt/sirnfs
     B．mount -t nfs /mnt/sirnfs 192.168.1.4:/opt/sirnfs
     C．mount nfs –t 192.168.1.4:/opt/sirnfs/mnt/sirnfs
     D．mount nfs –t /mnt/sirnfs192.168.1.4:/opt/sirnfs

106、同 CISC 相比，下面哪一项不属于 RISC 处理器的特征**\_D\_\_\_**
A、采用固定长度的指令格式，指令规整、简单、基本寻址方式有 2 ～ 3 种。
B、减少指令数和寻址方式，使控制部件简化，加快执行速度。
C、数据处理指令只对寄存器进行操作，只有加载/存储指令可以访问存储器，以提高指令的执行效率，同时简化处理器的设计。
D、RISC 处理器都采用哈佛结构

107、32 位数 0x12345678 用小端格式表示，则在 AXD 调试器下观察数据在内存中分布的情况是（B）  
A 12 34 56 78 B 78 56 34 12 C 21 43 65 87 D 87 65 43 21

108、RISC 是指（C）
A 复杂指令计算机 B 并行机 C 精简指令计算机 D 多处理器计算机

109、在 ARM 体系结构中，**C**寄存器作为连接寄存器，当进入子程序时或者处理器响应异常的时候，用来保存 PC 的返回值；\_C\_\_\_寄存器作为处理器的程序计数器指针。
A、R0，R14 B、R13，R15
C、R14，R15 D、R14，R0

110、在 ARM 体系结构中，要从主动用户模式（User）切换到超级用户模式（Supervisor），应采用何种方法？C
A、直接修改 CPU 状态寄存器（CPSR）对应的模式
B、先修改程序状态备份寄存器（SPSR）到对应的模式，再更新 CPU 状态
C、使用软件中断指令（SWI）
D、让处理器执行未定义指令

111、表达式 A⊕B 实现的功能是（C）
A 逻辑与 B 逻辑非 C 逻辑异或 D 逻辑或

112、嵌入式系统的开发通常是在交叉开发环境实现的，交叉开发环境是指( A )
A 在宿主机上开发，在目标机上运行 B 在目标机上开发，在宿主机上运行
C 在宿主机上开发，在宿主机上运行 D 在目标机上开发，在目标机上运行

113、在 ARM 系统结构中，MMU 映射最小的单元空间是**D**
A、64KB B、16KB C、4KB D、1KB

114、在 ARM Linux 启动的过程中，开启 MMU 的时候，如何实现从实地址空间到虚拟地址空间的过度？D
A、开启 MMU，在内存中创建页表（映射内核到 3G 以上的虚拟地址空间）并继续运行。
B、开启 MMU，在内存中创建页表（映射内核到 3G 以上的虚拟地址空间），跳转到虚拟地址空间继续运行。
C、在内存中创建页表（映射内核到 3G 以上的虚拟地址空间），开启 MMU，跳转到虚拟地址空间继续运行。
D、在内存中创建页表（映射内核到 3G 以上的虚拟地址空间，同时把内核所在的前 1MB 空间到和其实地址相同的虚拟地址空间），开启 MMU，跳转到虚拟地址空间继续运行。

115、在 ARM 体系中，MMU 的第一级描述符有**\_项，每个描述符占用\_\_**字节
A、1024，32 B、4096，4
C、4096，4 D、1024，32
答案：C（B 和 C 一样的，A 和 D 是一样的）

116、在 ARM 体系中，下面 MMU 的一级描述符中，是节描述符的是\_A\_\_\_
A、0xA0000C0E B、0xA0000C0F
C、0x00000000 D、0xC0000C01

117、在 ARM Linux 体系中，用来处理外设中断的异常模式是\_C**\_**
A、软件中断（SWI） B、未定义的指令异常
C、中断请求（IRQ） D、快速中断请求（FIQ）

118 、指令 ADD R2,R1,R1,LSR #2 中，LSR 的含义是（B）。  
A 逻辑左移 B 逻辑右移 C 算术右移 D 循环右移

119、以下 ARM 异常中，优先级最高的是（D ）。  
A Data abort B FIQ C IRQ D Reset

120、指令 LDR R0,[R4]对源操作数的寻址方式是（ A ）  
A 寄存器间接寻址 B 寄存器寻址 C 立即数寻址 D 相对寻址

121、在 Linux 2.4 或者 2.6 内核中，和 ARM 体系结构相关的中断处理程序的 C 代码在源码树的\_*B*文件中
A、kernerl/irq.c
B、arch/arm/kernel/irq.c
C、arch/arm/mach/irq.c
D、arch/arm/kernel/entry-armv.S

122、以下关于 init 进程，描述不正确的是：（A）
A. 一个通用进程
B. 可以产生新的进程
C. 在某些程序退出的时候能重起它们
D. 负责在系统启动的时候运行一系列程序和脚本文件

123、哈佛结构和冯诺依曼结构的区别是( A)
A 指令和数据分开存储 B 不需要程序计数器 C 统一编址 D 单一数据总线

124、fstab 文件存放在（A）目录中。
A．/etc B．/boot
C．/sbin &
