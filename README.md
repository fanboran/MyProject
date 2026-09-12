# MyProject

基于 **Qt 6 + QGraphicsView** 的 2D 游戏项目，C++17 编写，CMake 构建。

这是我本科阶段的游戏开发练习项目，从零搭建了一套完整的 2D 游戏窗口框架：
地图滚动、角色控制、碰撞系统与主菜单，并做了中文本地化。

## 功能特性

- **角色控制** — 键盘控制角色移动，视口随角色平滑滚动
- **碰撞系统** — 障碍物碰撞 + 可配置的「空气墙」边界，接口化封装便于调整
- **地图系统** — 支持大尺寸地图图片加载与视口跟随
- **主菜单** — 顶部菜单栏，支持开始游戏与坐标传送对话框
- **动图 Logo** — 启动界面的动态 Logo 展示（`AnimatedLogo`）
- **状态栏** — 实时显示鼠标坐标与角色世界坐标
- **中文本地化** — 通过 Qt Linguist（`Game_zh_CN.ts`）支持界面翻译
- **自定义光标** — 游戏内光标绘制（`Cursor`）

## 技术栈

| 组件 | 说明 |
| --- | --- |
| 语言 | C++17 |
| 框架 | Qt 6 Widgets（同时兼容 Qt 5） |
| 构建 | CMake ≥ 3.14 |
| 国际化 | Qt LinguistTools |
| 图形 | QGraphicsView / QGraphicsScene / QGraphicsPixmapItem |

## 项目结构

```
MyProject/
├── CMakeLists.txt          # CMake 构建脚本
├── main.cpp                # 程序入口
├── Window.{h,cpp}          # 主窗口：菜单栏 + 状态栏 + 游戏启动
├── View.{h,cpp}            # 游戏视图：输入处理、地图移动、碰撞、光标
├── Map.{h,cpp}             # 地图图元
├── Sprite.{h,cpp}          # 精灵（角色）
├── MainMenu.{h,cpp}        # 主菜单
├── AnimatedLogo.{h,cpp}    # 动图 Logo
├── Cursor.{h,cpp}          # 自定义光标
├── Input.{h,cpp}           # 输入处理
├── Entity.hpp              # 实体基类
├── Game_zh_CN.ts           # 中文翻译源文件
└── images/                 # 游戏素材（地图、角色、UI）
```

## 构建与运行

### 前置要求

- Qt 6（或 Qt 5），需包含 `Widgets` 与 `LinguistTools` 模块
- CMake ≥ 3.14
- 支持 C++17 的编译器（MSVC / MinGW / GCC / Clang）

### 命令行构建

```bash
mkdir build && cd build
cmake ..
cmake --build . --config Release
```

### Qt Creator

直接用 Qt Creator 打开根目录的 `CMakeLists.txt` 即可，选择对应 Kit 后构建运行。

### 运行

编译产物为 `Game`（Windows 下为 `Game.exe`），运行前确保 Qt 运行库在 `PATH` 中。

## 已知问题

- 碰撞重构后角色在特定情况下可能出现抖动（见提交历史）

## 许可

本项目采用 [MIT License](LICENSE)。
