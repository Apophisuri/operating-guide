# macOS 高效使用与 U 盘跨平台指南

## 一、macOS 核心效率技巧

### 1. Spotlight 全局搜索

快捷键：

```text
Command + Space
```

用途：

- 打开 App
- 搜索文件
- 数学计算
- 单位换算
- 查找系统设置
- 网页搜索

示例：

```text
25*37
usd to sgd
safari
```

---

### 2. 触控板手势

系统设置 → 触控板

推荐开启：

- 三指上滑：Mission Control
- 三指左右滑：切换桌面
- 三指轻点：查词

---

### 3. Stage Manager（台前调度）

路径：

```text
系统设置 → 桌面与程序坞 → 台前调度
```

适用于：

- 学习
- 编程
- 写作

---

### 4. 分屏

长按窗口左上角绿色按钮：

- 平铺到左侧
- 平铺到右侧

适用于：

- 阅读 + 笔记
- 视频课程 + 文档
- 编程 + 浏览器

---

## 二、Finder 文件管理

### 1. 启动 Finder

#### 方法一：切换到 Finder

```text
Command + Tab
```

#### 方法二：点击桌面

桌面本身属于 Finder。

#### 方法三：新建 Finder 窗口

```text
Command + N
```

---

### 2. Finder 常用快捷键

| 功能         | 快捷键              |
| ------------ | ------------------- |
| 新建窗口     | Command + N         |
| 新建标签页   | Command + T         |
| 删除文件     | Command + Delete    |
| 新建文件夹   | Command + Shift + N |
| 显示隐藏文件 | Command + Shift + . |

---

### 3. 快速访问目录

| 功能     | 快捷键               |
| -------- | -------------------- |
| 下载     | Option + Command + L |
| 文稿     | Shift + Command + O  |
| 桌面     | Shift + Command + D  |
| 应用程序 | Shift + Command + A  |
| AirDrop  | Shift + Command + R  |

---

### 4. 快速跳转路径

```text
Shift + Command + G
```

例如：

```text
/Users/用户名/Desktop
```

---

### 5. Quick Look 快速预览

选中文件：

```text
Space
```

支持：

- PDF
- 图片
- 视频
- Word
- Markdown

---

### 6. Finder 标签

右键文件 → 标签

建议：

- 红色：紧急
- 黄色：待处理
- 绿色：已完成
- 蓝色：学习资料

---

## 三、多任务与窗口管理

### 1. 应用切换

```text
Command + Tab
```

---

### 2. 同应用窗口切换

```text
Command + ~
```

---

### 3. Mission Control

```text
Control + ↑
```

查看：

- 所有窗口
- 所有桌面

---

### 4. 多桌面管理

创建桌面：

```text
Control + ↑
```

然后点击右上角：

```text
+
```

建议：

- 桌面1：学习
- 桌面2：开发
- 桌面3：浏览器
- 桌面4：娱乐

---

### 5. 强制退出程序

```text
Command + Option + Esc
```

---

## 四、文本编辑效率

### 光标移动

按词移动：

```text
Option + ← / →
```

行首行尾：

```text
Command + ← / →
```

---

### 删除

删除一个单词：

```text
Option + Delete
```

删除整行：

```text
Command + Delete
```

---

### 文本选择

按词选择：

```text
Shift + Option + ← / →
```

整行选择：

```text
Shift + Command + ← / →
```

---

## 五、截图与录屏

### 全屏截图

```text
Command + Shift + 3
```

---

### 区域截图

```text
Command + Shift + 4
```

---

### 截图与录屏控制台

```text
Command + Shift + 5
```

功能：

- 截图
- 录屏
- 定时截图
- 指定保存位置

---

### 截图到剪贴板

```text
Command + Control + Shift + 4
```

直接粘贴即可使用。

---

## 六、Safari 与学习效率

### 标签页

新建：

```text
Command + T
```

关闭：

```text
Command + W
```

恢复：

