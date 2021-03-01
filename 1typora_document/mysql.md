 1. mysql主从配置
 server-id=1        #数据库唯一ID，主从的标识号绝对不能重复。
 log-bin=mysql-bin    #开启bin-log，并指定文件目录和文件名前缀
 binlog-do-db=liting　  #需要同步liting数据库。如果是多个同步库，就以此格式另写几行即可。如果不指明对某个具体库同步，就去掉此行，表示同步所有库（除了ignore忽略的库）。
 binlog-ignore-db=mysql  #不同步mysql系统数据库。如果是多个不同步库，就以此格式另写几行；也可以在一行，中间逗号隔开。
 sync_binlog=1      ＃确保binlog日志写入后与硬盘同步
 binlog_checksum=crc32  ＃跳过现有的采用checksum的事件，mysql5.6.5以后的版本中binlog_checksum=crc32,而低版本都是binlog_checksum=none
 binlog_format=mixed   ＃bin-log日志文件格式，设置为MIXED可以防止主键重复。