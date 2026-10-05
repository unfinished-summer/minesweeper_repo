# 扫雷游戏

基于 C/C++ 与 EasyX 图形库实现的扫雷小游戏，支持左右键交互、右键插旗、胜负判定与贴图渲染。

## 项目功能

- 地图渲染：格子贴图、地雷隐藏与揭示
- 交互操作：左键翻开、右键插旗/取消插旗
- 游戏判定：踩雷失败、全部排雷胜利（弹窗提示）

## 项目特点

- 资源路径相对化，解除本地磁盘路径耦合，便于部署
- CMake 构建：POST_BUILD 自动拷贝贴图资源到 exe 旁，无需手动复制资源文件
- 源码与构建配置分离，编译产物不进入版本库

## 构建运行

### 依赖

- EasyX 图形库（仅 Windows；头文件与库路径集中在 `CMakeLists.txt` 顶部两行，换电脑只需修改这两行）
- CMake 3.10+，MSVC（Visual Studio 2019+）

### 构建运行（Visual Studio）

1. 用 VS 打开 `minesweeper_repo` 文件夹；
2. 顶部选择 x64 配置，点击「生成」；
3. 按 `F5` 运行。

### 构建运行（命令行）

```
cmake -B build -A x64
cmake --build build --config Release
build\Release\Minesweeper.exe
```

## 项目目录结构

```
minesweeper_repo/
├── Minesweeper.cpp      # 全部游戏主逻辑代码
├── CMakeLists.txt       # 构建配置（含 res 资源自动拷贝）
├── CMakePresets.json    # CMake 预设
├── res/                 # 贴图资源（0~8 数字、地雷、遮挡、旗子）
├── INSTALL.md           # 编译运行指南
├── TROUBLESHOOTING.md   # 问题与故障排查
├── DEVELOP.md           # 开发细节、代码结构
├── CHANGELOG.md         # 版本更新记录
├── TODO.md              # 待实现功能与现存缺陷
└── README.md
```

## 限制

EasyX 图形库仅支持 Windows 平台。

## 📂 文档导航

- [INSTALL.md](./INSTALL.md) — 编译运行指南
- [TROUBLESHOOTING.md](./TROUBLESHOOTING.md) — 问题与故障排查
- [DEVELOP.md](./DEVELOP.md) — 开发细节、代码结构
- [CHANGELOG.md](./CHANGELOG.md) — 版本更新记录
- [TODO.md](./TODO.md) — 待实现功能与现存缺陷