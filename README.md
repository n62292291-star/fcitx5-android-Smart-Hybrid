# Fcitx5 Android Smart Hybrid [中文](#中文) | [English](#english) --- # 中文 ## 项目简介 **Fcitx5 Android Smart Hybrid** 是基于 [Fcitx5 Android](https://github.com/fcitx5-android/fcitx5-android) 开发的个人功能增强分支。 这个项目的主要方向是探索一种更加灵活的 Android 输入方式，在保留 Fcitx5 Android 原有输入法框架、多语言支持以及插件生态的基础上，逐步加入： - 小鹤双拼 - 双拼与全拼混合输入 - 全拼输入 - 智能纠错与错字猜测 - 语音输入 - 更直观的键盘提示 - 其他针对移动端输入体验的改进 项目目前仍处于开发阶段。 --- ## 当前版本 ### v0.2 开发方向 目前首先实现的是**双拼键位提示**。 在英文键盘上显示对应的小鹤双拼提示，例如： ```text ┌─────┐ │ Q │ │ iu │ └─────┘ 

不同按键会显示对应的双拼提示。

例如：

Q → iu W → ia E → ua R → uan T → ue ... 

注意

目前的双拼提示主要用于键位学习和视觉提示。

也就是说： 当前版本显示双拼键位提示，但输入逻辑仍然使用原有键盘输入逻辑。

真正的双拼输入、双拼/全拼混合输入将在后续版本继续开发。

项目目标

项目希望逐步形成以下输入模式：

┌──────────────┐ │ Android │ │ Keyboard │ └──────┬───────┘ │ ├──────────────┬──────────────┐ │ │ │ ▼ ▼ ▼ 全拼输入 双拼输入 混合输入 │ │ │ └──────────────┼──────────────┘ ▼ 智能候选 / 纠错 │ ▼ 中文输入 

长期目标不是简单增加一种输入方式，而是让不同输入习惯可以在同一个输入法中自然共存。

计划功能

以下功能属于项目计划，并不代表当前版本已经全部实现。

1. 小鹤双拼

计划支持完整的小鹤双拼输入方案。包括：

双拼键位映射

声母输入

韵母输入

双拼候选词

双拼词库

双拼状态处理

2. 全拼输入

保留传统全拼输入方式。例如输入 nihao 得到 你好。

3. 双拼 / 全拼混合输入

计划允许用户在同一次输入过程中混合使用不同输入方式，例如 ni + 双拼 或 完整拼音 + 双拼。具体输入规则将在后续开发过程中确定。

4. 智能纠错

计划加入针对移动端输入习惯的智能纠错，可能包括：

拼音输入错误

双拼键位误按

相邻按键误触

常见拼音错误

候选词纠错

根据上下文猜测用户输入

5. 语音输入

计划加入语音输入能力。具体实现方式以及所使用的语音识别服务将在后续开发中确定。

6. 更直观的键盘提示

除了双拼提示以外，未来可能继续增加：

输入模式提示

当前输入状态

快捷键提示

特殊按键提示

用户自定义键位提示

下载

GitHub Releases

正式发布的 APK 将放在 GitHub Releases： GitHub Releases

如果项目尚未发布 Release，也可以通过 GitHub Actions 获取构建产物。

GitHub Actions

项目支持使用 GitHub Actions 自动构建 APK。

每次向 master 分支推送代码时，可以自动执行构建。

也可以在 GitHub Actions 页面手动运行构建工作流。

构建完成后，APK 会作为 GitHub Actions Artifact 提供下载。

本项目与上游项目的关系

本项目基于 Fcitx5 Android 开发。

上游项目： https://github.com/fcitx5-android/fcitx5-android

本项目主要针对个人需求进行功能实验和修改。上游项目的基础功能、输入法框架以及大量代码仍然由 Fcitx5 Android 提供。

如果你希望使用原版 Fcitx5 Android，建议直接访问上游项目。

