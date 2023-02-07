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
#include <bits/stdc++.h>
#include <algorithm>
#include <cmath>
#include <cstring>
#include <iostream>
#include <vector>
using namespace std;

int main() {
  // myFunc();
  return 0;
}
```

### 函数库说明

#### 1. algorithm
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

#### 2. cmath
 - ceil(x) 向上取整
 - floor(x) 向下取整
 - round(x) 四舍五入取整
 - fabs(x) x绝对值
 - sqrt(x) 开方
 - pow(x, y) x的y次方

#### 3. vector
 - vec.begin(); 第一个元素的指针,注意是 **指针**
 - vec.end(); vector中最后一个元素+1的 **指针**
 - vec[0],vec[1],vec[2] vector对象的访问
 - vec[0][1] vector二维对象的访问
 - vec.front(); vector中得到第一个元素的值
 - vec.back(); vector中得到最后一个元素的值
 - vec.at(i); 相当于vec[i];
 - vec.push_back(x) 将x加到末尾，x为数组元素，
 - vec.pop_back() 删除最后一个元素，不返回
 - vec.emplace_back(x) 将x添加到末尾，直接在容器尾部创建该元素，省去了拷贝或移动的过程 [参考](C++\emplace与push对比.md)
 - accumulate(vec.begin(), vec.end(), 0) 从`指针1`到`指针2 - 1`的所有元素相加；若第三个元素为0则实现求和，若为 `" "` 则实现字符串拼接

#### 4. stack
 - st.push(); 元素入栈
 - st.pop(); 栈顶元素出栈
 - st.size(); 返回栈的大小(元素个数)
 - st.top(); 返回栈顶元素
 - st.empty(); 判断栈是否为空

#### 5. string
 - s.begin()
 - s.end()
 - s.size()
 - s.back()
 - s.push_back()
 - s.pop_back()
 - s.erase()
 ```C++
 s.erase(int index); // 删除下标从index开始直到字符串结尾的所有元素
 s.erase(int index, int num); // 删除从下标index开始的num个元素
 // 删除[it1,it2)区域的元素，函数的返回值是指向删除元素的下一个元素的迭代器
 s.erase(string::iterator it1,string::iterator it2)
 ```
 - remove(s.begin(), s.end(), 0)
   - 将要区域内要保留的元素全部移动到区域前端，返回删除后的结尾迭代器end
   - 因此remove函数不会改变size
   - 在对字符串进行处理时，要结合erase使用 s.erase(remove(s.begin(), s.end(), ' '), a.end())
 - memset(void *s,int c,unsigned long n) 为指针变量s所指的前n个字节的内存单元填充给定的int型数值c，它可以为任何数据进行初始化。
 
#### 6. unordered_map 无序映射
 - 初始化方式
 > unordered_map<int, bool> map;
 - 查询是否存在
 > if(m.find(key) != m.end())

 - map.begin(); 返回第一个键值对的正向迭代器
 - map.end(); 返回最后一个键值对后一个位置的正向迭代器
 - map.size(); 返回map的大小
 - map.empty(); 判空
 - map.find(key); 查找 `key` 为键的键值对，找到返回该位置的迭代器，否则返回 `map.end()`
 - map.insert(std::make_pair(key, val)); 插入新键值对
 - map.emplace(key, val); 插入新键值对，效率比insert高
 - map.erase(key, val); 删除键值对
 - map.clear(); 清空map

## 性能分析

### 耗时分析

```C++
#include <time.h> // or  #include <ctime>

clock_t start, stop;
double duration; // 以秒为单位
int main() {
  start = clock();
  MyFunc();
  stop = clock();
  duration = ((double)(stop - start)) / CLK_TCK;

  return 0;
}
```
