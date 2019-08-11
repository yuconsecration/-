11### 使用该函数，只需引用头文件：

> #include<algoritnm>

### 语法描述为： 

> // 参数begin，end 表示一个范围，分别为待排序数组的首地址和尾地址

> // 排列的数组中包括左边的 begin 但不包括右边的 end 

> sort (begin,end)

> // sort (a,a+10)将把数组a按升序排序，因为sort函数默认为升序

### 将数组按降序排列的方法一：

> 自己编写 compare 函数

> // 两个分别表示待排序数组的首地址和尾地址，compare 表示比较的类型

> sort (begin ,end ,compare)

```
#include<iostream>
// 使用sort函数的头文件说明
#include<algorithm>
using namespace std;
// 自己编写函数来实现升序排列
bool compare (int a,int b)
{
    // 升序排列，如果改为return a>b ,则为降序
    return a<b;
}
int main()
{
    int a[10] = {7,4,5,23,2,73,41,52,28,60},i;
    for(i=0;i<10;i++)
        cout<<a[i]<<" ";
    cout<<endl;
    sort(a,a+10,compare);
    for(i=0;i<10;i++)
        cout<<a[i]<<" ";
    return 0;
}
```

### 将数组按降序排列方法二：

> 利用 functional 标准库
> 使用头文件 #include<functional>即可使用标准库
> functional 提供了如下的基于模板的比较函数对象
> equal_to<Type>: 等于
> not_equal_to<Type>: 不等于
> greater<Type>: 大于
> greater_equal<Type>: 大于等于
> less<Type>: 小于
> less_equal<Type>: 小于等于 
> 对于这个问题来说，greater和less就足够了，可以直接拿来用
> 升序：sort(begin,end,less<data-type>())
> 降序：sort(begin,end,greater<data-type>())

```
#include<iostream>
// 调用sort函数的头文件说明
#include<algorithm>
// 调用functional库的头文件说明
#include<functional>
using namespace std;
int main()
{
    int a[10] = {7,4,5,23,2,73,41,52,28,60},i;
    for(i=0;i<10;i++)
        cout<<a[i]<<" ";
    cout<<endl;
    // 降序
    sort(a,a+10,greater<int>());
    for(i=0;i<10;i++)
        cout<<a[i]<<" ";
    return 0;
}
```
