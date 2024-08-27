# linux

## netstat

**netstat -tunlp** 用于显示 tcp，udp 的端口和进程等相关情况。

netstat 查看端口占用语法格式：

```
netstat -tunlp | grep 端口号
```

- -t (tcp) 仅显示tcp相关选项
- -u (udp)仅显示udp相关选项
- -n 拒绝显示别名，能显示数字的全部转化为数字
- -l 仅列出在Listen(监听)的服务状态
- -p 显示建立相关链接的程序名

例如查看 80 端口的情况，使用以下命令：

```sh
# netstat -tunlp | grep 80
tcp        0      0 0.0.0.0:80            0.0.0.0:*               LISTEN      26993/nodejs   
```

更多命令：

```sh
netstat -ntlp              // 查看当前所有tcp端口
netstat -ntulp | grep 80   // 查看所有80端口使用情况
```

参数说明：

```sh
netstat --help
用法：netstat [-vWeenNcCF] [<Af>] -r         netstat {-V|--version|-h|--help}
       netstat [-vWnNcaeol] [<Socket> ...]
       netstat { [-vWeenNac] -i | [-cnNe] -M | -s [-6tuw] }

        -r, --route              显示路由表
        -i, --interfaces         显示接口表
        -g, --groups             显示多播组成员资格
        -s, --statistics         显示网络统计信息（类似SNMP）
        -M, --masquerade         显示伪装连接

        -v, --verbose            详细模式
        -W, --wide               不截断IP地址
        -n, --numeric            不解析名称
        --numeric-hosts          不解析主机名
        --numeric-ports          不解析端口名
        --numeric-users          不解析用户名
        -N, --symbolic           解析硬件名称
        -e, --extend             显示其他/更多信息
        -p, --programs          显示套接字的PID/程序名
        -o, --timers            显示计时器
        -c, --continuous         连续列表

        -l, --listening         显示监听服务器套接字
        -a, --all               显示所有套接字（默认：已连接）
        -F, --fib               显示转发信息基础（默认）
        -C, --cache             显示路由缓存而不是FIB
        -Z, --context           显示套接字的SELinux安全上下文

  <Socket>={-t|--tcp} {-u|--udp} {-U|--udplite} {-S|--sctp} {-w|--raw}
           {x|--unix} --ax25 --ipx --netrom
  <AF>=使用 '-6|-4' 或 '-A <af>' 或 '--<af>'; 默认：inet
  支持路由的可能地址族列表：
    inet (DARPA互联网) inet6 (IPv6) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP) 
    x25 (CCITT X.25)


netstat --help
usage: netstat [-vWeenNcCF] [<Af>] -r         netstat {-V|--version|-h|--help}
       netstat [-vWnNcaeol] [<Socket> ...]
       netstat { [-vWeenNac] -i | [-cnNe] -M | -s [-6tuw] }

        -r, --route              display routing table
        -i, --interfaces         display interface table
        -g, --groups             display multicast group memberships
        -s, --statistics         display networking statistics (like SNMP)
        -M, --masquerade         display masqueraded connections

        -v, --verbose            be verbose
        -W, --wide               don't truncate IP addresses
        -n, --numeric            don't resolve names
        --numeric-hosts          don't resolve host names
        --numeric-ports          don't resolve port names
        --numeric-users          don't resolve user names
        -N, --symbolic           resolve hardware names
        -e, --extend             display other/more information
        -p, --programs           display PID/Program name for sockets
        -o, --timers             display timers
        -c, --continuous         continuous listing

        -l, --listening          display listening server sockets
        -a, --all                display all sockets (default: connected)
        -F, --fib                display Forwarding Information Base (default)
        -C, --cache              display routing cache instead of FIB
        -Z, --context            display SELinux security context for sockets

  <Socket>={-t|--tcp} {-u|--udp} {-U|--udplite} {-S|--sctp} {-w|--raw}
           {-x|--unix} --ax25 --ipx --netrom
  <AF>=Use '-6|-4' or '-A <af>' or '--<af>'; default: inet
  List of possible address families (which support routing):
    inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP) 
    x25 (CCITT X.25)
```





## lsof

lsof(list open files)是一个列出当前系统打开文件的工具。

lsof 查看端口占用语法格式：

```sh
lsof -i:端口号
```

### 实例

查看服务器 8000 端口的占用情况：

```sh
# lsof -i:8000
COMMAND   PID USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
nodejs  26993 root   10u  IPv4 37999514      0t0  TCP *:8000 (LISTEN)
```

更多 lsof 的命令如下：

```sh
lsof -i:8080        // 查看8080端口占用
lsof abc.txt        // 显示开启文件abc.txt的进程
lsof -c abc         // 显示abc进程现在打开的文件
lsof -c -p 1234     // 列出进程号为1234的进程所打开的文件
lsof -g gid         // 显示归属gid的进程情况
lsof +d /usr/local/ // 显示目录下被进程开启的文件
lsof +D /usr/local/ // 同上，但是会搜索目录下的目录，时间较长
lsof -d 4           // 显示使用fd为4的进程
lsof -i -U          // 显示所有打开的端口和UNIX domain文件
```

# windows

## netstat

example：

```
netstat -aon | findstr 端口号
```

查看 80 端口占用情况：

```sh
netstat -aon | findstr 80
```

参数说明：

```sh
> netstat --help

显示协议统计信息和当前 TCP/IP 网络连接。

NETSTAT [-a] [-b] [-e] [-f] [-i] [-n] [-o] [-p proto] [-r] [-s] [-t] [-x] [-y] [interval]

  -a            显示所有连接和侦听端口。
  -b            显示在创建每个连接或侦听端口时涉及的
                可执行文件。在某些情况下，已知可执行文件托管
                多个独立的组件，此时会
                显示创建连接或侦听端口时
                涉及的组件序列。在此情况下，可执行文件的
                名称位于底部 [] 中，它调用的组件位于顶部，
                直至达到 TCP/IP。注意，此选项
                可能很耗时，并且可能因为你没有足够的
                权限而失败。
  -e            显示以太网统计信息。此选项可以与 -s 选项
                结合使用。
  -f            显示外部地址的完全限定
                域名(FQDN)。
  -i            显示 TCP 连接在当前状态所花费的时间。
  -n            以数字形式显示地址和端口号。
  -o            显示拥有的与每个连接关联的进程 ID。
  -p proto      显示 proto 指定的协议的连接；proto
                可以是下列任何一个: TCP、UDP、TCPv6 或 UDPv6。如果与 -s
                选项一起用来显示每个协议的统计信息，proto 可以是下列任何一个:
                IP、IPv6、ICMP、ICMPv6、TCP、TCPv6、UDP 或 UDPv6。
  -q            显示所有连接、侦听端口和绑定的
                非侦听 TCP 端口。绑定的非侦听端口
               不一定与活动连接相关联。
  -r            显示路由表。
  -s            显示每个协议的统计信息。默认情况下，
                显示 IP、IPv6、ICMP、ICMPv6、TCP、TCPv6、UDP 和 UDPv6 的统计信息；
                -p 选项可用于指定默认的子网。
  -t            显示当前连接卸载状态。
  -x            显示 NetworkDirect 连接、侦听器和共享
                终结点。
  -y            显示所有连接的 TCP 连接模板。
                无法与其他选项结合使用。
  interval      重新显示选定的统计信息，各个显示间暂停的
                间隔秒数。按 CTRL+C 停止重新显示
                统计信息。如果省略，则 netstat 将打印当前的
                配置信息一次。
```

