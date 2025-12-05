原因：VsCode [换行算法有问题](https://github.com/subframe7536/maple-font/issues/173#issuecomment-2841538123)，或者是字体本身的 Bug。

解决方法：

1. 将「editor.wrappingStrategy」从「simple」改成「advanced」。
2. 换用等宽字体（但似乎 [Maple Mono](https://github.com/subframe7536/maple-font) 不行）。

解决来源：[解决VsCode中文行折行不正常的问题](https://zhuanlan.zhihu.com/p/24645262267)