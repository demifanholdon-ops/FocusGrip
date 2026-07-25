# FocusGrip「指哪爬哪」

**—— 坐不住了？来爬两条线！**

FocusGrip 是一款面向 ADHD 攀岩爱好者的沉浸式指力训练软硬件一体化装置，由硬件指力训练板、软件攀岩游戏、像素心流（Pixel Flow）多模态 ADHD 辅助检测系统与 Dot 墨水屏 AI 反馈终端共同构成，核心是一套三层 AI 智能感知与干预体系。

---

## 三层 AI 智能感知与干预体系

**第一层 · 桌面行为监测 AI（主动触发）**：后台监测鼠标空闲与娱乐软件使用时长，超 10 分钟自动弹出攀岩弹窗，一键进入游戏。

**第二层 · 像素心流多模态 AI 守护（无感监测）**：MediaPipe 本地推理（面部 468 点 / 手部 21 点 / 姿态 33 点），三通道融合建立 90 帧个人基线，MiMo API 生成非诊断建议，Dot 墨水屏温和呈现。

**第三层 · 指力攀岩游戏（主动训练）**：FSR 压力传感器 + ESP32-S3 驱动的握力控制攀岩游戏，力度窗口抓点 + 持续保持点（sloper），6 条难度递增路线 + 雷霆姿势解锁系统。

> 三层协同：桌面行为 AI 发现时机 → 像素心流温和提醒 → 攀岩游戏承接行动。用户可按需选择任一层进入。

---

## 项目结构

```
FocusGrip/
├── README.md                           # 本文件
├── game/
│   ├── focusgrip.html                  # 攀岩游戏（单文件，浏览器即开即玩）
│   ├── mqtt.min.js                     # MQTT 客户端（巴法云通信）
│   └── README_V1.5.md                  # V1.5 更新说明
├── docs/
│   ├── FocusGrip_PRD.md                # 产品需求文档
│   ├── FocusGrip_角色与物理设计文档.md   # 角色比例、Verlet 物理引擎设计
│   ├── FocusGrip_作品简介_500字.md       # 500 字作品简介
│   └── FocusGrip_作品详细介绍.md         # 完整作品详细介绍（~2800 字）
└── tech-docs/
    ├── 像素心流与 Dot（墨水屏）AI 建议推送技术文档.md  # 墨水屏 AI 推送技术方案
    └── ADHD辅助检测技术文档.md                        # MediaPipe 多模态 ADHD 检测
```

---

## 快速开始

### 攀岩游戏

直接用浏览器打开 `game/focusgrip.html` 即可运行。

- 按住**空格键**或**鼠标** = 用力
- 松开 = 泄力
- 把握力控制在绿色窗口内完成攀登
- 接入硬件：修改 `INPUT_MODE = 'network'` 和 `WS_URL` 连接 ESP32

### 像素心流 ADHD 检测

```bash
cd pixel-flow
pnpm install
pnpm run dev
```

浏览器打开 `http://localhost:8569/`，允许摄像头权限即可开始多模态监测。

---

## 技术栈

| 模块 | 技术 |
|------|------|
| 攀岩游戏 | HTML5 Canvas + Matter.js |
| 角色物理 | 自研 Verlet IK 求解器（7.5 头身） |
| 传感器通信 | ESP32-S3 + WebSocket / Web Serial |
| 像素心流前端 | React 19 + TypeScript + Vinext/Vite |
| 视觉识别 | MediaPipe Tasks Vision（Face/Hand/Pose Landmarker） |
| 压力信号 | Web Serial API / 巴法云 MQTT |
| AI 建议生成 | 小米 MiMo Chat Completions API (mimo-v2.5-pro) |
| 墨水屏推送 | MindReset Quote/0 (296×152) + Dot. OpenAPI |

---

## 目标用户

ADHD 人群 ∩ 攀岩爱好者 —— 在久坐场景中需要身体参与来回收注意力的人群。

---

## 设计理念

不"压抑"ADHD 特质，而是将分心冲动转化为游戏动力，将多余精力导向身体参与。休息不是什么都不做——是换一种方式做一件有意义的事。

---

## 关键词

ADHD · 攀岩指力训练 · 软硬件结合 · 桌面行为 AI · MediaPipe 多模态感知 · MiMo AI · Dot 墨水屏 · 像素心流 · 游戏化干预 · 注意力回收
