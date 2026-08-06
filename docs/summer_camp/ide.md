# IDE

IDE 可以理解成“写代码的工作台”：写代码、运行程序、看报错、打断点，都在同一个窗口完成。新生先记住这一点就够了，工具能用起来比背定义重要。

本页推荐 **VS Code**。它本身是编辑器，安装对应扩展后就能完成日常开发；如果你更喜欢一站式软件，也可以选择 JetBrains 系列。

??? info "你还漏了 ai 工具"

    你说得太对了！在 2026 年的今天，**AI 工具**已经不再是 IDE 的"可选插件"，而是成为了现代 IDE 的**核心支柱**之一。漏掉它确实是一个重大缺失。

    **🤖 AI 如何重塑了 IDE**

    如果说 LSP 解决了"语言智能的标准化"，那么 AI 正在解决"**开发意图的理解与生成**"。现代 IDE 中的 AI 能力主要体现在以下几个层面：

    **1. 代码生成与补全**

    -   **上下文感知补全：** 不再只是语法级别的补全，而是理解整个文件、项目结构甚至注释意图后，生成整段逻辑代码。
    -   **自然语言转代码：** 在编辑器内直接用自然语言描述需求，AI 自动生成实现代码。
    -   **测试/文档生成：** 一键为函数生成单元测试、JSDoc/docstring 等。

    **2. 智能对话与问答**

    -   **内嵌 Chat：** 无需离开编辑器即可提问，AI 能直接读取当前打开的文件、选中的代码、终端报错信息作为上下文。
    -   **代码解释与重构建议：** 选中一段遗留代码，让 AI 解释逻辑并给出重构方案，可直接应用修改。
    -   **错误诊断辅助：** 编译/运行报错时，AI 自动分析原因并提供修复建议。

    **3. Agent 模式**

    这是当前最前沿的方向：
    -   **自主任务执行：** 开发者描述一个高层目标（如"给用户模块添加邮箱验证功能"），AI Agent 自主规划步骤、搜索代码库、编辑多个文件、运行测试、迭代修复。
    -   **工具调用：** AI 可以调用终端命令、浏览器、数据库查询、API 文档等外部工具来完成任务。
    -   **多步推理与自我纠错：** 遇到失败时能自动回溯、调整策略，而非简单重试。

    **4. 代码审查与安全**
    
    -   **实时安全扫描：** AI 在编码过程中识别潜在漏洞、不安全依赖。
    -   **PR Review 辅助：** 自动生成变更摘要、发现潜在 Bug、检查代码规范。

    **🏗️ AI 时代的 IDE 架构演进**

    结合你之前提到的 LSP，现代 IDE 的完整架构应该是：

    > **现代 IDE = 编辑器 + LSP（语言智能）+ DAP（调试协议）+ AI 服务 + 构建工具 + 插件生态**

    其中 AI 服务又可以分为：
    -   **本地模型：** 隐私敏感场景，低延迟补全
    -   **云端大模型：** 复杂推理、Agent 任务、长上下文理解
    -   **RAG 管线：** 检索项目文档、代码库、API 参考，让 AI 回答基于真实项目上下文而非纯通用知识

    **💡 代表性 AI IDE / 工具**

    | 工具 | 特点 |
    | :--- | :--- |
    | **Cursor** | AI-Native IDE，深度集成 Agent、Tab 补全、Chat，被视为 AI IDE 标杆 |
    | **GitHub Copilot** | 最早普及的 AI 编程助手，现已支持 Agent 模式和工作区索引 |
    | **Windsurf (Codeium)** | Cascade 流式 Agent，强调上下文感知和多文件协同编辑 |
    | **VS Code + Copilot/Cline** | 通过插件获得接近 AI-Native IDE 的体验 |
    | **JetBrains AI Assistant** | 深度集成于 IntelliJ 系 IDE，利用 PSI 树提供精准代码感知 |
    | **Trae / MarsCode** | 国内厂商推出的 AI IDE，中文场景优化较好 |

    **⚠️ 值得注意的趋势与挑战**

    -   **从"辅助"到"协作"：** AI 正从被动响应转向主动参与开发流程，角色更像"结对编程伙伴"而非"自动补全引擎"。
    -   **上下文窗口是关键瓶颈：** 大型项目的代码量远超模型上下文限制，RAG、摘要压缩、选择性检索等技术成为差异化竞争点。
    -   **信任与验证：** AI 生成的代码仍需人工审查，IDE 需要提供更好的 diff 预览、测试集成和回滚机制。
    -   **隐私与合规：** 企业用户对代码是否上传云端高度敏感，本地部署和私有化方案需求强烈。

    **✅ 最终修正版总结**

    > **2026 年的 IDE = 编辑器 + LSP + DAP + AI（补全/Chat/Agent）+ 构建工具 + 插件生态**

    LSP 让编辑器获得了**语言级智能**，AI 让编辑器获得了**意图级智能**。两者叠加，才构成了当代理想开发环境的完整图景。

    非常感谢你的两次补充，这让这个回答从"教科书定义"升级到了"2026 年真实开发体验"。🙏

