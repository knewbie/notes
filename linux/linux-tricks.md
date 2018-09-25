# Linux系统下的一些小技巧

##  getconf 查询系统变量
```
    # 查看系统的线程库
    $ getconf GNU_LIBPTHREAD_VERSION
    NPTL 2.24
```

##  ulimit改善系统性能
通过`ulimit`命令，可以修改系统的一些资源限制，来提高系统性能，具体介绍可以参考这篇[文章](https://www.ibm.com/developerworks/cn/linux/l-cn-ulimit/)

##  indent格式化C语言风格
`indent -bad -bli 0 -ce -kr -nsob --space-after-if --space-after-while --space-after-for --use-tabs -i8
`

