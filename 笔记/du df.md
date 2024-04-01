# df

Linux df（英文全拼：disk free） 命令用于显示目前在 Linux 系统上的文件系统磁盘使用情况统计。

## 语法

```sh
df [选项]... [FILE]...
```

- 文件-a, --all 包含所有的具有 0 Blocks 的文件系统
- 文件--block-size={SIZE} 使用 {SIZE} 大小的 Blocks
- 文件-h, --human-readable 使用人类可读的格式(预设值是不加这个选项的...)
- 文件-H, --si 很像 -h, 但是用 1000 为单位而不是用 1024
- 文件-i, --inodes 列出 inode 资讯，不列出已使用 block
- 文件-k, --kilobytes 就像是 --block-size=1024
- 文件-l, --local 限制列出的文件结构
- 文件-m, --megabytes 就像 --block-size=1048576
- 文件--no-sync 取得资讯前不 sync (预设值)
- 文件-P, --portability 使用 POSIX 输出格式
- 文件--sync 在取得资讯前 sync
- 文件-t, --type=TYPE 限制列出文件系统的 TYPE
- 文件-T, --print-type 显示文件系统的形式
- 文件-x, --exclude-type=TYPE 限制列出文件系统不要显示 TYPE
- 文件-v (忽略)
- 文件--help 显示这个帮手并且离开
- 文件--version 输出版本资讯并且离开

## example

```sh
# 使用人类可读的格式
> df -h
\Filesystem      Size  Used Avail Use% Mounted on
overlay         3.5T  146G  3.2T   5% /
tmpfs            64M     0   64M   0% /dev
tmpfs          1008G     0 1008G   0% /sys/fs/cgroup
cpfs01           10T  3.9T  6.2T  39% /share
/dev/nvme0n1    3.5T  146G  3.2T   5% /etc/hosts
tmpfs          1008G     0 1008G   0% /dev/shm
tmpfs          1008G   12K 1008G   1% /run/secrets/kubernetes.io/serviceaccount
tmpfs          1008G   12K 1008G   1% /proc/driver/nvidia
/dev/sdb1       440G   51G  372G  12% /usr/bin/nvidia-smi
tmpfs          1008G   16M 1008G   1% /run/nvidia-persistenced/socket
devtmpfs       1008G     0 1008G   0% /dev/nvidia5
tmpfs          1008G     0 1008G   0% /proc/acpi
tmpfs          1008G     0 1008G   0% /proc/scsi
tmpfs          1008G     0 1008G   0% /sys/firmware
```

```sh
# 用一个-i选项的df命令的输出显示inode信息而非块使用量
> df -ih
Filesystem     Inodes IUsed IFree IUse% Mounted on
overlay          224M  983K  223M    1% /
tmpfs            252M    21  252M    1% /dev
tmpfs            252M    18  252M    1% /sys/fs/cgroup
cpfs01           2.9G  1.9G 1006M   66% /share
/dev/nvme0n1     224M  983K  223M    1% /etc/hosts
tmpfs            252M     1  252M    1% /dev/shm
tmpfs            252M     9  252M    1% /run/secrets/kubernetes.io/serviceaccount
tmpfs            252M     6  252M    1% /proc/driver/nvidia
/dev/sdb1         28M  203K   28M    1% /usr/bin/nvidia-smi
tmpfs            252M  3.2K  252M    1% /run/nvidia-persistenced/socket
devtmpfs         252M  1.2K  252M    1% /dev/nvidia5
tmpfs            252M     1  252M    1% /proc/acpi
tmpfs            252M     1  252M    1% /proc/scsi
tmpfs            252M     1  252M    1% /sys/firmware
```

# du

Linux du （英文全拼：disk usage）命令用于显示目录或文件的大小。

du 会显示指定的目录或文件所占用的磁盘空间。

## 语法

```sh
du [-abcDhHklmsSx][-L <符号连接>][-X <文件>][--block-size][--exclude=<目录或文件>][--max-depth=<目录层数>][--help][--version][目录或文件]
```

**参数说明**：

- -a或-all 显示目录中个别文件的大小。
- -b或-bytes 显示目录或文件大小时，以byte为单位。
- -c或--total 除了显示个别目录或文件的大小外，同时也显示所有目录或文件的总和。
- -D或--dereference-args 显示指定符号连接的源文件大小。
- -h或--human-readable 以K，M，G为单位，提高信息的可读性。
- -H或--si 与-h参数相同，但是K，M，G是以1000为换算单位。
- -k或--kilobytes 以1024 bytes为单位。
- -l或--count-links 重复计算硬件连接的文件。
- -L<符号连接>或--dereference<符号连接> 显示选项中所指定符号连接的源文件大小。
- -m或--megabytes 以1MB为单位。
- -s或--summarize 仅显示指定目录或文件的总大小，而不显示其子目录的大小。
- -S或--separate-dirs 显示个别目录的大小时，并不含其子目录的大小。
- -x或--one-file-xystem 以一开始处理时的文件系统为准，若遇上其它不同的文件系统目录则略过。
- -X<文件>或--exclude-from=<文件> 在<文件>指定目录或文件。
- --exclude=<目录或文件> 略过指定的目录或文件。
- --max-depth=<目录层数> 超过指定层数的目录后，予以忽略。
- --help 显示帮助。
- --version 显示版本信息。

## example

```sh
# -h: 以K，M，G为单位，提高信息的可读性
# --max-depth=1: 只显示一层深度
> du -h --max-depth=1
6.0K    ./.jupyter
1.0K    ./.ssh
3.5K    ./.config
188M    ./demo
206M    ./.local
512     ./.ipynb_checkpoints
1.0K    ./.nv
1.5K    ./.modelscope
4.5K    ./models
66K     ./.filebrowserconfig
23G     ./.conda
36K     ./.ipython
6.5G    ./.cache
30G     .
```