原有功能

本项目继承 Fcitx5 Android 的基础输入法框架。因此除了本项目正在开发的新功能之外，也保留上游项目提供的输入法基础能力，包括：

Android 输入法服务

Fcitx5 输入法核心

多语言输入支持

键盘输入

输入法切换

输入法配置

Fcitx5 插件支持

输入法引擎支持

具体功能以及支持情况以当前代码版本为准。

支持的输入语言

本项目基于 Fcitx5 Android，因此可以使用 Fcitx5 Android 所支持的输入法和语言引擎。实际可用的输入方式取决于：

当前安装的输入法引擎

当前启用的插件

输入法配置

项目当前构建版本

项目不会因为增加中文双拼功能而移除原有的多语言输入框架。

开发

项目结构

主要 Android 代码位于： app/src/main/java/org/fcitx/fcitx5/android/

其中： core/ daemon/ data/ input/ provider/ ui/ utils/

键盘相关代码主要位于： app/src/main/java/org/fcitx/fcitx5/android/input/keyboard/

例如： BaseKeyboard.kt CommonKeyActionListener.kt CustomGestureView.kt KeyAction.kt KeyActionListener.kt KeyDef.kt KeyDefPreset.kt KeyDrawable.kt KeyView.kt KeyboardWindow.kt LangSwitchBehavior.kt NumberKeyboard.kt SpaceLongPressBehavior.kt SwipeSymbolDirection.kt TextKeyboard.kt

双拼提示实现

当前双拼提示主要涉及以下部分： KeyDef.kt KeyDefPreset.kt KeyView.kt DoublePinyin.kt

DoublePinyin.kt：负责保存双拼键位提示映射（例如 "Q" to "iu", "W" to "ia", ...）。

KeyDef.kt：为键盘按键定义增加双拼提示信息（val doublePinyinHint: String? = null）。

KeyDefPreset.kt：在创建字母键时读取对应的双拼提示（doublePinyinHint = DoublePinyin.Xiaohe.getHint(character)）。

KeyView.kt：负责将双拼提示显示在键盘按键上。

整個功能的结构大致为：

DoublePinyin.kt │ ▼ KeyDefPreset.kt │ ▼ KeyDef.kt │ ▼ KeyView.kt │ ▼ 键盘显示 

本地构建

环境要求

项目使用 Gradle 构建 Android APK。推荐使用：

JDK 17

Android SDK

Android NDK / CMake

Gradle Wrapper

具体版本以项目当前 Gradle 配置为准。

克隆项目

git clone --recursive [https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid.git](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid.git) cd fcitx5-android-Smart-Hybrid 

如果已经克隆但没有获取子模块：

git submodule update --init --recursive 

构建 Debug APK

./gradlew :app:assembleDebug 

生成的 APK 位于：app/build/outputs/apk/debug/

构建 Release APK

./gradlew :app:assembleRelease 

生成的 APK 位于：app/build/outputs/apk/release/

GitHub Actions 构建

项目提供 GitHub Actions 工作流。构建流程大致为： Push / 手动运行 ➔ Checkout ➔ Setup JDK ➔ Setup Android SDK ➔ Install build dependencies ➔ Gradle Build ➔ Release APK ➔ GitHub Actions Artifact

当前工作流位于：.github/workflows/

APK 签名

项目支持通过 GitHub Actions Secrets 对 Release APK 进行签名。目前使用的环境变量包括：

SIGN_KEY_BASE64（Base64 编码后的 JKS 签名文件）

SIGN_KEY_PWD（签名密钥库密码）

SIGN_KEY_ALIAS（签名密钥别名）

签名文件以及密码不应直接提交到 Git 仓库。

发布与开发流程

推荐的发布流程

修改代码 ➔ Commit ➔ Push ➔ GitHub Actions ➔ Build Release APK ➔ APK 签名 ➔ GitHub Release ➔ 用户下载 APK

开发流程

