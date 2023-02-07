emplace_back()是c++11的新特性。

和push_back()的区别在于

push_back()方法要调用构造函数和复制构造函数，这也就代表着要先构造一个临时对象，然后把临时的copy构造函数拷贝或者移动到容器最后面。

而emplace_back()在实现时，则是直接在容器的尾部创建这个元素，省去了拷贝或移动元素的过程。

```C++
vector<pair<int, int>> ret;
ret.push_back(1,1)//会报错，因为没有构造一个临时对象
ret.push_back(pair(1,1))//不会报错，因为构成了一个pair对象
ret.emplace_back(1,1)//不会报错，因为直接在容器的尾部创建对象
```
