
# 章2 主机规划与磁盘分区

1. 磁盘在Linux中的dev文件名，与实际的插槽位置顺序无关。
如有两块磁盘分别插在SATA1、SATA5上
 SATA1 -- dev/sda
 SATA5 -- dev/sdb
 

 # 章17 认识系统服务
1. 所有服务启动脚本放在/etc/init.d
2. CentOS 7.x 以后，Red Hat 系列的 distribution 放弃沿用多年的 System V 开机启动服务的流程，而使用systemd的启动机制.
3.  systemd 的服务类型: .service .socket .target .mount .automount .path .timer
4. systemctl命令
systemctl 命令 服务名 
如 systemctl restart network
命令： start/stop/restart/reload/enable/status/is-active(是否在运行)/is-enable(开机有没有预设这个unit)
deamon当前状态: active(running)/active(exited)仅运行一次/active(waiting)/inactive
deamon预设状态：enabled/disable/static/mask