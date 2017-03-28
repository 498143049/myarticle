---
title: C++ 常考知识点
tags: C++,C语言,选择错题
grammar_cjkRuby: true
##### 运算优先级与求值顺序
1. status(1)||status(2)&&status(3);
2. 输出顺序还是为1_ 2 _3  虽然&& 的运算优先级高于|| 但是运算优先级值得是结合顺序和不是求值顺序。还是
``` c
status(1)||status(2)&&status(3);  equal
status(1)||(status(2)&&status(3));  
``` 
##### C地址内存分配的问题
```
char* getMem(void) {     
      char p[] = “hello world ”;
       p[5] = 0x0;
       return p;
 }
 void test(void) {     
      char *s = 0x0;
       s = getMem();
       printf(s);
 }
```
由于内存分配的时候，数组会使放在常亮区域，而不是静态区域，因此会不输出。或者说不确定。
如果
```
char* getMem(void) {
    char *p = "hello world";
    return p;
}
```
则正确输出但是，P不能跟改。（各种情况讨论，见[http://m.nowcoder.com/questions?from=ios_app_1.02.05&uuid=46a867eb0dc148708c2dbf1729a1515e]）

##### 几种错误的诊断 
1.出错
2. 输出为“”
3. 输出不确定 
4. 输出烫烫烫烫烫。
free（ptr） 如果为null ，没有任何操作，如果未定义。程序奔溃。

###### 类析构
类析构也会调用自己成员变量的析构函数。

##### 虚函数和函数重载 


##### c++ traits 内容


##### C++关于栈和堆
栈是在静态分配，而堆是动态分配的

##### struct C和C++中 的区别
```
(不定项选择题) 下面有关C++的类和C里面的struct的描述，正确的有？ 1/1
A 在C++中，来自class的继承默认按照private继承处理，来自struct的继承默认按照public继承处理
B class的成员默认是private权限，struct默认是public权限
C c里面的struct只是变量的聚合体，struct不能有函数
D c++的struct可有构造和析构函数
答案ADCD
```
##### 虚函数的多态性 
1.一般不建议在构造函数的里面调用虚函数，因为构造函数和析构函 的虚函数没有多态性。
2。不是虚函数不会动态绑定 。
```
有如下C++代码：
struct A{
  void foo(){printf("foo");}
  virtual void bar(){printf("bar");}
  A(){bar();}
};
struct B:A{
  void foo(){printf("b_foo");}
  void bar(){printf("b_bar");}
};
那么 
1
2
3
A *p=new B;
p->foo();
p->bar();
输出为：  
1/1
A barfoob_bar
B foobarb_bar
C barfoob_foo
D foobarb_fpp
```
##### 虚函数 
声明纯虚函数的是抽象类，不能实例化
基类被虚继才是虚基类。

##### 父类析构函数
父类的析构函数必须为

```
 virtual
 A* a = new B  //B是A的子类
    delete a 
    此时父类析构函数需要加virtual，如果不加virtual，那么最后只会调用A的析构函    数，而派生的部分，并没有得到析构，导致内存泄露。

    B* b = new B
    delete b
    此时父类析构函数并不需要加virtual，就是一个很正常的构造析构过程
    http://m.nowcoder.com/answer/55505?tagId=&pos=1&type=0&onlyWrong=false&source=home
```

##### 优先const原则
编程规范
```
1.始终用const限制所有指向只输入参数的指针和应用。
2.优先通过值来取得原始类型（如char、float）和复制开学比较低的值对象（如point、complex<float>）的输入。
3.优先按const的引用取得其他用户定义类型的输入；
4.如果函数需要其参数的副本，则可以通过值传递代替
https://yq.aliyun.com/articles/17351
```

##### 代码重用的方法，区别

1. 继承
2. 组合
3. 模板
4. 过滤

##### STL模板的分类
1.比如容器支持下标[]运算