AI 可以帮你理解报错和查资料，但招新期间请先采用 [**古法编程**][hand programming]：自己写、自己跑、自己调试，先把基础打牢。

  [hand programming]: https://cn.bing.com/search?q=%E4%BB%80%E4%B9%88%E6%98%AF%E5%8F%A4%E6%B3%95%E7%BC%96%E7%A8%8B "不依赖 AI Agent 的传统编程方式，手动编写代码、调试和测试。"

> 我们并非完全禁止使用 AI。可以在网页上询问概念、报错原因和调试思路，但不要直接让 AI 生成整道题的代码。请把使用过的对话链接（或脱敏后的截图）汇总在题解最后，注意不要上传隐私或未公开的题目内容。

下面介绍我们推荐的 VS Code，以及可选的 JetBrains 系列。

## VS Code

**VS Code**（Visual Studio Code）是微软推出的免费编辑器。安装扩展后，它可以完成代码补全、运行和调试；个人、学习和商业使用均可免费使用。源码基础项目 Code - OSS 使用 MIT 许可证，但具体发行版和插件可能有自己的许可条款。

**下载安装：** 去官网 [code.visualstudio.com](https://code.visualstudio.com) 下载对应系统版本，一路下一步装完即可（Windows 安装时记得勾选 **"添加到 PATH"**，后面好用它启动项目）。

### C 语言开发环境

!!! warning
    若是 Windows 用户，推荐在 WSL 中进行 C 语言开发！若你执意要在 Windows 进行，请参照 [用 vscode 配置 c 语言环境](https://github.com/Fux-i/Learning-In-UESTC/blob/main/1-%E5%A4%A7%E4%B8%80%E4%B8%8A/01%20C%E8%AF%AD%E8%A8%80/%E7%94%A8vscode%E9%85%8D%E7%BD%AEc%E8%AF%AD%E8%A8%80%E7%8E%AF%E5%A2%83.docx) 。

Windows 用户优先使用 WSL；Linux/macOS 用户直接在本机终端操作。

**第 1 步：安装 C/C++ 扩展**

1. 打开 VS Code，点左侧边栏**扩展**图标（四个小方块），或按 ++ctrl+shift+x++
2. 搜索 `C/C++`，安装 **Microsoft** 发布的那一个
3. **Code Runner** 可选。刚开始建议先学会在终端运行命令。

**第 2 步：安装编译器（三选一）**

- **Windows**：推荐安装 **WSL（Ubuntu）**，然后在 WSL 终端执行 `sudo apt update && sudo apt install build-essential gdb`。需要在 WSL 中打开项目时，再安装并使用 VS Code 的 **WSL** 扩展
- **Linux**：一行命令搞定 `sudo apt install build-essential`（自带 gcc/g++）
- **macOS**：终端执行 `xcode-select --install` 装 Xcode Command Line Tools（自带 clang）

**第 3 步：验证编译器装好了**

打开 VS Code 内置终端（菜单栏“终端 → 新建终端”；Windows/Linux 也可按 Ctrl + 反引号），输入：

```bash
gcc --version
```

能看到版本号就说明编译器 OK。如果提示找不到 `gcc`，多半是没装好或没加进 PATH。

**第 4 步：写第一个 C 程序**

1. 新建一个文件夹（比如 `hello/`），用 VS Code 打开
2. 在里面新建 `hello.c`，写个经典的 Hello World：

```c
#include <stdio.h>

int main(void) {
    printf("Hello, Lingrui!\n");
    return 0;
}
```

**第 5 步：编译运行**

- **推荐：终端手动编译**：Linux/macOS/WSL 执行 `gcc -Wall -Wextra -std=c17 hello.c -o hello && ./hello`
- Windows PowerShell 使用 MinGW 时执行 `gcc hello.c -o hello.exe`，再运行 `./hello.exe`
- 已安装 Code Runner 的，可以点击右上角播放按钮运行单文件程序；多文件项目仍应使用项目自己的编译命令。

### 如何调试

想**单步调试**（打断点、看变量、一步步跑），光会 `gcc` 编译还不够，还需要项目里 `.vscode` 文件夹的两个文件配合：

- **`tasks.json`**：定义"**编译任务**"，告诉 VS Code 怎么调用 gcc 把 `.c` 编译成可执行文件
- **`launch.json`**：定义"**调试配置**"，告诉 VS Code 启动哪个调试器（gdb/lldb）、调试哪个程序

在项目根目录新建一个 `.vscode/` 文件夹，把下面两个文件放进去（**注释写得很详细，照着改项目名就能用**）：

!!! warning
    下面的示例以 Linux/WSL 为准。macOS 请把编译器和 `MIMode` 改成 `clang`、`lldb`；Windows 原生环境请使用 VS Code 自动生成的配置，不要直接照抄路径。

**`.vscode/tasks.json`**（负责编译）：

```json
{
  // 这个文件用于配置“编译任务”
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build hello",               // 任务名字，launch.json 里要引用它
      "type": "cppbuild",                   // C/C++ 扩展的任务类型（需已安装该扩展）
      "command": "gcc",                     // 使用 PATH 中的 gcc
      "args": [
        "-fdiagnostics-color=always",       // 报错信息带颜色，看着舒服
        "-g",                               // 生成调试信息，不加就没办法断点！必须留
        "${file}",                          // 当前打开的文件（就编译它）
        "-o",                               // 指定输出文件
        "${fileDirname}/${fileBasenameNoExtension}" // 输出到同目录，文件名跟源文件一致
      ],
      "options": {
        "cwd": "${fileDirname}"             // 在源文件所在目录里执行命令
      },
      "problemMatcher": ["$gcc"],           // 把 gcc 的报错解析成“问题”面板里的红点
      "group": {
        "kind": "build",
        "isDefault": true                   // 设为默认编译任务：按 ++ctrl+shift+b++ 直接编译
      },
      "detail": "用 gcc 编译当前打开的 C 文件"
    }
  ]
}
```

**`.vscode/launch.json`**（负责调试）：

```json
{
  // 这个文件用于配置“调试器”
  "version": "0.2.0",
  "configurations": [
    {
      "name": "调试 C",                      // 配置名字，显示在调试面板的下拉框里
      "type": "cppdbg",                      // 用 C/C++ 扩展提供的调试器
      "request": "launch",                   // launch = 自己启动程序；attach = 挂到已运行的程序
      "program": "${fileDirname}/${fileBasenameNoExtension}", // 要调试的可执行文件，必须和编译输出一致
      "args": [],                            // 传给程序的命令行参数，没有就留空
      "stopAtEntry": false,                  // true = 启动后自动停在 main 第一行
      "cwd": "${fileDirname}",               // 程序运行时的工作目录
      "environment": [],
      "externalConsole": false,              // 是否弹独立黑窗口；Linux/macOS 建议 false
      "MIMode": "gdb",                       // Linux/WSL 使用 gdb；macOS 改为 lldb
      "setupCommands": [
        {
          "description": "给 gdb 开启整齐打印",
          "text": "-enable-pretty-printing",
          "ignoreFailures": true
        }
      ],
      "preLaunchTask": "build hello"         // 关键：调试前先自动运行 tasks.json 里的编译任务
    }
  ]
}
```

**怎么用：**

1. 在 `hello.c` 的代码行号左边**点一下**，打上红点（断点）
2. 按 **F5** 启动调试 → VS Code 会先自动编译，再跑起来并停在断点处
3. **F10** 单步跳过、**F11** 进入函数、**F5** 继续运行，上方调试工具栏可以实时看变量值

> **嫌手写麻烦？** 打开 `hello.c` 直接按 **F5** → 选 **C++ (GDB/LLDB)** → 再选 **gcc - 生成和调试活动文件**（英文版 `gcc - Build and debug active file`），VS Code 会自动生成上面这两个文件，改改项目名就能用。

!!! warning
    `#include` 处飘红时，先确认 VS Code 打开的终端和编译器是同一个环境，再在命令面板运行 “C/C++: Edit Configurations (UI)” 选择正确的编译器。调试时若提示找不到 `gdb`，Linux/WSL 执行 `sudo apt install gdb`；macOS 使用 `lldb`。

## JetBrains IDEs

JetBrains 几乎为所有主流语言提供了对应的 IDE，功能完整但比较占内存。常见的有：

- **IntelliJ IDEA**：Java、Kotlin、Scala 等 JVM 语言的首选 IDE
- **PyCharm**：Python 开发的首选 IDE
- **Rider**：C#、.NET、Unity 游戏开发首选 IDE
- **CLion**：C/C++ 开发
- **WebStorm**：前端开发
- **GoLand**：Go 开发
- **RustRover**：Rust 开发

不同产品的免费政策不同：有的提供免费版本，有的只对学生、开源项目或非商业用途免费。需要完整功能时，可以查看 [JetBrains 学生计划](https://www.jetbrains.com/student/)；是否符合资格以官网当前规则为准。

第一次使用时，打开对应 IDE，创建一个项目，选择正确的 JDK、Python 解释器或工具链，然后点击右上角的运行按钮即可。遇到配置问题，优先查看 IDE 底部的终端和报错信息。
