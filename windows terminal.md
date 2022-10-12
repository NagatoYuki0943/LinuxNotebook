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

## 配置

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
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\negligible.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\paradox.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\peru.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\powerlevel10k_rainbow.omp.json | Invoke-Expression
oh-my-posh init pwsh --config C:\Users\Frostbite\AppData\Local\Programs\oh-my-posh\themes\velvet.omp.json | Invoke-Expression
```



# startship

> https://starship.rs/zh-CN/

## 安装

```
winget install --id Starship.Starship
```

## 配置pwsh

> 在Windows Terminal中的powershell中输入并回车
>
> powershell7和powershell都能这样用，下面复制即可

```powershell
notepad $profile
```

> 第一次会显示找不到该文件，选择创建新文件，然后输入并保存

```powershell
Invoke-Expression (&starship init powershell)
```



## 配置starship

> https://starship.rs/zh-CN/config
>
> 您需要创建配置文件 `~/.config/starship.toml` 以供 Starship 使用

Starship 的所有配置都在此 [TOML](https://github.com/toml-lang/toml)[ ](https://github.com/toml-lang/toml)

[ (opens new window)](https://github.com/toml-lang/toml) 配置文件中完成：

```toml
# 设置配置范例，开启编辑器的自动补全
"$schema" = 'https://starship.rs/config-schema.json'

# 在命令之间插入空行
add_newline = true

# 将提示符的“❯”替换为“➜”
[character] # “character”是我们正在配置的组件
success_symbol = "[➜](bold green)" # 设置“success_symbol” 字段为绿色加粗的“➜”

# 禁用 package 组件，完全隐藏它的提示符
[package]
disabled = true
    
```

您可以使用 `STARSHIP_CONFIG` 环境变量更改默认配置文件的位置：

```sh
export STARSHIP_CONFIG=~/example/non/default/path/starship.toml
```

在 PowerShell (Windows) 中，在 `$PROFILE` 中添加下面的代码行能达到同样的效果：

```powershell
$ENV:STARSHIP_CONFIG = "$HOME\example\non\default\path\starship.toml"    
```

或者在 Cmd (Windows) 中，将下面的代码添加到 `starship.lua`：

```lua
os.setenv('STARSHIP_CONFIG', 'C:\\Users\\user\\example\\non\\default\\path\\starship.toml')
```

| 选项              | 默认值                                                       | 描述                                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `format`          | [见下文](https://starship.rs/zh-CN/config/#default-prompt-format) | 配置提示符的格式。                                           |
| `right_format`    | `""`                                                         | See [Enable Right Prompt](https://starship.rs/advanced-config/#enable-right-prompt) |
| `scan_timeout`    | `30`                                                         | Starship 扫描文件的超时时间（单位：毫秒）。                  |
| `command_timeout` | `500`                                                        | Startship 执行命令的超时时间（单位：毫秒）。                 |
| `add_newline`     | `true`                                                       | 在 shell 提示符之间插入空行。                                |

## 提示符

以下是关于提示符的配置项。

### 配置项

| 选项              | 默认值 | 描述                                                         |
| ----------------- | ------ | ------------------------------------------------------------ |
| `format`          | 见下文 | 配置提示符的格式。                                           |
| `right_format`    | `""`   | See [Enable Right Prompt](https://starship.rs/advanced-config/#enable-right-prompt) |
| `scan_timeout`    | `30`   | Starship 扫描文件的超时时间（单位：毫秒）。                  |
| `command_timeout` | `500`  | Startship 执行命令的超时时间（单位：毫秒）。                 |
| `add_newline`     | `true` | 在 shell 提示符之间插入空行。                                |

### 示例

```toml
# ~/.config/starship.toml

# Use custom format
format = """
[┌───────────────────>](bold green)
[│](bold green)$directory$rust$package
[└─>](bold green) """

# Wait 10 milliseconds for starship to check files under the current directory.
scan_timeout = 10

# Disable the blank line at the start of the prompt
add_newline = false
```

### 默认提示符格式

如果没有提供`format`字段或者它的值是空的，将会使用默认的`format`配置来指定提示符的格式。 默认设置如下：

```toml
format = "$all"

# Which is equivalent to
# 去掉 $username 就不会显示用户了
format = """
$username\
$hostname\
$localip\
$shlvl\
$singularity\
$kubernetes\
$directory\
$vcsh\
$git_branch\
$git_commit\
$git_state\
$git_metrics\
$git_status\
$hg_branch\
$docker_context\
$package\
$c\
$cmake\
$cobol\
$daml\
$dart\
$deno\
$dotnet\
$elixir\
$elm\
$erlang\
$golang\
$haskell\
$helm\
$java\
$julia\
$kotlin\
$lua\
$nim\
$nodejs\
$ocaml\
$perl\
$php\
$pulumi\
$purescript\
$python\
$raku\
$rlang\
$red\
$ruby\
$rust\
$scala\
$swift\
$terraform\
$vlang\
$vagrant\
$zig\
$buf\
$nix_shell\
$conda\
$spack\
$memory_usage\
$aws\
$gcloud\
$openstack\
$azure\
$env_var\
$crystal\
$custom\
$sudo\
$cmd_duration\
$line_break\
$jobs\
$battery\
$time\
$status\
$container\
$shell\
$character"""
```

如果你只是想扩展默认的格式，你可以使用 `$all`; 你另外添加到格式中的modules不会重复出现。 例如：

```toml
# 将目录信息移到第二行
format = "$all$directory$character"
```
