# MilkCat

MilkCat 是一只住在 macOS 桌面里的本地小猫桌宠。

它不会联网，不接 AI，不需要 API Key，也不需要注册账号。打开之后，小猫“牛奶”会在桌面上慢慢走来走去、发呆、被摸摸时开心一下，偶尔用气泡自言自语，也会在本地提醒你喝水、站起来、休息眼睛和早点睡。

> 牛奶，真名韩建国，嘴硬心软的小猫监工。  
> 作者：Nico

## 特点

- 完全本地运行
- 不联网
- 不需要 API Key
- 不需要用户注册
- 不读取隐私数据
- 透明悬浮小猫窗口
- 支持拖动小猫
- 点击小猫显示开心气泡
- 本地文案库，自言自语不会调用 AI
- 喝水、久坐、护眼、早睡提醒
- 番茄专注计时
- 本地设置面板
- 右键菜单
- 可打包为 macOS `.app` / `.dmg`

## 下载和安装

当前本地构建好的安装包在：

```text
release/MilkCat-1.0.dmg
```

安装方式：

1. 打开 `MilkCat-1.0.dmg`
2. 把 `MilkCat.app` 拖到 `Applications`
3. 打开 `MilkCat`

如果 macOS 提示“Apple 无法验证 MilkCat 是否包含可能危害 Mac 安全或泄漏隐私的恶意软件”，这是因为当前版本没有 Apple Developer ID 公证。可以在终端运行：

```bash
xattr -dr com.apple.quarantine /Applications/MilkCat.app
```

然后再打开 `MilkCat`。

## 从源码运行

要求：

- macOS 13.0 或更高版本
- Xcode 15 或更高版本

构建：

```bash
open ScreenPets.xcodeproj
```

然后在 Xcode 中选择 `ScreenPets` scheme，点击 Run。

也可以用命令行构建 Release：

```bash
xcodebuild -project ScreenPets.xcodeproj \
  -scheme ScreenPets \
  -configuration Release \
  -derivedDataPath .build/DerivedDataRelease \
  build
```

构建产物会在：

```text
.build/DerivedDataRelease/Build/Products/Release/MilkCat.app
```

## 项目结构

```text
ScreenPets/
├── Managers/
│   ├── PetManager.swift
│   ├── PetWindowController.swift
│   ├── ReminderManager.swift
│   ├── PomodoroManager.swift
│   └── LaunchAtLoginManager.swift
├── Models/
│   ├── Pet.swift
│   ├── PetSettings.swift
│   ├── PhraseLibrary.swift
│   └── ReminderType.swift
├── Pets/
│   └── CatPet.swift
├── Resources/
│   ├── Assets.xcassets/
│   ├── CatFrames/
│   ├── zh-Hans.lproj/
│   └── en.lproj/
├── Views/
│   └── SettingsView.swift
├── Info.plist
└── ScreenPetsApp.swift
```

## 本地隐私说明

MilkCat 的设计目标是“朋友安装后直接可用”：

- 不上传数据
- 不接入 AI 问答
- 不调用远程模型
- 不需要 OpenAI Key 或任何第三方 API Key
- 设置保存在本机 `UserDefaults`
- 文案来自本地 `PhraseLibrary`

## 技术栈

- Swift
- SwiftUI
- AppKit `NSWindow`
- UserDefaults
- Xcode asset catalog

## 鸣谢

MilkCat 基于开源 macOS 桌宠项目 ScreenPets 改造而来，并针对本地小猫桌宠、提醒、番茄钟、透明悬浮交互窗口和本地文案库做了定制。

## License

MIT License. See [LICENSE](LICENSE).
