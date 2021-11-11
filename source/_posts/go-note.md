title: go_note
date: 2018-01-27 10:06:06
tags: golang note
---

# go 笔记 

### go package 

go 的package可以简单的理解问文件夹， 文件夹的名字就是package的名字。 这个文件夹 可以是通过go get下载到GOPATH下的 ，也可以是github上的repo，还可以是相对路径下的某个文件夹。
例如：godoc生成文档时以package为目标 

``` 
godoc chao
```
godoc会去GOPATH下的src目录中找chao目录

```
godoc ./chao
```
godoc会去当前目录下寻找chao package


