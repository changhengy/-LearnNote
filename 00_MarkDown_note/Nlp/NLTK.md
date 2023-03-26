# [NLTK安装方法](https://blog.csdn.net/weixin_47822556/article/details/114434233?ops_request_misc=&request_id=&biz_id=102&utm_term=nltk%E5%AE%89%E8%A3%85&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-114434233.142%5Ev63%5Econtrol,201%5Ev3%5Econtrol_1,213%5Ev1%5Econtrol&spm=1018.2226.3001.4187)

```python
pip install [nltk](https://so.csdn.net/so/search?q=nltk&spm=1001.2101.3001.7020)
import nltk
nltk.download()

```

此时会出现报错窗口，不用担心，此时我们需要自己手动下载nltk包。下载方式有两种。
（1）网站下载
[nltk_data](https://gitcode.net/mirrors/nltk/nltk_data?utm_source=csdn_github_accelerator) （可能是网速原因，我总是下载失败）

下载后，将文件解压，并将packages文件重命名为nltk_data。

将重命名的文件夹nltk_data放入窗口的下载路径下（注：重命名文件夹放在Roaming文件夹下）nltk包的下载就完成了。
关闭弹窗，再次输入如下代码

如图显示text1至text9即表明nltk安装成功，可以使用。



## punkt 找不到的问题

直接到 C:\Users\Pc-Lc\AppData\Roaming\nltk_data\tokenizers 下解压即可



Text  中的 plot 方法的使用问题 ，需要先安装下面这个包

pip install -U matplotlib 



# spaCy 速度快，数据量大的时候使用spaCy

https://spacy.io/  官网
