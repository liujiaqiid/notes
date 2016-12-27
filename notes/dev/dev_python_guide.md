# python guide

## basic

- points

```
# 1. 输入输出
name = input('please enter your name: ')
print('hello,', name)

# 2. 不转义 vs 转义
print(r'\\\t\\')
print('\\\t\\')

# 3. 字符转编码 vs 编码转字符
ord('中')
chr(25991)
len('中文'.encode('utf-8'))


# 4. 告诉编译器按UTF-8编码读取
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

# 5. 格式化 （如果你不太确定应该用什么，%s永远起作用，它会把任何数据类型转换为字符串）
'Hi, %s, you have $%d.' % ('Michael', 1000000)


# 6. 函数
def my_abs(x):
    if not isinstance(x, (int, float)):
        raise TypeError('bad operand type')
    if x >= 0:
        return x
    else:
        return -x

# 7. 必选 默认参数 & 可变参数 & 关键字参数
def f(a, b, c=0, *args, **kw):
  print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

# 8. 切片
range(10)[1:5]
range(10)[:5]
range(10)[-5:]
# 每5个取一个
range(10)[::5]

# 9. 列表生成
[m + n for m in 'ABC' for n in 'XYZ']


```

- file 1

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

' This is a test module '

__author__ = 'Jacky Liu'

import sys

def test():
    args = sys.argv
    if len(args)==1:
            print('Hello, world!')
    elif len(args)==2:
        print('Hello, %s!' % args[1])
    else:
        print('Too many arguments!')

if __name__=='__main__':
    test()
```
