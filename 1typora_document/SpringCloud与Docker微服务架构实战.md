<<SpringCloud与Docker微服务架构实战>>

# 章12 docker入门

1.docker常用命令

1）搜索镜像：docker search xx
2）下载镜像：docker pull  xxx
3）列出已下载镜像：docker images 
4）删除本地镜像：docker rmi xxx

2.docker容器常用命令

- run : 新建容器并启动（主要是新建）
  -d 后台运行
  -P 随机端口映射
  -p 指定端口映射
  --network 指定网络模式

- ps 列出正在运行的容器
- stop 停止容器
- kill 强制停止容器
- start 开启容器
- restart
- attach或nsenter 进入容器
- rm 删除容器

# 章13 将微服务运行在docker上

指令一般格式：指令名称  参数

- ADD 复制文件

  ADD src  dest
  将src的文件复制到容器的dest目录下。src可以是相对路径或者url、压缩包

- ARG
  ` ARG <name>[=<value>]`

- CMD 容器启动命令、一个docker容器只有一条CMD命令，有多条时，只有最后一条生效。

- COPY 复制文件 与ADD类似

- ENTRYPOINT 入口点与CMD类似

- ENV 环境变量

- EXPOSE 暴露端口

- FROM 指定镜像，放在最前面，之后的指令都是根据该镜像进行操作

- LABEL 为镜像添加元数据
  ![image-20201215113258821](G:\_document\1typora_document\SpringCloud与Docker微服务架构实战.assets\image-20201215113258821.png)

- MAINTAINER 指定维护者信息

- RUN 

- USER 设置用户，该用户才能启动该容器

- VOLUME 指定挂载点，作用是持久化目录



# 章14 使用 docker compose编排微服务

