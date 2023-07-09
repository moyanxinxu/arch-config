# Archlinux配置

## 解决Clash-for-windows-bin不能开启TUN模式

```bash
yay -S clash-for-windows-bin
rm -rf /home/$USER/.config/clash
rm -rf /home/$USER/.config/clash_win
sudo rm -rf /opt/clash-for-windows-bin/resources
sudo rm -rf /opt/clash-for-windows-bin/locales
sudo mv ~/cfw/resources/ /opt/clash-for-windows-bin/
sudo mv ~/cfw/locales/ /opt/clash-for-windows-bin
sudo rm -rf /home/$USER/cfw

```

## 安装

### 安装软件

```bash
yay -S wps-office wps-office-fonts wps-office-mime ttf-wps-fonts cups libtiff5 # cups解决打印机问题，libtiff5解决pdf无法使用wps打开的问题
yay -S visual-studio-code-bin
yay -S linuxqq libappindicator-gtk3 # libappindicator-gtk3允许QQ使用GTK3样式
yay -S flameshot
yay -S yesplaymusic
yay -S pandoc-bin
yay -S ttf-mac-fonts # 安装苹果字体
yay -S ttf-jetbrains-mono # 安装Jetbrain的编程字体

sudo pacman -S typora
```

### 安装微软雅黑

```bash
git clone https://gitee.com/hbk01/Windows-Fonts.git
cd Windows-Fonts && sudo cp -r ./* /usr/share/fonts
sudo mkfontscale && mkfontdir && fc-cache -fv
```

### 安装拓展

- [compiz-alike-magic-lamp-effect](https://extensions.gnome.org/extension/3740/compiz-alike-magic-lamp-effect/)
- [AppIndicator-and-KStatusNotifierItem-Support](https://extensions.gnome.org/extension/615/appindicator-support/)
- [Blur-My-Shell](https://extensions.gnome.org/extension/3193/blur-my-shell/)
- [GTK-Title-Bar](https://extensions.gnome.org/extension/1732/gtk-title-bar/)
- [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
- [Bluetooth Quick Connect](https://extensions.gnome.org/extension/1401/bluetooth-quick-connect/)
- [Transparent Window Moving](https://extensions.gnome.org/extension/1446/transparent-window-moving/)
- [Desktop Icons NG (DING)](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)
- [Window Is Ready - Notification Remover](https://extensions.gnome.org/extension/1007/window-is-ready-notification-remover/)
- [Lock-keys](https://extensions.gnome.org/extension/36/lock-keys/)

## Python相关环境

```bash
sudo pacman -S python-pip
yay -S miniconda3
```

### pip换源

```bash
cd ~
mkdir .pip/
cd .pip
vim pip.conf
```

```vim
[global]
index-url = http://pypi.douban.com/simple
[install]
use-mirrors =true
mirrors =http://pypi.douban.com/simple/
trusted-host =pypi.douban.com
```

### Conda 换源

```bash
cd ～
vim .condarc
```

```vim
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

```bash
conda clean -i

```

#### 激活miniconda环境

```bash
source /opt/miniconda3/bin/activate root #激活conda环境
```

#### 关闭miniconda环境

```bash
source /opt/miniconda3/bin/deactivate root # 关闭conda环境
```

#### 取消miniconda自动激活环境

```bash
conda config --set auto_activate_base false
```

## 系统细节

### grub默认启动系统

```bash
sudo vim /etc/default/grub
```

```txt
#GURB_DEFAULT=0
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

### 光标

```bash
yay -S apple_cursor

```

### 修复Vscode打开文件管理器

```bash
xdg-mime default org.gnome.Nautilus.desktop inode/directory
```

### 卸载孤儿包

```bash
sudo pacman -Rs $(pacman -Qdtq)
```

### 开启Pacman彩色输出

```bash
sudo vim /etc/pacman.conf
```

```vim
Color
VerbosePkgLists
```

### 解决无法调用输入法

```bash
export LC_ALL=zh_CN.UTF-8 
export GTK_IM_MODULE=fcitx 
export QT_IM_MODULE=fcitx 
export XMODIFIERS=@im=fcitx 
```
