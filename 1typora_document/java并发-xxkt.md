

# 并发实战



处理结果返回一个`实体类`，实体类里包含`枚举类型的TaskResultType`、数据、返回信息。

~~~java
public enum TaskResultType{
    SUCCESS,FAILURE,EXCEPTION;
}

public class TaskResult<R> {
    private final TaskResultType resultType;
    private final R returnValue;
    private final String reason;
    
    public TaskReuslt(TaskResultType resultType,R returnValue,String reason){
        this.resultType = resultType;
        this.returnValue = returnValue;
        this.reason = reason;
    }
    public TaskReuslt(TaskResultType resultType,R returnValue){  // 大多数可能返回的成功的结果，重载两个参数的
        this.resultType = resultType;
        this.returnValue = returnValue;
        this.reason = "success";
    }
    
}
~~~



