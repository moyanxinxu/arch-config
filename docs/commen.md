# 通用

## Git设置代理

```bash
git config --global https.proxy http://127.0.0.1:7890
git config --global https.proxy https://127.0.0.1:7890
```

## Git取消代理

```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```

## pip指定代理源

```bash
pip install torch -i https://pypi.tuna.tsinghua.edu.cn/simple
```

## pip换源

```bash
cd ~
mkdir .pip/
cd .pip
vim pip.conf
```

```bash
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
use-mirrors =true
mirrors = https://pypi.tuna.tsinghua.edu.cn/simple/
trusted-host = pypi.tuna.tsinghua.edu.cn
```

## Conda 换源

```bash
cd ～
vim .condarc
```

```bash
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
auto_activate_base: false
```

```bash
conda clean -i
```
