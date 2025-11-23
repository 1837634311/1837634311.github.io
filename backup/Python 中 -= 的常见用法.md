这两天无聊的时候在看 [wtfpython](https://github.com/satwikkansal/wtfpython)，想起似乎经常会忘记使用 `:=` 来简化代码，特此记录。

`:=` 也被称为海象表达式，是 Python 3.8 引入的特性，允许在表达式中给变量赋值，从而减少代码行数。

## 在 `if` 语句中简化代码

通常，我们会判断一个变量的状态，后续进行不同的操作，像这样：

```python
x = func()
if x > 0:
    print("positive")
```

使用 `:=` 可以少写一行：

```python
if (x := func()) > 0:
    print("positive")
```

## 在列表推导式避免重复计算

更进一步，当列表推导式中需要进行一次昂贵的计算，并且想基于这个结果进行后续操作，通过海象表达式可以避免重复计算。

传统写法：

```python
results = [func(x) for x in my_data if func(x) > 10]
```

`:=` 写法：

```python
results = [result for x in my_data if (result := func(x)) > 10]
```

## 在 `while` 中简化代码

在循环处理数据时，往往需要先获取一次数据，再接着运行：

```python
data = read_data()
while data is not None:
    process(data)
    data = read_data()
```

但用 `:=` 之后，可以同时获取并判断：

```python
while (data := read_data()) is not None:
    process(data)
```

另一种格式：

传统写法：

```python
while True:
    psw = input("请输入密码：")
    if psw == "123":
        break
```

`:=` 写法：

```python
while (psw := input("请输入密码：")) != "123":
    continue
```

> [!Tip]
> `:=` 只能在表达式中使用，而不能作为顶级的独立语句。因为它本身是一个表达式，会返回它所赋的值。

例如：

```python
>>> (a :=5)
5
>>> a := 5
  File "<stdin>", line 1
    a := 5
      ^^
SyntaxError: invalid syntax
```

## 参考

1. [Python 海象运算符](https://zhuanlan.zhihu.com/p/351140647)
2. Gemini 2.5 Flash
