---
title: cmake简单理解
tags:
  - C++
categories:
  - 学习记录
  - CMake
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 55690
date: 2025-02-24 22:04:08
updated: 2025-02-24 22:04:08
description:
cover:
banner:
sticky:
mermaid:
katex:
mathjax:
topic:
author:
references:
comments:
indexing:
breadcrumb:
leftbar:
rightbar:
h1:
type:
---





### 简介

CMake 是一个开源的跨平台构建系统生成工具，旨在简化和自动化项目的构建过程。它主要用于管理和控制软件构建的过程，特别是在处理复杂的项目结构和多个平台时。CMake 并不直接进行编译或链接，而是生成本地构建系统所需的文件（如 Makefile、Visual Studio 项目文件、Xcode 工程文件等），然后由这些工具进行实际的构建。

### 特点

1. **跨平台支持**： CMake 支持多种操作系统和编译器，包括 Windows、Linux、macOS、Android、iOS 等。它可以生成适应不同平台的构建文件，如 Makefile、Visual Studio、Xcode 工程文件等。
2. **生成构建系统文件**： CMake 通过读取 `CMakeLists.txt` 配置文件，生成适合目标平台的构建系统文件。这些文件可以是：
   * **Makefile**：用于 Linux 或类 Unix 系统上的构建。
   * **Visual Studio 项目文件**：用于 Windows 上的 Visual Studio 环境。
   * **Xcode 工程文件**：用于 macOS 上的 Xcode 工具链。
3. **易于管理复杂项目**： CMake 允许你将项目分解为多个子模块（subdirectories），每个子模块都可以有自己的 `CMakeLists.txt` 文件，从而使得管理大项目变得更加简单。例如，CMake 可以方便地处理项目中的静态库、动态库和可执行文件的构建。
4. **支持外部依赖管理**： CMake 通过 `find_package()` 来查找和配置项目所依赖的外部库和工具。例如，可以查找 Qt、OpenGL、Boost 等库，并自动配置其路径。
5. **支持多种编译选项**： CMake 允许设置编译器标志、优化级别、编译标准等，可以方便地支持 Debug 和 Release 模式的切换。
6. **简化配置和构建**： CMake 使得配置和构建流程简化为几条命令，避免了手动修改和维护平台特定的构建脚本。

### 基本概念

1. **CMakeLists.txt**： CMake 项目中的核心文件是 `CMakeLists.txt`。它用于定义构建系统的规则，包括项目的源文件、依赖库、编译选项、构建目标等。一个 CMake 项目通常会有多个 `CMakeLists.txt` 文件，每个子目录都有一个 `CMakeLists.txt` 文件。

2. **项目结构**： CMake 项目的结构通常包含：

   * `CMakeLists.txt`：用于配置项目的根目录文件。
   * `src/`：源代码文件夹。
   * `build/`：用于存放构建过程中生成的文件。
   * `include/`：头文件目录。
   * `lib/`：库文件目录。

   示例结构：

   ```
   project/
   ├── CMakeLists.txt
   ├── src/
   │   ├── main.cpp
   │   └── other.cpp
   ├── include/
   │   └── header.h
   └── lib/
       └── library.a
   ```

3. **CMake 语法**： CMake 使用一组简单的命令和语法，常见的命令包括：

   * `cmake_minimum_required(VERSION 3.16)`：设置 CMake 的最低版本要求。
   * `project(MyProject)`：定义项目的名称。
   * `add_executable(MyExecutable main.cpp)`：定义一个可执行文件。
   * `target_link_libraries(MyExecutable MyLibrary)`：链接库。
   * `find_package(Qt5 REQUIRED)`：查找外部库（如 Qt）。
   * `include_directories(path)`：指定头文件路径。
   * `set(VAR value)`：定义变量。
   * `add_subdirectory(path)`：处理子目录的 CMakeLists.txt 文件。

### 实际例子：

```cpp
project/
├── CMakeLists.txt  # 根目录
├── card/
│   └── CMakeLists.txt  # card 子模块
└── player/
    └── CMakeLists.txt  # player 子模块
```

当前有一个包含多个模块（`card`、`windows` 等）和依赖项（如 Qt）的项目，以下是从头到尾的构建流程：

1. **CMake 配置阶段**：
   * CMake 会扫描根目录的 `CMakeLists.txt` 文件，处理项目设置。
   * CMake 会依次处理每个子模块的 `CMakeLists.txt` 文件。
   * 例如，在 `card` 子目录下，CMake 会生成一个名为 `card` 的静态库，链接 Qt 核心库。
   * 根目录会通过 `target_link_libraries()` 连接各个模块，例如将 `card` 和其他模块（如 `windows`）链接到主程序 `client`。
2. **编译阶段**：
   * 运行 `make` 或 `cmake --build .` 命令，编译器会将源文件编译成目标文件。
   * 每个 `.cpp` 文件都会生成一个 `.o` 或 `.obj` 文件。
3. **链接阶段**：
   * 链接器将目标文件和静态库/动态库链接成最终的可执行文件。
   * 如果 `card` 是静态库，链接器会将 `card` 库的代码和目标文件合并。
   * 如果依赖了动态库（如 Qt），链接器会将动态库的路径信息嵌入可执行文件。
4. **生成可执行文件**：
   * 最终的 `client` 可执行文件会被生成。
5. **安装阶段**：
   * 可执行文件和库文件（如果有的话）会被安装到指定的目录，准备部署和使用。
