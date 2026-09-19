# Fcitx5 Android Smart Hybrid

[中文](#中文) | [English](#english)

---

## 中文

Fcitx5 Android 的增强版，基于 [Fcitx5 for Android](https://github.com/fcitx5-android/fcitx5-android) 开发。

本项目主要针对 Android 中文输入体验进行改进，并探索更加灵活的**双拼 / 全拼混合输入**方案。

### 当前功能

- **小鹤双拼按键提示**
  - 在键盘字母按键下方显示对应的双拼提示。
  - 例如：
    - `Q` → `iu`
    - `W` → `ia`
    - `E` → `ua`
  - 当前版本的双拼提示主要用于视觉辅助，暂时不会改变按键本身的输入行为。

### 计划中的功能

项目后续计划逐步加入：

- 小鹤双拼输入
- 全拼输入
- 双拼 / 全拼混合输入
- 更自然的双拼与全拼切换
- 语音输入
- 拼写错误猜测与纠正
- 进一步优化 Android 中文输入体验

> 除非明确标记为“当前功能”，否则上述功能均属于开发计划。

### 下载

可以从 [GitHub Releases](https://github.com/n62292291-star/fcitx5-android-Smart-Hybrid/releases/latest) 下载最新 APK。

> [!NOTE]
> 本项目是独立维护的 Fcitx5 Android 分支，APK 使用独立的签名证书。
>
> 因此，本项目 APK 与官方 Fcitx5 Android APK 应视为不同的应用构建版本。

### 项目目标

本项目希望在保留 Fcitx5 Android 原有架构和多语言支持的基础上，进一步改善 Android 上的中文输入体验。

主要发展方向：

```text
当前
 │
 ├─ Fcitx5 Android 基础功能
 │
 └─ 小鹤双拼按键提示
       │
       ▼
下一阶段
 │
 ├─ 双拼输入
 ├─ 全拼输入
 └─ 双拼 / 全拼混合输入
       │
       ▼
后续
 │
 ├─ 语音输入
 └─ 错字猜测 / 自动纠正