https://segmentfault.com/a/1190000041229788

###### Android 四大组件相关

Activity 与 Fragment 之间常见的几种通信方式？

LaunchMode 的应用场景？

> https://blog.csdn.net/hequnwang10/article/details/124955649

BroadcastReceiver 与LocalBroadcastReceiver 有什么区别？

> https://www.jianshu.com/p/36dbff3516bc
>
> BroadcastReceiver是针对应用间、应用与系统间、应用内部进行通信的一种方式
> LocalBroadcastReceiver仅在自己的应用内发送接收广播，也就是只有自己的应用能收到，数据更加安全广播只在这个程序里，而且效率更高。

对于 Context，你了解多少?

> 应用的上下文，这里整理了一张`Context`的继承关系类图，从这个图中可以看出，`Context`是一个接口，`ContextImp`和`ContextWrapper`都是其实现类，我们常用的`Activity`、`Service`、`Application`都直接或间接继承自`ContextWrapper`

IntentFilter是什么？有哪些使用场景？

> 过滤器么，注册广播监听的时候比较常用

谈一谈startService和bindService的区别，生命周期以及使用场景？

> ### startService 和bindService 区别
>
> startService： onCreate -> onStartCommand -> onDestory ，在多次调用startService的时候，onCreate不重复执行，但是onStartCommand会执行。startService调用了这后，会一直存在，直到其调用了stopService。
>  bindService :   onCreate -> onBind -> onUnbind -> onDestory，多次调用bindService，onCreate及onBind都只执行一次。它生命周期跟随其调用者，调用者释放的时候，必须对该Service解绑，当所有绑定全部取消后，系统即会销毁该服务。 bindService 的方式通过onServiceConnected方法，获取到Service对象，通过该对象可以直接操作到Service内部的方法，从而实现的Service 与调用者之间的交互。

Service如何进行保活？

> 极端一点我直接给app进程保活，设置预装的属性

**简单介绍下ContentProvider是如何实现数据共享的？**

> 

说下切换横竖屏时Activity的生命周期?

> 这个我最近还真有测试过，

Activity中onNewIntent方法的调用时机和使用场景？

> **singleTop**(栈顶复用模式): **singleTask**(栈内复用模式): 启动的Activity 会出发这个回调的

Intent传输数据的大小有限制吗？如何解决？

> 且被限制在`1MB`左右，不同机型大小不同。
>
> 解决方案就是不传大的数据，大的数据用其他方案解决，本身Intent也不是用来传大数据的

**说说ContentProvider、ContentResolver、ContentObserver 之间的关系？**

**说说Activity加载的流程？**

###### Android 异步任务和消息机制

HandlerThread 的使用场景和用法？

https://www.jianshu.com/p/5ce05c8edcdd

https://blog.csdn.net/u011240877/article/details/72905631

IntentService 的应用场景和使用姿势？

https://github.com/Moosphan/Android-Daily-Interview/issues/25

AsyncTask的优点和缺点？

https://github.com/Moosphan/Android-Daily-Interview/issues/28

谈谈你对 Activity.runOnUiThread 的理解？
子线程能否更新UI？为什么？
谈谈 Handler 机制和原理？
为什么在子线程中创建Handler会抛异常？
试从源码角度分析Handler的post和sendMessage方法的区别和应用场景？
Handler中有Loop死循环，为什么没有阻塞主线程，原理是什么?

https://www.jianshu.com/p/c7b87f8ed0c7

###### Android 性能调优相关

谈谈你对Android性能优化方面的了解？
一般什么情况下会导致内存泄漏问题？
自定义 Handler 时如何有效地避免内存泄漏问题？
哪些情况下会导致oom问题？
ANR 出现的场景以及解决方案？
谈谈Android中内存优化的方式？
谈谈布局优化的技巧？
Android 中的图片优化方案？
Android Native Crash问题如何分析定位？
谈谈怎么给apk瘦身？
谈谈你是如何优化App启动过程的？
谈谈代码混淆的步骤？

###### Android 中的 IPC

请回答一下Android进程间的通信方式？
请谈谈你对Binder机制的理解？
谈谈 AIDL？
