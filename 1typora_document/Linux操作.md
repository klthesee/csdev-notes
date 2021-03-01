
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


Linux 查看配置



