# CW 摩斯密码闪卡

> 一款基于 **科赫法（Koch Method）** 的摩尔斯电码学习 App，通过闪卡 + 音频的方式高效练习 CW 抄报。

**版本**：V1.5 | **作者**：BG4KRL

---

## 演示地址

https://morse.04091020.xyz/

## ✨ 功能特性

### 📚 科赫法练习
按照经典的 Koch 学习顺序，将 36 个字符（26 字母 + 10 数字 + 4 符号）分成 12 组，由浅入深逐步解锁：

| 组别 | 字符 |
|------|------|
| 第 1 组 | K, M |
| 第 2 组 | R, S, U |
| 第 3 组 | A, P, T, L |
| 第 4 组 | O, W |
| 第 5 组 | I, ., N |
| 第 6 组 | J, E, 1, F |
| 第 7 组 | 0, Y, V |
| 第 8 组 | ,, G, 5, / |
| 第 9 组 | Q, 9, Z, H |
| 第 10 组 | 3, 8, B, ? |
| 第 11 组 | 4, 2, 7, C |
| 第 12 组 | 1, D, 6, X |

- **看字猜码**：显示字符，猜对应的摩尔斯电码
- **看码猜字**：显示摩尔斯电码，猜对应字符
- 点击卡片翻转查看答案，翻卡时可自动播放摩尔斯码音频
- 支持组内随机换题，学习进度本地持久化保存

### 🎲 随机练习
在全量 36 个字符中随机出题，适合已学完全部字符后的巩固练习。

### 📖 摩尔斯码参考表
完整的字母、数字、符号摩尔斯码对照表，**点击任意字符即可播放**对应的摩尔斯音频，随时查阅和听辨。

### ⚙️ 个性化设置
- **发报速度**：5 ~ 30 WPM 可调，步进 1 WPM
- **侧音音调**：400 ~ 1000 Hz 可调，步进 10 Hz
- **翻卡自动播放**：开启后翻到答案自动播放摩尔斯码
- **主题切换**：黑白极简 / 彩色圆角，两种风格自由切换

### 🔊 音频引擎
采用 Web Audio API 实现，参考 [lcwo.net/jscwlib](https://lcwo.net/jscwlib) 方案：
- 单一持续振荡器 + 增益键控（Gain Keying），避免 Android/iOS 上的音频爆音
- 低通滤波器平滑音色，听感更纯净
- 无需加载任何外部音频文件，零延迟即时发声

---

## 🛠 技术栈

| 层级 | 技术 |
|------|------|
| 前端界面 | 纯 HTML / CSS / JavaScript（单文件，无框架依赖） |
| 音频引擎 | Web Audio API（Oscillator + GainNode + BiquadFilter） |
| 移动打包 | [Capacitor](https://capacitorjs.com/) v8.3.4 |
| 平台 | Android（APK），浏览器直接访问 |

---

## 📁 项目结构

```
morse_flashcard/
├── www/
│   └── index.html        # 主应用（单文件，所有逻辑在此）
├── android/               # Capacitor Android 原生工程
│   └── app/
│       └── src/main/
│           ├── assets/public/index.html  # 打包进 APK 的 Web 资源
│           └── java/com/morse/flashcard/MainActivity.java
├── capacitor.config.json  # Capacitor 配置
└── package.json
```

---

## 🚀 快速开始

### 浏览器直接运行

无需安装任何依赖，直接用浏览器打开：

```
www/index.html
```

### 开发调试

推荐使用本地 HTTP 服务器：

```bash
# Python
python -m http.server 8080 -d www

# Node.js
npx serve www
```

然后在浏览器访问 `http://localhost:8080`

---

## 📱 打包 Android APK

### 环境要求

- Node.js ≥ 18
- Android Studio（含 Android SDK）
- Java JDK 17+

### 步骤

```bash
# 1. 安装依赖
npm install

# 2. 同步 Web 资源到 Android 工程
npx cap sync

# 3. 用 Android Studio 打开工程
npx cap open android

# 4. 在 Android Studio 中：
#    - Build → Build Bundle(s) / APK(s) → Build APK(s)
#    - APK 输出路径：android/app/build/outputs/apk/
```

---

## 🎯 使用建议

1. **初学者**：从科赫法第 1 组（K, M）开始，先熟悉 2 个字符，逐步推进
2. **建议速度**：初学设置 15 WPM，熟练后逐步提高至 20 WPM 以上
3. **翻卡自动播放**：强烈建议开启，建立"听-看"联觉记忆
4. **每日练习**：每组建议练习至正确率 > 90% 再进入下一组
5. **参考表**：遇到不确定的字符，随时查阅参考表并点击听音

---

## 📄 License

MIT License

---

## 📡 联系

- 呼号：**BG4KRL**
- 欢迎 Ham 友提 Issue 或 PR 共同完善！

---

*73！祝你 CW 之路愉快！*
