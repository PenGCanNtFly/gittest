---
title: ubuntu安装oh-my-zsh
toc: true
comments: true
date: 2016-08-11 16:32:27
tags:
  - shell
---

参考： [池建强 终极shell](http://macshuo.com/?p=676)

ubuntu版本
```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
```
<!--more -->

# 安装zsh

```
$ sudo apt install zsh
```
查看当前系统有几种shell
```
$ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/bin/zsh
/usr/bin/zsh

```

安装完成之后设置当前用户使用zsh
```
$ sudo chsh -s /bin/zsh
```
之后注销 && 重新登入

# 安装oh-my-zsh
1. 自动安装
```
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

2. 手动安装
```
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```

oh my zsh主题：
1. github
[oh-my-zsh External themes](https://github.com/robbyrussell/oh-my-zsh/wiki/External-themes)

2. local
```
$ ls ~/.oh-my-zsh/themes
```
默认的主题
```
ZSH\_THEME=”robbyrussell”
```

修改`~/.zshrc`文件可更改主题:
```
ZSH\_THEME="agnosterzak"
```

oh my zsh 插件：
```
$ ls ~/.oh-my-zsh/plugins
```


# 字体乱码解决
解决参考链接： [fonts-powerline](https://github.com/robbyrussell/oh-my-zsh/issues/1906)

![fonts-powerline](/images/fonts-powerline.png)

In Ubuntu (16.04), this works:
```
$ sudo apt-get install fonts-powerline
```

# 安装`zsh`之后提示`hexo`命令找不到的解决
解决参考链接： [Command not found after npm install in zsh](http://stackoverflow.com/questions/12743928/command-not-found-after-npm-install-in-zsh)
![node\_not\_found](/images/node_cmd.png)

查看npm的安装路径：
```
$ whereis npm
npm: /usr/bin/npm /usr/share/npm /home/yangg01/.nvm/versions/node/v6.3.1/bin/npm /usr/share/man/man1/npm.1.gz
```

打开`~/.zshrc`在最后加入:
```
export PATH=/usr/share/npm/bin:$PATH
```

Done
