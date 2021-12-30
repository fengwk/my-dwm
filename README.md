# My Dwm

个人dwm环境。

# Installation

1. 克隆并安装

    ```shell
    git clone git@github.com:fengwk/my-dwm.git ~/prog/my-dwm
    cd ~/prog/my-dwm
    sudo make clean install
    ```

1. 安装渲染器

    ```shell
    sudo pacman -S picom
    ```

1. 配置`~/.xinitrc`

   ```shell
   # 多屏幕时可能需要用到下边的指令
   # xrandr --output eDP1 --scale 0.5x0.5

   # Xresources
   [[ -f ~/.Xresources ]] && xrdb -merge -I$HOME ~/.Xresources

   # Xmodmap
   [[ -f ~/.Xmodmap ]] && xmodmap ~/.Xmodmap

   # xbinkeys
   killall xbindkeys
   xbindkeys

   # fix java application
   export _JAVA_AWT_WM_NONREPARENTING=1
   export AWT_TOOLKIT=MToolkit
   wmname LG3D

   exec dwm

   # fix nvidia
   # 使用nvidia+startx启动会失败以至于黑屏，使用下边的命令可以进入但不能解决nvidia启用失败，使用
   sddm启动不会有这个问题
   # xrandr --auto
   ```

1. 配置`~/.Xresources`

   ```shell
   # 4k屏的HiDPI配置
   Xft.dpi: 192
   Xft.autohint: 0
   Xft.lcdfilter:  lcddefault
   Xft.hintstyle:  hintfull
   Xft.hinting: 1
   Xft.antialias: 1
   Xft.rgba: rgb
   ```

1. 配置`~/.Xmodmap`

   ```shell
   # MSI P15
   # keycode  93 = XF86TouchpadToggle NoSymbol XF86TouchpadToggle
   ```

1. 在`~/.local/share/dwm`目录里配置dwm启动脚本，见[my-dwm-autostart](https://github.com/fengwk/my-dwm-autostart)

1. 安装[nerd-fonts](https://github.com/ryanoasis/nerd-fonts)

# Usage

- dwm使用栈结构组织窗口，`alt+shift+enter`可以打开一个新窗口置于栈顶，`<alt-k>`和`<alt-j>`分别表示栈指针的上下移动，`alt+enter`表示将当前指示窗口与栈顶窗口互换（如果指示窗口本身就是栈顶元素则与栈顶下一个窗口互换），`alt+shift+c`表示关闭当前指针所指的窗口。

- 使用`alt+[1-9]`可以切换到相应的标签页，如果使用`alt+shift+[1-9]`即可将当前指示的窗口移动到指定数字的标签页，另外如果使用`alt+ctrl+[1-9]`可以将多个标签页合并展示，使用`alt+0`可以合并所有标签页。

- 如果存在多个显示器，使用`alt+,`或`alt+.`可以在多个显示器间切换，使用`alt+shift+,`或`alt+shift+.`可以将当前指示的窗口移动到另一个显示器中。

- 使用`alt+p`可以打开dmenu。

- 使用`alt+f`可以切换到浮动模式（><>），也就是鼠标可以拖动窗口的模式，使用`alt+t`切换为平铺模式（[]=），在一些特殊的场景下由于可能导致dwm识别模式失败，使用`alt+shift+space`可以开关浮动模式。
