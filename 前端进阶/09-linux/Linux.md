# Linux
	lamp----Linux   Apache   MySql  PHP
## linux目录
	文件地址分隔符：  '/'
	'/':表示盘的最顶层根目录
	
	/bin： 存放的一些二进制文件，linux中二进制文件可以直接执行，这个目录里面的命名文件是给普通用户使用的

	/etc: Linux的配置文件都会存放在这个里面
	/etc/passwd：存储用户的关键信息
	/etc/group :存储用户组的关键信息
	/etc/shadow:存储用户的密码信息

	/home: 所有非root用户家目录的一个集合 类似于window中的user

	/root: root用户的家目录

	/sbin(shell bin): 里面同样类似于bin目录，里面存放二进制文件，这些命令只能给root用户使用

	/usr: 用户自己安装的一些文件，其实类似于window下的program(程序) File目录

	/var: 存放的是linux下的日志文件，实际开发中有一些公司习惯把Apache和Neginx的站点目录放在这个目录里面

	/boot: linux引导启动的时候使用的文件

	/proc: 存放的是当前正在运行的进程 按照进程id命名目录  断电后就丢失

	/lost+found: 存放意外情况丢失的文件

## shell终端
	常见的shell	
		Csh、tcsh、zsh、bash(linux是这个).....
	
	root@localhost root用户在本机上  
	'#'表示当前用户的身份 目前是超级管理员
	'$' 表示当前用户是普通用户
	
	Linux严格区分大小写

##基本指令 []表示可写可不写  
	通用语法格式：# 指令名称 [选项] [操作的最终目标]  
	1. 简单指令
		1. ls [路径] ：列出指定目录下所有的文件以及文件夹
		2. ls -l [路径] ：列表的形式列出指定目录下所有的文件以及文件夹
		3. ls -la [路径] ：列表的形式列出指定目录下所有的文件以及文件夹[包括隐藏文件 特点是以'.'开头]
		4. clear ：清除当前界面的命令  其实没有清空，只是顶到上边去了
		5. su [用户名] ：切换用户  不写就默认切换到超级用户(root)
		6. cd 需要切换到的路径  ： 切换到指定路径，但是低权限用户不能切换到高权限目录
		7. pwd (print working directory)：打印当前的工作路径
			
	2. 文档指令
		1. touch 路径文件的名字  ：在该目录下创建一个文件 当前路径下创建文件  touch ./php.txt
		2. mkdir 文件路径 ：创建文件夹目录
		3. cp(copy) [-r] 需要复制的文件 需要保存的位置路径:复制文件   cp xxx /home/admin/ 复制到admin的家目录下
			选项说明: -r 递归 把一个文件夹所有的东西都复制过去,如果复制文件夹，-r是必须的  复制文件夹
			
		4. mv(move 剪切+粘贴) 需要移动的文档 需要移动到的文件夹: 移动文件
		5. mv(move 剪切+粘贴) 需要重命名的文档 新名字: 重命名
		6. rm [-rf] 需要删除的文档: 删除文档   r--递归   f--强制
			-rf 删除文件夹的时候加上这个选项
	

	3. 文档内容查看指令
		1. tail [n] 文件的路径 : 查看一个文件的末n行  n可以不写，默认10行
		2. head [n] 文件的路径 : 查看一个文件的头n行  n不写默认10行
		3. cat 文件路径1 文件路径2 文件路径3... : 查看某个文件的全部内容(将内容全部输出到命令行中  正序)
		4. tac 文件路径1 文件路径2 文件路径3 :查看某个文件的全部内容 倒序 
		5. vim : 打开一个文件显示内容 
	

	4. 关机和重启的指令
		1. reboot ：重启系统  普通用户无法使用reboot指令：自开机一来只有一个普通用户登录过
		2. shutdown -h 时间 :关闭系统  
			时间：now---立即关机  +m---m表示分钟数,+m表示m分钟之后关机
					
		3. halt： 关闭内存，也就是关机

