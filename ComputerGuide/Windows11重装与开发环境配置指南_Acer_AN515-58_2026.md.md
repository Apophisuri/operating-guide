# Windows11重装与开发环境配置指南（Acer AN515-58）

更新时间：2026-05

---

# 一、电脑配置

设备型号：

- Acer Nitro AN515-58（宏碁暗影骑士）

硬件配置：

- CPU：Intel Core i5-12500H
- GPU：NVIDIA GeForce RTX 3050 Ti Laptop GPU
- 内存：16GB DDR4
- 硬盘：512GB NVMe SSD（Micron 3400）
- 屏幕：1920×1080 165Hz

用途：

- 软件工程学习
- 408考研
- Java开发
- Python开发
- Docker
- WSL2
- VS Code
- IntelliJ IDEA

---

# 二、推荐系统版本

## 最终推荐

### Windows 11 家庭中文版 23H2 官方原版

原因：

- 与原厂授权完全匹配
- 重装后自动激活
- 稳定性优秀
- 驱动兼容性成熟
- 满足全部开发需求

适合：

- VS Code
- IDEA
- Python
- Java
- Docker
- WSL2
- Git

---

## 关于24H2

优点：

- 大小核调度优化
- Windows Sudo
- 原生支持7z
- WiFi 7支持
- AI底层能力增强

缺点：

- 相比23H2兼容性风险略高
- 对当前开发学习场景收益有限

---

## 关于25H2

本质：

```text
24H2 + Enablement Package
```

新增功能主要集中在：

- AI
- 搜索
- 开始菜单

对于当前硬件收益不明显。

---

## 推荐排序

| 版本                 | 推荐度 |
| -------------------- | ------ |
| Windows 11 23H2 Home | ★★★★★  |
| Windows 11 24H2 Home | ★★★★☆  |
| Windows 11 25H2 Home | ★★★☆☆  |

---

# 三、系统下载

微软官方下载：

https://www.microsoft.com/software-download/windows11

推荐：

- Windows 11 Home Chinese
- 官方原版 ISO

---

# 四、启动盘制作

工具：

- Rufus

官网：

https://rufus.ie

推荐设置：

```text
分区方案：GPT

目标系统：
UEFI（非CSM）

文件系统：
NTFS

簇大小：
默认
```

---

# 五、Rufus 与 微PE区别

## Rufus

作用：

```text
ISO
↓
制作启动盘
↓
安装系统
```

特点：

- 官方系统安装首选
- 简单
- 干净

---

## 微PE

作用：

```text
进入PE环境
↓
维护系统
↓
分区
↓
数据恢复
```

特点：

- 适合修复系统
- 适合数据抢救
- 非微软官方

---

## 当前推荐

```text
官方ISO
+
Rufus
```

即可。

无需微PE。

---

# 六、Secure Boot Fail解决方案

现象：

```text
插入U盘
↓
开机
↓
Security Boot Fail
```

原因：

```text
Secure Boot
+
启动盘验证失败
```

解决：

进入BIOS：

```text
F2
```

找到：

```text
Secure Boot
```

修改：

```text
Enabled
↓
Disabled
```

保存：

```text
F10
```

问题已解决。

---

# 七、磁盘规划方案

512GB SSD推荐：

## 分区

```text
EFI
MSR
Recovery
（系统自动创建）

C盘 220GB

D盘 剩余全部
```

不要再分：

```text
E盘
F盘
```

---

## 推荐目录结构

### D:\Study

```text
D:\Study
├─ 408
├─ 数学
├─ 英语
├─ 政治
└─ 中科大
```

---

### D:\Code

```text
D:\Code
├─ Java
├─ Python
├─ Cpp
├─ Algorithm
└─ Practice
```

---

### D:\Projects

```text
D:\Projects
├─ Personal
├─ School
└─ OpenSource
```

---

### D:\Notes

```text
D:\Notes
├─ Obsidian
└─ Markdown
```

---

### D:\Books

```text
D:\Books
├─ CS
├─ Java
├─ Python
└─ Algorithm
```

---

### D:\Backup

```text
D:\Backup
├─ SSH
├─ GitConfig
├─ Drivers
└─ System
```

---

# 八、重装前备份清单

## A级（必须）

### 用户数据

```text
Desktop
Downloads
Documents
Pictures
Videos
```

---

### 微信

备份：

- 聊天记录
- 文件

---

### 浏览器

备份：

- 书签
- 密码
- 插件配置

---

### SSH

路径：

```text
C:\Users\Apophisuri\.ssh
```

---

### Git配置

路径：

```text
C:\Users\Apophisuri\.gitconfig
```

---

## B级（开发）

### VS Code

建议：

开启 Settings Sync

---

### IDEA

导出配置：

```text
File
→ Manage IDE Settings
→ Export Settings
```

---

### WSL

检查：

```powershell
wsl -l -v
```

---

### Docker

检查：

- 容器
- 数据卷

---

## C级（学习）

### Obsidian

备份整个Vault

---

### PDF资料

```text
408
数学
英语
政治
专业课
```

---

# 九、SSH恢复记录

恢复后检查：

```powershell
dir $HOME\.ssh
```

结果：

```text
.ssh
├─ agent
├─ config
├─ gitee_id_ed25519
├─ gitee_id_ed25519.pub
├─ gitee_id_rsa
├─ gitee_id_rsa.pub
├─ id_ed25519
├─ id_ed25519.pub
├─ id_rsa
├─ id_rsa.pub
└─ known_hosts
```

