https://zhuanlan.zhihu.com/p/549380293

https://juejin.cn/post/7166415061089517582

#### 1 wait和 sleep 的区别

wait是Object的方法，wait是对象锁，锁定方法不让继续执行，当执行notify方法后就会继续执行，sleep 是Thread的方法，sleep 是使线程睡眠，让出cpu，结束后自动继续执行

#### 2 View和SurfaceView的区别

View基于主线程刷新UI，SurfaceView子线程又可以刷新UI

#### 3. View的绘制原理

View为所有图形控件的基类，View的绘制由3个函数完成 measure,计算视图的大小 layout,提供视图要显示的位置 draw,绘制

#### 4. 简述TCP，UDP，Socket

TCP是经过3次握手，4次挥手完成一串数据的传送 UDP是无连接的，知道IP地址和端口号，向其发送数据即可，不管数据是否发送成功 Socket是一种不同计算机，实时连接，比如说传送文件，即时通讯

#### 5.进程和线程的区别

概念：进程包括多个线程，一个程序一个进程，多线程的优点可以提高执行效率，提高资源利用率 创建：Thread类和Runnable接口， 常用方法有： start()用于启动线程 run()调用线程对象中的run方法 join()合并插队到当前线程 sellp()睡眠释放cpu资源 setPriority()设置线程优先级

#### 6.RecyclerView和ListView的区别

缓存上:前者缓存的是View+ViewHolder+flag，不用每次调用findViewById,后者则只是缓存View 刷新数据方面，前者提供了局部刷新，后者则全部刷新

#### 7.MVC ，MVP，MVVM

MVC:View是可以直接访问Model的！从而，View里会包含Model信息，不可避免的还要包括一些 业务逻辑。 在MVC模型里，更关注的Model的不变，而同时有多个对Model的不同显示，及View。所以，在MVC模型里，Model不依赖于View，但是 View是依赖于Model的。不仅如此，因为有一些业务逻辑在View里实现了，导致要更改View也是比较困难的，至少那些业务逻辑是无法重用的。 

MVP：MVP 是从经典的模式MVC演变而来，它们的基本思想有相通的地方：Controller/Presenter负责逻辑的处理，Model提供数据，View负 责显示。作为一种新的模式，MVP与MVC有着一个重大的区别：在MVP中View并不直接使用Model，它们之间的通信是通过Presenter (MVC中的Controller)来进行的，所有的交互都发生在Presenter内部，而在MVC中View会从直接Model中读取数据而不是通过 Controller。 

MVVM：数据双向绑定，通过数据驱动UI，M提供数据，V视图，VM即数据驱动层

#### 8.说下 Activity 跟 跟 window ， view 之间的关系？

Activity 创建时通过 attach()初始化了一个 Window 也就是PhoneWindow，一个 PhoneWindow 持有一个DecorView 的实例，DecorView 本身是一个 FrameLayout，继承于 View，Activty 通过setContentView 将xml 布局控件不断 addView()添加到 View 中，最终显示到 Window 于我们交互；

#### 9.Java中堆和栈的理解

在Java中内存分为两种，一种是栈内存，另一种是堆内存

堆内存：用于存储Java中的对象和数组，当我们new一个对象或创建一个数组的时候，就会在堆内存中开辟一段空间给它，用于存放，堆内存的特点：先进先出，后今后出，②可以动态的分配内存的大小，生存期不必告诉编译器，但存取速度较慢；

栈内存：主要用来执行程序用，比如基本类型的变量和对象的引用变量，其特点：①先进后出，后进后出，②存取速度比堆快，仅次于寄存器，栈数据可以共享，但其在栈中的数据大小和生存期必须是确定的；

栈内存和堆内存都属于Java内存的一种，系统会自动去回收它，但对于堆内存开发人员一般会自动回收。

栈是一块和线程紧密相关的内存区域，每个线程都有自己的栈内存，用于存储本地变量、方法参数和栈调用一个线程中存储的变量，对于其他线程是不可见的，而堆是所有线程共享的一个公用内存区域，对象都在堆里创建，但为了提升效率，线程会从堆中拷贝一个缓存到自己的栈中，如果多个线程使用该变量，就可能引发问题，这是volatile修饰变量就可以发挥作用，他要求线程从主存中读取变量的值。

#### 10.Android常用的数据存储方式（4种）

使用SharedPreference存储：保存基于xml文件存储的key-value键值对数据，通常用来存储一些简单的配置信息；

文件存储方式：Context提供了两个方法来打开数据文件的文件IO流；

SQLite存储数据：SQLite是轻量级的嵌入式数据库引擎，支持SQL语言；

网络存储数据：通过网络存储数据；

https://blog.csdn.net/m0_70748845/article/details/125647560

#### 广播注册的方式与区别

静态注册：在清单文件中声明广播，这种广播是常驻型广播，长期占用内存，占用CPU资源，但这种广播可以在app不运行的时候监听，例如开机广播
动态注册：在Application或其他组件中用代码动态声明的广播，非常驻型广播，广播的生命周期和组件绑定，但要在onDestroy的时候注销广播，否则容易造成内存泄漏

#### 进程保活，避免service死亡

进程保活：可以使用AlarmManager或WorkManager定时启动activity，当进程死亡后拉起；使用前台服务来提高进程的优先级，提高进程的存活率
service保活：设置为前台服务提高优先级；在进程中轮询service是否死亡，死亡则重新启动；在onStartCommand中返回STICKY,当service被杀死后，系统会尽量复活粘性服务；onDestroy时发送一个自定义广播，收到广播重启service
————————————————

#### Fragment与Fragment、Activity之间的通信

Fragment：Fragment之间是不能直接通信的，需要通过宿主Activity为桥梁通信
Activity：Activity可以在添加Fragment的时候使用Bundle给Fragment传递数据；可以使用FragmentManager的方法findFragmentById和findFragmentByTag来得到Fragment实例来传递数据
Fragment可以通过在onAttach回调中获取实现了自定义接口的Activity对象从而调用接口的方法进行向Activity传输数据；也可以使用getActivity获取宿主Activity的实例;共用viewmodel也可以实现通信。
————————————————

#### RecyclerView和ListView的区别

RecyclerView可以实现ListView的显示效果，同时也可以实现瀑布流的效果；也可以设置滚动的方向
RecyclerView的item复用不用手动实现，已经封装好了（viewHolder） RecyclerView可以实现局部刷新
需要使用动画的情况下，RecyclerView的性能比ListView好，而且RecyclerView提供了使用动画的API
单纯显示列表数据两者区别不大
————————————————

