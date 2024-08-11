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
yay -S visual-studio-code-bin
yay -S linuxqq libappindicator-gtk3 # libappindicator-gtk3允许QQ使用GTK3样式
yay -S flameshot
yay -S yesplaymusic
yay -S pandoc-bin
yay -S ttf-jetbrains-mono # 安装Jetbrain的编程字体

sudo pacman -S typora
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
