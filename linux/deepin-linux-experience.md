Deepin 15.5 体验总结
整体界面风格比几年前有了更好的体验，很多操作也跟Windows下相同了，docker有两种风格，可以类似于windows的，也可以类似于Mac的风格。

## Qt开发环境的输入法配置

自己安装的Qt5.9.0，踩到的坑是`fcitx`无法在`Qt Creator`中输入中文 ， 以及通过Qt编译出来的应用程序，原因是Qt缺少了`fcitx-qt5`的输入依赖库。
解决办法：下载`fcitx-qt5`源码编译生`libfcitxplatforminputcontextplugin.so`

* 1. fctix-qt5 的源码有两个地方可以下载：

```shell
    wget https://download.fcitx-im.org/fcitx-qt5/fcitx-qt5-1.0.5.tar.xztar -xJf fcitx-qt5-1.0.5.tar.xz

    git clone http://github.com/fcitx/fcitx-qt5.git
```

* 2. 编译, build.sh

```shell
    #!/bin/bash

    CMD_PATH=`dirname $0`
    FCITX_QT_DIR=`realpath $1`
    BUILD_DIR=$FCITX_QT_DIR/build
    
    if [ ! -d $FCITX_QT_DIR ]; then
        echo "Wrong fcitx-qt directory"
        exit 1
    fi

    userdir=`env | grep ^HOME= | cut -c 6-`
    
    # Qt5的安装目录，根据个人的自行修改
    qt5Creator=${userdir}/Qt5.9.0/Tools/QtCreator/lib/Qt/plugins/platforminputcontexts
    qt5gcc_64=${userdir}/Qt5.9.0/5.9/gcc_64/plugins/platforminputcontexts
    export Qt5_DIR=${userdir}/Qt5.9.0/5.9/gcc_64/lib/cmake/Qt5

    rm -r $BUILD_DIR
    mkdir $BUILD_DIR
    cd    $BUILD_DIR

    # 安装依赖
    sudo apt install gcc g++ cmake extra-cmake-modules
    sudo apt install libgl1-mesa-dev libglu1-mesa-dev libxkbcommon-dev fcitx-libs-dev

    cmake ../
    make

    libfcix=$BUILD_DIR/platforminputcontext/libfcitxplatforminputcontextplugin.so

    sudo cp $libfcix ${qt5Creator}
    sudo cp $libfcix ${qt5gcc_64}
    sudo chmod +x  ${qt5Creator}/libfcitxplatforminputcontextplugin.so
    sudo chmod 777 ${qt5Creator}/libfcitxplatforminputcontextplugin.so
    sudo chmod +x  ${qt5gcc_64}/libfcitxplatforminputcontextplugin.so
    sudo chmod 777 ${qt5gcc_64}/libfcitxplatforminputcontextplugin.so
```

* 3. 重启Qt Creator & 重新编译应用程序，解决无法输入中文的问题

如果是因为安装了不同版本的Qt， 一般都可以通过以上方法解决该问题的。

## 命令行工具
###  shell配置

默认为`bash`，为了用`oh my zsh`,  必须安装`zsh`。
```
    $ sudo apt-get install zsh
    $ chsh -s `which zsh`
    $ logout & login, 默认shell切成zsh
    $ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 剪贴板
 linux的系统剪贴板使用`xsel`，默认是不安装的，为了能使用`Ctrl-c`,`Ctrl+v`, 需要安装该命令: `sudo apt-get install xsel`

### locate命令
安装`mlocate`
```
    $ sudo apt-get install mlocate
    $ updatedb
```

### Linux下查看API文档工具Zeal
`sudo apt-get install zeal`
