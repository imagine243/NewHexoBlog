title: work_notify
date: 2017-02-16 14:31:00
tags: work
---

### 效率提高 － 工作中的通知
工作中经常有一些在命令行下的的任务，不需要实时看着，同时需要大量的时间。
这样的任务只需要工作完成后通知一下就可以。添加了一个系统的通知命令来实现。

#### 添加命令
参考的这里的答案  [参考链接](http://apple.stackexchange.com/questions/57412/how-can-i-trigger-a-notification-center-notification-from-an-applescript-or-shel)

AppleScript 可以发送系统的通知 命令如下

```
osascript -e 'display notification "Lorem ipsum dolor sit amet" with title "Title"'
```

![apple_sript_notify](/uploads/apple_sript_notify.png)

我们在/usr/local/bin 下添加一个名字是notify的脚本，然后chmod ＋x 添加执行权限，脚本如下。

```
#!/bin/bash
/usr/bin/osascript -e "display notification \"$*\" with title \"$1\" "
```

现在我们可以使用通知了

```
notify job done
```

延时5s通知

```
sleep 5; notify job done
```