这个项目主要采用 GitHub + GitHub Actions + Android 手机测试 进行开发：

修改源码

Commit

Push 到 GitHub

GitHub Actions 自动构建

下载 APK

Android 手机上安装测试

根据测试结果继续修改

这样可以不依赖本地电脑完成主要开发流程。

当前开发状态

已完成 / 当前代码中

基于 Fcitx5 Android

保留原有多语言输入框架

Android 键盘基础功能

小鹤双拼键位提示 UI

双拼提示数据独立管理

GitHub Actions 自动构建

Release APK 签名支持

正在开发 / 后续计划

完整小鹤双拼输入

双拼候选处理

双拼 / 全拼混合输入

更完善的拼音输入

智能纠错

错误输入猜测

语音输入

更多移动端输入体验优化

注意事项

1. 目前的双拼提示不是完整双拼输入

当前版本最重要的一点：看到键盘上的双拼提示，并不代表当前输入法已经可以直接使用小鹤双拼输入中文。 目前主要是帮助用户熟悉键位映射。真正的双拼输入逻辑仍然需要后续开发。

2. 项目处于开发阶段

由于这是一个持续开发中的个人分支，功能、UI、配置、APK 签名可能发生变化，部分功能可能暂时不稳定。请根据自己的需求选择是否安装测试版本。

问题反馈

如果发现问题，可以在 GitHub Issues 中提交： https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/issues

提交问题时建议包含：

Android 版本：

手机型号：

APK 版本：

输入法配置：

问题描述：

复现步骤：

日志：

如果是构建问题，也可以附上 GitHub Actions 的失败日志。

贡献

欢迎提交：

Bug 修复

功能改进

UI 改进

输入方案

双拼相关功能

文档改进

测试反馈

如果涉及较大的功能修改，建议先通过 Issue 讨论。

许可证

本项目基于 Fcitx5 Android。 Fcitx5 Android 以及相关组件的许可证信息请以各自源代码中的 SPDX 标识以及 LICENSE 文件为准。本项目新增或修改的代码应遵循其对应源文件声明的许可证。

请在修改和重新发布时保留原项目的版权声明以及许可证信息。

致谢

感谢 Fcitx5 Android 项目以及所有 Fcitx5 相关项目的贡献者。

上游项目： https://github.com/fcitx5-android/fcitx5-android

Fcitx5： https://github.com/fcitx/fcitx5

English

Introduction

Fcitx5 Android Smart Hybrid is a personal development fork based on Fcitx5 Android.

The project explores a more flexible Android input experience while keeping the existing Fcitx5 Android framework, multilingual input support, and plugin architecture.

The main development directions include:

Xiaohe double-pinyin

Hybrid double-pinyin / full-pinyin input

Full-pinyin input

Intelligent typo correction

Input guessing

Voice input

More informative keyboard hints

Other improvements for mobile input

The project is currently under active development.

Current Version

v0.2 Development

The current development focus is double-pinyin keyboard hints.

The keyboard displays a Xiaohe double-pinyin hint below alphabet keys. For example:

┌─────┐ │ Q │ │ iu │ └─────┘ 

Other keys display their corresponding hints. For example:

Q → iu W → ia E → ua R → uan T → ue ... 

Important

The current implementation is primarily a visual keyboard hint. The keyboard still uses the existing input behavior.

In other words: The current version displays double-pinyin hints, but it does not yet implement complete double-pinyin input.

Actual double-pinyin input and hybrid double-pinyin / full-pinyin input are planned for future development.

Project Goals

The long-term goal is to provide several input modes within the same input method:

Android Keyboard │ ┌────┴────┬───────────┐ │ │ │ ▼ ▼ ▼ Full Pinyin Double Pinyin Hybrid │ │ │ └────┬────┴───────────┘ ▼ Candidate / Correction │ ▼ Chinese Input 

The goal is not simply to add another input method, but to allow different input habits to coexist naturally.