---

# 十、Git配置恢复

检查：

```powershell
dir $HOME\.gitconfig
```

结果：

```text
C:\Users\Apophisuri\.gitconfig
```

恢复成功。

---

# 十一、SSH认证验证

GitHub：

```powershell
ssh -T git@github.com
```

输出：

```text
Hi Apophisuri!
You've successfully authenticated
```

成功。

---

Gitee：

```powershell
ssh -T git@gitee.com
```

输出：

```text
Hi Apophisuri(@apophisuri)!
You've successfully authenticated
```

成功。

---

# 十二、当前开发环境状态

## 已恢复

- Git
- GitHub SSH
- Gitee SSH
- .ssh
- .gitconfig

---

## 推荐安装软件

### 基础工具

- Chrome
- 7-Zip
- Everything
- PowerToys

---

### 开发工具

- Git
- VS Code
- JDK 21
- Python
- Node.js LTS
- Maven

---

### 后续开发

- WSL2
- Docker Desktop

---

### 学习工具

- Obsidian
- Typora
- SumatraPDF

---

# 十三、最终结论

当前最优方案：

```text
Windows 11 Home Chinese 23H2
+
UEFI
+
GPT
+
16GB RAM
+
512GB SSD
+
VS Code
+
Git
+
Python
+
JDK 21
+
WSL2
+
Docker
+
Obsidian
```

系统状态：

- Windows重装成功
- Secure Boot问题已解决
- Git恢复成功
- GitHub SSH恢复成功
- Gitee SSH恢复成功
- 开发环境可继续配置

# 宏碁暗影骑士·擎（AN515-58）Win11重装找不到硬盘解决方案

在操作 Intel 第 12 代或更新平台的笔记本（如宏碁暗影骑士·擎，搭载 i5-12500H 处理器及美光 3400 固态硬盘）重装 Windows 11 时，经常会遇到**找不到本机磁盘、只显示 U 盘**的情况。

这是因为系统默认开启了 **VMD（卷管理设备）** 技术，而原生 Windows 11 镜像中缺少对应的 Intel RST 驱动。以下是完整的解决与科普指南。

##  核心解决方案：BIOS 关闭 VMD（最快最省事）

宏碁笔记本的 VMD 开关默认是隐藏的，需要使用组合键解锁。

1. **进入 BIOS：** 电脑彻底关机，开机在屏幕亮起前，**疯狂连续按下 `F2` 键**。
2. **解锁隐藏选项：** 进入 BIOS 后，通过键盘左右方向键切换到 **Main** 选项卡。在此界面下，按下键盘上的 **`Ctrl + S`** 组合键。
3. **关闭 VMD：** 此时页面下方会弹原本隐藏的选项。找到 **`VMD Controller`**（或 *Intel VMD Technology*），将其状态从 `Enabled`（开启）修改为 **`Disabled`（关闭）**。
4. **保存退出：** 按下键盘上的 **`F10`** 键，选择 `Yes` 保存并退出。
5. **认准硬盘分区：** 电脑重启进入 U 盘安装界面后，本机的 **美光 512GB 固态硬盘**（显示为约 476 GB 的未分配空间或分区）即可正常显现。

##  备用解决方案：手动加载 Intel RST 驱动

如果不想修改 BIOS 设置，可以选择在重装界面手动注入驱动。

## ⚠️ 重装时的分区注意事项

认准本机硬盘（约 476 GB）后，根据数据情况选择操作：

- **全盘格式化（纯净重装）：** 若重要数据已备份，可将本机磁盘下的**所有分区统统删除**，使其变为一块“未分配的空间”，直接点击“下一步”，让系统自动规划最佳引导分区。
- **仅格式化 C 盘（保留 D/E 盘）：** 根据容量大小认准原本的 C 盘（大约 221 GB 左右），选中它并点击 **“格式化”**，洗干净后选中该分区点击“下一步”安装。**切勿删除其他分区，否则 D 盘、E 盘数据会丢失。**

## 💡 科普：什么是 VMD？重装后需要重新开启吗？

### 1. 重装后需要重新开启吗？

**绝对不需要。** 系统重装完成后，请让 VMD 保持关闭（Disabled）状态。如果此时回到 BIOS 重新开启，刚装好的系统会因为缺少 VMD 驱动而直接触发 **蓝屏崩溃（INACCESSIBLE_BOOT_DEVICE）**。

### 2. VMD 的作用是什么？

VMD（Intel Volume Management Device）是 Intel 从第 11 代酷睿处理器开始引入的硬件级卷管理技术。它就像是固态硬盘的“高级大管家”：

- **热插拔（Hot Plug）：** 允许在不关机的情况下拔掉坏硬盘并插上新硬盘（主要用于企业级服务器和高端工作站）。
- **硬件级 RAID 管理：** 在插有多块固态硬盘时，方便组建磁盘阵列（如速度翻倍的 RAID 0 或镜像备份的 RAID 1）。
- **报错隔离：** 硬盘断电或报错时，将错误隔离在内部，防止 CPU 或系统直接蓝屏。

### 3. 关闭它对我的电脑有影响吗？

**对普通个人用户和游戏玩家而言：毫无影响。**

普通人既不会开机拆笔记本插拔固态硬盘，也很少去组建 NVMe RAID。关闭 VMD 后，固态硬盘会直接通过原生 NVMe 通道与系统和 CPU 对话，**硬盘的读写速度、游戏加载时间及日常流畅度不会受到任何降级影响**。