title: 在mac终端中使用at命令
date: 2015-09-19 22:02:43
tags: mac 
tags: at命令
categories : mac
---

### 在mac终端中使用at命令
今天发现在mac下没有办法使用at命令。
提示到

> Note that at is implemented through the launchd(8) daemon periodically invoking atrun(8), which is disabled by default.  See atrun(8) for information about enabling atrun.

接着man atrun
> The atrun utility runs commands queued by at(1).  It is invoked periodi-cally by launchd(8) as specified in the com.apple.atrun.plist propertylist.  By default the property list contains the Disabled key set to true, so atrun is never invoked.
>
> Execute the following command as root to enable atrun:
> launchctl load -w /System/Library/LaunchDaemons/com.apple.atrun.plist

看来只需要在mac中开启atrun的配置。
### 开启atrun配置

修改 /System/Library/LaunchDaemons/com.apple.atrun.plist 文件，把其中true改为false
先调用 
> sudo launchctl unload -F /System/Library/LaunchDaemons/com.apple.atrun.plist
然后调用 
> sudo launchctl load -F /System/Library/LaunchDaemons/com.apple.atrun.plist

### at 命令
> $ at now + 1 minute  
> echo 'test at commond ' > test.txt
> <EOD>

<EOD> 是ctrl ＋ D

然后就可以看到新建了一个test.txt文件， 内容是'test at commond'。
