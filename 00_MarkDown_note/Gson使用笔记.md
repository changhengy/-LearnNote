**https://www.freesion.com/article/1057683004/**

https://www.yiibai.com/gson/gson_overview.html

https://blog.csdn.net/hellodakee/article/details/106055298

https://blog.csdn.net/Ever69/article/details/86469320

Google Gson是一个简单的基于Java的库，用于将Java对象序列化为JSON，反之亦然。 它是由Google开发的一个开源库。

以下几点说明为什么应该使用这个库 -

- **标准化** - Gson是一个由Google管理的标准化库。
- **高效** - 这是对Java标准库的可靠，快速和高效的扩展。
- **优化** - Gson库经过高度优化。
- **支持泛型** - 它为泛型提供了广泛的支持。
- **支持复杂的内部类** - 它支持具有深度继承层次结构的复杂对象。

## Gson的特点

这里列出了Gson的一些最显着的特点 -

- **易于使用** - Gson API提供了一个高级外观来简化常用的用例。
- **无需创建映射** - Gson API为大部分要序列化的对象提供了默认映射。
- **性能优** - Gson速度相当快，内存占用量低。 它适用于大型对象图或系统。
- **干净JSON** - Gson创建一个干净而紧凑的JSON结果，它易于阅读。
- **无依赖性**—Gson库不需要JDK以外的任何其他库。
- **开源** - Gson库是开源的; 它是免费提供的。

## 处理JSON的三种方法

Gson提供了三种处理JSON的替代方法 - 

**1. 流媒体API**

它读取和写入JSON内容作为离散事件。 `JsonReader`和`JsonWriter`将数据读取/写入令牌，称为`JsonToken`。

这是处理JSON的三种方法中最强大的方法。 它具有最低的开销，并且在读/写操作中速度非常快。 它类似于用于XML的Stax解析器。

**2. 树模型**
它准备JSON文档的内存树表示。 它构建了一个`JsonObject`节点树。 这是一种灵活的方法，类似于XML的DOM解析器。

**3. 数据绑定**
它使用属性访问器将JSON转换为POJO(普通旧Java对象)并从中转换。 Gson使用数据类型适配器读取/写入JSON。 它类似于XML的JAXB解析器。

