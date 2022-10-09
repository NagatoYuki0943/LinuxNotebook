# windows terminal 配置详解

> https://zhuanlan.zhihu.com/p/144612614#

## 配置右键打开

### github脚本

> https://github.com/lextm/windowsterminal-shell

1. 安装powershell7

> https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7
>
> windows商店下载的不支持一些操作

```powershell
winget search Microsoft.PowerShell

winget install --id Microsoft.Powershell --source winget
```

2. 运行脚本

```shell
git clone https://github.com/lextm/windowsterminal-shell
```

3. 在 powershell7 中运行 `install.ps1`

#### 注册表位置

> 可以删除不需要的terminal

```
计算机\HKEY_CLASSES_ROOT\Directory\ContextMenus
```



### or 手动方式

> `win+r`输入`regedit`打开注册表编辑器
>
> 然后在注册表编辑器依次找到

```
计算机\HKEY_CLASSES_ROOT\Directory\Background\shell
```

> 然后在`shell`项右键点击新建项
>
> 起名叫terminal或者wt之类的你能分辨的名字，不要打中文！
>
> 然后选中刚刚新建的这一项，可以在右边看到注册表的属性或者理解为成员变量
>
> 选中右键点击编辑，数值数据填你想在鼠标右键显示的文本，比如Open Terminal Here
>
> 这时在桌面右键已经可以看到Open Terminal Here的选项，但现在还不能呼出终端，同时相比于我之前的那一项少个图标
>
> 为了添加图标，需要实现将图标存在一个电脑上一个固定的位置，将下面的图标保存下来并确保是icon格式，并改名然后放在电脑上一个位置
>
> 然后再次选中刚刚新建的terminal项，右键新建，选择字符串值，命名为`icon`
>
> 然后同样右键编辑，将保存的terminal.icon文件路径填进去，最后点确定

```powershell
C:\Users\Frostbite\AppData\Local\Microsoft\WindowsApps\Terminal.icon
```

> 最后一项，选中之前新建的terminal项右键点击新建，选择项
>
> 新建项的名字为command
>
> 然后点击下图标注的command的默认属性右键编辑，填入

```powershell
C:\Users\Frostbite\AppData\Local\Microsoft\WindowsApps\wt.exe
```

## 设置

> powershell和cmd设置启动目录为 使用父进程目录 在文件管理器中就在文件目录打开终端

## 配置文件位置



```powershell
# powershell5
我的文档\WindowsPowerShell

# powershell7
我的文档\PowerShell
```

# anaconda miniconda3

```powershell
conda init powershell
conda init powershell7
```

# oh-my-posh

> https://ohmyposh.dev/
>
> 安装字体 MesloLGM NF
>
> https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Meslo.zip

> terminal设置字体
>
> 在defaults中添加

```json
"font":
{
    "face": "MesloLGM NF"
}
```

> https://ohmyposh.dev
>
> [美化](https://zhuanlan.zhihu.com/p/354603010)
>
> 安装

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

> 在Windows Terminal中的powershell中输入并回车
>
> powershell7和powershell都能这样用，下面复制即可

```powershell
notepad $profile
```

> 第一次会显示找不到该文件，选择创建新文件，然后输入并保存

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

## theme

> 查看

```powershell
Get-PoshThemes
```

> 主题路径

```powershell
C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes
```

> 好用的主题，可以看到虚拟环境
>
> hunk
>
> iterm2
>
> kali
>
> negligible
>
> powerlevel10k_modern
>
> velvet.omp

> 更改theme

```powershell
notepad $profile
                                                                                             //填写文件夹中的主题json
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\hunk.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\iterm2.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\kali.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\negligible.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\powerlevel10k_modern.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\velvet.omp.json | Invoke-Expression
```



# startship

> https://starship.rs/zh-CN/

## 安装

```
winget install --id Starship.Starship
```

## 配置

```
$PROFILE
Invoke-Expression (&starship init powershell)
```

