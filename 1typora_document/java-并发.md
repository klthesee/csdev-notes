juc

semaphore
release调用链
// 这里已经到了底层 native方法了 unsafe声明的是native
unsafe.compareAndSwapInt(this, stateOffset, expect, update); 
compareAndSetState:566, AbstractQueuedSynchronizer (java.util.concurrent.locks) 
tryReleaseShared:193, Semaphore$Sync (java.util.concurrent)
releaseShared:1341, AbstractQueuedSynchronizer (java.util.concurrent.locks)
release:426, Semaphore (java.util.concurrent)
run:37, SemaphoreDemo$MyThread (com.zk.concurrent)

acquire调用链：（非公平锁）
tryAcquireShared:229, Semaphore$NonfairSync (java.util.concurrent)
acquireSharedInterruptibly:1303, AbstractQueuedSynchronizer (java.util.concurrent.locks) //是否需要加入到chl
~~~
    public final void acquireSharedInterruptibly(int arg)
            throws InterruptedException {
        if (Thread.interrupted())
            throw new InterruptedException();
        if (tryAcquireShared(arg) < 0) //sem的判断逻辑
            doAcquireSharedInterruptibly(arg); // 加入到chl
    }
~~~
~~~
        protected int tryAcquireShared(int acquires) {  //重写
            return nonfairTryAcquireShared(acquires); // sem写的
        }
~~~
acquire:312, Semaphore (java.util.concurrent)
run:24, SemaphoreDemo$MyThread (com.zk.base)

-------------------------
这里判断是否获取锁，如果获取了则继续执行业务代码，否则进入CLH队列 
~~~
    public final void acquireSharedInterruptibly(int arg)
            throws InterruptedException {
        if (Thread.interrupted())
            throw new InterruptedException();
        if (tryAcquireShared(arg) < 0) // 未获取到则进入等待队列，否则不会进入这个if，继续执行
            doAcquireSharedInterruptibly(arg); // 进入注释队列
    }
~~~
唤醒线程，调用的是底层的unsafe类去唤醒
~~~
    public static void unpark(Thread var0) {
        if (var0 != null) {
            UNSAFE.unpark(var0);
        }

    }
~~~

获取锁方法：如果还有锁能够获取
~~~
    final int nonfairTryAcquireShared(int acquires) {
        for (;;) {
            int available = getState();
            int remaining = available - acquires;
            if (remaining < 0 ||
                compareAndSetState(available, remaining))
                return remaining;
        }
    }

--->    protected final boolean compareAndSetState(int expect, int update) {
            // See below for intrinsics setup to support this
            return unsafe.compareAndSwapInt(this, stateOffset, expect, update);
        }
~~~

判断CLH队列是否有等待线程
~~~
    public final boolean hasQueuedPredecessors() {
        // The correctness of this depends on head being initialized
        // before tail and on head.next being accurate if the current
        // thread is first in queue.
        Node t = tail; // Read fields in reverse initialization order
        Node h = head;
        Node s;
        return h != t &&
            ((s = h.next) == null || s.thread != Thread.currentThread());
    }
~~~


原子类

并发容器

线程池



资料
xingshaocheng/architect-awesome