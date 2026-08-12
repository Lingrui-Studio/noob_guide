# 入门 Linux

在上一节中，我们已经介绍了 Linux 的重要性和学习它的理由，并且推荐了 VS Code 作为主要的开发工具。这一节我们开始介绍 Linux 常用的各种命令，跟着下面的顺序一步步来：先认识终端长什么样，再搞清楚「我在哪、这里有什么、怎么走」，然后开始建文件、看文件、装软件。

这里有个交互式的教程网站，推荐大家前往体验

- [Beginners](https://webterm.app/en/tutorials/beginner)
- [Fundamentals](https://webterm.app/en/tutorials/basic)
- [Advanced](https://webterm.app/en/tutorials/advanced)

## 先认识终端

终端（Terminal）就是给你敲命令的地方。VS Code 里按 ++shift+esc++，或菜单 **Terminal → New Terminal** 打开；在 Linux 桌面上找 Terminal 图标也行。

打开后你会看到一行类似这样的字（本文以 Ubuntu 为例）：

```bash
student@ubuntu:~$
```

这就是**提示符**。几个部分的意思：

- `student`：当前用户名
- `ubuntu`：机器名
- `~`：当前所在目录，`~` 代表家目录
- `$`：普通用户的提示符（root 用户显示 `#`）

光标停在 `$` 后面，输入命令回车就执行。

## 我在哪：pwd

先回答一个最基础的问题——**我现在在哪个目录**。敲：

```bash
pwd
```

`pwd` 是 print working directory，会打印当前目录的完整路径，比如 `/home/student`。迷路了就 `pwd` 一下。

## 这里有什么：ls

`ls` 列出当前目录里的文件：

```bash
ls
```

光秃秃一个列表，没什么信息。加参数看详情：

```bash
ls -l
```

`-l` 显示权限、所有者、大小、修改时间。想连隐藏文件（以 `.` 开头）一起看：

```bash
ls -la
```

`-a` 是 all。排查问题时 `ls -la` 是最常用的姿势。

> 第一次看到 `drwxr-xr-x` 别慌：第一位 `d` 表示目录，`-` 表示普通文件，剩下的权限位先不用管，用到再说。

## 走起来：cd

`cd`（change directory）切换目录：

```bash
cd 目录名      # 进入子目录
cd ..         # 回上一级
cd ~          # 回自己的家目录
cd            # 不带参数，默认也回 home
```

几个约定俗成的写法：

- `.` 当前目录
- `..` 上一级
- `~` 家目录
- `/` 根目录

!!! tip "两个偷懒技巧"
    敲目录名按 ++tab++ 自动补全，候选多就按两下 tab 列出来。按 ↑ 上箭头翻历史命令，重复的命令不用重打。

## 动手建东西：mkdir、touch、cp、mv、rm

光看不练没意思，自己建一个试试：

```bash
mkdir testdir      # 建目录
touch hello.txt    # 建一个空文件
```

`cp` 复制，`mv` 移动或重命名：

```bash
cp hello.txt hello2.txt   # 复制一份
mv hello2.txt testdir/    # 移到 testdir 里
mv hello.txt bye.txt      # 重命名
```

`rm` 删除：

```bash
rm bye.txt          # 删文件
rm -r testdir       # -r 递归删目录，连同里面的东西
```

!!! warning "rm 没有回收站"
    删了就没了。`rm -r` 尤其要小心，先 `ls` 看清要删什么。网上流传的 `rm -rf /` 是拿来坑新手的，见到别敲。

## 看文件：cat、less、head、tail

写代码、看配置，第一步都是把文件打开：

```bash
cat hello.txt       # 整个文件直接打印，适合小文件
less /etc/hosts     # 分页浏览，按 q 退出，适合大文件
head -n 20 xxx.log  # 只看开头 20 行
tail -n 20 xxx.log  # 只看末尾 20 行，看日志最常用
```

!!! tip "在一堆输出里找关键词"
    用管道 `|` 把上一条命令的输出喂给下一条：`cat xxx.log | grep error`，只留下含 `error` 的行。排查问题靠这一条能省很多时间。

## 管道与重定向：|、<、>、>>、<<

Linux 命令通常从键盘读取输入，再把结果打印到终端。管道和重定向可以改变数据的去向：让一个命令接着处理另一个命令的结果，或者在命令和文件之间传递内容。

**管道 `|`：把左边的输出交给右边**

```bash
ls -la | less                 # 文件太多，交给 less 分页查看
grep error xxx.log | tail -n 20  # 找出 error，再只看最后 20 条
```

一条命令处理不完，就用 `|` 串起来。数据从左往右流，每个命令只负责一步。

**输出重定向 `>` 和 `>>`：把结果写进文件**

```bash
echo "hello" > hello.txt     # 写入文件；文件原有内容会被覆盖
echo "world" >> hello.txt    # 追加到文件末尾，不会覆盖原内容
ls -la > files.txt            # 把 ls 的结果保存下来
```

!!! warning "用 > 前先看清文件名"
    `>` 会直接覆盖目标文件。想保留原内容就用 `>>`，重要文件操作前可以先 `cat` 一眼。

**输入重定向 `<`：让命令从文件读取输入**

```bash
wc -l < hello.txt             # 统计 hello.txt 有多少行
sort < names.txt              # 读取 names.txt，排序结果仍打印到终端
sort < names.txt > sorted.txt # 从文件读，排序后写入另一个文件
```

**多行输入 `<<`：临时输入一整段内容**

`<<` 后面跟一个自定义的结束标记，常用 `EOF`。Shell 会持续读取，直到再次遇到这个标记：

```bash
cat << EOF
第一行
第二行
EOF
```

上面的 `cat` 会收到两行文本并打印出来。`EOF` 不是固定写法，换成 `END` 等其他单词也可以，只要开头和结尾一致。

!!! tip "记法"
    `|` 是命令接命令；尖括号朝哪边，数据就大致往哪边走。`>` 写入，`>>` 追加，`<` 读取，`<<` 输入多行。

## 装软件：sudo 和 apt

Ubuntu 这类发行版用 apt 装软件，一条命令搞定：

```bash
sudo apt update         # 先更新软件源索引
sudo apt install vim    # 再装软件，vim 换成你要的
```

`sudo` 以管理员权限执行，会要求输密码——输入时不显示字符，这是正常的，不是没敲上。

!!! tip "装之前先 update"
    新系统或很久没装过东西，先 `sudo apt update` 刷新索引再 `install`，不然可能提示找不到软件包。

## 编辑文件：vim

在 VS Code 中虽然可以很方便地编辑**工作目录**下的文件，但是若要为了少数不在工作目录下的文件而频繁切换工作目录，就未免有些麻烦了。好在 Linux 中也有轻量级编辑器，常用的比如 **vim**，几乎每台 Linux 都有（没有的话 `sudo apt install vim`）。它可以通过`vim 文件名`直接打开文件，且各种操作都无需用到鼠标，双手无需在键盘和鼠标之间切换，效率很高。

!!! tip
    `man`、`less`等命令打开的文件内容也基本与 vim 的操作逻辑类似，所以学会 vim 的基本操作后，其他命令的使用也会变得更加顺手。

vim 和普通编辑器最大的区别是**有模式**。刚打开是**命令模式**，这时按键不是输入文字，是发命令。按 ++i++ 可进入**插入模式**打字，按 ++esc++ 回命令模式——记住这一个循环，剩下就是记按键了。

**移动光标**（命令模式下）

| 按键 | 作用 |
|------|------|
| `h` / `j` / `k` / `l` | 左 / 下 / 上 / 右（方向键也行） |
| `w` / `b` | 按词跳下一个 / 上一个 |
| `0` / `$` | 跳到行首 / 行尾 |
| `gg` / `G` | 跳到文件开头 / 结尾 |
| `ctrl+d` / `ctrl+u` | 向下 / 向上翻半页 |

**编辑**

| 按键 | 作用 |
|------|------|
| `x` | 删光标处的字符 |
| `dd` | 删整行 |
| `yy` | 复制整行 |
| `p` | 粘贴 |
| `u` / `ctrl+r` | 撤销 / 重做 |

命令前加数字是重复次数：`3dd` 删三行，`5yy` 复制五行，很常用。

**查找**

- 命令模式按 `/` 进入查找，输入关键词回车，`n` / `N` 跳下一个 / 上一个

**插入模式不只有 ++i++**

- `a`：光标后插入
- `A`：行尾插入
- `o`：下一行新开一行插入
- `O`：上一行新开一行插入

**保存退出**

| 按键 | 作用 |
|------|------|
| `:w` | 保存，不退出 |
| `:q` | 退出 |
| `:wq` | 保存并退出 |
| `:q!` | 不保存强制退出 |

对于更加详细的 vim 教程，可以参考 [OI Wiki - Vim](https://oi-wiki.org/tools/editor/vim/) 和 [Open Vim](https://www.openvim.com/)。

## 终端复用：tmux

`tmux` 是终端复用器。一句话说它的用处：**让你断开连接后，终端里的东西还活着**。

最常见的场景：SSH 连上服务器跑个任务，窗口一关任务就断了。用 tmux 跑，窗口随便关，任务照常继续，下次连上 `tmux a` 就回来了。

```bash
sudo apt install tmux   # 安装
tmux                    # 新建会话
tmux a                  # 重新连上之前的会话
tmux ls                 # 看当前有哪些会话
```

tmux 里所有操作都靠前缀键 ++ctrl+b++，**按完再按**功能键：

- ++c++：新建窗口
- ++n++ / ++p++：切上一个 / 下一个窗口
- ++d++：脱离（detach），会话在后台继续跑
- ++"%"++：左右分屏
- ++double-quote++：上下分屏
- ++space++：切换分屏布局
- ++comma++：给窗口重命名

!!! info "Cheatsheet"
    [tmux Cheat Sheet: All Key Bindings & Commands - Terminal Guide](https://www.terminal.guide/tools/multiplexer/tmux/cheatsheet/)

## 不会用怎么办：man 和 --help

忘了命令怎么用，先问它自己：

```bash
man ls       # 完整手册，按 q 退出
ls --help    # 快速帮助
```

若你觉得`man`太啰嗦，也可以用 [tldr](https://tldr.sh/)。

也有在线查询 [explainshell.com](https://explainshell.com/) 可以用。

## 拓展阅读

想要更详细的 Linux 教程？请看中科大出品的 [Linux 101 - USTC](https://101.lug.ustc.edu.cn/)，以及：

- [Linux 教程 - 菜鸟教程](https://www.runoob.com/linux/linux-tutorial.html)：中文入门，命令速查方便
- [Linux Commands Reference - Terminal Guide](https://www.terminal.guide/linux/commands/)：布局更加好看的 Linux 命令手册
- [计算机教育中缺失的一课](https://missing-semester-cn.github.io/)：MIT - 计算机教育中缺失的一课
