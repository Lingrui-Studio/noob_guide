# 入门 Linux

在上一节中，我们已经介绍了 Linux 的重要性和学习它的理由，并且推荐了 VS Code 作为主要的开发工具。这一节我们开始介绍 Linux 常用的各种命令，跟着下面的顺序一步步来：先认识终端长什么样，再搞清楚「我在哪、这里有什么、怎么走」，然后开始建文件、看文件、装软件。每步只讲够用的。

## 先认识终端

终端（Terminal）就是给你敲命令的地方。VS Code 里按 ++shift+esc++，或菜单 **Terminal → New Terminal** 打开；在 Linux 桌面上找 Terminal 图标也行。

打开后你会看到一行类似这样的字：

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
sudo apt install tmux   # 装
tmux                    # 新建会话
tmux new -s work        # 新建会话并起名 work
tmux a -t work     # 重新连上 work
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

!!! tip "记住这个循环就行"
    `tmux new -s work` 开一个 → 干活 → ++ctrl+b++ → ++d++ 脱离 → 下次 `tmux a -t work` 回来。这一个循环覆盖了日常九成用法。

## 不会用怎么办：man 和 --help

忘了命令怎么用，先问它自己：

```bash
man ls       # 完整手册，按 q 退出
ls --help    # 快速帮助
```

报错看不懂，把报错原文复制去搜，关键词带上系统版本和命令名，比如 `Ubuntu 24.04 apt permission denied`，别只搜「apt 报错」。

## 拓展阅读

- [Linux 教程 - 菜鸟教程](https://www.runoob.com/linux/linux-tutorial.html)：中文入门，命令速查方便
- [Linux Journey](https://linuxjourney.com/)：英文循序渐进，从命令行到 shell 脚本
- [The Linux Command Line](https://linuxcommand.org/tlcl.php)（官方免费 PDF）：很多人入门命令行从这本开始
- [explainshell.com](https://explainshell.com/)：把一条命令逐词拆开解释，看不懂组合命令时用
- [tldr pages](https://tldr.sh/)：嫌 `man` 啰嗦就用它，给常用命令的极简示例
- [Ubuntu 官方文档](https://help.ubuntu.com/)：系统问题的第一手资料
- [Arch Wiki](https://wiki.archlinux.org/)：讲原理最清楚，虽然是 Arch 的 wiki，全发行版通用
- [计算机教育中缺失的一课](https://missing-semester-cn.github.io/)：MIT - 计算机缺失的一科
