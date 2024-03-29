---
layout:     post
title:      算法
summary:
categories: Interview
technique: true
---

> 判断一个算法的好坏，一般从执行时间和占用空间来看,执行时间越短，占用的内存空间越小，那么它就是好的算法。对应的，我们常常用时间复杂度代表执行时间，空间复杂度代表占用的内存空间。

# 时间复杂度
> 时间复杂度的计算并不是计算程序具体运行的时间，而是算法执行语句的次数。

随着n的不断增大，时间复杂度不断增大，算法花费时间越多。 常见的时间复杂度有

- 常数阶O(1)
- 对数阶O(log2 n)
- 线性阶O(n)
- 线性对数阶O(n log2 n)
- 平方阶O(n^2)
- 立方阶O(n^3)
- k次方阶O(n^K)
- 指数阶O(2^n)

如果算法的执行时间不随n的增加而增长，假如算法中有上千条语句，执行时间也不过是一个较大的常数。此类算法的时间复杂度是O(1)。 举例如下：代码执行100次，是一个常数，复杂度也是O(1)。

```javascript
let x = 1;
while (x <100) {
  x++;
}
``` 
有多个循环语句时候，算法的时间复杂度是由嵌套层数最多的循环语句中最内层语句的方法决定的。举例如下：在下面for循环当中，外层循环每执行一次，内层循环要执行n次，执行次数是根据n所决定的，时间复杂度是O(n^2)。

```javascript
for (i = 0; i < n; i++){
  for (j = 0; j < n; j++) {
      // ...code
  }
}
```

循环不仅与n有关，还与执行循环判断条件有关。举例如下：在代码中，如果arr[i]不等于1的话，时间复杂度是O(n)。如果arr[i]等于1的话，循环不执行，时间复杂度是O(0)。

```javascript
for(var i = 0; i<n && arr[i] !=1; i++) {
  // ...code
}
```
  
# 空间复杂度
> 空间复杂度是对一个算法在运行过程中临时占用存储空间的大小。
