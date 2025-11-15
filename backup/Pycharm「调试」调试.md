今天不知道为什么，Pycharm 的调试不能用了，报错：

```
OMP: Error #15: Initializing libiomp5md.dll, but found libiomp5md.dll already initialized.
```

网上搜索，可能是 pytorch 和 numpy 冲突了，也可能是 matplotlib 的问题。

我本来还对后者不以为然，但在百番尝试无果，想说重装一次 matplotlib 试试。结果发现，我并没有安装 matplotlib（但是我就不知道我之前怎么画上图的），于是安装之后就好了。

不明白是什么原理，只是把我的解决方案分享出来，供大家参考。

## 参考文献
1. [总结该问题解决方案：OMP: Error #15: Initializing libiomp5md.dll, but found libiomp5md.dll already initialized](https://blog.csdn.net/peacefairy/article/details/110528012)