## 进阶指令
	1. du(directory used) [-sh] 目录：  显示出目录所占磁盘空间大小的情况
		-s sumary----汇总统计   -h---以较高可读性的形式显示

	2. df(disk free) [-m] : 查看磁盘剩余情况
		-m---以MB为单位进行查看   -h---以较高可读性查看剩余空间

	3. free [-m]：查看内存的使用情况  区分可用内存  和 剩余的内存
		-m---以MB为单位进行查看  swap ---内存不够用时，使用硬盘预留的空间作为内存使用

	4. find [56个选型...] ：表示根据条件查询文档的所在位置
		语法：find 范围 选项 关键词 --- 与通用语法格式有点区别
			 -name---根据名字进行查询  支持通配符'*',也就是模糊查询
			 -type---根据文档类型进行查询[d：文件夹、f：文件、s：套接字、l：连接文件、c：字符设备文件、d：块状设备文件]
			 -size---根据大小
			 -user---根据使用者
			 -group--根据分组

		例子：查询.conf的文件--------find / -name *.conf -type f

	5. ps (process show) [-ef]：查看进程
		-ef<==>A ----- 表示全部
		-f ----- 显示全部的列
		UID：该进程的启动用户名
		PID：进程的id号
		P PID：父级进程ID
		C：cpu的使用情况
		STIME：进程开始时间
		TTY：终端的设备编号 '?'代表不是由终端(命令行那个执行框就是终端编号)发起的
		TIME：持续运行的时间 基本无意义
		CMD：进程的名称或者位置

	6. service ：用来操作服务，包括 启动、停止、重启
		语法：service 服务名 start/stop/restart
		注意：要求服务名必须存在于'/etc/init.d'目录下
		ps：开启服务的另外一种方式 /etc/init.d/服务 start/stop/restart

	7. grep：搜索过滤 用于对于文件或者内容进行筛选，选出需要的内容
		语法：grep [选项] "关键字" 文档路径
			 -v --- 排除
			 -E(extension) "关键词1|关键词2|..." 文档路径 -- 表示多条件筛选

		-E...  <====>  egrep "关键词1|关键词2|..." 文档路径 --- 

	8. wc：用于统计文件的各项数值  包括 行、单词数、字节数
		语法：wc -lwc 文档路径 ---- -l：行数   -w：单词数  c：字节数  可单独用
	
	9. 管道
		严格来说并不是指令，只是一个符号"|",主要起到辅助作用，能够将多个指令合并在一行上进行操作，主要用于搜索过滤上面
		语法：指令1|指令2...  指令1必须是能在终端中有输出的指令才行|指令2必须能够读取文件的内容

		核心：管道前面指令的输出其实就是管道后面指令的输入

## Vim编辑器
	vi：Linux下标准的编辑器
	vim：vi的高级版本，vi用于文本编辑  vim可以用来编辑coding

	1. 3种模式
		命令模式：不能对文件直接编辑，可以输入快捷键进行一些操作(删除行、复制行、移动光标、粘贴...)
		编辑模式(输入模式)：可以对文件内容直接操作编辑
		末行模式(尾行模式)：可以在末行输入命令来对文件进行操作

	2. vim打开文件
		vim 文件路径：打开指定的文件
		vim +数字  文件路径 -- 打开指定位置，并且光标移动到指定行
		vim +/关键词 文件路径 -- 打开指定位置，并且高亮显示关键字
			 		
### 命令模式
	1. 移动到当前行的行首      shift+6/^   
	2. 移动到当前行的尾部      shift+4/$  与正则有关
	3. 光标移动到首行的行首    gg
	4. 光标移动到末行的行首    G
	5. 向上翻屏        ctrl+b /PgUp
	6. 向下翻屏        ctrl+f /PgDn
	7. 快速定位到指定行    数字 G
	
	8. 复制光标所在行    yy  粘贴的时候按'p/P'键
	
	9. 以光标所在行为准，复制指定的行数    数字 yy
	
	9. p粘贴在光标所在行之后   P(大写)粘贴在光标所在行之前

	10. 剪切/删除光标所在行    dd 删除之后下一行上移

	11. 剪切/删除包括光标所在行以后的n行     n dd

	12. 剪切/删除之后下一行不上移     D

	13. 撤销       ':u  /  u'

	14. 恢复之前的撤销操作   ctrl+r

### 三种模式的切换
	命令 -> 末行   输入:(英文状态)
	末行 -> 命令   1.按一下esc  2.按两下esc  3.删除末行中的全部命令

	命令 -> 编辑   i、a .....
	编辑 -> 命令  按一下esc  

	编辑与末行没有办法直接切换，先转换成命令模式再说

	末行模式特征：光标在最后
	编辑模式特征：出现 类似'插入/insert'

