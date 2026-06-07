# WSL (Windows Subsystem for Linux) 完整操作指南

> 2026-06-07

## 一、 什么是 WSL？

WSL 的全称是 **Windows Subsystem for Linux**（适用于 Linux 的 Windows 子系统）。
它是一项微软提供的功能，让你能够在 Windows 系统上直接运行原生的 Linux 环境，无需安装双系统或笨重的传统虚拟机。

**核心优势：**

* **轻量且启动极快：** 几秒钟启动一个 Linux 终端。
* **资源占用低：** 动态分配内存。
* **无缝集成：** Windows 与 Linux 文件系统双向打通互访。
* **WSL 2 架构：** 内置真实的 Linux 内核，支持 Docker 和 GPU 硬件加速。

---

## 二、 基础安装与初始化

### 1. 标准安装步骤
在 Windows PowerShell（管理员）中运行：
```bash
wsl --install
```

*此命令会自动启用虚拟化功能并默认安装 Ubuntu。完成后需重启电脑。*

### 2. 常见网络问题排查 (403 Forbidden 或极慢)

如果在安装过程中遇到 `已禁止(403)` 报错或下载极慢，通常是代理软件或网络环境导致的阻断。

**解决步骤：**

1. **中断下载：** 在终端中按 `Ctrl + C`。

2. **彻底关闭代理：** 退出所有网络加速器/代理软件，确保 Windows 系统代理为关闭状态。

3. **指定版本直连下载：**

   ```bash
   wsl.exe --install Ubuntu-26.04
   ```

### 3. 系统初始化

安装完成后，终端会自动弹出并进行本地展开。 你需要设置一个纯英文的 **UNIX 用户名** 和 **密码**（注意：输入密码时屏幕不会有任何显示，盲打回车即可）。

## 三、 突破网络限制：配置极速开发环境

### 1. 解决 Linux 终端内的下载龟速

WSL 内默认不会走 Windows 的代理，且官方源服务器较远。必须将软件源替换为国内镜像站（如阿里云）。

在 Ubuntu 终端中执行：

```bash
# 替换为阿里云镜像源
sudo sed -i 's/[archive.ubuntu.com/mirrors.aliyun.com/g](https://archive.ubuntu.com/mirrors.aliyun.com/g)' /etc/apt/sources.list.d/ubuntu.sources
sudo sed -i 's/[security.ubuntu.com/mirrors.aliyun.com/g](https://security.ubuntu.com/mirrors.aliyun.com/g)' /etc/apt/sources.list.d/ubuntu.sources

# 刷新软件列表
sudo apt update
```

### 2. 开启 WSL 镜像网络模式 (解决 localhost 代理冲突)

为了让 WSL 能完美共享 Windows 的局域网 IP 和代理配置：

1. 在 Windows 资源管理器打开 `%USERPROFILE%`（如 `C:\Users\用户名`）。

2. 新建名为 `.wslconfig` 的文件（注意前面有句号）。

3. 写入以下内容：

   ```Ini, TOML
   [wsl2]
   networkingMode=mirrored
   
   [experimental]
   autoProxy=true
   ```

4. 在 PowerShell 中强制重启 WSL：`wsl --shutdown`。

## 四、 打造 C/C++ 核心开发环境

### 1. 安装基础工具链

在 Ubuntu 终端中执行：

```bash
sudo apt update
sudo apt install build-essential gdb git -y
```

*(这会安装 gcc, g++, make 编译器及 Git 版本控制工具)*

### 2. 打通 VS Code (神仙体验)

**黄金法则：** 将项目代码存放在 Linux 原生主目录 `~` 下，性能最强。

1. 进入 Linux 主目录并创建项目文件夹：

   ```bash
   cd ~
   mkdir -p Projects/C
   cd Projects/C
   ```

2. 唤起 VS Code：

   ```bash
   code .
   ```

   *(VS Code 会自动在后台下载 Server 组件，实现 Windows 界面完美操控 Linux 底层)*

## 五、 C 语言工程化实践：编译、调试与构建

### 1. 基础单文件编译

- 编写 `hello.c`
- 终端编译：`gcc hello.c -o hello`
- 运行程序：`./hello` （注意必须带 `./` 表示当前目录）

### 2. VS Code 图形化断点调试

1. 在 VS Code 中安装微软官方的 **C/C++** 插件及 **Extension Pack**（必须安装在 WSL 侧）。
2. 在代码左侧行号处点击打上红点（断点）。
3. 按 **F5**，选择 `C++ (GDB/LLDB)` -> `gcc 生成和调试活动文件`。
4. 在左侧面板即可实时监控变量变化及内存分配。

### 3. 多文件自动化构建 (Makefile)

编写 `Makefile` 文件管理复杂工程：

```makefile
CC = gcc
CFLAGS = -Wall -g

app: main.o order.o
	$(CC) $(CFLAGS) -o app main.o order.o

main.o: main.c order.h
	$(CC) $(CFLAGS) -c main.c

order.o: order.c order.h
	$(CC) $(CFLAGS) -c order.c

clean:
	rm -f *.o app
```

- **注意：** `Makefile` 中的执行命令前必须是真实的 **Tab 键缩进**。
- **使用：** 终端输入 `make` 自动编译，输入 `make clean` 清理垃圾文件。

## 六、 Git 版本控制与推送到 GitHub

### 1. 本地仓库初始化

```bash
# 配置身份
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
git config --global init.defaultBranch main

# 初始化仓库
git init

# 配置忽略名单（绝对不要把编译产物存入 Git）
echo "*.o" > .gitignore
echo "app" >> .gitignore
```

### 2. 提交代码

```bash
git add .
git commit -m "init: 首次提交，完成基础架构搭建"
```

### 3. 推送到远程 GitHub

**注意坑点：** 密码处绝对不能填网页登录密码，必须填写 **Personal Access Token (PAT)**。

```bash
# 关联远程仓库并推送
git push -u origin main
```

*在提示输入 Username 时填邮箱，Password 处粘贴你的 `ghp_` 开头的 Token。*

### 4. 记住凭证（一劳永逸）

推送成功后，输入以下命令让系统记住 Token，以后即可实现一键无感推送：

```bash
git config --global credential.helper store
```

## 附录：日常生存必备命令

- `wsl`：在 Windows 中进入 Linux 终端。
- `wsl --shutdown`：在 Windows 中彻底关闭并重启 WSL 后台。
- `exit`：退出当前 Linux 终端。
- `explorer.exe .`：在 Linux 中快速唤起 Windows 资源管理器查看当前目录文件。
- `pwd`：打印当前所在绝对路径。
- `cd ~`：一键返回 Linux 用户主目录。