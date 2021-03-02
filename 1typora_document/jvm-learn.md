# jvm各参数意思

1. verbose:gc
2. -XX:+printGC
3. -XX:+printDetails
4. -XX:+printGCTimeStamps



nacos中相关jvm参数

![image-20210130224558952](jvm-learn.assets/image-20210130224558952.png)

sed -i 's/\r$//' ./startup.sh

~~~shell
/usr/local/java/jdk1.8.0_161/bin/java  -server -Xms2g -Xmx2g -Xmn1g -XX:MetaspaceSize=128m -XX:MaxMetaspaceSize=320m 
发送oom堆栈存放位置
-XX:-OmitStackTraceInFastThrow -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/usr/local/nacos/logs/java_heapdump.hprof
 -XX:-UseLargePages 

-Dnacos.member.list= -Djava.ext.dirs=/usr/local/java/jdk1.8.0_161/jre/lib/ext:/usr/local/java/jdk1.8.0_161/lib/ext 
gc日志存放位置
-Xloggc:/usr/local/nacos/logs/nacos_gc.log -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintGCTimeStamps -XX:+UseGCLogFileRotation -XX:NumberOfGCLogFiles=10 -XX:GCLogFileSize=100M

 -Dloader.path=/usr/local/nacos/plugins/health,/usr/local/nacos/plugins/cmdb -Dnacos.home=/usr/local/nacos -jar /usr/local/nacos/target/nacos-server.jar  --spring.config.additional-location=file:/usr/local/nacos/conf/ --logging.config=/usr/local/nacos/conf/nacos-logback.xml --server.max-http-header-size=524288

~~~




# 2.理论+实战 构建完整JVM知识体系
