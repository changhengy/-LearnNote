Android 五种数据存储的方式分别为：

| 名字              | 介绍                                                         |
| ----------------- | ------------------------------------------------------------ |
| SharedPreferences | 以Map形式存放简单的配置参数；                                |
| ContentProvider   | 将应用的私有数据提供给其他应用使用；                         |
| 文件存储          | 以IO流形式存放，可分为手机内部和手机外部（sd卡等）存储，可存放较大数据； |
| SQLite            | 轻量级、跨平台数据库，将所有数据都是存放在手机上的单一文件内，占用内存小； |
| 网络存储          | 数据存储在服务器上，通过连接网络获取数据；                   |

**Sharedpreferences**是Android平台上一个轻量级的存储类，用来保存应用程序的各种配置信息，其本质是一个以“键-值”对的方式保存数据的xml文件，其文件保存在**/data/data/包名/shared_prefs**目录下。在全局变量上看，其优点是不会产生Application 、 静态变量的OOM（out of memory）和空指针问题，其缺点是效率没有上面的两种方法高。

#### 使用SharedPreferences

##### 获取SharedPreferences对象

首先要获取SharedPreferences才能进行操作。获取SharedPreferences对象有下面两个方式：

1. `getSharedPreferences(String name, int mode)`
     通过Context调用该方法获得对象。它有两个参数，第一个name 指定了SharedPreferences存储的文件的文件名，第二个参数mode 指定了操作的模式。
     mode的模式：

```css
Context.MODE_PRIVATE: 指定该SharedPreferences数据只能被本应用程序读、写；
Context.MODE_WORLD_READABLE:  指定该SharedPreferences数据能被其他应用程序读，但不能写；
Context.MODE_WORLD_WRITEABLE:  指定该SharedPreferences数据能被其他应用程序读；
Context.MODE_APPEND：该模式会检查文件是否存在，存在就往文件追加内容，否则就创建新文件；
```

2. `getPreferences(int mode)`
     通过Activity调用获得对象。它只有一个参数mode 指定操作模式。这种方式获取的对象创建的文件 属于Activity,只能在该Activity中使用，且没有指定的文件名，文件名同Activity名字。

例子：

```kotlin
mContextSp = this.getSharedPreferences( "testContextSp", Context.MODE_PRIVATE );
mActivitySp = this.getPreferences( Context.MODE_PRIVATE );
```

##### 写数据

步骤1：创建一个SharedPreferences对象

```bash
SharedPreferences sharedPreferences= getSharedPreferences("data",Context.MODE_PRIVATE);
```

步骤2： 实例化SharedPreferences.Editor对象

```undefined
SharedPreferences.Editor editor = sharedPreferences.edit();
```

步骤3：将获取过来的值放入文件

```bash
editor.putString("name", “Tom”);
editor.putInt("age", 28);
editor.putBoolean("marrid",false);
```

步骤4：提交

```css
editor.commit();
```

##### 读取数据

```dart
SharedPreferences sharedPreferences= getSharedPreferences("data", Context .MODE_PRIVATE);
String userId=sharedPreferences.getString("name","");
```

##### 删除指定数据

```csharp
editor.remove("name");
editor.commit();
```

##### 清空数据

```css
editor.clear();
editor.commit();
```

#### commit和apply区别

- apply函数立即更改内存中的SharedPreferences对象，但异步地将更新写入磁盘。
- commit函数同步地将数据写入磁盘。在主线程调用它应该多注意，因为可能引起阻塞，引起ANR。
- commit有返回值，返回是否成功写入永久性存储种。apply没有返回值。

