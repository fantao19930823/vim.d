This repository contains three configuration files:

* vimrc
* tmux.conf

---

## VIM

1. It works fine on 64bit Lubuntu with VIM 7.4.
1. It should be OK for other Linux and VIM 7.+.
1. Cmake is needed, apt-get install cmake

### Install & Upgrade

#### Install

1. Install `vundle`

        git clone http://github.com/gmarik/vundle.git ~/.vim/bundle/vundle

1. Clone `vim.d`

        git clone https://github.com/tafanfly/vim.d.git ~/workspace/vim.d

1. Create `~/.vimrc`

        ln -s ~/workspace/vim.d/vimrc ~/.vimrc

1. Open `vim`, execute `:BundleInstall`
1. Patch `power-line` font

    ```sh
    mkdir ~/.fonts
    git clone https://github.com/powerline/fonts.git ~/.fonts/powerline-fonts
    cd ~/.fonts/powerline-fonts
    ./install.sh
    ```
1. Install `YouCompleteMe`

    ```sh
    cd ~/.vim/bundle/YouCompleteMe
    ./install.sh
    ```
1. Open `vim` again, enjoy!


#### Upgrade

1. Update vim.d

```bash
    cd ~/Workspace/vim.d
    git pull
```

1. Open `vim`, execute `:BundleClean`
1. Open `vim`, execute `:BundleUpdate`

### Update colorscheme
1. Copy intersted colorscheme file such as [monokai.vim](https://github.com/sickill/vim-monokai/blob/master/colors/monokai.vim) under ~/.vim/bundle/vim-colors-solarized/colors
2. Set `colorscheme monokai` in your ~/vimrc file

### Issue

1. Open vim without color

```bash
    vim ~/.vimrc
    add line syntax on
```

### Plugins

The plugins I used are:

* gmarik/vundle
* altercation/vim-colors-solarized
* ctrlpvim/ctrlp.vim
* tacahiroy/ctrlp-funky
* FelikZ/ctrlp-py-matcher
* scrooloose/nerdtree
* NERD_tree-Project
* scrooloose/nerdcommenter
* plasticboy/vim-markdown
* majutsushi/tagbar
* bling/vim-airline
* tpope/vim-fugitive
* Valloric/YouCompleteMe
* godlygeek/tabular
* scrooloose/syntastic
* digitaltoad/vim-jade
* rking/ag.vim
* mfukar/robotframework-vim
* ntpeters/vim-better-whitespace
* elzr/vim-json
* tpope/vim-surround
* pangloss/vim-javascript
* mxw/vim-jsx
* othree/html5.vim
* airblade/vim-gitgutter
* wavded/vim-stylus
* moll/vim-node
* jiangmiao/auto-pairs
* ekalinin/Dockerfile.vim
* fatih/vim-go
* fcitx.vim
* christoomey/vim-tmux-navigator


### Shortcuts

1. `,e`

    open file

1. `,s`

    open file in split window

1. `,vs`

    open file in vertical split window

1. `,m`

    comment/uncomment code

1. `,f`

    open function list of current file, like `Ctrl-R` in sublime

1. `<F4>`

    open/close tag bar on the right panel

1. `<F5>`

    execute "make test" in project root

1. `<F12>`

    open/close project browser on the left panel

1. `<Ctrl-Tab>`

    in `normal` mode, switch files in minibuffer; in `insert` mode, used to select code snippet

1. `<Ctrl-p>`

    in `insert` mode, used to open specified file quickly;
    see detail in `ctrlp.vim` plugin

1. `,;`

    auto complete

1. `,c`

    copy to system clipboard

1. `,v`

    paste from system clipboard


## Some Tips

### Edit file in column

1. in `normal` mode, `<Ctrl-v>` start to select column, `<Shift-v>` to select multiple lines
1. after select several columns,
    * `I` used to add content before cursor column
    * `A` used to add content after cursor column
    * `r` used to modify content under cursor
    * `x` used to delete content under cursor

### Quick Move

1. `<Ctrl-o>` move to previous edit position
1. `<Ctrl-i>` move to forward edit position
1. `b` move to previous word, `w` move to next word
    * try `B` and `W`, and see what's the difference
1. `{` move to previous block, `}` move to next block
1. `0` move to start of the line, `$` move to end of the line
    * `^` move to first char of the line
1. `gg` move to the start of the file, `G` move to the end of the file
1. `<Ctrl-]>` jump to the definition of content under cursor, while `<Ctrl-t>` jump back

### Quick Edit

1. `u` undo, `<Ctrl-r>` redo
1. `.` report last step
1. `di'` delete content in `'`
1. `dt'` delete content from current position to `'`
1. `cw` modify the current word
1. `caw` modify the current word
1. `c0` modify from start to current position
1. `c$` modify from current position to end of this line
1. `R` update the content until got `ESC`

### 总结常用的command
  vim命令 |  描述 | 
  ---- |----|
  ,e    | 打开一个文件 |
  Tab  | 普通模式下切换文件 |
  ,m  | 注释一行/解注释 |
  F12  | 浏览/关闭项目目录|
  Ctrl + v  | 普通模式下选择列|
  Shift + v  | 普通模式下选择行|
  Ctrl + v/Shift + y  + p | 普通模式下选择,然后copy,再paste|
  u  | 撤销上一步|
  c0  | 修改行开头到当前位置|
  c$  | 修改当前位置到行未|
  0  | 跳到行头|
  $  | 跳到行末|
  ^  | 跳到该行第一个字符|
  b  | 跳到前一个word|
  w  | 跳到后一个word|
  gg  | 跳到文件开头|
  G  | 跳到文件末尾|
  {  | 跳到上一个block|
  }  | 跳到下一个block|

### Macro

1. `qa` start to record macro `a`
1. execute some steps
1. `q` stop to record
1. `@a` execute the macro
1. `@@` execute the last executed macro

## Screenshot

![panel](/img/panel.png "VIM Panel")
![usage](/img/usage.gif "VIM Usage")

## Reference

1. [VIM Tips](http://www.rayninfo.co.uk/vimtips.html)
1. [VIM scripts](http://vim-scripts.org)
1. [ctrlp.vim introduction](http://zuyunfei.com/2013/08/26/vim-plugin-ctrlp/)
1. [Practical VIM](http://www.amazon.com/Practical-Vim-Thought-Pragmatic-Programmers/dp/1934356980/ref=sr_1_1?ie=UTF8&qid=1407823913&sr=8-1&keywords=practical+vim)

## Tmux

See in [tmux.readme](https://github.com/tafanfly/vim.d/blob/master/tmux.md), [tmux.config](https://github.com/tafanfly/vim.d/blob/master/.tmux.conf)
