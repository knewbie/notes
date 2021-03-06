# go依赖安装

## 1. 问题
在安装一些Go的应用时，经常会有对`golang.org/x/*`库的依赖，这个依赖下的库都是托管在`google`的服务器上的，国内不FQ的话一般都不能正常访问，依赖库无法正常下载安装，就导致应用无法正常安装。

## 2.解决
既然没法直接安装`golang.org/x/*`的依赖问题，但是我们可以从`github.com/golang`下去手动安装这些依赖库的镜像，`clone`的时候，只需要保证程序中对这些库的引入目录结构就可以了。类似于`golang.org/x/crypto` 这样的结构，为了自动这些问题，通过以下脚本来处理实现：
我们取名脚本为：`x_dep_pull.sh`

```shell
#!/bin/sh

X_DEP_PREFIX="https://github.com/golang/"
X_DEPS="crypto text net tools sys"

```