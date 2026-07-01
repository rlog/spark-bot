# SparkBot Task Backlog

本文档是 SparkBot 仓库的可执行任务清单。AI Agent 应按任务逐步推进，每个任务尽量对应一个清晰 commit。

## 阶段说明

| 阶段 | 目标 |
| --- | --- |
| P0 | 项目规范、资料索引、路线图 |
| P1 | 增强版 BOM、采购风险、Component Cards |
| P2 | 硬件装配、首次上电、故障树 |
| P3 | ESP-IDF、官方固件编译烧录 |
| P4 | 自定义固件 SparkBot OS |
| P5 | 桌面控制台和 AI Agent 联动 |

---

# P0：项目规范与资料基础

## T0001: 完善项目总览

阶段：P0  
类型：docs  
产出文件：`docs/01-overview.md`

要求：

- [ ] 说明项目定位。
- [ ] 说明官方资料源。
- [ ] 说明复刻资料源。
- [ ] 说明当前阶段。
- [ ] 标记未验证内容。

建议 Commit：

```text
docs(overview): expand project overview
```

## T0002: 建立资料索引

阶段：P0  
类型：docs  
产出文件：`docs/02-source-index.md`

要求：

- [ ] 收录官方开源项目页。
- [ ] 收录复刻教程站点。
- [ ] 收录固件源码仓库。
- [ ] 收录结构文件来源。
- [ ] 标注每个资料的可信度和用途。

建议 Commit：

```text
docs(source): add source index
```

## T0003: 建立版本历史文档

阶段：P0  
类型：analysis  
产出文件：`docs/03-version-history.md`

要求：

- [ ] 记录 V1.0 / V1.1 / V1.2 差异。
- [ ] 标注官方明确说明和工程推测。
- [ ] 列出需要原理图验证的点。

建议 Commit：

```text
analysis(version): document SparkBot version history
```

## T0004: 建立项目架构文档

阶段：P0  
类型：docs  
产出文件：`docs/04-project-architecture.md`

要求：

- [ ] 用 Mermaid 画出模块图。
- [ ] 说明 ESP32-S3 与 LCD、Camera、Audio、Motion 的关系。
- [ ] 标记每个模块对应的后续文档。

建议 Commit：

```text
docs(architecture): add system architecture map
```

---

# P1：增强版 BOM 与 Component Cards

## T0101: 扩展增强版 BOM

阶段：P1  
类型：docs  
产出文件：`docs/04-enhanced-bom.md`

要求：

- [ ] 按模块整理器件。
- [ ] 标记采购优先级。
- [ ] 标记风险等级。
- [ ] 标记是否必须原型号。
- [ ] 标记待确认项目。

建议 Commit：

```text
docs(bom): expand enhanced BOM
```

## T0102: ESP32-S3 Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/esp32-s3.md`

要求：

- [ ] 说明 ESP32-S3 在 SparkBot 中的作用。
- [ ] 说明为什么适合桌面机器人。
- [ ] 说明 Wi-Fi、USB、Camera、LCD、I2S 关系。
- [ ] 标注待核对的官方型号。

建议 Commit：

```text
docs(component): add ESP32-S3 component card
```

## T0103: ES8311 Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/es8311.md`

要求：

- [ ] 说明 ES8311 是什么。
- [ ] 说明它在音频系统中的作用。
- [ ] 说明与 I2S、麦克风、扬声器的关系。
- [ ] 记录 V1.2 与 ES8311 修改相关。
- [ ] 标注哪些结论需要原理图验证。

建议 Commit：

```text
docs(component): add ES8311 component card
```

## T0104: BMI270 Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/bmi270.md`

要求：

- [ ] 说明 BMI270 是 IMU。
- [ ] 说明 SparkBot 中可能用于动作/姿态感知。
- [ ] 记录误买 BMI220 风险。
- [ ] 给出采购核对建议。

建议 Commit：

```text
docs(component): add BMI270 component card
```

## T0105: LCD Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/lcd.md`

要求：

- [ ] 说明 LCD 作用。
- [ ] 说明 SPI/LVGL/DMA 基本关系。
- [ ] 说明首次验证目标：背光和第一帧。
- [ ] 列出黑屏可能原因。

建议 Commit：

```text
docs(component): add LCD component card
```

## T0106: Camera Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/camera.md`

要求：

- [ ] 说明摄像头用途。
- [ ] 说明与 ESP32-S3 Camera 接口关系。
- [ ] 说明排线和初始化风险。
- [ ] 定义首次验证标准：成功采集一帧。

建议 Commit：

```text
docs(component): add camera component card
```

## T0107: Power System Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/power-system.md`

要求：

- [ ] 说明电源系统为什么优先级最高。
- [ ] 说明 USB、电池、3.3V 的关系。
- [ ] 提供首次上电前检查清单。
- [ ] 标记供电不足可能导致 Wi-Fi/Camera 重启。

建议 Commit：

```text
docs(component): add power system component card
```

## T0108: Speaker Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/speaker.md`

要求：

- [ ] 说明扬声器作用。
- [ ] 说明与功放/codec 的关系。
- [ ] 说明常见故障：无声、卡顿、破音、底噪。

建议 Commit：

```text
docs(component): add speaker component card
```

## T0109: Battery Component Card

阶段：P1  
类型：docs  
产出文件：`docs/component-cards/battery.md`

要求：

- [ ] 说明电池作用。
- [ ] 说明为什么首次调试不建议先接电池。
- [ ] 说明容量、放电能力、接口、尺寸需要核对。

建议 Commit：

