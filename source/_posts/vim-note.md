title: vim_note
date: 2017-07-22 13:51:31
tags: vim
---
# vim note
我的vimrc是[vimrc](https://raw.githubusercontent.com/imagine243/dotfile/master/.vimrc) 


##### 新的环境下配置自己的vim

首先从github上将的vimrc clone下来，并链接到用户~目录下 
            git clone https://github.com/imagine243/dotfile.git
            ln -s dotfile/.vimrc ~/vimrc
然后手动安装Vundle 插件， 通过Vundle安装其他插件
            mkdir ~/.vim
            mkdir ~/.vim/bundle
            git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
            进入vim 执行 PluginInstall 命令
    安装每个插件需要的软件
            ctrlp 使用了 ag （https://github.com/ggreer/the_silver_searcher） 来搜索  需要安装ag
            YouCompleteMe (https://github.com/Valloric/YouCompleteMe)  按照文档安装
    


##### 在 normal模式下输入 q：（不是:q 不是退出vim） 就可以显示出 历史命令列表，可以把之前用过的几个命令组成函数来一次性执行。

##### 添加了vim-go的快捷键在vim-go的bundle下

##### 添加了buffer切换的快捷键 <f5>
```
" switch buffers
nnoremap <F5> :buffers<CR>:buffer<Space> 
```
按下f5再输入buffer的id 或者名字  或者 tab选择都可以

##### 搜索
搜索当前光标下的单词  直接按 *


```
" Search for visually selected text use key //
vnoremap // y/<C-R>"<CR>
```
搜索当前选中的文字  按两下//


