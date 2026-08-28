# DEVELOP 开发文档

## 目录结构
```bash
├─ res/                # BMP/PNG 图片资源
├─ Minesweeper.cpp     # 主逻辑全部代码
├─ Minesweeper.vcxproj # VS 项目配置，内置后期生成事件自动复制 res 资源
└─ Minesweeper.sln     # VS 解决方案
```

## 代码模块划分
1. 地图初始化：生成地雷、计算周边地雷数字
2. 绘图渲染模块：EasyX绘制格子、数字、地雷、插旗贴图
3. 鼠标交互模块：左键翻开格子，右键插旗/取消插旗
4. 胜负判定模块：踩雷失败、全部排雷胜利逻辑
5. 窗口消息、弹窗提示逻辑

## 重要开发约束
1. **资源路径全部使用相对路径，禁止写死绝对磁盘路径**，保证换电脑可以直接运行。
2. EasyX 的 `IMAGE` 对象**禁止放在函数局部栈**，优先全局 / static，防止退出时内存崩溃。
3. 访问地图数组前，必须做下标边界校验，防止数组越界随机崩溃。
4. 弹窗 MessageBox 不要放在绘图主循环内部，避免画面闪烁。
5. 开启双缓冲 `BeginBatchDraw / EndBatchDraw`，降低画面闪烁。

## Release打包流程
1. VS切换 x64‑Release，运行库设置 `/MT`（静态链接，绿色免运行库）
2. 编译成功，取出输出目录下 `Minesweeper.exe`
3. 将 `res` 资源文件夹与 exe 放在同一级
4. 压缩为 `Minesweeper‑Win64.zip`，上传至 GitHub Release。

## 已知限制
- EasyX 仅支持 Windows；无法在 Linux / macOS 原生运行。
- 窗口大小固定，暂不支持窗口缩放。
