# shell

## 查看所有shell

```sh
cat /etc/shells
```

## 修改shell

> 修改后重启生效

```sh
sudo chsh -s /usr/bin/bash
sudo chsh -s /usr/bin/zsh
sudo chsh -s /usr/bin/fish
```



# bash

## .bashrc

```bash
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/opt/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/opt/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/opt/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<

# cuda
export CUDNN_DIR=/usr/local/cuda-11.3
export PATH=$PATH:/usr/local/cuda-11.3/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.3/lib64

# onnxruntime
export ONNXRUNTIME_DIR=~/onnxruntime-gpu
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:~/onnxruntime-gpu/lib

#tensorRT
export TENSORRT_DIR=~/TensorRT
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:~/TensorRT/lib

# 使用colorls
alias ls='colorls -a'
alias ll='colorls -alh'
export PATH=~/.local/share/gem/ruby/3.0.0/bin:$PATH
```



## anaconda

```sh
# 使用anaconda
export PATH=/opt/anaconda/bin:$PATH
conda init
```

## colorls

```bash
# 使用colorls
alias ls='colorls -a'
alias ll='colorls -alh'
# export PATH=~/.local/share/gem/ruby/3.0.0/bin:$PATH
```

---

# zsh

https://ohmyz.sh/

## 1 安装zsh

```sh
sudo pacman -S zsh
sudo apt install zsh
```

## 2 安装oh-my-zsh

```sh
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
# 或者
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 3 .zshrc 语法和bash相同

```sh
# 使用colorls
alias ls='colorls -a'
alias ll='colorls -alh'
export PATH=$PATH:~/.local/share/gem/ruby/3.0.0/bin
```

### 添加插件

```sh
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-autosuggestions.git
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```

> 然后在 `.zshrc` 中添加，多个插件使用空格区分

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

#### incr

> https://mimosa-pudica.net/zsh-incremental.html
>
> 将下载好的插件放到 `~/.oh-my-zsh/custom/plugins/incr` 目录下
>
> 在 `.zshrc` 最后一行写上

```bash
source $ZSH/custom/plugins/incr/incr*.zsh
```

### 切换主题

> 在 `.zshrc` 中修改

```bash
ZSH_THEME="robbyrussell"
```

#### powerlevel10k

> https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k
>
> 安装多个字体，github有下载,同时要更改terminal以及编辑器的terminal字体
>
> 配置文件在 `~/.p10k.zsh`



```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# gitee
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

> Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.

##### 设置 p10k(出现字体乱码就重新设置即可)

```sh
p10k configure
```

## 4 anaconda

```sh
# 使用anaconda
export PATH=$PATH:/opt/anaconda/bin
codna init zsh
```

## 字体乱码

> 可以尝试安装powerline字体
>
> https://github.com/powerline/fonts
>
> 下载解压后 `./install` 安装



---

# fish

https://github.com/oh-my-fish/oh-my-fish

## 1 安装fish

```sh
sudo pacman -S fish
sudo apt install fish
```

## 2 安装oh-my-fish

安装 omf 很简单。你要做的只是在你的 Fish shell 中运行下面的命令。

```sh
curl -L https://get.oh-my.fish | fish
```

## 3 omf 使用

### config和path

> 配置文件
>
> echo $OMF_CONFIG
>
> `~/.config/omf/`

```python
~/.config/omf/
    ├── bundle		# 主题历史
    ├── channel		# 更新通道
    └── theme		# 当前主题
```

> 安装路径
>
> echo $OMF_PATH
>
> `~/.local/share/omf`

### 列出所有的安装包，运行：

```sh
omf list
```

这条命令将显示已安装的主题和插件。请注意，包可以是主题或插件。安装包意味着安装主题和插件。



### 查看可用的和已安装的主题列表

```sh
omf theme
```

会显示 installed和 available

### 安装主题或插件

> https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md 查看主题样式
>
> https://xiao_beita.gitee.io/009_fish_omf/

```sh
omf install clearance es
```

### 改变主题

> separation  emoji-powerline  ocean  neolambda  zish  ays  

```sh
omf theme <theme-name>
# 例如：
omf theme agnoster
```

### 搜索主题或插件

```sh
omf search <search_string>
# 例如：
omf search nvm
```

> 为了限制搜索的主题范围，使用 `-t` 选项。
>
> 这条命令只会搜索主题名字中包含 “chain” 的主题。

```sh
omf search -t chain
```

> 为了限制搜索的插件范围，使用 `-p` 选项

```sh
omf search -p emacs
```

### 更新包

> 要仅更新核心功能（`omf` 本身），运行：

```sh
omf update omf
```

> 如果是最新的，你会看到以下输出：

```sh
Oh My Fish is up to date.
You are now using Oh My Fish version 6.
Updating https://github.com/oh-my-fish/packages-main master... Done!
```

> 更新所有包：

```sh
omf update
```

> 要有选择地更新软件包，只需包含如下所示的包名称：

```sh
omf update clearance agnoster
```

### 显示关于包的信息

> 当你想知道关于一个主题或插件的信息时，使用以下命令：

```sh
omf describe clearance
```

> 这条命令将显示关于包的信息。

```sh
Package: clearance
Description: A minimalist fish shell theme for people who use git
Repository: https://github.com/oh-my-fish/theme-clearance
Maintainer:
```

### 移除包

> 移除一个包，例如 emacs，运行：

```sh
omf remove emacs
```

### 管理仓库

> 默认情况下，当你安装了 Oh My Fish 时，会自动添加官方仓库。这个仓库包含了开发人员构建的所有包。要管理用户安装的仓库包，使用这条命令：

```sh
omf repositories [list|add|remove]
```

> 列出所有安装的仓库，运行：

```sh
omf repositories list
```

> 添加一个仓库：

```sh
omf repositories add <URL>
# 例如：
omf repositories add https://github.com/ostechnix/theme-sk
```

> 移除一个仓库：

```sh
omf repositories remove <repository-name>
```

### Oh My Fish 排错

> 如果出现了错误，`omf` 足够聪明来帮助你，它可以列出解决问题的方法。例如，我安装了 clearance 包，得到了文件冲突的错误。幸运的是，在继续之前，Oh My Fish 会指示我该怎么做。因此，我只是简单地运行了以下代码来了解如何修正错误。

```sh
omf doctor
```

> 通过运行以下命令来解决错误：

```sh
rm ~/.config/fish/functions/fish_prompt.fish
```

### 获取帮助

> 显示帮助部分，运行：

```sh
omf -h
omf --help
```

### 卸载 Oh My Fish

> 卸载 Oh My Fish，运行以下命令：

```sh
omf destroy
```

## 4 ~.config/fish/config.fish

#### 环境变量

```sh
set -p PATH $PATH:{新路径}
```

## 5 anaconda

```sh
# 使用anaconda
set -p PATH $PATH:/opt/anaconda/bin
conda init fish
```

---

# colorls

## ruby

```sh
sudo pacman -S ruby
sudo apt install ruby-full
```

## colorls安装卸载

```sh
sudo gem install colorls

sudo gem uninstall colorls
```

## 设置别名

> `~/.bashrc`
>
> `./zshrc`
>
> `./.config/fish/config.fish`

```bash
alias ls=colorls
alias ll="colorls -la"
```

