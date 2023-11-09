![](https://p.ipic.vip/cfnkto.png)

质数（Prime Number）是指大于1且只能被1和自身整除的正整数。计算质数是数论中的一个经典问题，也在编程中常常出现。

本文将介绍多种计算质数的方法，从最基础的方法到更高效的算法，以及一些Python中的优化技巧。

## 一、基础方法

### 1.1 暴力法

最简单的方法是使用暴力法，逐个检查每个正整数是否为质数。这种方法对于小数字是有效的，但在大数字上效率很低。

```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, n):
        if n % i == 0:
            return False
    return True
```

### 1.2 优化暴力法

可以通过减少检查的范围来优化暴力法。因为质数必定大于1，所以只需检查2到√n之间的数是否能整除n。

```python
import math

def is_prime(n):
    if n <= 1:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    for i in range(3, int(math.sqrt(n)) + 1, 2):
        if n % i == 0:
            return False
    return True
```

## 二、更高效的方法

### 2.1 埃拉托斯特尼筛法（Sieve of Eratosthenes）

埃拉托斯特尼筛法是一种高效的方法，用于生成一定范围内的所有质数。它通过不断排除合数来找到质数。

```python
def sieve_of_eratosthenes(n):
    is_prime = [True] * (n + 1)
    is_prime[0] = is_prime[1] = False
    p = 2
    while p**2 <= n:
        if is_prime[p]:
            for i in range(p**2, n + 1, p):
                is_prime[i] = False
        p += 1
    primes = [i for i in range(2, n + 1) if is_prime[i]]
    return primes
```

### 2.2 Miller-Rabin素数测试

Miller-Rabin素数测试是一种概率性的方法，用于测试一个数是否为质数。虽然它不是绝对确定的，但通常可以提供可接受的结果。

```python
import random

def miller_rabin(n, k=5):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0:
        return False
    
    # 将n-1表示为(2^r) * d
    r, d = 0, n - 1
    while d % 2 == 0:
        r += 1
        d //= 2
    
    def witness(a, d, n):
        x = pow(a, d, n)
        if x == 1 or x == n - 1:
            return True
        for _ in range(r - 1):
            x = pow(x, 2, n)
            if x == n - 1:
                return True
        return False
    
    for _ in range(k):
        a = random.randint(2, n - 2)
        if not witness(a, d, n):
            return False
    return True
```

## 三、Python中的质数计算

Python标准库提供了一些用于计算质数的函数和模块，例如`sympy`和`math`。

### 3.1 使用`sympy`模块

`sympy`是Python中用于符号数学的强大库，它包含了许多数论函数，包括判断质数的函数。

```python
from sympy import isprime

print(isprime(17))  # 输出：True
```

### 3.2 使用`math`模块

`math`模块提供了一些数学函数，包括`sqrt`函数，可以用来优化暴力法中的质数判断。

```python
import math

def is_prime(n):
    if n <= 1:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    for i in range(3, int(math.sqrt(n)) + 1, 2):
        if n % i == 0:
            return False
    return True
```

## 总结

计算质数是数学和计算机科学中的一个经典问题，涉及多种算法和技术。本文介绍了计算质数的多种方法，包括基础方法、更高效的方法和Python中的内置函数和模块。选择合适的方法取决于具体的需求和性能要求。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
