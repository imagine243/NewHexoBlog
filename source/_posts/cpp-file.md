Ititle: cpp_file
date: 2016-09-03 23:16:02
tags: c++
---

## c++ 的文件操作

资料 http://www.cplusplus.com/doc/tutorial/files/

原来一直分不清c与c＋＋ 对文件的读写的不同，同时对c＋＋ 中文件读写也了解的不够详细，cplusplus 上的这篇文章详细易懂，写一下笔记。

### 文件操作类
- ofstream: Stream class to write on files
- ifstream: Stream class to read from files
- fstream: Stream class to both read and write from/to files.

    // basic file operations
    #include <iostream>
    #include <fstream>
    using namespace std;
    
    int main () {
      ofstream myfile;
      myfile.open ("example.txt");
      myfile << "Writing this to a file.\n";
      myfile.close();
      return 0;
    }

### 打开关闭文件
open(filename, mode)

mode :
- ios::in	打开读取的文件
- ios::out	打开写入的文件
- ios::binary	以二进制的方式打开文件
- ios::ate	设置初始的指针在文件的末尾，如果没有设置这个，初始的指针在文件的开头
ios::app	All 所有的写入操作都会添加在文件的末尾
ios::trunc 如果写入的文件已经存在且有内容，原来的内容会被删除写入新的内容。

    ofstream myfile;
    myfile.open ("example.bin", ios::out | ios::app | ios::binary);
    
默认情况下：
ofstream ios::out
ifstream ios::in
fstream ios::in | ios::out

这三个类的构造函数跟open函数有异样的作用

    ofstream myfile ("example.bin", ios::out | ios::app | ios::binary);

可以使用is_open() 来检查文件是否成功的打开

    if (myfile.is_open()) { /* ok, proceed with output */ }

关闭文件

    myfile.close()
    
### 文本文件
    // writing on a text file
    #include <iostream>
    #include <fstream>
    using namespace std;
    
    int main () {
      ofstream myfile ("example.txt");
      if (myfile.is_open())
      {
        myfile << "This is a line.\n";
        myfile << "This is another line.\n";
        myfile.close();
      }
      else cout << "Unable to open file";
      return 0;
    }
    
    // reading a text file
    #include <iostream>
    #include <fstream>
    #include <string>
    using namespace std;
    
    int main () {
      string line;
      ifstream myfile ("example.txt");
      if (myfile.is_open())
      {
        while ( getline (myfile,line) )
        {
          cout << line << '\n';
        }
        myfile.close();
      }
    
      else cout << "Unable to open file"; 
    
      return 0;
    }

### 检查状态

- bad()
Returns true if a reading or writing operation fails. For example, in the case that we try to write to a file that is not open for writing or if the device where we try to write has no space left.
- fail()
Returns true in the same cases as bad(), but also in the case that a format error happens, like when an alphabetical character is extracted when we are trying to read an integer number.
- eof()
Returns true if a file open for reading has reached the end.
- good()
It is the most generic state flag: it returns false in the same cases in which calling any of the previous functions would return true. Note that good and bad are not exact opposites (good checks more state flags at once).

### 读取写入的位置

tellg() 和 tellp() 函数 返回值是 streampos类型的

seekg() 和 seekp()

seekg ( position );
seekp ( position );

seekg ( offset, direction );
seekp ( offset, direction );

- ios::beg	offset counted from the beginning of the stream
- ios::cur	offset counted from the current position
- ios::end	offset counted from the end of the stream

    // obtaining file size
    #include <iostream>
    #include <fstream>
    using namespace std;
    
    int main () {
      streampos begin,end;
      ifstream myfile ("example.bin", ios::binary);
      begin = myfile.tellg();
      myfile.seekg (0, ios::end);
      end = myfile.tellg();
      myfile.close();
      cout << "size is: " << (end-begin) << " bytes.\n";
      return 0;
    }
    
### 二进制
    // reading an entire binary file
    #include <iostream>
    #include <fstream>
    using namespace std;
    
    int main () {
      streampos size;
      char * memblock;
    
      ifstream file ("example.bin", ios::in|ios::binary|ios::ate);
      if (file.is_open())
      {
        size = file.tellg();
        memblock = new char [size];
        file.seekg (0, ios::beg);
        file.read (memblock, size);
        file.close();
    
        cout << "the entire file content is in memory";
    
        delete[] memblock;
      }
      else cout << "Unable to open file";
      return 0;
    }
    
### buffer和同步

在写入操作时是先写入了一块固定大小的buffer中，当文件关闭或者buffer满了就会写入文件，也可以调用sync() 将buffer写入文件



