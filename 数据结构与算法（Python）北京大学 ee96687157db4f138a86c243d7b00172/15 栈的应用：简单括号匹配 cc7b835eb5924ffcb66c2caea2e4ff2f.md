# 15. 栈的应用：简单括号匹配

- (5+6)*(7+8)/(4+3)

    这里的括号是用来置顶表达式的计算优先级的

- 有些函数式语言，如Lisp，在定义函数时就会用到大量的括号
- 当然，括号的使用要遵循“平衡”规则

    有开必有闭，开闭括号正确嵌套

- 如何构造括号匹配识别算法

    从左到右扫描括号串，最新打开的左括号，应该匹配最先遇到的右括号

    这样第一个左括号（最早打开），就应该匹配最后一个右括号（最后遇到）

    这种次序反转的识别，正好符合栈的特性！

    ![15%20%E6%A0%88%E7%9A%84%E5%BA%94%E7%94%A8%EF%BC%9A%E7%AE%80%E5%8D%95%E6%8B%AC%E5%8F%B7%E5%8C%B9%E9%85%8D%20cc7b835eb5924ffcb66c2caea2e4ff2f.png](15%20%E6%A0%88%E7%9A%84%E5%BA%94%E7%94%A8%EF%BC%9A%E7%AE%80%E5%8D%95%E6%8B%AC%E5%8F%B7%E5%8C%B9%E9%85%8D%20cc7b835eb5924ffcb66c2caea2e4ff2f.png)

    ```python
    from stack import Stack

    def parChecker(symbolString):
        s = Stack()
        balanced = True
        index = 0
        while index < len(symbolString) and balanced:
            symbol = symbolString[index]
            if symbol == "(":
                s.push(symbol)
            else:
                if s.isEmpty():
                    balanced = False
                else:
                    s.pop()
            
            index += 1
        
        if balanced and s.isEmpty():
            return True
        else:
            return False

    print(parChecker("((()))"))
    print(parChecker("(()"))
    ```

## 更多种括号的匹配

- 在实际应用里，我们会碰到更多种括号
- 这些不同的括号有可能混合在一起使用，因此就要注意各自的开闭匹配情况

下面这些是匹配的

**{ { ( [ ] [ ] ) } ( ) }**

**[ [ { { ( ( ) ) } } ] ]**

**[ ] [ ] [ ] ( ) { }**

下面这些是不匹配的

**( [ ) ]**

**( ( ( ) ] ) )**

**[ { ( ) ]**

## 通用括号匹配算法

```python
from stack import Stack

def parChecker(symbolString):
    s = Stack()
    balanced = True
    index = 0
    while index < len(symbolString) and balanced:
        symbol = symbolString[index]
        if symbol in "([{":
            s.push(symbol)
        else:
            if s.isEmpty():
                balanced = False
            else:
                top = s.pop()
                if not matches(top,symbol):
                    balanced = False
        
        index += 1
    
    if balanced and s.isEmpty():
        return True
    else:
        return False

def matches(open, close):
    opens = "([{"
    closes = ")]}"
    return opens.index(open) == closes.index(close)

print(parChecker("{{([][])}()}"))
print(parChecker("[{()]"))
```

---