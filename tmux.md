## Tmux
Tmux���ܰ���������
* install
* config
* command
---
### Install
ֱ����apt���װ�� ��Ȼ��ͬ��linux �����»��в�ͬ�İ�װ���
> sudo apt-get install tmux
### Config
tmux ��Ĭ�������ļ���`~/.tmux.conf`
##### tmux ��ݼ�ǰ׺
tmux ��Ĭ�Ͽ�ݼ�ǰ׺��`ctrl -b`����̫���ϳ���Ա�İ������룬������Ҫ�����Լ��������޸ģ� �ҵ���������`ctrl -a`(���º����**prefixָ�ľ���ctrl -a**)��
��`~/.tmux.conf`�����������ݣ�
```
unbind ^b 
set -g prefix ^a
```
ֱ����`source ~/.tmux.conf`ʹ����Ч��������ģ�stackoverflow����[�������](https://stackoverflow.com/questions/17041647/unable-to-source-tmux-conf)��
���£�
>����һ��session�� tmux new -s demo
��������  ctrl -a + :������ͬʱ����ctrl ��a���� Ȼ��ſ���������
Ȼ����������source-file ~/.tmux.conf

##### ���������ļ�
������޸�̫�鷳�ˣ����԰�װ����������������
>bind e new-window -n ".tmux.conf" "sudo vim ~/.tmux.conf"  # ���ٴ������ļ�
bind-key r source-file ~/.tmux.conf\; display-message "Config reloaded" # �����ļ���Ч

`prefix + e`����Ͽ�������Ѹ�ٵĴ�`~/.tmux.conf` �����������޸ģ��������֮��ʹ�� `prefix + r`�ķ�ʽ���¼��ء�
##### ���´������
��session������Ĭ�ϴ�0��ʼ�ģ��������ô�1��ʼ��
```
set -g base-index 1         
set -g pane-base-index 1 
```

##### ���·ָ����Ŀ�ݼ�
tmux ��ֱ��ˮƽ�ָ����Ŀ�ݼ��ֱ�Ϊ`prefix + %`��`prefix + "`�������������Ƚ��Ѽ��䣬���ǿ��Խ������Ϊ`prefix + |`��`prefix + -`�����������ü��� `~/.tmux.conf`��
```
bind-key | split-window -h 
bind-key - split-window
```
##### ���ģʽ
���ģʽ��ʱ��Ҳ���ܷǳ����ã�������������������ѡ��һ�������ߴ��ڣ�������������С�������������������Ϲ��������ʷ�����������ü��� `~/.tmux.conf`��`prefix + m` ���������ģʽ�Ŀ��͹ء�
```
bind m run 'old=$(tmux show -gv mouse);new=""; if [ "$old" = "on" ]; then new="off"; else new="on"; fi; tmux set -g mouse $new; tmux display "mouse: $new"'
```
##### ������������
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
* ע�����������������ú�ģ���tmuxĬ�����**prefixָ�ľ���ctrl -a**��
  ���� |  ���� | 
  ---- |----|
  tmux new -s demo    | �½�һ����Ϊdemo��session |
  tmux ls    | �鿴��ǰ�ն��µ�����session |
  tmux a -t demo  | ������demo���session |
  prefix + s  | ѡ�񲢿����л�session |
  prefix + $  | Ϊsession������ |
  prefix + n/w  | �����л�����|
  prefix + 1/2/3  | �л���ָ������1/2/3 |
  prefix + ��  | Ϊ���������� |
  exit   | �˳����� |
  prefix + x/&  | ǿ���˳��ô��� |
  prefix + e  | ���ٴ������ļ�config |
  prefix + r  | �����ļ�config������Ч |
  prefix + \|  | ��ֱ�и�� |
  prefix + -  | �����и�� |
  prefix + ctrl + ����� | �������ڴ�С |
  prefix + o/�����  | �л��ѷָ�Ĵ��� |
  prefix + z  | ȫ�����ѷָ����壬�Լ��ָ�ԭ״ |

### Ч��ͼ
![image.png](https://upload-images.jianshu.io/upload_images/5605276-7a7b2f344d4e5534.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 
### Refenence
[Ч��Ϊ�����ն˹����� Tmux](https://gitbook.cn/books/5a362ddc2edf834ef46b6415/index.html)
[tmux.conf �ļ�](https://github.com/tafanfly/vim.d/blob/master/tmux.conf)