Linux C编程时常会用到的一些头文件：

## 数据类型
### stdint.h

```
    uint8_t
    uint16_t
    uint32_t
    uint64_t
    ....
```

### stdbool.h

 C语言中是没有bool类型的（C++中有），若要使用此类型，需要包含头文件stdbool.h  

```
    bool/true/flase/
```

###  stddef.h
```
size_t  //机器相关的无符号类型，它被设计的足够大以便能表示内存中任意对象的大小
ptrdiff_t // 表示指针相减的结果，是一种带符号类型
NULL

```

##  变量 
### errno.h
```
errno
```

### stdlib.h
```
EXIT_SUCCESS
EXIT_FAILURE
```

### sys/stat.h
通过`open`在操作文件时需要指定相关的操作标志，针对用户权限定义时的变量有：
```
S_IRUSR：用户读权限
S_IWUSR：用户写权限
S_IRGRP：用户组读权限
S_IWGRP：用户组写权限
S_IROTH：其他组都权限
S_IWOTH：其他组写权限
```