```text
docs(component): add battery component card
```

---

# P2：Bring-up 与 Failure Cases

## T0201: 首次上电检查清单

阶段：P2  
类型：hardware  
产出文件：`docs/06-first-bringup.md`

要求：

- [ ] 说明不要一上来接电池。
- [ ] 说明万用表短路检查。
- [ ] 说明 USB 供电检查。
- [ ] 说明 3.3V 检查。
- [ ] 说明异常发热处理。

建议 Commit：

```text
docs(bringup): add first power-on checklist
```

## T0202: 黑屏故障树

阶段：P2  
类型：docs  
产出文件：`docs/failure-cases/001-black-screen.md`

要求：

- [ ] 区分背光亮/不亮。
- [ ] 区分未刷机/刷机失败/驱动问题/排线问题/供电问题。
- [ ] 给出最小排查流程。

建议 Commit：

```text
docs(failure): add black screen troubleshooting tree
```

## T0203: USB 无法识别故障树

阶段：P2  
类型：docs  
产出文件：`docs/failure-cases/002-usb-not-detected.md`

要求：

- [ ] 区分线材、驱动、BOOT 模式、焊接、电源问题。
- [ ] 给出 Windows/macOS/Linux 基础检查方式。

建议 Commit：

```text
docs(failure): add USB not detected troubleshooting
```

## T0204: 重启故障树

阶段：P2  
类型：docs  
产出文件：`docs/failure-cases/003-random-reset.md`

要求：

- [ ] 说明供电不足、Wi-Fi 峰值电流、Camera、Brownout 的关系。
- [ ] 给出串口日志关键词。

建议 Commit：

```text
docs(failure): add random reset troubleshooting
```

---

# P3：Knowledge Base

## T0301: SPI Knowledge

阶段：P3  
类型：docs  
产出文件：`docs/knowledge/spi.md`

要求：

- [ ] 解释 SPI 是什么。
- [ ] 说明为什么屏幕常用 SPI。
- [ ] 说明与 DMA、刷新率的关系。
- [ ] 说明在 SparkBot 中的作用。

建议 Commit：

```text
docs(knowledge): explain SPI in SparkBot
```

## T0302: I2S Knowledge

阶段：P3  
类型：docs  
产出文件：`docs/knowledge/i2s.md`

要求：

- [ ] 解释 I2S 是什么。
- [ ] 说明为什么音频系统使用 I2S。
- [ ] 说明与 ES8311、麦克风、扬声器的关系。

建议 Commit：

```text
docs(knowledge): explain I2S audio path
```

## T0303: LVGL Knowledge

阶段：P3  
类型：docs  
产出文件：`docs/knowledge/lvgl.md`

要求：

- [ ] 解释 LVGL 的作用。
- [ ] 说明 draw buffer、flush callback、display driver。
- [ ] 说明屏幕刷新链路。

建议 Commit：

```text
docs(knowledge): explain LVGL rendering path
```

## T0304: DMA Knowledge

阶段：P3  
类型：docs  
产出文件：`docs/knowledge/dma.md`

要求：

- [ ] 解释 DMA 是什么。
- [ ] 说明为什么屏幕和音频需要 DMA。
- [ ] 说明与 CPU 占用的关系。

建议 Commit：

```text
docs(knowledge): explain DMA basics
```

---

# P4：Design Review

## T0401: V1.2 ES8311 Change Review

阶段：P4  
类型：analysis  
产出文件：`docs/design-review/v1-2-es8311-change.md`

要求：

- [ ] 记录官方提到的 V1.2 变化。
- [ ] 分析可能原因。
- [ ] 明确哪些是推测。
- [ ] 列出验证计划。

建议 Commit：

```text
analysis(audio): review V1.2 ES8311 change
```

## T0402: Power Architecture Review

阶段：P4  
类型：analysis  
产出文件：`docs/design-review/power-architecture.md`

要求：

- [ ] 分析 USB、电池、3.3V 供电链路。
- [ ] 记录潜在电流峰值问题。
- [ ] 给出调试建议。

建议 Commit：

```text
analysis(power): review SparkBot power architecture
```

---

# P5：Experiments

## T0501: LCD First Frame Experiment

阶段：P5  
类型：experiment  
产出文件：`docs/experiments/exp001-lcd-first-frame.md`

要求：

- [ ] 定义实验目标。
- [ ] 定义硬件环境。
- [ ] 定义固件最小代码目标。
- [ ] 定义成功标准。

建议 Commit：

```text
experiment(display): add LCD first frame test plan
```

## T0502: Audio Playback Experiment

阶段：P5  
类型：experiment  
产出文件：`docs/experiments/exp002-audio-playback.md`

要求：

- [ ] 定义播放测试音频目标。
- [ ] 定义 I2S/codec 验证路径。
- [ ] 记录无声/破音/卡顿排查方向。

建议 Commit：

```text
experiment(audio): add audio playback test plan
```

## T0503: Camera Capture Experiment

阶段：P5  
类型：experiment  
产出文件：`docs/experiments/exp003-camera-capture.md`

要求：

- [ ] 定义采集一帧图像目标。
- [ ] 记录初始化参数。
- [ ] 记录失败日志。

建议 Commit：

```text
experiment(camera): add camera capture test plan
```

---

# 推荐执行顺序

当前优先执行：

1. T0002
2. T0003
3. T0101
4. T0102
5. T0103
6. T0104
7. T0105
8. T0107
9. T0201
10. T0202

每完成一个任务，更新本文件对应 checkbox 或在相关 issue 中记录。