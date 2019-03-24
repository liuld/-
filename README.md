# 面试题总结
  # 1.linux运行级别
    运行级别0：关机
    运行级别1：单用户模式
    运行级别2：多用户文本状态(没有NFS)
    运行级别3：多用户文本模式(有NFS)
    运行级别4：系统未使用，保留
    运行级别5：图形模式
    运行级别6：重启
  # 2.linux启动过程
    加电自检，根据bios设定查找主引导记录来加载grub,然后根据grub加载指定的kernel，kernel加载驱动，
    挂在rootfs，初始化第一个init（centos7为systemd）进程，init进程根据设定的运行级别运行和停止相关的服务，之后启动终端等待用户登陆。
    开机加电BIOS自检———–>MBR引导———–>grub引导菜单———–>加载内核———–>启动init进程———–>读取inittab文件———–>启动mingetty进程———–>登录系统
  # 3.dns解析过程（www.baidu.com)
    1.检查本地hosts文件是否有记录，没有的话向指定的dns服务器发起请求（递归查询）
    2.dns服务器收到请求后先检查一下自己的缓存中有没有这个地址，有的话就直接返回，没有的话则向13个根域名服务器其中一台发起请求
    3.根域名服务器收到请求后，返回com域的ns服务器地址
    4.dns服务器向com域的ns服务器发起请求，com域的ns服务器返回baidu.com的NS服务器地址
    5.dns服务器向baidu.com服务器发起请求，baidu.com服务器返回www.baidu.com的ip地址
    6.dns服务器向客户端返回www.baidu.com的ip地址
