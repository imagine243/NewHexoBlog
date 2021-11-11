title: cpp_duotai
date: 2016-10-19 19:53:54
tags: c++
---

## c++的运行时多态
之前看到一个介绍c＋＋多态的例子，亲手实验的结果与我设想的结果不一致，我自己在这个问题上产生了错误。
例子是：
    #include <iostream>

    class A
    {
        public :
        virtual ~A()
        {
            std::cout<< "A deleted" <<std::endl;
        };
        virtual void out1() = 0;
        virtual void out2()
        {
            std::cout<< "A (out2) "<<std::endl;
        }
        
        void out3()
        {
            std::cout<< "A (out3) "<<std::endl;
        }
    };
    
    
    class B : public A
    {
    public:
        virtual ~B()
        {
            std::cout<< "B deleted" <<std::endl;
        };
        
        void out1()
        {
            std::cout<< "B (out1) " <<std::endl;
        }
        
        void out2()
        {
            std::cout<< "B (out2) " <<std::endl;
        }
        
        void out3()
        {
            std::cout<< "B (out3) " <<std::endl;
        }
    };
    
    int main(int argc, const char * argv[]) {   
        A * a = new B;
        a->out1();
        a->out2();
        a->out3();
        
        B * b = new B;
        b->out1();
        b->out2();
        b->out3();
        
        B * c = new B;
        c->B::out1();
        c->A::out2();
        c->A::out3();
        
        delete a;
        delete b;
        delete c;
        
        return 0;
    }

### 笔记

A::out1() 是纯虚函数 只能被子类实现，不能直接调用  c->A::out1() 是错误的
 
 a->out3() 调用的是A::out3() out3 是一个普通的函数  a指针是A类型的所以调用的是A::out3()  (震惊到我了)
 
 out2 是虚函数 实现了运行时多态 父类的指针在运行时动态执行子类的out2函数
 
 总结 out1 纯虚函数 就像是java中的接口定义了子类必须要实现的行为
      out2  虚函数 在cpp中实现了运行时多态
     out3 普通函数  子类的out3并不会替代父类中的out3，而是同时存在，根据指针类型来调用 或者显式的声明调用的是哪个函数 通过A::out3() 或者 B::out3() 这样的方式