Planned Features

The following features are planned and are not necessarily implemented in the current version.

1. Xiaohe Double Pinyin

Planned support includes:

Double-pinyin key mapping

Initial input

Final input

Double-pinyin candidates

Double-pinyin dictionary support

Double-pinyin state handling

2. Full Pinyin

Traditional full-pinyin input will remain available (e.g., inputting nihao to get 你好).

3. Hybrid Double Pinyin / Full Pinyin

The project plans to allow different input methods to be used within the same input session (e.g., full pinyin + double pinyin or double pinyin + full pinyin). The exact input rules are still under development.

4. Intelligent Correction

Possible future improvements include:

Pinyin typo correction

Double-pinyin key mistakes

Adjacent-key mistakes

Common pinyin errors

Candidate correction

Context-aware input guessing

5. Voice Input

Voice input is planned for a future version. The exact speech recognition implementation and services will be determined during development.

6. Keyboard Hints

Future versions may provide additional hints such as:

Input mode indicators

Input state

Shortcut hints

Special-key hints

User-defined key hints

Download

GitHub Releases

Release APKs will be published on GitHub Releases: GitHub Releases

If no Release is available yet, APKs can also be obtained from GitHub Actions artifacts.

GitHub Actions

The project supports automated APK builds through GitHub Actions:

A build can be triggered by pushing to the master branch or manually from GitHub Actions.

The resulting APK is uploaded as a GitHub Actions artifact.

Upstream Project

This project is based on Fcitx5 Android.

Upstream repository: https://github.com/fcitx5-android/fcitx5-android

This repository is an independent development fork focused on personal experimentation and additional features. The basic Android input method framework and a large amount of the existing implementation come from Fcitx5 Android.

For the original Fcitx5 Android project, please visit the upstream repository.

Existing Features

This project inherits the basic input method framework from Fcitx5 Android. The inherited functionality includes:

Android input method service

Fcitx5 input method core

Multilingual input support

Keyboard input

Input method switching

Input method configuration

Fcitx5 plugin support

Input method engines

Actual functionality depends on the current project version, enabled plugins, and configuration.

Supported Languages

Because this project is based on Fcitx5 Android, it can use the input methods and language engines supported by the Fcitx5 Android framework. Actual available input methods depend on:

Installed input method engines

Enabled plugins

Input method configuration

Current project version

Adding Chinese double-pinyin support does not remove the existing multilingual input framework.

Development

Project Structure

The main Android source code is located at: app/src/main/java/org/fcitx/fcitx5/android/

Main packages include: core/ daemon/ data/ input/ provider/ ui/ utils/

Keyboard-related code is mainly located at: app/src/main/java/org/fcitx/fcitx5/android/input/keyboard/

Important files include: BaseKeyboard.kt CommonKeyActionListener.kt CustomGestureView.kt KeyAction.kt KeyActionListener.kt KeyDef.kt KeyDefPreset.kt KeyDrawable.kt KeyView.kt KeyboardWindow.kt LangSwitchBehavior.kt NumberKeyboard.kt SpaceLongPressBehavior.kt SwipeSymbolDirection.kt TextKeyboard.kt

Double-Pinyin Hint Implementation

The current double-pinyin hint implementation mainly involves: KeyDef.kt KeyDefPreset.kt KeyView.kt DoublePinyin.kt

DoublePinyin.kt: Stores the double-pinyin hint mapping (e.g., "Q" to "iu", "W" to "ia", ...).

KeyDef.kt: Provides a field for the double-pinyin hint (val doublePinyinHint: String? = null).

KeyDefPreset.kt: Reads the corresponding hint when creating alphabet keys (doublePinyinHint = DoublePinyin.Xiaohe.getHint(character)).

KeyView.kt: Displays the hint on the keyboard key.

The current architecture is approximately:

DoublePinyin.kt │ ▼ KeyDefPreset.kt │ ▼ KeyDef.kt │ ▼ KeyView.kt │ ▼ Keyboard UI 

