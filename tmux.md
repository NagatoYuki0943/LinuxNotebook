


```text
# 开启新session
tmux


# 开启新session并命名
tmux new -s my_session


# 显示所有session
tmux ls


# 使用session编号接入
tmux attach -t 0


# 使用session名称接入
tmux attach -t <session-name>
tmux a -t name # 简写


# 使用session编号kill
tmux kill-session -t 0
# 使用session名称kill
tmux kill-session -t <session-name>


# 使用session编号切换
tmux switch -t 0
# 使用session名称切换
tmux switch -t <session-name>


# 重命名会话
tmux rename-session -t <old-name> <new-name>
```

```
# 断开当前session
Ctrl + b d

# 选择需要跳转的session会话
Ctrl + b s

# 重命名当前会话
Ctrl + b $

# 在当前session中多加一个window
Ctrl + b c

# 在一个session中的多个window中作出选择
Ctrl + b w

# 关闭当前session中的当前window
Ctrl + b x

# 进入tmux翻屏模式, 实现上下翻页
Ctrl + b [  
### 进入翻屏模式后PgUp PgDn 实现上下翻页（mac可以用fn + ↑ ↓实现上下翻页）
### q 退出翻屏模式

#############
# 其他常用快捷键
##############

Ctrl + b ！  #关闭一个session中所有窗口
Ctrl + b % #将当前窗口分成左右两分
Ctrl + b " #将当前窗口分成上下两分
Ctrl + b 方向键 #让光标在不同的窗口中跳转 
Ctrl + b 方向键 #按住C+b不放，同时按住方向键，可以调节光标所在窗口的大小 
```