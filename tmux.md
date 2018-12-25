## Tmux
Tmux介绍包含几部分
* install
* config
* command
---
### Install
直接用apt命令安装， 当然不同的linux 环境下会有不同的安装命令。
> sudo apt-get install tmux
### Config
tmux 的默认配置文件是`~/.tmux.conf`
##### tmux 快捷键前缀
tmux 的默认快捷键前缀是`ctrl -b`，不太符合程序员的按键输入，所以需要根据自己的需求修改， 我的是配置了`ctrl -a`(文章后面的**prefix指的就是ctrl -a**)。
在`~/.tmux.conf`加入下列内容：
```
unbind ^b 
set -g prefix ^a
```
直接用`source ~/.tmux.conf`使其生效是有问题的，stackoverflow上有[解决方案](https://stackoverflow.com/questions/17041647/unable-to-source-tmux-conf)。
如下：
```
随便打开一个session， tmux new -s demo
输入命令  ctrl -a + :，就是同时摁着ctrl 和a键， 然后放开再摁：键
然后输入命令source-file ~/.tmux.conf
```

##### 快速配置文件
上面的修改太麻烦了，可以安装下面的命令快速配置
```
bind e new-window -n ".tmux.conf" "sudo vim ~/.tmux.conf"  # 快速打开配置文件
bind-key r source-file ~/.tmux.conf\; display-message "Config reloaded" # 配置文件生效
```

`prefix + e`的组合可以让你迅速的打开`~/.tmux.conf` 并进行配置修改，配置完成之后使用 `prefix + r`的方式重新加载。
##### 更新窗口序号
打开session窗口是默认从0开始的，可以配置从1开始。
```
set -g base-index 1         
set -g pane-base-index 1 
```

##### 更新分割面板的快捷键
tmux 垂直和水平分割面板的快捷键分别为`prefix + %`和`prefix + "`。这两个按键比较难记忆，我们可以将其更改为`prefix + |`和`prefix + -`。将以下配置加入 `~/.tmux.conf`。
```
bind-key | split-window -h 
bind-key - split-window
```
##### 鼠标模式
鼠标模式有时候也可能非常有用，比如你可能想用鼠标来选中一个面板或者窗口，用鼠标调整面板大小，或者用鼠标滚轮来向上滚动浏览历史。将以下配置加入 `~/.tmux.conf`。`prefix + m` 来触发鼠标模式的开和关。
```
bind m run 'old=$(tmux show -gv mouse);new=""; if [ "$old" = "on" ]; then new="off"; else new="on"; fi; tmux set -g mouse $new; tmux display "mouse: $new"'
```
##### 所有配置如下
```
unbind ^b
set -g prefix ^a
bind e new-window -n ".tmux.conf" "vim ~/.tmux.conf"
bind-key r source-file ~/.tmux.conf\; display-message "Config reloaded"
set -g base-index 1
set -g pane-base-index 1
bind-key | split-window -h
bind-key - split-window
bind m run 'old=$(tmux show -gv mouse);new=""; if [ "$old" = "on" ]; then new="off"; else new="on"; fi; tmux set -g mouse $new; tmux display "mouse: $new"'
bind a send-prefix
set -g status-bg black
set -g status-fg white
set-option -g status-justify centre
set-option -g status-left '#[bg=black,fg=red][#[fg=green]#S#[fg=red]]'
set-option -g status-left-length 20
set -g automatic-rename on
set-window-option -g window-status-format '#[dim]#I:#[default]#W#[fg=grey,dim]'
set-window-option -g window-status-current-format '#[fg=red,bold]#I#[fg=red]:#[fg=red]#W#[fg=dim]'
set -g status-right '#[fg=red][#[fg=green]%Y-%m-%d#[fg=red]]'
set -g default-terminal "screen-256color"
```

### Command
* 注意以下命令是在配置后的，非tmux默认命令，**prefix指的就是ctrl -a**。

  vim命令 |  描述 | 
  ---- |----|
  tmux new -s demo    | 新建一个名为demo的session |
  tmux ls    | 查看当前终端下的所有session |
  tmux a -t demo  | 连接上demo这个session |
  prefix + s  | 选择并快速切换session |
  prefix + $  | 为session重命名 |
  prefix + n/w  | 快速切换窗口|
  prefix + 1/2/3  | 切换到指定窗口1/2/3 |
  prefix + ，  | 为窗口重命名 |
  exit   | 退出窗口 |
  prefix + x/&  | 强制退出该窗口 |
  prefix + e  | 快速打开配置文件config |
  prefix + r  | 配置文件config快速生效 |
  prefix + \|  | 垂直切割窗口 |
  prefix + -   | 横向切割窗口 |
  prefix + ctrl + 方向键 | 调整窗口大小 |
  prefix + o/方向键  | 切换已分割的窗口 |
  prefix + z  | 全屏该已分割的面板，以及恢复原状 |

### 效果图
![image.png](https://upload-images.jianshu.io/upload_images/5605276-7a7b2f344d4e5534.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 
### Refenence
[效率为王：终端管理工具 Tmux](https://gitbook.cn/books/5a362ddc2edf834ef46b6415/index.html)
[tmux.conf 文件](https://github.com/tafanfly/vim.d/blob/master/tmux.conf)
