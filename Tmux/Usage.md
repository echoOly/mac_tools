### Session操作命令

启动新会话

```
$ tmux
```

启动新会话并指定名字`myname`

```
$ tmux new -s myname
```

在后台启动新会话并指定名字`myname`

```
$ tmux new -s myname -d
```

列出所有的会话

```
$ tmux ls
```

加载默认会话（最近打开的会话）

```
$ tmux a #
```

根据名字加载会话

```
$ tmux a -t myname
```

终止指定会话（也可以进入指定回话，然后`exit`退出）

```
$ tmux kill-session -t myname
```

### 配置文件

> `tmux`的前缀命令（`PREFIX`）默认是`ctrl+b`；个人习惯使用`ctrl+a`，如果需要更改，可以在配置文件中`~/.tmux.conf`修改，如下：

```angularjs
# bind a reload key
bind R source-file ~/.tmux.conf ; display-message "Config reloaded.."
 
unbind C-b
set -g prefix C-a
 
set -g base-index 1
setw -g pane-base-index 1
setw -g mode-keys vi

# 状态栏
# 颜色
set -g status-bg black
set -g status-fg white

# 对齐方式
set-option -g status-justify centre

# 左下角
set-option -g status-left '#[bg=black,fg=green][#[fg=cyan]#S#[fg=green]]'
set-option -g status-left-length 20

# 窗口列表
setw -g automatic-rename on
set-window-option -g window-status-current-format '#[dim]#I:#[default]#W#[fg=grey,dim]'
set-window-option -g window-status-format '#[fg=cyan,bold]#I#[fg=blue]:#[fg=cyan]#W#[fg=dim]'

# 右下角
set -g status-right '#[fg=green][#[fg=cyan]%Y-%m-%d#[fg=green]]'
#开启window事件提示
setw -g monitor-activity on
set -g visual-activity on
  
```

>其他设置

```angularjs
setw -g mouse-resize-pane on
setw -g mouse-select-pane on
setw -g mouse-select-window on
setw -g mode-mouse on
```
这几行的作用分别是:
* 开启用鼠标拖动调节pane的大小（拖动位置是pane之间的分隔线）
* 开启用鼠标点击pane来激活该pane
* 开启用鼠标点击来切换活动window（点击位置是状态栏的窗口名称）
* 开启window/pane里面的鼠标支持（也即可以用鼠标滚轮回滚显示窗口内容，此时还可以用鼠标选取文本，复制文本按住shift）

### 操作快捷键
> 在执行具体功能命令之前都需要先按`PREFIX`(`ctrl+a`)，下面列出了一些常用的操作命令

#### Session相关操作 

|快捷键 |说明
|--------|--------
|`PREFIX + s`   | 查看/切换session
|`PREFIX + d`   | detach；退出会话，tmux会话在后台继续执行
|`PREFIX + $`   | 重命名当前Session

#### Window相关操作

|快捷键 |说明
|--------|--------
|`PREFIX + c`   | 创建新的窗口
|`PREFIX + space`  | 切换到上一个活动的窗口
|`PREFIX + &`   | 关闭一个窗口，输入`exit`等效
|`PREFIX + 1~9`   | 使用窗口号切换
|`PREFIX + ,`   | 命名窗口
|`PREFIX + .`   | 移动窗口

#### Pane相关操作

|快捷键 |说明
|--------|--------
|`PREFIX + "`   | 创建垂直分割面板
|`PREFIX + %`   | 创建水平分割面板
|`PREFIX + 方向键` or `PREFIX + o`   | 切换到下一个窗格
|`PREFIX + [`   | 滚屏
|`PREFIX + z`   | 暂时把一个窗体放到最大
|`PREFIX + q`   | 查看所有窗格的编号

#### 附加技能
有时情况需要登录堡垒机，才能登录远程机器；登录堡垒机时，避免反反复复的输入token，我们可以配置复用ssh链接；创建（编辑）文件~/.ssh/config， 内容如下：
```angularjs
host *
ControlMaster auto
ControlPath ~/.ssh/master-%r@%h:%p
ControlPersist yes
```
> 打开不同终端远程登录同一个地址时不需要每次都输入密码了

