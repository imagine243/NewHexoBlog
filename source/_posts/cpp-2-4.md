title: const
date: 2017-02-28 17:38:14
tags: cpp
---

# const

# const作用范围
默认情况下 const的对象仅在文件内有效， 要做到每个使用了const 对象的文件都能访问到它的初始值，就需要在每个文件中定义同名的const变量。
这样就会产生大量的重复定义，解决办法是 在定义前面添加 extern 关键字，这样就只需要定义一次。

![](/uploads/14882751985729.jpg)

# const 引用

一种引用方式是原本的对象就是常量，引用也是常量，都不可以改变

~~~
        const int ci = 1024;
        const int &ri = ci;
        cout<< ri<< endl;
~~~

但是原本的对象可以不适常量， 引用可以是常量也可以不是，但是引用和原本对象之间的绑定关系不可以改变，原本对象可以改变。如下图所解释的。

![](/uploads/14883392364050.jpg)

~~~
        int ci = 1024;
        const int &ri = ci;
        ci = 1111;
        cout<< ri<< endl;
~~~

这中间的机制是，原本ci进行了自动转化为const int类型。


# 顶层const与底层const

![](/uploads/14887833321005.jpg)

![](/uploads/14887833419019.jpg)

# constexpr 
constexpr 类型定义一个编译器来验证变凉的值是否是一个常量表达式，关键是在编译期检查。
constexpr 可以定义变量和函数。
constexpr定义的指针是顶层const。

# decltype


