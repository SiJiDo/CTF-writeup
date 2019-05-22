**linux的配置文件**

```
/proc/self/environ
```

这个文件可以获取以下属性

`PWD`:当前目录

`HOME`:当前用户文件夹

`NAME`:当前用户名

`MAIL`:邮箱位置



在linux下如果可以直接运行的命令，一般路径为

```
/bin			#该路径下存放的是基本系统命令，如:cat
/sbin			#该路径下存放的是系统级命令，如：reboot
/usr/bin		#该路径下存放的是普通下载软件的命令,如:sqlmap
/usr/sbin		#该路径下存放的是网络级软件命令，如:sshd
```

如果是一般情况下，去`/usr/bin`里面找会有额外发现，但讲道理，一般是ELF二进制文件，很少有py脚本，sh脚本之类的



对于重定向shell脚本中的变量可以利用该方式创建新文件

```
Note that the filename is prepended with %09 which is a horizontal tab. This is required because the reply function would interpret the name as directory name and the command would fail.

第二种解释
The bug is due to array handling in bash, which is indicated by the parenthesis. You’re actually creating a 2 element array with the first element being the file you want. When you dereference an array in bash with no index, it’s implicitly the first element.
```

不光%09, %20也可以,但是并不能复现个简单的demo，还是我太菜不太清楚shell语言的问题



再附上一个shell的rec脚本

```
$output=$($URL_PARAMS['cmd']); echo $output;
```



知识点源于：csaw-ctf-2016-quals WEB wtf.sh
