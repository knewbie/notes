<<<<<<< HEAD
# linux_cmd_ar

`ar`命令是*nix系统下的一个命令行工具，用来打包`C/C++`编译过后的`.o`对象文件的.
=======
vnote_backup_file_826537664 /home/kevin/mynotebooks/notes/linux/linux_cmd_ar.md
# linux_cmd_ar

`ar`命令是*nix系统下的一个命令行工具，用来打包`C/C++`编译过后的`.o`对象文件的。

在项目接入iOS渠道SDK时，经常会碰到一个文件
>>>>>>> 61068dbc34675157c9a2e38d96add539666dda2f

原文标题：ar命令解压.a时候，报错 is a fat file (use libtool(1) or lipo(1) and ar(1) on it)

原文链接：http://www.ithao123.cn/content-5582077.html

查看静态库文件的命令

file xxx.a

lipo -info xxx.a

在解压 .a 文件时，报了一个类似 xxx.a is a fat file (use libtool(1) or lipo(1) and ar(1) on it) 的错误，

经过查找资料，原来是因为该 .a 文件包含了多个 cpu 架构，比如 armv7，armv7s 等，此时可以用如下命令：

lipo xx. a -thin armv7 -output xx_armv7.a

lipo lxx. a -thin armv7s -output xx_armv7s.a

可以参考：ar : is a fat file (use libtool(1) or lipo(1) and ar(1) on it)

然后再使用，ar -x xx_armv7.a，就可以成功的解压出各个 .o 了。

如果还想查看 .o 的反编译代码，在 Mac 上可以用 otool 这个命令来反编译 .o 文件，比如 otool -tv xx.o

可以参考： Mac 的反编译工具一：otool （objdump 工具的 OSX 对应工具）