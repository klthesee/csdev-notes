# ruoyi-common

## ruoyi-common-core

1.ruoyi-common-core模块已经有spring依赖，但是引用它的模块可能没有扫描到这个包，所以需要用spi中使用spring类加载器加载指出。
![image-20201221101951782](G:\_document\1typora_document\ruoyi.assets\image-20201221101951782.png)



#### 熔断和降级

- nacos-discovery 和 openfeign包含了hystrix

![image-20210302162628797](C:\Users\OO\Desktop\test\csdev-notes\1typora_document\github-ruoyi.assets\image-20210302162628797.png)
![image-20201221101951782](G:\_document\1typora_document\ruoyi.assets\image-20201221101951782.png)
