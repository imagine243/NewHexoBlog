title: summary about reading <<cpp primer>>
date: 2017-02-23 18:11:54
tags: cpp
---
# summary about reading <<cpp primer>>

## Entering an End-of-File from the Keyboard

When we enter input to a program from the keyboard, different operating systems use different conventions to allow us to indicate end-of-file. On Windows systems we enter an end-of-file by typing a control-z—hold down the Ctrl key and press z—followed by hitting either the Enter or Return key. On UNIX systems, including on Mac OS X machines, end-of-file is usually control-d.

输入文件终止符 

从键盘上输入文件终止符 在windows上是 ctrl + z 在unix系统上包括mac 是ctrl + d.

## Using File Redirection 
It can be tedious to repeatedly type these transactions as input to the programs you are testing. Most operating systems support file redirection, which lets us associate a named file with the standard input and the standard output:

$ addItems <infile >outfile

Assuming $ is the system prompt and our addition program has been compiled into an executable file named addItems.exe (or addItems on UNIX systems), this command will read transactions from a file named infile and write its output to a file named outfile in the current directory.

使用文件重定向 我们可以使用文件重定向到程序中的输入 cin 输出 cout ，这样程序就可以使用文件作为输入和输出。

# Advice: Deciding which Type to Use
C++, like C, is designed to let programs get close to the hardware when necessary. The arithmetic types are defined to cater to the peculiarities of various kinds of hardware. Accordingly, the number of arithmetic types in C++ can be bewildering. Most programmers can (and should) ignore these complexities by restricting the types they use. A few rules of thumb can be useful in deciding which type to use:

• Use an unsigned type when you know that the values cannot be negative.

• Use int for integer arithmetic. short is usually too small and, in practice, long often has the same size as int. If your data values are larger than the minimum guaranteed size of an int, then use long long.

• Do not use plain char or bool in arithmetic expressions. Use them only to hold characters or truth values. Computations using char are especially problematic because char is signed on some machines and unsigned on others. If you need a tiny integer, explicitly specify either signed char or unsigned char.

• Use double for floating-point computations; float usually does not have enough precision, and the cost of double-precision calculations versus single-precision is negligible. In fact, on some machines, double-precision operations are faster than single. The precision offered by long double usually is unnecessary and often entails considerable run-time cost.

建议 使用哪种类型
* 去定是正数时使用 unsigned 类型
* 使用int做数值运算
* 不要char 和 bool 类型 在算数运算中
* 使用 double类型做浮点运算

# 建议：避免强制类型转换
![](/uploads/14889592935857.jpg)


