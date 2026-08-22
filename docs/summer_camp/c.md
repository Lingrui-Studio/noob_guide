---
icon: lucide/code
---

# C 语言编程入门

C 语言是各大高校计算机专业默认的「新生第一门编程语言」，因为它语法比较简单，又能让你了解到变量怎么占内存、函数怎么被调用、程序怎么跟操作系统打交道。后面的数据结构、操作系统、编译原理等课程也都基于此。

我们学校也不例外：软件工程专业大一上先过 C 的基本语法，大一下用 C 写各种数据结构和算法。

??? info "C 语言在编程世界里的地位"

    C 语言在编程世界中拥有**“基石”、“母语”和“永恒经典”**般的崇高地位。尽管它诞生于 1972 年（已有 50 多年历史），但它从未过时，反而随着计算机体系结构的发展，其核心价值愈发凸显。

    如果用一句话概括：**C 语言是现代软件文明的底座，是连接人类逻辑与机器硬件的最短桥梁。**

    以下从五个维度解析 C 语言的不可替代性：

    **1. 系统级开发的“绝对统治者”**
    
    C 语言是构建数字世界的钢筋混凝土。几乎所有关键基础设施都是用 C 写的：

    - **操作系统内核：** Linux, Windows, macOS, Android, iOS 的内核核心部分均为 C 语言。
    - **数据库引擎：** MySQL, PostgreSQL, SQLite, Redis 等高性能存储引擎。
    - **网络协议栈：** TCP/IP 实现、Nginx、Apache 等服务器软件。
    - **嵌入式与物联网：** 从航天飞机、汽车 ECU 到智能手表、微波炉，C 是硬件交互的首选。

    > 💡 **核心原因：** C 语言提供了对内存的直接操控能力和极低的运行时开销，这是 Java、Python 等高级语言无法比拟的。在需要“榨干硬件性能”的场景下，C 是唯一解。

    **2. 编程语言的“元语言” (Meta-Language)**

    C 语言定义了现代编程的语法范式和底层模型：
    
    - **语法祖先：** C++, Java, C#, JavaScript, Go, Rust, Swift 等主流语言的语法都深受 C 影响。学会了 C，学习这些语言的语法成本极低。
    - **ABI 标准：** C 的调用约定和二进制接口是跨语言互操作的通用标准。Python 调 C++ 库、Rust 调系统 API，本质上都是通过 **C FFI** 完成的。C 是不同语言之间沟通的“世界语”。
    - **编译器自举：** GCC, Clang/LLVM 等编译器本身主要由 C/C++ 编写。

    **3. 性能与控制的“黄金标杆”**

    在性能敏感的领域，C 语言依然是衡量标准：

    - **零抽象成本：** 没有垃圾回收、没有虚函数表、没有隐式分配。你写什么代码，机器就执行什么指令。
    - **可预测性：** 在实时系统中，开发者必须精确知道每一行代码消耗多少时钟周期，只有 C 能提供这种确定性。
    - **基准测试参照系：** 当人们评价一门新语言“快不快”时，通常是以 C 的性能作为 100% 的参照线。

    **4. 教育领域的“内功心法”**

    虽然很多大学入门课转向了 Python，但 C 语言在计算机科学教育中的地位依然不可动摇：

    - **理解计算机本质：** 学 C 不仅仅是学语法，更是学**指针、内存布局、栈帧、缓存局部性、链接过程**。这些是理解计算机如何工作的必修课。
    - **培养严谨思维：** C 语言不会帮你兜底。段错误、内存泄漏、未定义行为迫使程序员养成严谨、负责的工程习惯。
    - **区分“码农”与“工程师”：** 掌握 C 语言往往被视为具备扎实计算机基础的标志。

    **5. 现状与挑战：老当益壮，但有继任者**
    
    C 语言并非完美无缺，它的地位也在发生微妙的演变：

    | 维度 | C 的现状 | 趋势与挑战 |
    | :--- | :--- | :--- |
    | **安全性** | 内存安全问题是 C 最大的阿喀琉斯之踵（缓冲区溢出、UAF 等） | **Rust** 正在系统编程领域逐步替代 C，提供同等性能+内存安全 |
    | **开发效率** | 手动管理内存繁琐，缺乏现代抽象 | 在应用层已被 Go/C++/Java 取代，但在底层依然稳固 |
    | **标准化** | C11/C17/C23 持续更新，增加原子操作、泛型等现代特性 | 演进保守，向后兼容性是其护城河也是枷锁 |
    | **生态** | 极其成熟稳定，几乎所有平台都有 C 编译器 | 新兴领域（AI、Web）不再是 C 的主场 |

    **📌 总结**

    C 语言在编程世界的地位可以类比为 **“拉丁语之于欧洲语言”** 或 **“地基之于摩天大楼”**：

    - 你可能在日常业务开发中不再直接写 C；
    - 但你使用的每一个工具、运行的每一行代码、依赖的每一个库，背后都有 C 的影子；
    - 它是**性能的天花板、安全的地板、以及所有程序员理解机器的起点**。

    只要计算机还需要直接与硬件对话，只要人类还需要极致地控制机器，C 语言就永远不会消亡。它已经从“唯一的语言”进化为“基础设施级的语言”，这是一种更深层、更永恒的地位。

