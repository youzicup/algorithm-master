# C++刷题技巧

## 代码风格

代码风格按照[谷歌C++标准](https://zh-google-styleguide.readthedocs.io/en/latest/google-cpp-styleguide/formatting)进行。

主要有以下几点需要注意：

 - 变量命名小驼峰式
 - 缩进统一采用两个空格
 - 大括号与条件在同一行

## 前置工作

### 基础结构

一般的C++解题框架可以按以下方式编写：

```C++
#include<bits/stdc++.h>
#include<algorithm>
#include<cmath>
#include<cstring>
#include<iostream>
#include<vector>
using namespace std;

int main() {
  // myFunc();
  return 0;
}
```

### 函数库说明

1. algorithm
 - max(a, b)
 - min(a, b)
 - abs(a, b) 返回a的绝对值，a必须为整型，浮点型需要用math.h下的fabs
 - swap(a, b)
 - reverse(a, a+n) 将a中元素倒序，一般用于数组
 - fill(a, a+n, value) 将 `[a,a+n)` 的元素填充值value
 - sort(a, a+n, fun()) 将 `[a,a+n)` 中的元素按照比较函数f进行排序
 - lower_bound(a, a+n, key) 返回 `[a,a+n)` 中第一个大于等于key的位置，没有则返回末位，底层为二分查找
 - upper_bound(a, a+n, key) 返回 `[a,a+n)` 中第一个小于等于key的位置，没有则返回末位，底层为二分查找
 - max_element(a, a+n) 查找 `[a,a+n)` 最大值所在地址
 - min_element(a, a+n) 查找 `[a,a+n)` 最小值所在地址

2. cmath
 - ceil(x) 向上取整
 - floor(x) 向下取整
 - round(x) 四舍五入取整
 - fabs(x) x绝对值
 - sqrt(x) 开方
 - pow(x, y) x的y次方

3. vector
 - vec.begin(); 第一个元素的指针,注意是 **指针**
 - vec.end(); vector中最后一个元素+1的 **指针**
 - vec[0],vec[1],vec[2] vector对象的访问
 - vec[0][1] vector二维对象的访问
 - vec.front(); vector中得到第一个元素的值
 - vec.back(); vector中得到最后一个元素的值
 - vec.at(i); 相当于vec[i];
