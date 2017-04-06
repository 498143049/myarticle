# Leetcode 解题报告


标签（空格分隔）： leetcode 解题报告

---
### Populating Next Right Pointers in Each Node II
### Populating Next Right Pointers in Each Node I

这道题目的思路很明显，考点就是层次遍历。因此采用层次遍历最为经典的做法，通过队列去实现。然后为了使层次可以区分开来，因此在采用递归的方式。对于时间复杂度就是N。
由于每一个都必须访问，因此时间已经不能再优化了。

显然程序访问下一个节点的时候，可以由父节点在子节点确定，因此，访问这一层的时候，可以由上层父节点可以本层节点确定。因此可以省去队列。

有人还提出了单循环的方法，其本质还是多循环，通过判断最后一个是NUll而且进行循环跳转，其实也是广度的优先的搜索的思想。

对于广度优先算法也可以使用3个点进行遍历

####Maximum Product Subarray
非常简单的动态规划，完全对。记住3个数的匹配算法。

####8. String to Integer (atoi)
1. 字符串混入非数字字符
2. 字符串为空 
3. 正常字符 -+(开头) .   
4. -2147483648  INT 最大最下值，还要记得防止溢出1

Longest Common Prefix  注意查看返回值的错误情况

### 13. Roman to Integer
罗马转化到整数，注意后面一个到一定比前面大的特点
string.back()   
std::string str ("hello world.");
  str.back() = '!';   //返回的是引用
## 12. Integer to Roman
采用枚举的方法，把900给枚举出来

### 牛客网刷题　
１. 注意整数　与字符串　cout 输出

### n　sum 问题
//Target Sum 获取一个目标值　








