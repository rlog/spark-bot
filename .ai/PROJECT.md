# SparkBot Project Constitution

本文件定义 `rlog/spark-bot` 的长期项目方向。所有人类维护者和 AI Agent 在修改本仓库前，都应该先阅读本文件。

## 1. 项目定位

本项目不是普通的 ESP-SparkBot 复刻仓库。

本项目的目标是构建一个长期可维护、可学习、可复刻、可扩展的 SparkBot 工程知识库。

最终形态应该同时满足：

- 初学者可以照着完成硬件复刻。
- 嵌入式开发者可以理解 ESP32-S3 系统设计。
- 前端/全栈开发者可以理解机器人如何与桌面应用、AI Agent、云服务联动。
- AI Agent 可以持续扩充文档、任务、实验、代码和排障案例。

项目不是单纯追求“做出来”，而是追求“做出来，并真正理解为什么”。

## 2. 核心目标

### Goal 1：完成 SparkBot 复刻

覆盖：

- PCB
- BOM
- 外壳
- 焊接
- 首次上电
- 固件编译
- 固件烧录
- 基础功能验证

### Goal 2：理解系统设计

每个模块必须回答：

- What：它是什么？
- Why：为什么需要它？为什么官方这样设计？
- How：它如何工作？如何验证？
- Alternative：还有什么替代方案？如果重新设计会怎么做？

### Goal 3：发展 SparkBot OS

在官方固件跑通后，逐步形成自己的固件方向：

- display：屏幕和 UI
- audio：录音、播放、TTS
- vision：摄像头、图像识别
- motion：履带和运动控制
- network：Wi-Fi、HTTP、WebSocket、MQTT
- llm：大模型 API 适配
- config：配置管理
- plugin：插件机制
- agent：与桌面 AI Coding Agent 联动

### Goal 4：沉淀工程过程

所有踩坑、推测、验证、修复、实验都应该记录。

目标是让后来的复刻者：

- 不用反复看视频。
- 不用在群里重复问同样的问题。
- 不用靠猜测排障。
- 可以仅靠仓库完成整个项目。

## 3. 仓库哲学

本仓库不是“教程集合”，而是“工程知识库”。

文档不要只写操作步骤，更要写设计原因、风险、验证方式和替代方案。

禁止只写：

```text
焊接这个器件。
刷入这个固件。
连接这个接口。
```

必须补充：

```text
为什么是这个器件？
为什么这个接口容易出错？
如果失败会出现什么现象？
如何用万用表或日志验证？
有哪些替代方案？
```

## 4. 内容分层

仓库内容分为五层：

1. Quick Start：最快完成复刻。
2. Build Notes：硬件装配和调试记录。
3. Component Cards：每个器件的知识卡。
4. Knowledge Base：底层通用知识，如 SPI、I2S、DMA、LVGL。
5. Design Review / Experiments：设计分析和实验验证。

## 5. 目录约定

建议逐步形成以下目录：

```text
.ai/                    # AI Agent 规范、任务、模板
apps/                   # 桌面控制台、Web UI、调试工具
docs/                   # 主文档
  component-cards/      # 器件知识卡
  knowledge/            # 底层知识
  failure-cases/        # 故障案例
  design-review/        # 官方设计 Review
  experiments/          # 实验记录
  lessons/              # 课程式学习路径
firmware/               # ESP-IDF 固件
hardware/               # PCB、结构、装配、调试
scripts/                # 辅助脚本
```

## 6. 来源规则

所有关键结论必须标记来源类型：

- Official：来自官方项目页、官方仓库、官方原理图、官方 PCB、官方文档。
- Datasheet：来自芯片数据手册。
- Source Code：来自固件源码。
- Test：来自实际测量或实验。
- Inference：基于资料的工程推测。
- Unknown：暂未确认。

禁止把推测写成事实。

## 7. 质量标准

任何新增文档至少满足：

- 有明确目的。
- 有适用阶段。
- 有具体内容，不是空目录或空标题。
- 有后续 TODO。
- 能帮助后来的复刻者少踩一个坑。

理想标准：三年后重新阅读，仍然有价值。

## 8. AI Agent 工作原则

AI Agent 可以创建文件、整理文档、拆任务、生成模板、补充知识，但必须遵守：

- 不生成大量空文档。
- 不虚构官方资料。
- 不把未验证内容写成确定结论。
- 不删除人类记录的调试过程。
- 每次提交都应该围绕一个清晰主题。
- Commit message 必须可读、可追踪。

## 9. 当前项目阶段

当前阶段：P0 / P1

重点：

- 建立 AI Agent 可执行规范。
- 建立文档模板。
- 建立任务清单。
- 整理官方资料和复刻资料。
- 建立增强版 BOM。
- 开始 Component Cards。