### 末行模式
	1. :w --- 保存文件
	2. ":w 文件路径" ---- 另存为
	3. :q ----- 退出文件  
	4. :wq ----- 保存并退出
	5. :q! ------ 强制退出不保存
	6. /关键词  ---- 搜索查找
	7. N/n ---- 搜索出来的关键字 上一个(N)/下一个(n)切换  
	8. :%s/搜索的关键词/新替换的内容/g  ----- 替换整个文档符合条件的内容
	9. :set nu ----- 显示行号
	10. :set nonu ---- 取消行号
		要想永久显示行号： "vim  ~/.vimrc" ->输入模式 set nu 保存 (改变的是对于用户来说)

	11. :开始行号,结束行号 co 粘贴到的行号 ---- 一步到位的复制粘贴语法
	12. :开始行号,结束行号 m 粘贴到的行号 ----- 一步到位的剪切粘贴语法

	13. 异常退出
		 编辑过得文件并没有走正常流程保存的时候就属于异常退出
		 删除'xx.swp'文件即可
	
## 用户和用户组
	Linux是一个多用户多任务的操作系统
	每个用户都拥有一个唯一的用户名和各自的密码
	用户的增加、删除、修改和用户密码的管理

### 用户管理
	1. useradd [选项] 用户名 --- 添加用户
		-g 指定用户的主(主要)组     亲生父母 主组有且只能有一个
		-G 指定用户的附加(额外)组   干爹干妈
		-u uid,用户的id，系统会默认分配(从500开始)，也可以自定义
		-c comment,添加注释
		-s 指定用户登录后所使用的shell解释器[专门的接待员]  比如：/sbin/nologin 无法登陆
		-d 指定用户登入时的起始目录(家目录)
		-n 取消建立以用户名称为名的群组

	2. 验证用户是否存在
		tail -1 /etc/passwd  

	3. usermode 选项 用户名 ----- 用户的修改
		-g 指定用户的主(主要)组     亲生父母 主组有且只能有一个
		-G 指定用户的附加(额外)组   干爹干妈
		-u uid,用户的id，系统会默认分配(从500开始)，也可以自定义
		-c comment,添加注释
		-s 指定用户登录后所使用的shell解释器[专门的接待员]  /sbin/nologin 无法登陆
		-d 指定用户登入时的起始目录(家目录)
		-n 取消建立以用户名称为名的群组
		-l 修改用户名

	4. 用户密码设置
		passwd [用户名] ：如果不带用户名就是修改自己的密码

	5. 用户的删除
		userdel 选项 用户名
			-r ----- 删除用户的时候将其家目录一起删除
		已经登录过得用户删除的时候会失败 --- 
			1、可以先 'kill 进程id' ，然后再执行'userdel 用户名'删除
			2、先'su 用户'  然后'ctrl+d' 然后再执行 'userdel 用户名'

	6. 用户组管理
		增加、删除、修改就是操作 /etc/group文件
		
		group文件格式：用户组:密码:用户组id:组内用户名

		1、用户组添加 --- groupadd 选项 用户组名
			-g --- 表示自己设置一个自定义的用户组ID数字，如果自己不指定从500开始递增

		2、用户组编辑 --- groupmod 选项 用户组名
			-g 修改用户组ID
			-n 设置新的用户组名字

		3、用户组的删除 ---- groupdel 用户组名
			删除的时候不能是任何用户的主组，附加组可以，要想删除，先移除所有的用户

	ps：除了passwd普通用户可以执行，其他的需要管理员用户才可以执行
			
	
## 权限
### Linux权限概念
	1. 读权限
	
	2. 写权限
		对于文件夹来说，代表是否在该文件夹中“创建/删除/复制到/移动到”操作
	3. 执行权限
		对于文件来说，特别是脚本文件，影响是否可以执行这个文件
		对于文件夹来说，影响是否能在该文件夹中执行指令

### 身份介绍
	Linux是多用户、多任务的操作系统
	1. Root 超级用户  神一样的用户，拥有最高权限
	2. Owner 身份 (文档的所有者。默认是文档创建者)
	3. group 身份 (与文档所有者同一组的用户)
	4. others 身份 (其他人，除了文档所有者和用户组)
		理解：一套房子有大明、二明、三明，房产证上写的大明(Owner) ，大明一家就是一个用户组，这时来了个张三，张三跟他们都没有关系，就属于others，大明几个人都有自己的房间，每个人可以自由进出自己的房间，但是大明可以不让小明看到自己的私密空间，这就是文档所有者的定义

