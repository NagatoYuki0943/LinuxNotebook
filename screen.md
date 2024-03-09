

# screen

`screen`是窗口管理器的命令行界面版本，它提供了统一的管理多个会话的界面和相应的功能。**简单说只要`screen`还在，就算你断开了SSH连接，你这个连接中运行的东西还在，你再开个窗口输入命令又能进入这个`screen`对应的窗口状态**

## cmd

```sh
screen -S yourname          # 创建一个新的session,名字是yourname
screen -ls                  # 列出所有的session
screen -r yourname          # 进入指定的session
screen -d yourname          # 断开指定的session
screen -d -r yourname       # 断开当前的session并进入指定的session
screen -x yourname          # 恢复之前离线的指定session
screen -X -S yourname quit  # 删除指定的session
```

## example

```sh
> screen -S llm # 创建名为 llm 的 screen

> screen -ls    # 列出所有的session
There is a screen on:
        1188255.llm     (03/09/2024 09:24:57 AM)        (Detached)
1 Socket in /run/screen/S-root.

> screen -r llm # 进入 llm

> screen -d llm # 断开 llm

> screen -ls
There is a screen on:
        1188255.llm     (03/09/2024 09:24:58 AM)        (Detached)
> screen -X -S llm quit # 删除 llm
> screen -ls
No Sockets found in /run/screen/S-root.
```

