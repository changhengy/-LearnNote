你知道MVC模式吧？M Model, V View, C Control，在Android里面View就是 View 类， Control之一就是Activity 类了
　　首先View不代表一个屏幕，View可以代表一个按钮(ButtonView)，一行字(TextView)，一个文本框(EditText)，也可以代表一个不可见的容器(ViewGroup的子类们），装了一打按钮之类的东西，ViewGroup可以它里面东西的排列显示方式，横着、竖着、可以滚动的，等等，随心所欲。ViewGroup里面可以套ViewGroup，就像俄罗斯套娃，最外面那个才充满整个屏幕。
　　Acitivity当然代表一个屏幕，但和view的作用不同。看View，不说别的，就onDraw()方法，Activity有吗？Activity连个带draw字的方法都没有，所以它不直接负责显示工作。你看Activity的方法，大部分都处理这些事的，比如触摸、按件、呼出菜单、保存状态、暂停、继续，都是处理程序的。如果你不给Acitvity里面“setContentView"，它就没有东西显示。所以Activity就像是个后台打杂的，和前台唱戏的View是互相配合的关系



​	 **简言之，Activity是一个单独的、聚焦的和用户直接进行交互的组件，这个组件是View的容器，View控件只有放置在这个容器里面才有意义。在MVC的设计模式里面，Activity是Control，负责与用户交互的业务逻辑，而View控件则是将这些业务逻辑显示在屏幕上。**