### Linux权限查看
	ls -l 路径	 ls -l等同于'll'

	权限属性定义：
		drwxrwx---
			 第一位表示文档类型('d-- 文件夹'、'-表示文件'、'i表示软连接'、's表示套接字'、'c表示字符设备'、'b表示块装设备')
			 r:读权限  w:写权限  x:执行权限 execute  这三个位置时固定的，不会改变
			 2-4位：表示文档所有者权限
			 5-7位：表示文件所属用户组权限
			 8-10位：表示其他人的权限	

### Linux权限操作
	1. 权限设置 
		语法：chmod [选项] 权限模式 文档路径
			-R :递归设置权限
			权限模式 ：就是该文档需要设置的权限信息
			文档：可以是文件，也可以是文件夹，可以是相对路径，也可以是绝对路径
		ps：文档所有者和root用户才能给该文档设置权限

		权限信息选项1--字母形式
			给谁设置：	u - 给文档所有者设置权限
						g - 给所有者同组用户设置权限
						o - 给其他人设置权限
						a - 给所有用户设置权限
			权限分配方式：
				+ - 相对增加权限
				- - 相随减少权限
				= - 表示将权限设置为具体的值
			设么权限：
				r - 读
				w - 写
				x - 执行
				- - 没有权限
		设置多个身份权限的时候，每个身份之间需要使用','隔开
	ps：给/root/anaconda-ks.cfg文件(-rw-------)设置权限，要求文件所有者拥有全部权限，所有者同组用于读写权限，其他人只有读权限
		chmod u+x,g+rw,o+r /root/anaconda-ks.cfg 或者 chmod u=rwx,g=rw,o=r /root/anaconda-ks.cfg		

		权限信息选项2--数字形式
			r - 4  w - 2   x - 1  没有任何权限 - 0   所有权限：4+2+1 = 7
			chmod 764 /root/anaconda-ks.cfg  与上面ps的结果等同  
			单独出现2，3的权限是有问题的，因为写权限必须要读权限，这是奇葩的权限设定

		权限设置注意事项：
			创建文件夹默认权限是755  创建文件的的默认权限是644

	属主和属组
		属主：文档所有者
		属组：所属的用户组

	2. chown 
		更改文档的所属用户
		语法：chown [-R] 新的username:groupname 文档路径 同时修改所属用户以及用户组
			 -R - 递归 使用文件夹的时候使用
		ps：修改的人必须是文档所有者或者root

	3. chgrp  --- 了解
		更该文档的所属用户组
		语法：chgrp [-R] groupname 文档路径

	4. sudo
		管理员允许普通用户执行一些或者全部的root命令
		visudo -- 打开配置文件 98行附近  添加用户权限
		ps：root ALL=(ALL 以xx的身份运行指令) 指令位置(多个指令之间使用','隔开) 
		- 查看命令路径  which 命令名称
		- 执行命令时需要加上 sudo xxx
		- sudo -l 查看当前用户可以使用什么sudo指令

	5. 运行级别 -- 运行模式
		Linux存在一个进程：init，进程id=1  ，位于/etc/inittab  运行级别就在里面
		0 - 关机模式
		1 - 单用户模式 找回root密码
		2 - 多用户模式 不带NFS 与3类型就是不带网
		3 - 完全的多用户模式 不带图形化界面，纯命令行
		4 - 保留模式 没有使用到的
		5 - x11 带桌面的模式
		6 - 表示重启级别 不要将默认的运行级别设置为这个值

		与这些级别对应的命令
		  1、临时设置，立即生效
			init0   init1   init2  init3   init4  init5   init6  需要超级管理员模式

### 网络设置
	1. 查看ip地址 远程连接、配置相关软件
		指令：ifconfig  inet addr 就是ip地址
		
	2. 网卡配置文件
		位置：/etc/sysconfig/network-scripts/ifcfg-*文件
		mac地址：计算机之间的通信都是通过mac地址，因为不好记所以使用ip地址，使用之前通过ip地址寻找mac地址

		ps：针对像网卡配置目录层次比较深的文件，如果需要频繁修改，可以放置一个快捷方式
			语法：ln -s  原始路径 快捷方式路径
		
	3. 网络服务操作  不要随便在服务器上用
		语法：service network start/stop/restart  操作所有网卡
			 单网卡：ifdown 网卡名  关闭网卡
					ifup 网卡名    开启网卡

