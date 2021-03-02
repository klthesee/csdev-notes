# << netty权威指南>>



## 章20：Java多线程编程在netty中的应用

ChannelOutboundBuffer如何对发送的总字节数进行计数和更新？

通过自旋更新

~~~java
long oldValue = totalPendingSize;
long newWriteBufferSize = oldValue + size;
while(!TOTAL_PENDING_SIZE_UPDATER(this,oldValue,newWriteBufferSize)){ //由于是多线程，可以上面的没有更新到，所以自旋执行，直到更新成功。
    oldValue = totalPendingSize;
    newWriteBufferSize = oldValue + size;
}
~~~





~~~java
    private static final AtomicLongFieldUpdater<ChannelOutboundBuffer> TOTAL_PENDING_SIZE_UPDATER = AtomicLongFieldUpdater.newUpdater(ChannelOutboundBuffer.class, "totalPendingSize");
    private volatile long totalPendingSize;
~~~

首先定义了一个volatile类型的totalPendingSize，然后定义了一个原子类型AtomicLongFieldUpdater的 TOTAL_PENDING_SIZE_UPDATER。实现totalPendingSize的线程安全。


compareAndSet

~~~java
        boolean b = TOTAL_PENDING_SIZE_UPDATER.compareAndSet(this, expect, newVal);
~~~

compareAndSet(属性所在的对象，预期值，要设置的值):

~~~java
    /**
     * Atomically sets the field of the given object managed by this updater
     * to the given updated value if the current value {@code ==} the
     * expected value. This method is guaranteed to be atomic with respect to
     * other calls to {@code compareAndSet} and {@code set}, but not
     * necessarily with respect to other changes in the field.
     *
     * @param obj An object whose field to conditionally set
     * @param expect the expected value
     * @param update the new value
     * @return {@code true} if successful
     * @throws ClassCastException if {@code obj} is not an instance
     * of the class possessing the field established in the constructor
     */
    public abstract boolean compareAndSet(T obj, int expect, int update);
~~~



线程池参数：

~~~java
    /**
     * Creates a new {@code ThreadPoolExecutor} with the given initial
     * parameters.
     *
     * @param corePoolSize the number of threads to keep in the pool, even
     *        if they are idle, unless {@code allowCoreThreadTimeOut} is set
     * @param maximumPoolSize the maximum number of threads to allow in the
     *        pool
     * @param keepAliveTime when the number of threads is greater than
     *        the core, this is the maximum time that excess idle threads
     *        will wait for new tasks before terminating.
     * @param unit the time unit for the {@code keepAliveTime} argument
     * @param workQueue the queue to use for holding tasks before they are
     *        executed.  This queue will hold only the {@code Runnable}
     *        tasks submitted by the {@code execute} method.
     * @param threadFactory the factory to use when the executor
     *        creates a new thread
     * @param handler the handler to use when execution is blocked
     *        because the thread bounds and queue capacities are reached
     * @throws IllegalArgumentException if one of the following holds:<br>
     *         {@code corePoolSize < 0}<br>
     *         {@code keepAliveTime < 0}<br>
     *         {@code maximumPoolSize <= 0}<br>
     *         {@code maximumPoolSize < corePoolSize}
     * @throws NullPointerException if {@code workQueue}
     *         or {@code threadFactory} or {@code handler} is null
     */
    public ThreadPoolExecutor(int corePoolSize,
                              int maximumPoolSize,
                              long keepAliveTime,
                              TimeUnit unit,
                              BlockingQueue<Runnable> workQueue,
                              ThreadFactory threadFactory,
                              RejectedExecutionHandler handler)
~~~

#### ch21:多线程编程在netty中的应用
