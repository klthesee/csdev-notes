
一、Linux三剑客
sed、grep、awk
awk对数据进行分析并生成报告
sed编辑
grep查找


《循序渐进学Linux》
# ch3 
systemd命令和sysvinit命令对比

| |  ||
| --- | -- |-|
|service http start|systemctl start httpd.service|
|service http stop|systemctl stop httpd.service|
|serivce http restart|systemctl restart httpd.service|
|service httpd reload| systemctl reload httpd.service|重新加载而不重启服务|
|service httpd restart|systemctl restart httpd.service |
|service httpd status|systemctl statuts httpd.service|
|chkconfig httpd on|systemctl enable httpd.service|
|chkconfig httpd|systemctl is-enable httpd.service|查看httpd是否启用|
|chkconfig --list|systemctl list-unit-files --type=service|
|chkconfig httpd --list|ls /etc/systemd/system/*.wants/httpd.serice|查看httpd在各个运行级别下是否启用
|chkconfig httpd --add|system deamon-reload|
|||


3. Linux 查看配置
一、linux CPU大小
  cat /proc/cpuinfo |grep "model name" && cat /proc/cpuinfo |grep "physical id"


说明：Linux下可以在/proc/cpuinfo中看到每个cpu的详细信息。但是对于双核的cpu，在cpuinfo中会看到两个cpu。常常会让人误以为是两个单核的cpu。
其实应该通过Physical Processor ID来区分单核和双核。而Physical Processor ID可以从cpuinfo或者dmesg中找到. flags 如果有 ht 说明支持超线程技术 判断物理CPU的个数可以查看physical id 的值，相同则为
二、内存大小

cat /proc/meminfo |grep MemTotal



三、硬盘大小
fdisk -l |grep Disk


四、 
uname -a # 查看内核/操作系统/CPU信息的linux系统信息命令

五、head -n 1 /etc/issue # 查看操作系统版本，是数字1不是字母L



六、cat /proc/cpuinfo # 查看CPU信息的linux系统信息命令





七、hostname # 查看计算机名的linux系统信息命令



八、lspci -tv # 列出所有PCI设备



九、lsusb -tv # 列出所有USB设备的linux系统信息命令

十、lsmod # 列出加载的内核模块

十一、env # 查看环境变量资源

十二、free -m # 查看内存使用量和交换区使用量

十三、df -h # 查看各分区使用情况

十四、du -sh # 查看指定目录的大小
十五、grep MemTotal /proc/meminfo # 查看内存总量
十六、grep MemFree /proc/meminfo # 查看空闲内存量
十七、uptime # 查看系统运行时间、用户数、负载
十八、cat /proc/loadavg # 查看系统负载磁盘和分区
十九、mount | column -t # 查看挂接的分区状态
二十、fdisk -l # 查看所有分区
二十一、swapon -s # 查看所有交换分区
二十二、hdparm -i /dev/hda # 查看磁盘参数(仅适用于IDE设备)
二十三、dmesg | grep IDE # 查看启动时IDE设备检测状况网络
二十四、ifconfig # 查看所有网络接口的属性
二十五、iptables -L # 查看防火墙设置
二十六、route -n # 查看路由表
二十七、netstat -lntp # 查看所有监听端口
二十八、netstat -antp # 查看所有已经建立的连接
二十九、netstat -s # 查看网络统计信息进程
三十、ps -ef # 查看所有进程
三十一、top # 实时显示进程状态用户
三十二、w # 查看活动用户
三十三、id # 查看指定用户信息
三十四、last # 查看用户登录日志
三十五、cut -d: -f1 /etc/passwd # 查看系统所有用户
三十六、cut -d: -f1 /etc/group # 查看系统所有组
三十七、crontab -l # 查看当前用户的计划任务服务
三十七、chkconfig –list # 列出所有系统服务
三十八、chkconfig –list | grep on # 列出所有启动的系统服务程序
三十九、rpm -qa # 查看所有安装的软件包
四十、cat /proc/cpuinfo ：查看CPU相关参数的linux系统命令
四十一、cat /proc/partitions ：查看linux硬盘和分区信息的系统信息命令
四十二、cat /proc/meminfo ：查看linux系统内存信息的linux系统命令
四十三、cat /proc/version ：查看版本，类似uname -r
四十四、cat /proc/ioports ：查看设备io端口
四十五、cat /proc/interrupts ：查看中断
四十六、cat /proc/pci ：查看pci设备的信息
四十七、cat /proc/swaps ：查看所有swap分区的信息


