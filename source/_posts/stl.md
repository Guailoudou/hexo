---
title: C++ stl学习笔记
date: 2024-03-11 20:03:35
tags: 日志
---
万用头文件：`#include<bits/stdc++.h>` ~~（不知道能不能用）~~

公用的：
- 查询长度（大小） `.size()`
- 清空 `.clear()`
- 判空 `.empty()`
### vector 普通数组的替代
头文件：`#include<vector>`

构造：`vector<类型> arr(长度,[初值])`

示例：`vector<int> arr(10,1)`

插入：`arr.push_back(元素)` 在 vector 尾接一个元素，数组长度 +1

删除：`arr.pop_back()` 删除 vector 尾部的一个元素，数组长度 −1

改变长度：`arr.resize(长度),[默认值]`

修改：`arr[索引]=元素`

### stack 栈
头文件：`#include<stack>`

构造：`stack<类型> 栈名`

示例：`stack<int> s`

进栈：`栈名.push(元素)`
 
出栈：`栈名.pop()` （不可直接访问内部）

获取栈顶:`栈名.top()`

### queue 队列
头文件：`#include<queue>`

构造：`queue<类型> 队列名`

示例：`queue<int> q`

进队：`队列名.push(元素)`

出队：`队列名.pop()` （不可直接访问内部）

取队头:`队列名.front()`

取队尾：`队列名.back()`

### set 集合 (内部元素不可重复,不可用下标访问)
头文件：`#include<set>`

构造：`set<类型, 比较器> 集合名`

示例：
```c++
set<int> st1;               // 储存int的集合（从小到大）
set<int, greater<int>> st2; // 储存int的集合（从大到小）
```

插入：`集合名.insert(元素)`

删除：`集合名.erase(元素)`

查找：`集合名.find(元素)` 返回指向元素位置的迭代器，如果元素不存在，返回指向集合尾的迭代器

判断存在：`集合名.count(元素)` 返回 1 表示存在，返回 0 表示不存在

遍历:
```c++
for (set<int>::iterator it = st.begin(); it != st.end(); ++it)
    cout << *it << endl;
```

### map 映射
头文件：`#include<map>`

构造：`map<键类型, 值类型,比较器> 映射名` (比较器可省，默认从小到大`greater<int>`为从大到小)

示例：`map<int, string> mp`

增删查改：`mp[1] = 2;`(使用中括号)

插入：`映射名.insert(pair<类型, 类型>(键, 值))`

删除：`映射名.erase(键)`

查找：`映射名.find(键)` 返回指向键位置的迭代器，如果键不存在，返回指向映射尾的迭代器

判断存在：`映射名.count(键)` 返回 1 表示存在，返回 0 表示不存在

遍历:
```c++
for (map<int, string>::iterator it = mp.begin(); it != mp.end(); ++it)
    cout << it->first << " " << it->second << endl;
```
### string 字符串
头文件：`#include<string>`

构造：`string 字符串名`

示例：`string s1 = "hello";`

`int / long long / float / double / long double`转`string`:to_string(变量)

数值与字符串互转:
|源	|目的|函数|
|---|---|---|
|int/long long/float/double/long double|string|to_string()|
|string	|int	|stoi()|
|string	|long long	|stoll()|
|string	|float	|stof()|
|string	|double	|stod()|
|string	|long double	|stold()|

### 常用函数

`swap(a, b)` 交换 a 和 b 的值

`max(a, b)` 返回 a 和 b 中的最大值

`min(a, b)` 返回 a 和 b 中的最小值

`abs(a)` 返回 a 的绝对值

`pow(a, b)` 返回 a 的 b 次方

`sqrt(a)` 返回 a 的平方根

`ceil(a)` 返回大于或等于 a 的最小整数(向上取整)

`floor(a)` 返回小于或等于 a 的最大整数（向下取整）

`sort()` 排序

`gcd(a, b)` 最大公约数

`lcm(a, b)` 最小公倍数

### 常见头文件
`#include <iostream>`  `using namespace std;`
`#include<algorithm>` - 排序sort max min...的头文件

```
#include<bits/stdc++.h>
using namespace std;
int main(){
    return 0;
}
```
pair：`pair<类型1, 类型2> 变量名(元素1, 元素2)`(可以用来储存两个元素，~~把map塞进去~~ ) pair头文件为`#include<utility>`

塞入vector中：`vector< pair<string,double> > v(maps.begin(),maps.end());`(然后可以直接用迭代器了)
```
//实现对map的排序
bool cmp(pair<string,double> a,pair<string,double> b){
	return a.second>b.second; //>降序 <升序  自定义排序规则
}
vector< pair<string,double> > v(map.begin(),map.end());
sort(v.begin(),v.end(),cmp); 
```