```text
Command + Shift + T
```

---

### 标签组

适合：

- 考研
- 开发项目
- 论文阅读

---

### 阅读器模式

适用于：

- 英文阅读
- 去广告
- 长文章

---

## 七、苹果生态功能

### Universal Clipboard

要求：

- 同 Apple ID
- 蓝牙开启
- Wi-Fi 开启

功能：

```text
iPhone复制
↓
Mac粘贴
```

---

### AirDrop

快捷键：

```text
Shift + Command + R
```

---

### Sidecar

使用 iPad 作为 Mac 副屏。

适用于：

- 编程
- 阅读 PDF
- 记笔记

---

## 八、终端基础

### 打开 Terminal

Spotlight：

```text
terminal
```

---

### 常用命令

| 命令  | 功能     |
| ----- | -------- |
| pwd   | 当前目录 |
| ls    | 查看文件 |
| cd    | 切换目录 |
| mkdir | 创建目录 |
| clear | 清屏     |

---

## 九、推荐软件

### 开发

- Visual Studio Code
- iTerm2

### 笔记

- Obsidian
- Notion

### 效率

- Raycast
- Alfred
- Rectangle

---

## 十、macOS 使用建议

### 建议 1

不要安装各种系统清理软件。

---

### 建议 2

优先学习快捷键。

---

### 建议 3

充分利用触控板。

---

### 建议 4

掌握 Finder。

---

### 建议 5

熟练使用：

```text
Spotlight + 多桌面
```

---

# 十一、macOS 与 Windows 的 U 盘使用

## 文件系统兼容性

| 文件系统  | macOS        | Windows  | 说明             |
| --------- | ------------ | -------- | ---------------- |
| FAT32     | 读写         | 读写     | 单文件最大4GB    |
| **exFAT** | **读写**     | **读写** | **推荐**         |
| **NTFS**  | **默认只读** | **读写** | **Windows 默认** |
| APFS      | 读写         | 不支持   | mac 专用         |
| HFS+      | 读写         | 不支持   | 老版 mac         |

---

## 最佳方案

推荐格式：

```text
exFAT
```

优点：

- macOS 支持
- Windows 支持
- 支持大文件
- 无需安装驱动

---

## macOS 格式化 U 盘

打开：

```text
磁盘工具
```

步骤：

1. 选择 U 盘设备
2. 点击「抹掉」
3. 格式选择：

```text
exFAT
```

4. 方案选择：

```text
GUID 分区图
```

---

## Windows 格式化 U 盘

步骤：

1. 右键 U 盘
2. 格式化
3. 文件系统：

```text
exFAT
```

---

## 常见问题

### 文件超过 4GB 无法复制

原因：

```text
FAT32 限制
```

解决：

```text
改为 exFAT
```

---

### Mac 无法写入 NTFS

原因：

```text
macOS 默认仅支持读取 NTFS
```

解决：

```text
使用 exFAT
```

---

### Windows 无法识别 APFS

原因：

```text
APFS 为 Apple 专用格式
```

解决：

```text
改用 exFAT
```

---

## 安全使用建议

### 使用完成后弹出设备

macOS：

```text
推出
```

Windows：

```text
安全删除硬件
```

---

### 重要资料备份

推荐：

- iCloud Drive
- OneDrive
- 外置 SSD

---

## 推荐目录结构

```text
U盘/
├── 学习
│   ├── 英语
│   ├── 数学
│   └── 专业课
│
├── 编程
│   ├── Python
│   ├── C++
│   └── 项目
│
├── 工具
│
└── 临时文件
```

---

# 总结

macOS 核心效率来源：

1. Spotlight
2. Finder
3. 多桌面
4. 触控板手势
5. 快捷键操作

跨平台 U 盘最佳实践：

```text
文件系统：exFAT
格式化方案：GUID 分区图
使用习惯：安全弹出
```

这样可以保证 macOS 与 Windows 长期稳定兼容。