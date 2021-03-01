

使用model中使用枚举属性，对应数据库中的varchar

```sql
这个表d_tenant

  `connect_type` varchar(10) DEFAULT NULL COMMENT '链接类型\n#TenantConnectTypeEnum{LOCAL:本地;REMOTE:远程}',
`status` varchar(10) DEFAULT 'NORMAL' COMMENT '状态\n#{NORMAL:正常;WAIT_INIT:待初始化;FORBIDDEN:禁用;WAITING:待审核;REFUSE:拒绝;DELETE:已删除}',
```



~~~java
    @TableField("connect_type")
    @ApiModelProperty(value = "连接类型", example = "LOCAL,REMOTE")
    @Excel(name = "连接类型", width = 20, replace = {"本地_LOCAL", "远程_REMOTE", "_null"})
    private TenantConnectTypeEnum connectType;

    /**
     * 类型
     * #{CREATE:创建;REGISTER:注册}
     */
    @ApiModelProperty(value = "类型")
    @TableField("type")
    @Excel(name = "类型", width = 20, replace = {"注册_REGISTER", "创建_CREATE", "_null"})
    private TenantTypeEnum type;
~~~

