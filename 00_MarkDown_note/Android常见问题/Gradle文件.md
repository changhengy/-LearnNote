## Android Gradle 插件版本说明

https://developer.android.google.cn/studio/releases/gradle-plugin?hl=zh_cn#groovy



# Android面试：compileSdkVersion、targetSdkVersion、minSdkVersion作用与区别

https://blog.csdn.net/cpcpcp123/article/details/114754529

### compileSdkVersion:和编译时有关。

**1、只和编译相关**

**2、和运行时行为无关**

比如我们当前compileSdkVersion=28（Andorid 9.0），Android 10 新增了有关5G的api。我们的app想尽早使用5G相关的api，这时只需要将compileSdkVersion=29（Android 10），就能在编译阶段编译通过。此外，还需要注意的是，由于这个5G api是新增的，因此需要判断当前系统版本>=29才能使用新api。

### minSdkVersion：

指定app运行的最低设备sdk版本，如minSdkVersion=19 表示该app最低支持Android 4.4（API 19）设备，低于此版本的设备将不能使用该app。

### targetSdkVersion

直观翻译是“目标版本”，

大致意思就是：当我们更新targetSdkVersion时，比如从26（Android 8.0）变更到29（Android 9.0），意味着我们对26～29之间的系统兼容性进行了充分的测试，因此每当我们变更targerSdkVersion时，要充分测试其系统兼容性。
也许你会说，那我可以不更新targetSdkVersion值嘛，一劳永逸，理论上没啥问题。但是，如果你想在新的系统上使用api新的行为，那么就需要更新targetSdkVersion。再者，google会对targetSdkVersion进行一些强关联，比如app上传到google play，必须要求targetSdkVersion>=26（具体的值随着时间的推移，要求不一样）。

## 三者联系

compileSdkVersion>=targetSdkVersion>minSdkVersion

### 一句话总结：

**targerVersion字段来区分同一api在不同系统上的行为：**

​	对于同一个API(方法），新版本的系统更改了它的内部实现逻辑，新逻辑可能会影响之前调用此API的App，为了兼容此问题，引入targetSdkVersion。当targetSdkVersion>=xx(某个系统版本）时再生效其新修改的逻辑，否则还是沿用之前的逻辑。换句话说：如果你更改了targetSdkVersion值，说明你已经测试过兼容性问题了。

**minSdkVersion字段****

用来指定app运行的最低设备sdk版本**，如minSdkVersion=19 表示该app最低支持Android 4.4（API 19）设备，低于此版本的设备将不能使用该app。

**compileSdkVersion代表着编译的时候，会采用该api的规范进行代码检查和警告**，

但是并不会编译进apk中。开发的应用程序在Android 7.0系统运行，不会以Android 7.0新增的行为运行，决定Android系统行为的仍然是targetSDKVersion