NumPy 现在推荐使用 `Generator` 对象来生成随机数。

我们通常通过 `default_rng(seed)` 来获取一个 `Generator` 实例，并将其命名为 `rng`。

```python
import numpy as np

rng = np.random.default_rng(42)
```

## 以下是 `rng` 最常用的一些方法及其关键参数

### `integers(low, high=None, size=None, endpoint=False)`

生成随机整数。

#### 参数

1. `low`: 生成的随机数的最小值（包含此值）。
2. `high`: 生成的随机数的最大值（默认不包含此值）。如果未提供 `high`，则范围变为 `[0, low)`。
3. `size`: 一个整数或元组，指定输出数组的形状。
4. `endpoint`: 如果设置为 `True`，则范围变为 `[low, high]`。

#### 示例

```python
# 生成 5 个 [1, 10] 之间的整数 (包含 1 和 10)
rng.integers(low=1, high=10, size=5, endpoint=True)
"""
[ 1,  9, 10,  7,  2]
"""

# 生成一个 3x4 的矩阵，元素在 [0, 5) 之间 (不包含 5)
rng.integers(low=5, size=(3, 4))
"""
[[0 0 1 4]
 [1 4 0 0]
 [2 0 4 1]]
"""
```

### `random(size=None)`

在 `[0.0, 1.0)` 范围内生成均匀分布的随机浮点数。

#### 参数

`size`: 一个整数或元组，指定输出数组的形状。

#### 示例

```python
# 生成一个 2x3 的矩阵，元素在 [0.0, 1.0) 之间
rng.random(size=(2, 3))
"""
[[0.61823309 0.53271588 0.55477724]
 [0.41003725 0.12228595 0.99907367]]
"""
```

### `normal(loc=0.0, scale=1.0, size=None)`

生成正态分布（高斯分布）随机数。

#### 参数

1. `loc`: 正态分布的均值（μ）。
2. `scale`: 正态分布的标准差（σ）。
3. `size`: 一个整数或元组，指定输出数组的形状。

#### 示例

```python
# 生成均值为 100，标准差为 15 的 5 个随机数
rng.normal(loc=100, scale=15, size=5)
"""
[143.87226087 100.77054565 130.20014801  82.1918359  110.18557885]
"""
```

### `standard_normal(size=None)`

标准正态分布随机数生成器。

#### 参数

1. `size`: 可选。一个整数或元组，指定输出数组的形状。

#### 示例

```python
# 生成一个 2x3 的标准正态分布矩阵
rng.standard_normal(size=(2, 3))
"""
[[ 2.92481739  0.05136971  2.0133432 ]
 [-1.18721094  0.67903859  1.09159915]]
"""
```

### `choice(a, size=None, replace=True, p=None)`

从给定的数组中生成一个随机样本。

#### 参数

1. `a`: 可以是一维数组（从中抽样），或一个整数（此时等同于从 `np.arange(a)` 中抽样）。
2. `size`: 一个整数或元组，指定输出数组的形状。
3. `replace`: 有放回抽样。
4. `p`: 一个一维数组，与 `a` 长度相同，指定 `a` 中每个元素被抽到的概率。

#### 示例

```python
my_array = np.array(['A', 'B', 'C', 'D'])

# 有放回地抽取 3 个元素
rng.choice(my_array, size=3, replace=True)
"""
['A' 'C' 'C']
"""

# 无放回地抽取 3 个元素
rng.choice(my_array, size=3, replace=False)
"""
['C' 'A' 'B']
"""

# 按指定概率抽样 (B 的概率最高)
rng.choice(my_array, size=1, p=[0.1, 0.7, 0.1, 0.1])
"""
['B']
"""
```

### `shuffle(x)`

> [!WARNING]
> 在原地对数组的元素进行随机排序，并且返回 `None`。

#### 示例

```python
rng.shuffle(my_array)
print(my_array)
"""
['A' 'B' 'D' 'C']
"""
```

### `permutation(x)`

返回数组的一个随机排列的副本。

#### 示例

```python
# 获取一个打乱后的副本，原数组不变
shuffled_copy = rng.permutation(data)

print("打乱后的数组：", shuffled_copy)
# ['A' 'B' 'D' 'C']
print("原数组 :", my_array)
# ['A' 'B' 'C' 'D']
```
