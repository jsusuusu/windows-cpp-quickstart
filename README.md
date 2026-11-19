# Windows C++ 入门

这份指南记录如何在 Windows 上从 VS Code 的终端编译并运行第一个 C++ 程序。使用 MSYS2 的 UCRT64 版本，让编译器和调试器来自同一套工具链。

## 安装与检查

1. 安装 VS Code 和 Microsoft 的 C/C++ 扩展。
2. 安装 MSYS2，打开 **MSYS2 UCRT64** 终端，运行 `pacman -S --needed mingw-w64-ucrt-x86_64-toolchain`。
3. 把 UCRT64 的 `bin` 目录加入 Windows 用户 `Path`。按默认位置安装时，该目录是 `C:\msys64\ucrt64\bin`。彻底退出并重新启动 VS Code。
4. 在 VS Code 的新终端运行 `g++ --version` 和 `gdb --version`。如果出现多套编译器，用 `where.exe g++` 和 `where.exe gdb` 看实际命中哪个目录。

安装过程可对照 [VS Code 的 MinGW-w64 配置指南](https://code.visualstudio.com/docs/cpp/config-mingw)。

## 编译第一道练习

新建 `main.cpp`。下面的程序读取一个小整数，并输出它的两倍。

```cpp
#include <iostream>

int main() {
    int value = 0;
    if (!(std::cin >> value) || value < -10000 || value > 10000) {
        return 1;
    }

    std::cout << value * 2 << '\n';
    return 0;
}
```

在保存代码的文件夹打开 VS Code 的 PowerShell 终端，运行：

```powershell
g++ -std=c++17 -Wall -Wextra -g main.cpp -o main.exe
.\main.exe
```

输入 `7` 并回车，正常时输出 `14`。如果程序还在等待输入，按 `Ctrl+C` 结束后再重新编译。

## 爱发电创作者认证

我已在爱发电开设「Windows 编程工具箱」主页，分享面向初学者的 Windows 编程练习模板和开发小工具。本 GitHub 仓库用于公开 C++ 入门指南，并作为爱发电创作者认证的来源页面。

[Windows 编程工具箱｜爱发电](https://ifdian.net/a/wincppworkbench)
