# My Dwm

个人dwm环境。

# Installation

1. 克隆并安装

    ```shell
    git clone git@github.com:fengwk/my-dwm.git ~/prog/my-dwm
    cd ~/prog/my-dwm
    sudo make clean install
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
