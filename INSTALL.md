# Install 编译运行指南

## 开发环境
- Visual Studio 2026
- EasyX for Visual C++ 图形库
- 仅支持 Windows 平台

## 编译步骤
```bash
1. 克隆仓库到本地
git clone https://github.com/你的用户名/Minesweeper_repo.git
cd Minesweeper_repo
2.使用 VS 打开 Minesweeper.sln 解决方案
3.顶部配置选择 x64 Debug，点击「生成 → 重新生成解决方案」
项目已配置后期生成事件，编译完成自动将 res 贴图资源复制到 x64/Debug 输出目录，无需手动拷贝图片。
4.按下 F5 启动调试运行。
## 独立 exe 直接运行注意事项
若不通过 VS 调试，直接双击 exe 启动游戏：
必须将仓库内 res 完整资源文件夹，与 Minesweeper.exe 放在同一目录，否则贴图加载失败，程序窗口直接闪退。
Release 模式编译：项目属性 C/C++ → 代码生成，运行库选择 /MT，生成绿色免安装程序包。
