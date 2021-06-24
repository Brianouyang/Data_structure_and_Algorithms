# 10. 大O表示法

## 算法时间度量指标

- 一个算法所实施的操作步骤或步骤数可作为独立于具体程序/机器的度量指标
- 赋值语句是一个合适的选择

    一条赋值语句同时包含了（表达式）计算和（变量）存储两个基本资源

    仔细观察程序设计语言特性，除了与计算资源无关的定义语句外，主要就是控制流语句和赋值语句，而控制流仅仅起了组织语句的作用，并不实施处理。

## 分析SumOfN的赋值语句执行语句

赋值语句数量T(n) = 1 + n

## 问题规模影响算法执行时间

- 问题规模：影响算法执行时间的主要因素
- 算法分析的目标是要找出问题规模会怎么影响一个算法的执行时间

## 数量级函数 Order of Magnitude

- 基本操作数量函数 T(n) 的精确值并不是特别重要，重要的部分是T(n) 中起决定性因素的主导部分
- 数量级函数描述了T(n)中随着n增加而增加速度最快的主导部分

    称作“大O”表示法，记作 $O(f(n))$，其中 $f(n)$ 表示 T(n) 中的主导部分

## 确定运行时间数量级大O的方法

例1： $T(n) = 1+n$

$O(n)$

例2 : $T(n) = 5n^2 + 27n + 1005$

$O(n^2)$

## 影响算法运行时间的其他因素

- 有时决定运行时间的不仅是问题规模
- 某些具体数据也会影响算法运行规模

    分为最好，最坏和平均状况，平均状况体现算法的主流性能

    对算法的分析最好看主流

## 常见的大O数量级函数

[https://img-blog.csdn.net/20180308045850712?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZ2RzZmdh/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](https://img-blog.csdn.net/20180308045850712?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZ2RzZmdh/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

[常见数量级](10%20%E5%A4%A7O%E8%A1%A8%E7%A4%BA%E6%B3%95%20fcfe8abd76244142aefd8c9c7df8de58/%E5%B8%B8%E8%A7%81%E6%95%B0%E9%87%8F%E7%BA%A7%2080201f1d718a4a82ba6a2ebd31f3d57e.csv)

## 从代码分析确定执行时间数量级函数

```python
a = 5
b = 6
c = 10
# T = 3

for i in range(n):
    for j in range(n):
        x = i * i
        y = j * j
        z = i * j
# T = 3n^2

for k in range(n):
    w = a * k + 45
    v = b * b
# T = 2n

d = 33
# T = 1
```

所以：

$T(n) = 3n^2 + 2n + 4$

## 其他算法复杂度表示法

- 大O表示法

    表示了所有上限中最小的那个上限。

- 大Ω表示法

    表示了所有下限中最大的那个下限

    $f(n) = Ω(g(n)) 当且仅当 g(n) = O(f(n))$

---