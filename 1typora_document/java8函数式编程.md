

## Optional



# 章3 流

1.collect：将stream转成set、list、聚合等
Collectors.groupby();
Collectors.toList();
Collectors.toSet();

2.map：将这个集合的所有元素转成另一个类型进行输出。

![image-20201229142902127](G:\_document\1typora_document\java8函数式编程.assets\image-20201229142902127.png)

3.fillter：过滤该容器的元素，返回符合过滤规则的元素。

<img src="G:\_document\1typora_document\java8函数式编程.assets\image-20201229142913880.png" alt="image-20201229142913880" style="zoom:100%; " />



4.flatMap：将多个容器合并成一个进行输出。

5.reduce：拿 accumulator 和集合中的每一个元素做运算，再将运算结果赋给 accumulator ，最后
accumulator 的值就是想要的结果。

![image-20201229143632860](G:\_document\1typora_document\java8函数式编程.assets\image-20201229143632860.png)

