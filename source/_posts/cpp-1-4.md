title: Reading an Unknown Number of Inputs
date: 2017-02-23 17:58:50
tags: cpp
---
# Reading an Unknown Number of Inputs

code is 

```
#include <iostream>

int main(int argc, const char * argv[]) {
    int sum = 0;
    int value = 0;
    while (std::cin >> value) {
        sum += value;
    }
    
    std::cout << "sum is " << sum << std::endl;
    return 0;
}
```

When we use an istream as a condition, the effect is to test the state of the stream. If the stream is valid—that is, if the stream hasn’t encountered an error—then the test succeeds. An istream becomes invalid when we hit end-of-file or encounter an invalid input, such as reading a value that is not an integer. An istream that is in an invalid state will cause the condition to yield false.

当我们使用istream当作一个条件变量时， 相当于测试这个stream的状态，当是stream是合法的，stream不会触犯一个error，这个测试就是成功的，返回true。 当istream读取到文件末尾符 或者读区到不合法的输入 （比如不适int类型的）istream就会处在一个不合法的状态，返回false。


