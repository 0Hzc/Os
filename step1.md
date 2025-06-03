# 实践从0实现linux
根据指导，在ubuntu20.04环境下，进行开发
## 1. 配置环境
### 1.1 安装必要的软件包
```bash
# 更新软件包列表
sudo apt update
# 安装基本开发工具
sudo apt install build-essential
# 安装编译器、汇编器和调试工具
sudo apt install gcc nasm make gdb
# 安装QEMU模拟器
sudo apt install qemu-system-x86
# 安装其他有用的工具
sudo apt install git vim
```
安装所需的软件包后，就可以开始编写和运行Linux内核了。

安装完所需软件包，构建整个项目的架构：

```plaintest
/home/ubuntu/myos/         # 项目根目录
├── Makefile              # 在这里创建Makefile
├── link.ld               # 链接脚本也放在这里
├── src/                  # 源代码目录
│   ├── boot/             # 引导加载程序
│   ├── kernel/           # 内核代码
│   ├── drivers/          # 设备驱动
│   ├── fs/               # 文件系统
│   └── include/          # 头文件
└── build/                # 编译输出目录
```

### 1.2 创建项目目录结构
```bash
# 创建项目主目录
mkdir -p ~/myos
cd ~/myos

# 创建子目录
mkdir -p src/boot    # 引导加载程序代码
mkdir -p src/kernel  # 内核代码
mkdir -p src/drivers # 设备驱动
mkdir -p src/fs      # 文件系统
mkdir -p src/include # 头文件
mkdir -p build    
```

### 1.3 创建基本的构建系统
构建系统能自动化编译、链接和测试过程，提高开发效率。

