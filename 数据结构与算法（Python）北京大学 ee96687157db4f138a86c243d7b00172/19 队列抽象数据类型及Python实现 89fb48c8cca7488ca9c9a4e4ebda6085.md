# 19. 队列抽象数据类型及Python实现

## 队列Queue：什么是队列？

- 队列是一种有次序的数据集合，其特征是：

    新数据项的添加总发生再一端（通常称为“尾rear”端）

    而现存数据项的移除总发生在另一端（通常称为“首front”端）

    ![19%20%E9%98%9F%E5%88%97%E6%8A%BD%E8%B1%A1%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E5%8F%8APython%E5%AE%9E%E7%8E%B0%2089fb48c8cca7488ca9c9a4e4ebda6085.png](19%20%E9%98%9F%E5%88%97%E6%8A%BD%E8%B1%A1%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E5%8F%8APython%E5%AE%9E%E7%8E%B0%2089fb48c8cca7488ca9c9a4e4ebda6085.png)

 

- 新加入的数据项必须在数据集的末尾等待，而等待时间最长的数据项则是队首
- 这种次序安排的原则称为（FIFO：First-in-first-out）先进先出
- 队列仅有一个入口和一个出口

    不允许数据项直接插入队中，也不允许从中间移除数据项

## 计算机科学中队列的例子：打印队列

- 一台打印机面向多个用户/程序提供服务

    打印速度比打印请求提交的速度要慢得多

    有任务在打印时，后来的打印请求就要排成队列

## 计算机科学中队列的例子：进程调度

- 操作系统核心采用多个队列在对系统中同时运行的进程进行调度

    线程数远多于CPU核心数

    有些进程还要等待不同类型I/O事件

## 计算机科学中队列的例子：键盘缓冲

- 键盘敲击并不会马上显示在屏幕上

    需要一个队列性质的缓冲区，将尚未显示的敲击字符暂时存在其中

## 抽象数据类型Queue

抽象数据类型Queue是一个有次序的数据集合

数据仅添加到“尾rear”端

而且仅从“首front”端移除

Queue具有FIFO的操作次序

[Operation](19%20%E9%98%9F%E5%88%97%E6%8A%BD%E8%B1%A1%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E5%8F%8APython%E5%AE%9E%E7%8E%B0%2089fb48c8cca7488ca9c9a4e4ebda6085/Operation%20fe85064b61ab49dba532846fcf2a35dc.csv)

## Python实现ADT Queue

```python
class Queue:
    def __init__(self):
        self.items = []
    
    def isEmpty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.insert(0, item)
    
    def dequeue(self):
        return self.items.pop()
    
    def size(self):
        return len(self.items)
```

---