Building Locally

Requirements

The project uses Gradle to build the Android application. Recommended environment:

JDK 17

Android SDK

Android NDK / CMake

Gradle Wrapper

Exact versions are determined by the project's current Gradle configuration.

Clone the Repository

git clone --recursive [https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid.git](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid.git) cd fcitx5-android-Smart-Hybrid 

If the repository has already been cloned:

git submodule update --init --recursive 

Build Debug APK

./gradlew :app:assembleDebug 

The APK will be generated under: app/build/outputs/apk/debug/

Build Release APK

./gradlew :app:assembleRelease 

The APK will be generated under: app/build/outputs/apk/release/

GitHub Actions Build

The project provides GitHub Actions workflows. The general build process is: Push / Manual Trigger ➔ Checkout ➔ Setup JDK ➔ Setup Android SDK ➔ Install Build Dependencies ➔ Gradle Build ➔ Release APK ➔ GitHub Actions Artifact

The workflows are located under: .github/workflows/

APK Signing

The project supports signing Release APKs through GitHub Actions Secrets. The current signing environment variables include:

SIGN_KEY_BASE64 (Base64-encoded JKS keystore)

SIGN_KEY_PWD (Keystore password)

SIGN_KEY_ALIAS (Signing key alias)

Signing files and passwords should never be committed directly to the repository.

Release & Development Workflow

Release Process

The intended release process is: Modify Source ➔ Commit ➔ Push ➔ GitHub Actions ➔ Build Release APK ➔ Sign APK ➔ GitHub Release ➔ Download APK

Development Workflow

The project is primarily developed using GitHub + GitHub Actions + Android device testing:

Modify source code

Commit changes

Push to GitHub

GitHub Actions builds the APK

Download the APK

Install and test it on Android

Continue development based on the test results

Development Status

Currently implemented / available in the codebase

Based on Fcitx5 Android

Existing multilingual input framework

Android keyboard functionality

Xiaohe double-pinyin keyboard hints

Separate double-pinyin hint mapping

GitHub Actions build support

Release APK signing support

Planned / Future Development

Complete Xiaohe double-pinyin input

Double-pinyin candidate handling

Double-pinyin / full-pinyin hybrid input

More complete pinyin input

Intelligent typo correction

Input guessing

Voice input

Further mobile input improvements

Important Notes

1. The Current Double-Pinyin Hint Is Not Full Double-Pinyin Input

The most important distinction in the current version is: The double-pinyin hints displayed on the keyboard do not mean that full Xiaohe double-pinyin input is already implemented. The current feature is mainly intended to help users learn key mapping. The actual double-pinyin input engine still needs to be implemented.

2. Development Status

Since this is a continuously developed fork, features, UI, configurations, and APK signing details may change, and some features may be unstable during development. Use development builds according to your own needs.

Issue Reporting

Please submit issues through GitHub Issues: https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/issues

When reporting an issue, please provide:

Android version:

Device:

APK version:

Input method configuration:

Problem description:

Steps to reproduce:

Logs:

For build failures, GitHub Actions logs are also useful.

Contributing

Contributions are welcome, including:

Bug fixes

Feature improvements

UI improvements

Input schemes

Double-pinyin features

Documentation

Testing and feedback

For larger changes, discussing the idea in an Issue before implementation is recommended.

License

This project is based on Fcitx5 Android. The licenses of Fcitx5 Android and its related components should be determined from their respective source files, SPDX identifiers, and LICENSE files. New or modified code in this project should follow the license declared by the corresponding source file.

Please retain the original copyright notices and license information when modifying or redistributing the project.

Acknowledgements

Special thanks to the Fcitx5 Android project and all contributors to the Fcitx5 ecosystem.

Upstream project: https://github.com/fcitx5-android/fcitx5-android

Fcitx5: https://github.com/fcitx/fcitx5

