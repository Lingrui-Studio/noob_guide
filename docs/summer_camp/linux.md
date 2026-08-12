# 初识 Linux

嘿，同学。

你是否曾有过这样的感觉：你的电脑，这台你花了不少钱买来的设备，似乎并不完全属于你？没完没了的强制更新，在你最忙的时候突然重启；系统越来越慢，好像每过一年，它都在“变老”；硬盘上充斥着你从不使用却又删不掉的软件……

Windows 虽然有着最强的兼容性，但随之而来的是无数历史遗留问题和无法改进的设计缺陷，这导致基于 Windows 环境的开发往往会遇到各种问题，参考 [停止用 Windows 工作！- 知乎](https://zhuanlan.zhihu.com/p/2024527609388627701)。

如果这些场景让你有所触动，那么，请允许我向你介绍一位新朋友：**Linux**。

> MacOS 与 Linux 同属 Unix 系统，在大部分场景下也能有与 Linux 相似的体验，所以若你是 Mac 用户，可以直接使用 MacOS 进行学习，或是通过 Linux 虚拟机来获得更接近 Linux 的体验。

## 不只是换个系统，更是打开计算机世界的钥匙

对于普通用户来说，操作系统 (Operating System) 只是一个运行软件的平台。但对于我们——未来的程序员、系统工程师、网络安全专家、AI 科学家，以及所有对技术充满好奇心的学习者——操作系统本身就是一个值得探索的宝藏。

Windows 和 macOS 为我们提供了精美的图形界面和“开箱即用”的便利，它们像是设计精良的汽车，你只需要学会方向盘和油门。而 Linux，则像是给你一整套顶级赛车的零部件，附上一本开源的图纸。它不仅让你驾驶，更邀请你打开发动机盖，去了解、去修改、去创造真正属于你自己的“座驾”。

## 为什么说 Linux 是计算机学生的“必修课”？

如果你想在计算机领域走得更远，学习 Linux 不是一个“选项”，而是一项至关重要的投资。原因如下：

### 1. 透明的内在，让你看透 OS 的本质

在学习操作系统原理、计算机网络这些核心课程时，你是否感觉理论很抽象？Linux 将这些理论活生生地展现在你面前。

!!! declaration "核心哲学：一切皆文件"
    这是 Linux 的核心哲学。无论是硬件设备、进程还是网络连接，都可以通过文件系统的形式来访问和操作。这让你能直观地理解操作系统是如何管理资源的。

* **开放的源代码**：从内核 (Kernel) 到系统工具，再到桌面环境，几乎所有东西都是开源的。遇到好奇的机制，你可以直接去读它的源代码——这是任何“黑箱”系统都无法提供的学习体验。
* **清晰的文件系统结构**：`/bin`、`/etc`、`/var`、`/home`…… 每个目录都有其明确的用途。理解了这套结构，你就理解了一个操作系统的基本骨架。
    ```bash title="Linux 文件系统结构示例 （简化）"
    / （根目录，所有文件和目录的起点）
    |
    ├── bin/      (Binaries) - 存放所有用户都能使用的基本命令，如 ls、cp
    ├── etc/      (Etcetera) - 存放系统范围的配置文件
    ├── home/     (Home) - 存放用户的个人文件和配置
    │   └── your_username/
    ├── lib/      (Libraries) - 存放程序运行时需要的共享库文件
    ├── tmp/      (Temporary) - 存放临时文件
    └── var/      (Variable) - 存放经常变化的文件，如日志、数据库等
        └── log/  （存放系统和应用的日志文件）
    ```

### 2. 命令行（CLI），程序员的超能力

图形界面很直观，但命令行 (Command Line Interface, CLI) 才是效率和自动化的王者。在 Linux 中，你将真正掌握命令行这个强大的工具。

* **精准高效**：忘掉鼠标在层层窗口间的繁琐点击。一条命令就能完成在图形界面下可能需要数分钟甚至数小时才能完成的复杂日志分析工作。
    ```bash title="命令组合示例"
    grep "error" /var/log/syslog | sort | uniq -c
    ```
* **组合与管道**：`|`（管道）这个小小的符号是 Linux 的精髓。它能将多个小程序的功能组合起来，像乐高积木一样，构建出无限强大的工作流。
* **自动化脚本**：学习 Shell 脚本（如 Bash），你可以将日常的重复性任务自动化，从备份文件到部署一个网站。这是通往 DevOps 和自动化运维的第一步。

### 3. 无缝衔接的开发环境

几乎所有顶级的开发工具都诞生于 Linux/Unix 环境，或者将它们作为第一公民。

* **“一行代码”安装一切**：无论是 `gcc`、Python、`Node.js` 还是 `PostgreSQL`，你只需要通过包管理器 (Package Manager) ，用一行命令就能完成安装和配置，干净利落。
* **原生支持**：Git、Docker、Kubernetes、Nginx、Apache…… 这些现代软件开发和部署的基石，在 Linux 上拥有最原生的支持和最佳的性能。你本地的开发环境将与服务器的生产环境保持高度一致，避免了无数“在我电脑上明明是好的”的尴尬。

### 4. 驰骋在 AI 与数据科学的前沿

人工智能 (Artificial Intelligence) 是当今最热门的领域，而 Linux 正是这片前沿阵地的默认操作系统。

* **生态系统**：顶级的深度学习框架如 TensorFlow、PyTorch，以及 NVIDIA 的 CUDA 工具包，都在 Linux 上拥有最优先、最完善的支持。
* **性能与驱动**：在 Linux 上，你可以更底层、更直接地与 GPU 等硬件交互，这对于需要极致性能的 AI 模型训练至关重要。
* **自动化与复现**：AI 研究和工程高度依赖实验的自动化和环境的可复现性。Linux 强大的命令行工具和以 Docker 为代表的容器化技术，为此提供了完美的解决方案。可以说，掌握 Linux 是成为一名合格 AI 工程师的必要条件。

### 5. 通往服务器与云计算的大门

你知道吗？全球超过 90% 的云服务器、几乎所有的超级计算机，以及你口袋里安卓手机的核心，都运行着 Linux。当你熟练掌握 Linux 时，你实际上已经拿到了进入后端开发、云计算、数据中心、嵌入式系统等广阔领域的门票。从在本地虚拟机里配置 Nginx，到在 AWS 上管理上百台服务器集群，底层的知识和技能是相通的。

## 如何开启你的 Linux 之旅？

作为一名计算机学习者，你有比普通用户更多的选择和更安全的方式来入门：

=== "Windows Subsystem for Linux (WSL)"

    如果你主要使用 Windows，WSL 是天赐神器。它让你可以在 Windows 中无缝地运行一个 Linux 子系统，直接使用 Linux 的命令行工具和开发环境，无需重启或虚拟机，并且还能直接在 Linux 中访问 Windows 本机的文件系统（通过`/mnt/c` 等路径）。

    **建议按这个顺序操作：**

    1. [微软官方：安装 WSL](https://learn.microsoft.com/zh-cn/windows/wsl/install)——先完成 WSL 2 和 Ubuntu 的安装。
    2. [微软官方：WSL 的基本命令](https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands)——学会查看发行版、关机、更新等常用操作。
    3. [VS Code 官方：在 WSL 中开发](https://code.visualstudio.com/docs/remote/wsl)——需要写代码时，再把 VS Code 接入 WSL。

=== "虚拟机 (Virtual Machine)"

    使用 VirtualBox 或 VMware，你可以在当前的 Windows 或 macOS 系统中，像运行一个普通软件一样运行一个完整的 Linux 系统。安全、隔离，可以随意“折腾”坏了也不怕。

    **任选一个虚拟机软件，跟着对应教程做即可：**

    * [Ubuntu 官方：使用 VirtualBox 运行 Ubuntu Desktop](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox)
    * [Ubuntu 官方：使用 VMware Workstation Player 运行 Ubuntu Desktop](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-vmware-workstation-player)
    * [VirtualBox 官方手册：创建你的第一台虚拟机](https://www.virtualbox.org/manual/ch01.html)——遇到教程版本不一致时用来查设置项。

=== "双系统 (Dual Boot)"

    当你准备好后，可以选择安装双系统。这能让 Linux 直接运行在硬件上，发挥全部性能，获得最原生的体验。

    !!! warning "动分区前先备份"

        双系统安装会修改磁盘分区和启动项。**先备份重要文件，并保存好 Windows 的 BitLocker 恢复密钥**；看不懂某个分区是干什么的，就先停手问导生。

    **建议同时对照下面几篇：**

    1. [Ubuntu 官方：在 Windows 中制作启动 U 盘](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows)
    2. [Ubuntu 官方：安装 Ubuntu Desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop)
    3. [Ubuntu 社区文档：Windows 与 Ubuntu 双系统](https://help.ubuntu.com/community/WindowsDualBoot)——重点看分区和启动相关说明。

!!! tip "发行版选择建议"

    对于发行版的选择，**Ubuntu** 依然是新手的最佳选择（推荐选择最新的长期支持版本，如 Ubuntu 26.04 LTS），它们拥有庞大的社区和丰富的文档。当你更加熟练后，可以去挑战 **Arch**、**NixOS** 等，它们会让你对系统有更深层次的理解。

有了 Linux 系统之后，便要自己动手操作一番体验一下了，这里推荐使用 **VS Code**。怎么用？两种姿势，任选其一：

=== "姿势一：VS Code 远程连接（推荐）"

    代码、终端、界面全都在本机 VS Code 里，体验最舒服；文件直接存在 Linux 里，本机与 Linux 两边都能用。WSL 和虚拟机 / 远程 Linux 机器都适用。

    **1. 连接 WSL（Windows 用户）**

    1. 在 VS Code 扩展市场安装 **WSL** 扩展（`ms-vscode-remote.remote-wsl`）。
    2. 点左下角绿色按钮（`><`），选择 **Connect to WSL**。
    3. VS Code 会重新打开一个窗口并自动接入 WSL，下方终端里直接就是 Linux 环境，`pwd` 敲一下就能确认。

    **2. 通过 SSH 连接虚拟机 / 远程 Linux 机器**

    1. 先在 Linux 里装好并启动 SSH 服务：
        ```bash
        sudo apt update && sudo apt install -y openssh-server
        sudo systemctl enable --now ssh
        ```
    2. 在 Linux 终端里用 `ip addr`（或 `ip a`）查一下它的 IP 地址，形如 `192.168.x.x`。
    3. 在 VS Code 安装 **Remote - SSH** 扩展（`ms-vscode-remote.remote-ssh`）。
    4. 点左下角绿色按钮 → **Connect to Host...** → 输入 `用户名@IP`（例如 `student@192.168.1.100`）→ 回车，输入密码就连上了。
    5. 想免密的话，可以后续再配置 SSH 密钥。

    **参考链接：**

    * [VS Code 官方：使用 WSL 进行远程开发](https://code.visualstudio.com/docs/remote/wsl)
    * [VS Code 官方：SSH 远程开发](https://code.visualstudio.com/docs/remote/ssh)
    * [VS Code 官方：SSH 连接教程（手把手演示）](https://code.visualstudio.com/docs/remote/ssh-tutorial)

=== "姿势二：在 Linux 图形界面里直接装 VS Code"

    直接在虚拟机的图形桌面上装一个 VS Code，打开就像 Windows 里一样用，适合想完整体验 Linux 桌面环境的同学。

    **Ubuntu 系（推荐）：**

    1. 打开 VS Code 官网 [https://code.visualstudio.com](https://code.visualstudio.com/) 下载 **.deb** 安装包。
    2. 在终端里进入下载目录并安装：
        ```bash
        sudo apt install ./code_*.deb
        ```
    3. 装好后在应用菜单里搜索 **Visual Studio Code** 启动即可。
    4. 首次使用建议在扩展市场装 **中文（简体）语言包**（`ms-ceintl.vscode-language-pack-zh-hans`），界面就切换成中文了。

    !!! tip "其他安装方式"
        也可以用 Snap 一键安装：`sudo snap install code --classic`。想跟随官方源自动更新的同学，可以参考下方链接里的 apt 仓库安装方式。

    **参考链接：**

    * [VS Code 官方：在 Linux 上安装](https://code.visualstudio.com/docs/setup/linux)
    * [VS Code 官方：中文语言包](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-zh-hans)

!!! tip "在 VS Code 中使用终端"

    你可以在 VS Code 左上方找到 **Terminal**（终端）-> **New Terminal**（新建终端）打开，或使用快捷键：++shift+esc++ 快速切换。

## 结语

学习 Linux，你得到的绝不仅仅是简历上的一行技能。你将获得一种更接近计算机本质的视角，一种解决问题的思维方式，以及一把能打开无数前沿技术大门的钥匙。

所以，别再犹豫了。今天就去下载一个镜像，启动你的虚拟机，敲下你的第一个 `ls -la` 吧。这片广阔的新大陆，正等待着你的探索。