## C 语言开发环境

说实在的，在 VS Code 里从零配 C 环境对新生来说绝对是个噩梦。所以我把原本一大篇配置指南删了，并自己做了一个 [C 语言项目模板](https://github.com/Lingrui-Studio/ctemplate)。你只需要：

- `git clone` 该仓库到本地 WSL Ubuntu 中
- 用 VS Code 连接 WSL 并打开该项目
- 安装 VS Code 右下角弹出的推荐插件
- 按仓库 `readme.md` 里的指引装系统依赖

就可以愉快的 coding 啦~

仓库中的各种配置文件还附带了非常详细的中文注释，如果你还有不清楚的，可以询问 AI。

## C 语言学习资源

学习编程最重要的就是一定要自己上手实操，熟能生巧，切忌只看不练！以下是一些广受好评的 C 语言学习资源：

- [C 语言教程 | 菜鸟教程](https://www.runoob.com/cprogramming/c-tutorial.html)
- [浙江大学翁恺：C 语言程序设计](https://www.bilibili.com/video/BV1dr4y1n7vA/)

如果你喜欢看书，那么也有推荐的：

- 《C 程序设计语言》（第 2 版），作者 Kernighan & Ritchie
- 《C Primer Plus》（第 6 版）中文版，作者 斯蒂芬·普拉达

也可以先把下面这一节跟一遍，再回头用教程补全语法表。

## C 语言基础

每一步只加一点点，加完就能再跑一次。示例都是自己带 `main` 的单文件，放到上面模板项目的 `examples/` 里跑，**不要**丢进 `src/`（那里已经有一个 `main` 了）。

### 1. 最小可运行程序

新建 `examples/01_min.c`：

```c title="examples/01_min.c"
int main(void) {
    return 0;
}
```

跑完终端里几乎什么都没有。正常：程序没往屏幕写字，只是正常结束了。

- **`main`**：操作系统从这里开始执行你的程序。一个进程里只能有一个 `main`。
- **`(void)`**：这个 `main` 不接收命令行参数。带参数的写法放到最后一节。
- **`return 0`**：退出码。`0` 表示正常结束，非 `0` 通常表示出错。终端里用 `echo $?` 能看到刚才那个程序的退出码。

### 2. `printf` 和头文件

```c title="examples/02_hello.c"
#include <stdio.h>

int main(void) {
    printf("hello, 凌睿\n");
    return 0;
}
```

运行后应看到一行 `hello, 凌睿`。

- **`printf`** 不是关键字，是标准库函数，按格式往标准输出（默认是终端）写字符。
- **`\n`** 是换行。没有它，下一行提示符可能会粘在这行后面。
- **`#include <stdio.h>`** 把「标准输入输出」相关函数的**声明**引进来。编译器先要知道 `printf` 长什么样，链接时再去标准库里找实现。

对照实验：把 `#include` 删掉再编译，报错一般会说 `printf` 没声明。

| 写法 | 去哪找 | 例子 |
| --- | --- | --- |
| `#include <stdio.h>` | 编译器的系统头文件目录 | 标准库 |
| `#include "printer.h"` | 工程自己的 `include/`（模板已配好） | 你写的模块 |

模板里的 `include/printer.h` 就是第二种：头文件只写函数长什么样，实现放在对应的 `.c` 里。

`gcc` 一条命令背后大致是：预处理（展开 `#include`）→ 编译 → 链接。报「没声明」多半是头文件；报 `undefined reference` 多半是链接时没找到实现。

### 3. 变量和数据类型

要存一个值，先声明变量：写出类型、名字，需要的话再赋初值。

```c title="examples/03_vars.c"
#include <stdio.h>

int main(void) {
    int year = 2026;
    char grade = 'A';
    double pi = 3.14159;

    printf("year = %d\n", year);
    printf("grade = %c\n", grade);
    printf("pi = %f\n", pi);
    printf("int 占 %zu 字节\n", sizeof(year));
    return 0;
}
```

先记住这三种就够：

| 类型 | 放什么 | `printf` 占位符 |
| --- | --- | --- |
| `int` | 整数 | `%d` |
| `char` | 一个字符（本质也是整数） | `%c` |
| `double` | 小数 | `%f` |

占位符必须和后面的参数对上，对不上轻则打印乱，重则程序直接崩。`sizeof` 给出这个变量占几个字节；常见机器上 `int` 是 4，**别把它当定理**，以你机器上跑出来的为准。

`char` 用单引号 `'A'`，字符串用双引号 `"hello"`。字符串先当 `printf` 的现成参数用，后面第 8 节再拆开看。

改一改再跑：把 `year` 改成你的入学年；占位符故意写成 `%f`，看一眼会乱成什么样。

### 4. 从键盘读入

`scanf` 按格式从标准输入读：

```c title="examples/04_scanf.c"
#include <stdio.h>

int main(void) {
    int n;

    printf("输入一个整数：");
    if (scanf("%d", &n) != 1) {
        printf("没读到整数\n");
        return 1;
    }

    printf("你输入的是 %d，它的两倍是 %d\n", n, n * 2);
    return 0;
}
```

- **`&n`**：`scanf` 要改 `n` 的值，所以要的是 `n` 的地址。`&` 是取地址。第 9 节讲指针时会回到这里。
- **检查返回值**：`scanf` 返回成功读入了几项。输入 `abc` 时读失败，`n` 里是未初始化的垃圾值，拿去算没有意义。失败就 `return 1`，和退出码对上。

运行后点一下终端，输入数字再回车。程序在等输入时看起来像卡住，敲一个整数并回车。

### 5. 分支：`if` / `else`

```c title="examples/05_if.c"
#include <stdio.h>

int main(void) {
    int score;

    printf("输入分数：");
    if (scanf("%d", &score) != 1) {
        printf("输入无效\n");
        return 1;
    }

    if (score >= 60) {
        printf("及格\n");
    } else {
        printf("不及格\n");
    }
    return 0;
}
```

条件写在 `if (...)` 里，成立走后面的大括号，否则走 `else`。比较用 `>=`、`<=`、`==`、`!=`。**判断相等是 `==`，一个 `=` 是赋值**——`if (score = 60)` 能编过，但几乎一定是 bug。

多个档位用 `else if` 接下去：

```c title="examples/06_else_if.c"
#include <stdio.h>

int main(void) {
    int score;

    printf("输入分数：");
    if (scanf("%d", &score) != 1) {
        printf("输入无效\n");
        return 1;
    }

    if (score < 0 || score > 100) {
        printf("分数应在 0 到 100\n");
        return 1;
    } else if (score >= 90) {
        printf("优秀\n");
    } else if (score >= 60) {
        printf("及格\n");
    } else {
        printf("不及格\n");
    }
    return 0;
}
```

`||` 是「或者」，`&&` 是「并且」。

### 6. 循环：`while` / `for`

分支解决「走哪条路」，循环解决「做几遍」。下面把 1 加到你输入的 `n`：

```c title="examples/07_while.c"
#include <stdio.h>

int main(void) {
    int n;
    int i = 1;
    int sum = 0;

    printf("输入 n：");
    if (scanf("%d", &n) != 1 || n < 1) {
        printf("请输入正整数\n");
        return 1;
    }

    while (i <= n) {
        sum = sum + i;
        i = i + 1;
    }

    printf("1 到 %d 的和是 %d\n", n, sum);
    return 0;
}
```

`while （条件）`：条件成立就执行大括号，然后回来再判断。`i` 每次必须有变化，忘了写就会死循环。怀疑死循环时在终端中按 ++ctrl+c++ 停掉，再看循环变量是不是没在变。

作业里更常见的是 `for`，和上面的 `while` 是同一件事：

```c
for (int i = 1; i <= n; i = i + 1) {
    sum = sum + i;
}
```

三个表达式分别是：进循环前做一次、每次进入前检查、每圈结束时做一次。

### 7. 数组

一组**同类型**的值排在一起，用下标访问。下标从 `0` 开始。

```c title="examples/08_array.c"
#include <stdio.h>

int main(void) {
    int a[5] = {10, 20, 30, 40, 50};
    int n = (int)(sizeof(a) / sizeof(a[0]));
    int sum = 0;

    for (int i = 0; i < n; i = i + 1) {
        printf("a[%d] = %d\n", i, a[i]);
        sum = sum + a[i];
    }
    printf("和是 %d\n", sum);
    return 0;
}
```

- `int a[5]`：5 个 `int` 连在一起。`a[0]` 是第一个，`a[4]` 是最后一个。
- `sizeof(a) / sizeof(a[0])`：整段内存除以单个元素的大小，得到元素个数。只对「还看得见整段数组」的变量成立，传进函数之后这招会失效（下一节指针会碰到）。
- **不要写 `a[5]`**。合法下标是 `0`～`4`。C 不管越界，写出去是未定义行为，可能当时没事、下次运行就不一定了。

`char s[16]` 也是数组，只是元素类型是 `char`。字符串就是在这个基础上约定多存一个结束符。

### 8. 字符串

C **没有**单独的 `string` 类型。字符串是一段 `char` 数组，最后一个有效字符后面跟一个 `'\0'`（值为 0），表示到这儿结束。

```c title="examples/09_str.c"
#include <stdio.h>
#include <string.h>

int main(void) {
    char word[] = "hi";

    printf("内容：%s\n", word);
    printf("数组长度（含结束符）%zu\n", sizeof(word));
    printf("strlen 不计结束符，所以是 %zu\n", strlen(word));
    return 0;
}
```

`word` 在内存里是 `'h'`、`'i'`、`'\0'`，所以 `sizeof(word)` 是 3。`%s` 从第一个字符打到 `'\0'` 为止。

自己声明数组时，长度要够装下字符**再加结束符**：

```c title="examples/10_scanf_str.c"
#include <stdio.h>
#include <string.h>

int main(void) {
    char name[16];

    printf("输入名字（不要有空格）：");
    if (scanf("%15s", name) != 1) {
        printf("没读到\n");
        return 1;
    }

    printf("你好，%s，名字长度 %zu\n", name, strlen(name));
    return 0;
}
```

- `%15s` 最多读 15 个字符。`name` 长度是 16，最后一格留给 `'\0'`。写成 `%s` 也能跑，输入太长会写出数组外面。
- `%s` 读到空格或换行就停。

比较两个字符串不要写 `==`。`==` 比的是「是不是同一块内存」，不是内容相不相等。用 `strcmp`：

```c title="examples/11_strcmp.c"
#include <stdio.h>
#include <string.h>

int main(void) {
    char a[16];
    char b[16];

    printf("输入两个单词：");
    if (scanf("%15s%15s", a, b) != 2) {
        printf("没读够\n");
        return 1;
    }

    if (strcmp(a, b) == 0) {
        printf("这两个一样\n");
    } else {
        printf("这两个不一样\n");
    }
    return 0;
}
```

`strcmp` 返回 `0` 表示相同。`<string.h>` 里常用的还有 `strlen`、`strcpy` / `strncpy`。拷贝前先确认目标数组够大。

### 9. 指针

指针是一种变量，里面存的是**另一个变量的地址**。

第 4 节的 `&n` 已经用过取地址。把这个地址存起来，再用 `*` 顺着地址读写，就是指针：

```c title="examples/12_ptr.c"
#include <stdio.h>

int main(void) {
    int n = 10;
    int *p = &n;

    printf("n 的值 %d，地址 %p\n", n, (void *)&n);
    printf("p 里存的地址 %p，顺着它读到 %d\n", (void *)p, *p);

    *p = 20;
    printf("改完之后 n = %d\n", n);
    return 0;
}
```

- `int *p`：`p` 指向一个 `int`。
- `p = &n`：把 `n` 的地址放进 `p`。
- `*p`：顺着 `p` 里的地址，读或写那个 `int`。所以上面改 `*p`，`n` 也会变——它们是同一块内存。

`scanf("%d", &n)` 就是这个机制：把 `n` 的地址交给 `scanf`，让它往那儿写。

数组名在大多数表达式里会变成「首元素的地址」，所以指针也能用来走数组：

```c title="examples/13_ptr_array.c"
#include <stdio.h>

int main(void) {
    int a[4] = {1, 2, 3, 4};
    int *p = a; /* 等价于 &a[0] */

    printf("p[2] = %d，*(p + 2) = %d\n", p[2], *(p + 2));
    return 0;
}
```

`p[i]` 和 `*(p + i)` 是同一件事。`p + 1` 不是地址加 1 个字节，而是加 **1 个 `int` 的大小**。

现在可以回头看第 7 节那句「数组传进函数后 `sizeof` 会失效」：函数参数写成 `int *p` 或 `int p[]` 时，函数里看到的只是一个指针，不再知道原来有几个元素。所以长度要另外传进去。

指针用错的典型结果是段错误（访问了不该访问的地址）。现在先保证：指针先指向一个真实存在的变量或数组元素，再解引用；不要解引用未初始化的指针。`malloc` 自己向系统要内存，是后话，课上会单独讲。

### 10. `main` 的参数

`int main(void)` 不接收命令行参数。操作系统可以把你在终端里空格分开的那些词递进来：

```c title="examples/14_args.c"
#include <stdio.h>

int main(int argc, char *argv[]) {
    printf("一共 %d 个参数\n", argc);
    for (int i = 0; i < argc; i = i + 1) {
        printf("argv[%d] = %s\n", i, argv[i]);
    }
    return 0;
}
```

看到这里，这只是「指针数组 + 字符串」：

- **`argc`**：参数个数，至少是 1。
- **`argv`**：`char *` 的数组。`argv[i]` 指向第 `i` 个字符串。
- **`argv[0]`** 通常是启动方式，比如 `./examples/14_args`。你敲的第一个参数从 `argv[1]` 开始。

用终端传参（Code Runner 的 ▶ 不太方便带参数）：

```bash
gcc -std=c11 -g -Wall examples/14_args.c -o examples/14_args
./examples/14_args hello 2026
```

应看到 3 行：路径、`hello`、`2026`。`2026` 此时仍是字符串，要拿去算得先转成 `int`（`sscanf` / `atoi`），作业里再细究即可。

`scanf` 是程序跑起来之后从键盘读；`argv` 是启动时就带上的。`ls -l`、`gcc -o a.out foo.c` 都是同一套机制。

### 11. 练习

按顺序做，卡了就回头对一下对应小节：

1. 改 `02_hello.c`，打印你的名字和今天的日期。
2. 读两个整数，打印较大的那个（只用 `if` / `else`）。
3. 读一个整数，判断它是正、负，还是零。
4. 读 `n`，打印 `n!`。`n` 稍大时 `int` 会溢出，先拿 `n = 10` 对一下是不是 `3628800`。
5. 读 `n`，再读 `n` 个整数放进数组，打印最大值。
6. 读一个单词，用 `strlen` 打印长度。
7. 写一个函数 `void add1(int *p)`，把指针指向的那个 `int` 加 1；在 `main` 里验证。
8. 用 `argv` 接收两个单词，判断是否相同。参数不够就打印用法并 `return 1`。

做到这儿，课内最前面那一截——类型、输入输出、分支循环、数组、字符串、指针、命令行参数——你就有个基本的了解了！

下一步，请前往 [clings-lingrui-recruit
](https://github.com/Lingrui-Studio/clings-lingrui-recruit) 继续完成 C 语言进阶！
