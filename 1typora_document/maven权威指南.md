<<maven权威指南>>



## 章10：构建生命周期

1.clean：删除当前mudule下target目录下的所有文件![image-20201202164513005](G:\_document\1typora_document\maven权威指南.assets\image-20201202164513005.png)

还可以自定义clean文件

~~~
<project>
<modelVersion>4.0.0</modelVersion>
...
<build>
    <plugins>
        <plugin>
            <artifactId>maven-clean-plugin</artifactId>
            <configuration>
                <filesets>
                    <fileset>
                        <directory>target-other</directory>
                        <includes>
                            <include>*.class</include>
                        </includes>
                	</fileset>
            </filesets>
            </configuration>
        </plugin>
    </plugins>
</build>
</project>
~~~

