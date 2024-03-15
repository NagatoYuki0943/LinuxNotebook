https://www.runoob.com/linux/linux-comm-cp.html

Linux cp（英文全拼：copy file）命令主要用于复制文件或目录。

### 语法

```sh
cp [options] source dest
或
cp [选项] 源文件 目标文件
```

其中，source（源文件）表示要复制的文件或目录的路径，dest（目标文件）表示复制后的文件或目录的路径。

或

```sh
cp [options] source... directory
```

**选项说明**：

- -a：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于 dpR 参数组合。
- -d：复制时保留链接。这里所说的链接相当于 Windows 系统中的快捷方式。
- `-r` 或 `--recursive`：用于复制目录及其所有的子目录和文件，如果要复制目录，需要使用该选项。
- `-i` 或 `--interactive`：在复制前提示确认，如果目标文件已存在，则会询问是否覆盖，回答 **y** 时目标文件将被覆盖。。
- `-u` 或 `--update`：仅复制源文件中更新时间较新的文件。
- `-v` 或 `--verbose`：显示详细的复制过程。
- `-p` 或 `--preserve`：保留源文件的权限、所有者和时间戳信息。
- `-f` 或 `--force`：强制复制，即使目标文件已存在也会覆盖，而且不给出提示。
- -l：不复制文件，只是生成链接文件。

### 实例

将文件 file.txt 复制到目录 /path/to/destination/ 中：

```sh
cp file.txt /path/to/destination/
```

使用指令 **cp** 将当前目录 **test/** 下的所有文件复制到新目录 **newtest** 下，输入如下命令：

```sh
cp –r test/ newtest
```

使用指令 **cp** 将当前目录 **test** 复制到新目录 **newtest** 下，输入如下命令：

```sh
cp –r test newtest 
```

注意：用户使用该指令复制目录时，必须使用参数 **-r** 或者 **-R** 。

复制文件，并在目标文件已存在时进行确认：

```sh
cp -i file.txt /path/to/destination/
```

以上只是 cp 命令的一些常见用法，你可以通过运行 **man cp** 命令查看更多选项和用法。

```sh
# 将 lib 目录下的文件全部复制到 lib64 目录下
cp -riv lib/* /usr/local/cuda/lib64

# 将 lib 目录复制到 lib64 目录下,生成新目录 lib        ❌error❌
cp -riv lib /usr/local/cuda/lib64
```

