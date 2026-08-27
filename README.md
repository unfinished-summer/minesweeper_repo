# 扫雷游戏

基于 C 语言 + EasyX 图形库实现的扫雷小游戏，支持左右键交互、右键插旗、胜负判定与贴图渲染。

## 项目功能

- 地图渲染：格子贴图、地雷隐藏与揭示
- 交互操作：左键翻开、右键插旗/取消插旗
- 游戏判定：踩雷失败、全部排雷胜利（弹窗提示）

## 项目特点
- 资源路径相对化，解除本地磁盘路径耦合，便于部署
- VS后期生成事件自动拷贝贴图资源，无需手动复制资源文件

## 限制
EasyX图形库仅支持 Windows 平台。

## 📂 文档导航
- [INSTALL.md](./INSTALL.md) 编译运行指南
- [TROUBLESHOOTING.md](./TROUBLESHOOTING.md) 问题与故障排查
- [DEVELOP.md](./DEVELOP.md) 开发细节、代码结构
- [CHANGELOG.md](./CHANGELOG.md) 版本更新记录
- [TODO.md](./TODO.md) 待实现功能与现存缺陷

## 项目目录结构
```
Minesweeper
├─ res                  # 贴图资源文件夹，完整提交至 Git 仓库
│  ├─ 0.png ~ 8.png     # 数字 0~8 格子贴图
│  ├─ Mine.png          # 地雷贴图
│  ├─ block.png         # 未翻开遮挡格子贴图
│  └─ flag.png          # 插旗标记贴图
├─ Minesweeper.cpp      # 全部游戏主逻辑代码
├─ Minesweeper.vcxproj  # VS 项目配置（自动拷贝 res 资源脚本内置）
└─ Minesweeper.sln     # VS 解决方案文件
```


## License
MIT
