# counter_deep

课程第 5 课（Flutter 工程结构与 Widget 体系）实践作业：基于 Flutter 官方计数器示例的精读与改造。

## 项目说明

在官方计数器模板的基础上完成以下改造：

1. **步长调节**：每点击一次 FAB 计数 +2（原为 +1）
2. **主题定制**：种子色由默认 deepPurple 改为 `Colors.teal`，并在页面中自行添加两处 `Theme.of(context)` 取用（FAB 背景色、提示文字颜色）
3. **生命周期日志**：为 `_MyHomePageState` 的 6 个生命周期钩子（initState / didChangeDependencies / build / didUpdateWidget / deactivate / dispose）各添加一行 `[lifecycle]` 日志
4. **资源替换**：在 `assets/` 放入自定义图片，作为 AppBar 背景（`flexibleSpace` + `Image.asset`），pubspec 声明后完整重启验证

完整 Widget 树手绘图见 [docs/widget-tree.png](docs/widget-tree.png)。

## 文件结构

```text
counter_deep/
├── lib/
│   └── main.dart            # 全部代码：入口 main() + MyApp + MyHomePage + _MyHomePageState
├── assets/
│   └── bg.jpg               # AppBar 背景图（在 pubspec.yaml 的 flutter.assets 段声明）
├── docs/
│   └── widget-tree.png      # Widget 树手绘图（含 StatelessWidget/StatefulWidget 标注）
├── test/                    # 默认 widget 测试
├── pubspec.yaml             # 依赖与资源声明
├── android/ ios/ web/ windows/   # 平台目录（平台级配置时才修改）
└── build/                   # 构建产物（不入库，.gitignore 已忽略）
```

## 打开与运行方式

环境要求：Flutter SDK 3.47.4 stable（Dart 3.13.3），Windows 11。

```powershell
flutter pub get     # 拉取依赖
flutter run         # 启动，按提示选择设备：[3] Edge(web) 或 [1] Windows(desktop)
```

运行中的调试按键：

| 按键 | 作用 |
|---|---|
| `r` | 热重载（State 保留，build 重新执行） |
| `R` | 热重启（State 销毁重建，全套生命周期重来） |
| `q` | 退出应用 |

> 注意：修改 pubspec.yaml（如新增资源）后热重载无效，必须完整重启。本应用为单页面，web 端按 q、桌面端关窗口均为进程直接终止，因此 deactivate/dispose 日志不会触发，属正常现象。

## AI 工具使用说明

- **工具**：TraeCode
- **使用范围**：Widget 树结构讲解与纠错、提供改造对照方案、生命周期钩子讲解、pubspec 报错定位
- **使用方式**：AI 提供方案与讲解，全部代码由本人手动录入并在本地运行验证。
