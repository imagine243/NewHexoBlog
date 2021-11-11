title: 类型转换
date: 2017-02-27 14:53:11
tags: cpp
---

# 类型转换

![](/uploads/14881784087961.jpg)

• When we assign one of the nonbool arithmetic types to a bool object, the result is false if the value is 0 and true otherwise.

• When we assign a bool to one of the other arithmetic types, the resulting value is 1 if the bool is true and 0 if the bool is false.

• When we assign a floating-point value to an object of integral type, the value is truncated. The value that is stored is the part before the decimal point.

• When we assign an integral value to an object of floating-point type, the fractional part is zero. Precision may be lost if the integer has more bits than the floating-point object can accommodate.

• If we assign an out-of-range value to an object of unsigned type, the result is the remainder of the value modulo the number of values the target type can hold. For example, an 8-bit unsigned char can hold values from 0 through 255, inclusive. If we assign a value outside this range, the compiler assigns the remainder of that value modulo 256. Therefore, assigning –1 to an 8-bit unsigned char gives that object the value 255.

• If we assign an out-of-range value to an object of signed type, the result is undefined. The program might appear to work, it might crash, or it might produce garbage values.

![](/uploads/14881789121875.jpg)

经常遇到的 给一个类型赋值超出了他的表达范围时 可以使用这个方法。

几个例子 

~~~
    unsigned char c ;
    int i;
    c = -5;
    i = c;
    std::cout << "unsigned char c is " << c << "  " << i <<std::endl;
    
    c = -246;
    i = c;
    std::cout << "unsigned char c is " << c << "  " << i <<std::endl;
    
    c = 266;
    i = c;
    std::cout << "unsigned char c is " << c << "  " << i <<std::endl;
~~~

输出是

~~~
unsigned char c is \373  251
unsigned char c is 
  10
unsigned char c is 
  10
~~~


![](/uploads/14881820834730.jpg)



