# Zsh

我们将安装 `zsh` ，其拓展功能和主题将由 [oh-my-zsh](http://ohmyz.sh/) 提供。其中`Env.sh` 文件用于维护别名（aliases），输出（exports）和路径改变（path changes）等等，以免影响 `~/.zshrc`。

### Zsh

使用 Homebrew 完成 zsh 和 zsh completions 的安装

        brew install zsh zsh-completions

安装 oh-my-zsh 让 zsh 获得拓展功能和主题

        curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh

用文本编辑器或 vi 打开 `.zshrc` 进行以下编辑:

        ZSH_THEME="dpoggi"
        alias zshconfig="vi ~/.zshrc"
        plugins=(git history history-substring-search jsontools python autojump osx wd extract zsh-autosuggestions)
        
        ### 选择性使用下面快捷配置
        alias envconfig="vi ~/Projects/config/env.sh"
        
用文本编辑器或 vi 打开 `~/Projects/config/env.sh` 进行以下编辑:
~~~
    #!/bin/zsh

    # PATH
    export PATH="/usr/local/share/python:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    export EDITOR='vi -w'
    # export PYTHONPATH=$PYTHONPATH
    # export MANPATH="/usr/local/man:$MANPATH"

    # Virtual Environment
    export WORKON_HOME=$HOME/.virtualenvs
    export PROJECT_HOME=$HOME/Projects
    source /usr/local/bin/virtualenvwrapper.sh

    # Owner
    export USER_NAME="YOUR NAME"
    eval "$(rbenv init -)"

    # FileSearch
    function f() { find . -iname "*$1*" ${@:2} }
    function r() { grep "$1" ${@:2} -R . }

    #mkdir and cd
    function mkcd() { mkdir -p "$@" && cd "$_"; }

    # Aliases
    alias cppcompile='c++ -std=c++11 -stdlib=libc++'
~~~

---
`注：`

如果是新增环境变量或者是修改环境变量的值，都需要 source 一下才能立即生效。

如果是删除一个环境变量，必须输入 exit 以 logout 当前 shell ，然后再重新打开一个新的 shell 并 login 才能生效。

#### 默认进入zsh
```angularjs
    $ cat /etc/shells
    $ chsh -s /bin/zsh
```

### Zsh插件
zsh提供了丰富的插件，具体见上面`oh-my-zsh`的拓展，下面例举实用插件：

#### 插件wd
能够建立快捷进入某个目录，如：

建立快捷

    $ cd /home/local/www
    $ wd add www

使用快捷，进入目录`/home/local/www`

    $ wd www
 
#### 相关快捷键

- `ctrl + r` : 历史指令联想
- `ctrl + w` : 删除当前指令前一个单词
- `ctrl + u` : 删除当前指令行
- `ctrl + a` ：指令行首
- `ctrl + e` ：指令行尾
- `ctrl + e` ：指令行尾
- `ctrl + e` ：指令行尾
- `x cms.tar.gz` : 解压文件