### SSH 
	安全外壳协议(secure shell) 远程连接 、远程文件传输
	默认端口号：22 可修改  /etc/ssh/ssh_config
	ssh服务管理 --  service sshd start/stop/restart
	1. 远程连接
		运维人员连接远程服务器的shell终端 putty xshell

	2. 远程文件传输
		filezilla 应用
		sftp  ssh文件传输协议

## 软件的安装
	软件的管理方式有三种:rpm、yum、编译方式
	1. rpm 
		对于软件包的操作比较方便，通过简单指令即可操作，无法解决依赖关系
		语法：
			1. 查询 -> rpm -qa 关键词 -q:query  -a:all  查询有没有按装某软件
			2. 卸载 -> rpm -e 软件包全称 [--nodeps 忽略依赖关系]  e:卸载
			3. 安装 -> rpm -ivh 软件包路径  i:install   -v:显示安装过程   -h：以'#'的形式显示安装过程
			4. 更新 -> rpm -Uvh 软件包路径  U:Update    -v:显示安装过程   -h：以'#'的形式显示安装过程
	
	2. yum 
		优点：自动从服务器上下载包安装，自动解决依赖关系
		缺点：缺失对软件的自定义功能
		语法：
			1. 搜索 -> yum search [all] 关键词  根据关键词搜索可安装的包
					   yum list [关键词]  列出服务器上的包
					   yum list installed [关键字] 列出已经安装的包

			2. 安装 -> yum [-y] install 关键词  安装指定的软件
			3. 卸载 -> yum [-y] remove  关键词  卸载指定的软件
			4. 更新 -> yum [-y] update  [关键词 不带这个更新整个系统，包括内核] 
			
	3. 编译安装 --- 难点
		ps:编译安装Nginx
			开源的web服务器软件

		
		1. 下载压缩包 wget 地址 
		2. 解压压缩包 tar -jxvf 路径 (针对.tar.bz2格式)    tar -zxvf 路径 (针对.tar.gz格式) 
		3. 进入解压后的目录
		4. 配置安装  指定安装的位置、需要的模块功能
			指定位置：./绿色的文档 --prefix=/usr/local/nginx
		5. 编译&安装
	
## Lamp安装
	pam安装顺序来
	yum install php
	yum install mysql-server

	mysql初始化:
		service mysqld start     启动mysql
		mysql_secure_installation

	apache启动
		service httpd start

	安装好的apache默认站点在"var/www/html"
	Apache配置文件在 /etc/httpd/conf/httpd.conf中

## 扩展
	1. 回到命令首部  ctrl+a
	2. 去命令尾部    ctrl+e
	3. mstsc:window远程桌面连接命令

## Linux常用软件安装

### git工具
	1. 先git --version 查看git版本号
	2. 如有 yum remove git
	3. 下载 wget https://github.com/git/git/archive/v2.17.0.tar.gz
	4. 解压 tar -zxvf  本地压缩包
	5. 安装编译源码所需依赖 yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker
	6. 进入解压后的文件夹内部 cd git-2.17.0
	7. 编译 make prefix=/usr/local/git all
	8. 安装 make prefix=/usr/local/git install
	9. 配置环境 vim /etc/profile 
		PATH=$PATH:/usr/local/git/bin
		(当有多个PATH的时候：export PATH=$PATH:<PATH 1>:<PATH 2>:<PATH 3>:------:<PATH N>路径之间使用:隔开)
	
		export PATH
	10. 设置配置文件生效 source /etc/profile
	11. 查看安装git版本号 git --version  
	
### java工具
	1. 在/usr 目录下创建文件夹 mkdir java
	2. 下载压缩文件
		wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u141-b15/336fa29ff2bb4ef291e347e091f7f4a7/jdk-8u141-linux-x64.tar.gz"

	3. 解压 tar -zxvf xxx.tar.gz
	4. 配置环境 vim /etc/profile 
		JAVA_HOME=/usr/java/jdk1.8.0_191
		PATH=$PATH:$JAVA_HOME/bin
		CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
		export JAVA_HOME
		export PATH
		export CLASSPATH

	5. 设置配置文件生效 source /etc/profile
	6. 查看版本号 java -version

### php安装与卸载

	