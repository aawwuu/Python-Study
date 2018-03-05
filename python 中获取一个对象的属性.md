python 中获取一个对象的属性

通过 `dir() ` 函数和 ` __dict__ `  列出对象属性

`dir()` 函数会自动寻找一个对象的所有属性，包括父类的属性，也包括`__dict__`中的属性， 返回一个 list 。

`__dict__` 是`dir()` 的子集，是一个字典，键为属性名，值为属性值，只包括对象本身相关的属性，类的`__dict__`并不包含其父类的属性。

**不是所有对象都拥有`__dict__`属性。**

```python
class A:
    def __init__(self):
        self.a = 'aaaaaaa'
        self.b = 'bbbbbbb'
        self.c = 'ccccccc'
 
if __name__ == '__main__':
    a = A()
    for key in a.__dict__:
        print key, ':', a.__dict__[key]
```

另外还有 `getattr()`, `hasattr()`, `setattr()` 这几个与属性有关的函数