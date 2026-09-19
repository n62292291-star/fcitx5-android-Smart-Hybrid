# Fcitx5 Android Smart Hybrid

> 基于 Fcitx5 Android 的个人功能增强分支，探索双拼、全拼、混合输入以及更智能的移动端输入体验。

[![Build APK](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/actions/workflows/publish.yml/badge.svg)](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/actions)
[![GitHub Releases](https://img.shields.io/github/v/release/n62292291-star/fcitx5-android-Smart-Hybrid)](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/releases)
[![GitHub License](https://img.shields.io/github/license/n62292291-star/fcitx5-android-Smart-Hybrid)](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid)

**中文** · [English](#english)

---

# 中文

## ✨ 项目简介

**Fcitx5 Android Smart Hybrid** 是基于
[Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)
开发的个人功能增强分支。

项目希望在保留 Fcitx5 Android 原有输入法框架、多语言支持以及插件生态的基础上，逐步加入更加灵活的中文输入方式。

### 主要方向

- 🐦 小鹤双拼
- 🔀 双拼 / 全拼混合输入
- ⌨️ 全拼输入
- 🧠 智能纠错与输入猜测
- 🎙️ 语音输入
- 💡 更直观的键盘提示
- 📱 面向移动端的输入体验优化

> 项目目前处于持续开发阶段。

---

## 🚀 当前功能

### 小鹤双拼键位提示

当前版本首先实现了**小鹤双拼键位提示**。

字母键下方会显示对应的双拼提示，例如：

```text
┌─────┐
│  Q  │
│  iu │
└─────┘
```

部分键位示例：

| 按键 | 提示 |
|:---:|:---:|
| Q | `iu` |
| W | `ia` |
| E | `ua` |
| R | `uan` |
| T | `ue` |

### ⚠️ 当前功能范围

目前的双拼提示主要用于：

- 学习双拼键位
- 熟悉键盘布局
- 提供视觉提示

**目前还不是完整的双拼输入。**

也就是说：

> 当前版本可以看到双拼键位提示，但实际输入逻辑仍然使用原有键盘输入逻辑。

完整的小鹤双拼输入将在后续版本继续开发。

---

## 🗺️ 开发计划

| 功能 | 状态 |
|---|:---:|
| 小鹤双拼键位提示 | ✅ 已完成 |
| 双拼键位映射 | 🚧 开发中 |
| 完整小鹤双拼输入 | 📋 计划中 |
| 双拼候选处理 | 📋 计划中 |
| 双拼 / 全拼混合输入 | 📋 计划中 |
| 更完善的全拼输入 | 📋 计划中 |
| 智能纠错 | 📋 计划中 |
| 输入错误猜测 | 📋 计划中 |
| 语音输入 | 📋 计划中 |
| 更多移动端输入优化 | 📋 计划中 |

---

## 🎯 项目目标

项目希望逐步形成多种输入方式可以共存的输入体验：

```text
                    Android Keyboard
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
         全拼输入        双拼输入       混合输入
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                    智能候选 / 纠错
                           │
                           ▼
                        中文输入
```

长期目标不是简单增加一种输入方式，而是让不同输入习惯可以在同一个输入法中自然共存。

---

## 📥 下载

### GitHub Releases

正式发布版本：

**[下载最新 Release](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/releases)**

### GitHub Actions

开发版本可以从 GitHub Actions 获取：

**[查看 GitHub Actions](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/actions)**

> 开发版本可能包含尚未完成的功能，不保证稳定性。

---

## 🛠️ 构建

### 环境要求

项目使用 Gradle 构建 Android APK。

推荐环境：

- JDK 17
- Android SDK
- Android NDK / CMake
- Gradle Wrapper

具体版本以项目当前 Gradle 配置为准。

### 克隆项目

```bash
git clone --recursive https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid.git
cd fcitx5-android-Smart-Hybrid
```

如果已经克隆但没有获取子模块：

```bash
git submodule update --init --recursive
```

### 构建 Debug APK

```bash
./gradlew :app:assembleDebug
```

APK 输出目录：

```text
app/build/outputs/apk/debug/
```

### 构建 Release APK

```bash
./gradlew :app:assembleRelease
```

APK 输出目录：

```text
app/build/outputs/apk/release/
```

---

## ⚙️ GitHub Actions

项目支持通过 GitHub Actions 自动构建 APK。

基本流程：

```text
Push / 手动运行
       │
       ▼
    Checkout
       │
       ▼
    Setup JDK
       │
       ▼
 Setup Android SDK
       │
       ▼
Install dependencies
       │
       ▼
  Gradle Build
       │
       ▼
 Release APK
       │
       ▼
GitHub Actions Artifact
```

工作流位于：

```text
.github/workflows/
```

---

## 🔐 APK 签名

项目支持通过 GitHub Actions Secrets 对 Release APK 进行签名。

目前使用：

```text
SIGN_KEY_BASE64
SIGN_KEY_PWD
SIGN_KEY_ALIAS
```

其中：

- `SIGN_KEY_BASE64`：Base64 编码后的 JKS 签名文件
- `SIGN_KEY_PWD`：签名密钥库密码
- `SIGN_KEY_ALIAS`：签名密钥别名

签名文件和密码不应直接提交到 Git 仓库。

---

## 🔄 开发流程

项目主要采用：

**GitHub + GitHub Actions + Android 手机测试**

进行开发。

基本流程：

```text
修改源码
   │
   ▼
 Commit
   │
   ▼
Push 到 GitHub
   │
   ▼
GitHub Actions 自动构建
   │
   ▼
 下载 APK
   │
   ▼
Android 手机上测试
   │
   ▼
根据测试结果继续修改
```

这样可以不依赖本地电脑完成主要的开发、构建和测试流程。

---

## 🧩 项目结构

主要 Android 代码位于：

```text
app/src/main/java/org/fcitx/fcitx5/android/
```

主要模块：

```text
core/
daemon/
data/
input/
provider/
ui/
utils/
```

键盘相关代码位于：

```text
app/src/main/java/org/fcitx/fcitx5/android/input/keyboard/
```

主要文件包括：

```text
BaseKeyboard.kt
CommonKeyActionListener.kt
CustomGestureView.kt
KeyAction.kt
KeyActionListener.kt
KeyDef.kt
KeyDefPreset.kt
KeyDrawable.kt
KeyView.kt
KeyboardWindow.kt
LangSwitchBehavior.kt
NumberKeyboard.kt
SpaceLongPressBehavior.kt
SwipeSymbolDirection.kt
TextKeyboard.kt
```

---

## 💡 双拼提示实现

目前的双拼键位提示主要涉及：

```text
DoublePinyin.kt
KeyDef.kt
KeyDefPreset.kt
KeyView.kt
```

基本结构：

```text
DoublePinyin.kt
       │
       ▼
KeyDefPreset.kt
       │
       ▼
KeyDef.kt
       │
       ▼
KeyView.kt
       │
       ▼
   键盘显示
```

### `DoublePinyin.kt`

负责保存双拼键位提示映射。

例如：

```kotlin
"Q" to "iu",
"W" to "ia",
"E" to "ua",
"R" to "uan",
```

### `KeyDef.kt`

为键盘按键提供双拼提示字段：

```kotlin
val doublePinyinHint: String? = null
```

### `KeyDefPreset.kt`

创建字母键时读取对应提示：

```kotlin
doublePinyinHint = DoublePinyin.Xiaohe.getHint(character)
```

### `KeyView.kt`

负责将双拼提示显示在键盘按键上。

---

## 📱 当前开发状态

### 已完成 / 当前代码中

- ✅ 基于 Fcitx5 Android
- ✅ 保留原有多语言输入框架
- ✅ Android 键盘基础功能
- ✅ 小鹤双拼键位提示 UI
- ✅ 双拼提示数据独立管理
- ✅ GitHub Actions 自动构建
- ✅ Release APK 签名支持

### 正在开发 / 后续计划

- 🚧 完整小鹤双拼输入
- 📋 双拼候选处理
- 📋 双拼 / 全拼混合输入
- 📋 更完善的全拼输入
- 📋 智能纠错
- 📋 输入错误猜测
- 📋 语音输入
- 📋 更多移动端输入体验优化

---

## ⚠️ 注意事项

### 1. 当前双拼提示不是完整双拼输入

看到键盘上的双拼提示，并不代表当前输入法已经可以直接使用小鹤双拼输入中文。

当前功能主要用于帮助用户熟悉：

```text
Q → iu
W → ia
E → ua
R → uan
T → ue
...
```

真正的双拼输入逻辑仍在后续开发中。

### 2. 项目处于开发阶段

这是一个持续开发中的个人分支，因此：

- 功能可能发生变化
- UI 可能发生变化
- 配置可能发生变化
- APK 签名可能发生变化
- 部分功能可能暂时不稳定

请根据自己的需求选择是否安装开发版本。

---

## 🐛 问题反馈

如果发现问题，可以提交 GitHub Issue：

**[提交 Issue](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/issues)**

建议提供：

```text
Android 版本：
手机型号：
APK 版本：
输入法配置：

问题描述：

复现步骤：

日志：
```

如果是构建问题，也可以附上 GitHub Actions 的失败日志。

---

## 🤝 贡献

欢迎提交：

- Bug 修复
- 功能改进
- UI 改进
- 输入方案
- 双拼相关功能
- 文档改进
- 测试反馈

如果涉及较大的功能修改，建议先通过 Issue 讨论。

---

## 🔗 上游项目

本项目基于：

**[Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)**

本项目主要针对个人需求进行功能实验和修改。

上游项目提供了本项目使用的基础输入法框架以及大量基础代码。

如果你希望使用原版 Fcitx5 Android，请访问：

**[Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)**

---

## 📄 许可证

本项目基于 Fcitx5 Android。

Fcitx5 Android 以及相关组件的许可证信息，请以各自源代码中的 SPDX 标识以及 LICENSE 文件为准。

本项目新增或修改的代码应遵循对应源文件声明的许可证。

修改或重新发布项目时，请保留原项目的版权声明以及许可证信息。

---

## 🙏 致谢

感谢 Fcitx5 Android 项目以及所有 Fcitx5 相关项目的贡献者。

- [Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)
- [Fcitx5](https://github.com/fcitx/fcitx5)

---

# English

## ✨ Introduction

**Fcitx5 Android Smart Hybrid** is a personal development fork based on [Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android).

The project explores a more flexible Android input experience while keeping the existing Fcitx5 Android framework, multilingual input support, and plugin ecosystem.

### Main directions

- 🐦 Xiaohe double-pinyin
- 🔀 Hybrid double-pinyin / full-pinyin input
- ⌨️ Full-pinyin input
- 🧠 Intelligent typo correction and input guessing
- 🎙️ Voice input
- 💡 More informative keyboard hints
- 📱 Mobile input experience improvements

> The project is currently under active development.

---

## 🚀 Current Features

### Xiaohe Double-Pinyin Keyboard Hints

The current version first introduces **Xiaohe double-pinyin keyboard hints**.

Alphabet keys display their corresponding double-pinyin hints:

```text
┌─────┐
│  Q  │
│  iu │
└─────┘
```

Examples:

| Key | Hint |
|:---:|:---:|
| Q | `iu` |
| W | `ia` |
| E | `ua` |
| R | `uan` |
| T | `ue` |

### ⚠️ Current Scope

The current double-pinyin feature is primarily intended for:

- Learning the key mapping
- Familiarizing yourself with the keyboard
- Visual input hints

**It is not a complete double-pinyin input engine yet.**

The current keyboard still uses the existing input logic.

Full Xiaohe double-pinyin input will be developed in future versions.

---

## 🗺️ Roadmap

| Feature | Status |
|---|:---:|
| Xiaohe double-pinyin keyboard hints | ✅ Done |
| Double-pinyin key mapping | 🚧 In Progress |
| Full Xiaohe double-pinyin input | 📋 Planned |
| Double-pinyin candidate handling | 📋 Planned |
| Hybrid double-pinyin / full-pinyin input | 📋 Planned |
| Improved full-pinyin input | 📋 Planned |
| Intelligent typo correction | 📋 Planned |
| Input error guessing | 📋 Planned |
| Voice input | 📋 Planned |
| Further mobile input improvements | 📋 Planned |

---

## 🎯 Project Goals

The long-term goal is to allow multiple input methods to coexist naturally:

```text
                    Android Keyboard
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
         Full Pinyin   Double Pinyin   Hybrid
             │             │             │
             └─────────────┼─────────────┘
                           ▼
                    Candidate / Correction
                           │
                           ▼
                      Chinese Input
```

The goal is not simply to add another input method, but to allow different input habits to coexist within the same keyboard.

---

## 📥 Download

### GitHub Releases

Official releases:

**[Download Latest Release](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/releases)**

### GitHub Actions

Development builds can be obtained from:

**[GitHub Actions](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/actions)**

> Development builds may contain unfinished features and may not be stable.

---

## 🛠️ Build

### Requirements

Recommended environment:

- JDK 17
- Android SDK
- Android NDK / CMake
- Gradle Wrapper

Exact versions depend on the current Gradle configuration.

### Clone

```bash
git clone --recursive https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid.git
cd fcitx5-android-Smart-Hybrid
```

If submodules were not initialized:

```bash
git submodule update --init --recursive
```

### Debug APK

```bash
./gradlew :app:assembleDebug
```

Output:

```text
app/build/outputs/apk/debug/
```

### Release APK

```bash
./gradlew :app:assembleRelease
```

Output:

```text
app/build/outputs/apk/release/
```

---

## ⚙️ GitHub Actions

The project supports automated APK builds through GitHub Actions.

The general workflow is:

```text
Push / Manual Trigger
        │
        ▼
     Checkout
        │
        ▼
     Setup JDK
        │
        ▼
  Setup Android SDK
        │
        ▼
Install Dependencies
        │
        ▼
   Gradle Build
        │
        ▼
    Release APK
        │
        ▼
GitHub Actions Artifact
```

Workflows are located under:

```text
.github/workflows/
```

---

## 🔐 APK Signing

Release APKs can be signed through GitHub Actions Secrets.

The current signing variables are:

```text
SIGN_KEY_BASE64
SIGN_KEY_PWD
SIGN_KEY_ALIAS
```

- `SIGN_KEY_BASE64` — Base64-encoded JKS keystore
- `SIGN_KEY_PWD` — Keystore password
- `SIGN_KEY_ALIAS` — Signing key alias

Signing files and passwords should never be committed directly to the repository.

---

## 🔄 Development Workflow

The project is primarily developed using:

**GitHub + GitHub Actions + Android device testing**

Typical workflow:

```text
Modify Source
      │
      ▼
   Commit
      │
      ▼
Push to GitHub
      │
      ▼
GitHub Actions Build
      │
      ▼
 Download APK
      │
      ▼
Test on Android
      │
      ▼
Continue Development
```

This allows most development, building, and testing to be performed without a local computer.

---

## 🧩 Project Structure

Main Android source code:

```text
app/src/main/java/org/fcitx/fcitx5/android/
```

Main modules:

```text
core/
daemon/
data/
input/
provider/
ui/
utils/
```

Keyboard-related code:

```text
app/src/main/java/org/fcitx/fcitx5/android/input/keyboard/
```

Important files include:

```text
BaseKeyboard.kt
CommonKeyActionListener.kt
CustomGestureView.kt
KeyAction.kt
KeyActionListener.kt
KeyDef.kt
KeyDefPreset.kt
KeyDrawable.kt
KeyView.kt
KeyboardWindow.kt
LangSwitchBehavior.kt
NumberKeyboard.kt
SpaceLongPressBehavior.kt
SwipeSymbolDirection.kt
TextKeyboard.kt
```

---

## 💡 Double-Pinyin Hint Implementation

The current double-pinyin hint implementation mainly involves:

```text
DoublePinyin.kt
KeyDef.kt
KeyDefPreset.kt
KeyView.kt
```

Architecture:

```text
DoublePinyin.kt
       │
       ▼
KeyDefPreset.kt
       │
       ▼
KeyDef.kt
       │
       ▼
KeyView.kt
       │
       ▼
Keyboard UI
```

### `DoublePinyin.kt`

Stores the double-pinyin hint mapping.

For example:

```kotlin
"Q" to "iu",
"W" to "ia",
"E" to "ua",
"R" to "uan",
```

### `KeyDef.kt`

Provides the double-pinyin hint field:

```kotlin
val doublePinyinHint: String? = null
```

### `KeyDefPreset.kt`

Reads the corresponding hint when creating alphabet keys:

```kotlin
doublePinyinHint = DoublePinyin.Xiaohe.getHint(character)
```

### `KeyView.kt`

Displays the double-pinyin hint on the keyboard key.

---

## 📊 Development Status

### Currently Available

- ✅ Based on Fcitx5 Android
- ✅ Existing multilingual input framework
- ✅ Android keyboard functionality
- ✅ Xiaohe double-pinyin keyboard hints
- ✅ Separate double-pinyin hint mapping
- ✅ GitHub Actions build support
- ✅ Release APK signing support

### Planned

- 🚧 Full Xiaohe double-pinyin input
- 📋 Double-pinyin candidate handling
- 📋 Hybrid double-pinyin / full-pinyin input
- 📋 Improved full-pinyin input
- 📋 Intelligent typo correction
- 📋 Input error guessing
- 📋 Voice input
- 📋 Further mobile input improvements

---

## ⚠️ Important Notes

### The Current Double-Pinyin Hint Is Not Full Double-Pinyin Input

Seeing double-pinyin hints on the keyboard does not mean that complete Xiaohe double-pinyin input is already implemented.

The current feature is mainly intended to help users learn the key mapping:

```text
Q → iu
W → ia
E → ua
R → uan
T → ue
...
```

The actual double-pinyin input engine is still under development.

### Development Status

This is a continuously developed personal fork.

Therefore:

- Features may change
- UI may change
- Configuration may change
- APK signing details may change
- Some features may be unstable during development

Use development builds at your own discretion.

---

## 🐛 Issues

If you encounter a problem, please submit a GitHub Issue:

**[Submit an Issue](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/issues)**

Please include:

```text
Android version:
Device:
APK version:
Input method configuration:

Problem description:

Steps to reproduce:

Logs:
```

For build problems, GitHub Actions logs are also helpful.

---

## 🤝 Contributing

Contributions are welcome, including:

- Bug fixes
- Feature improvements
- UI improvements
- Input schemes
- Double-pinyin features
- Documentation
- Testing and feedback

For larger changes, discussing the idea in an Issue first is recommended.

---

## 🔗 Upstream Project

This project is based on:

**[Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)**

This repository is an independent development fork focused on personal experimentation and additional features.

The basic input method framework and a large amount of the underlying code are provided by the upstream Fcitx5 Android project.

For the original project:

**[Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)**

---

## 📄 License

This project is based on Fcitx5 Android.

Please refer to the SPDX identifiers and LICENSE files of the respective source files and components for their applicable licenses.

New or modified code should follow the license declared by the corresponding source file.

Please retain the original copyright notices and license information when modifying or redistributing the project.

---

## 🙏 Acknowledgements

Thanks to the Fcitx5 Android project and all contributors to the Fcitx5 ecosystem.

- [Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android)
- [Fcitx5](https://github.com/fcitx/fcitx5)