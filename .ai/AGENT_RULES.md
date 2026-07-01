# SparkBot AI Agent Rules

本文档给 Claude Code、Codex、Cursor Agent、Gemini CLI 等工具使用。

## 1. 工作目标

你的目标不是快速堆文件，而是持续把 `rlog/spark-bot` 变成一个高质量的 SparkBot 工程知识库。

每次修改都应该让仓库更可复刻、更可理解、更可维护。

## 2. 修改前必须阅读

每次开始任务前，先阅读：

1. `.ai/PROJECT.md`
2. `.ai/STYLE_GUIDE.md`
3. `.ai/DOC_TEMPLATE.md`
4. `.ai/TASKS.md`
5. 相关已有文档

## 3. 禁止行为

禁止：

- 生成大量空文件。
- 只创建标题和 TODO，没有正文。
- 编造器件型号、引脚、采购链接、官方结论。
- 把推测写成事实。
- 删除人工调试记录。
- 大范围重命名目录而不说明原因。
- 一次提交混入多个无关主题。
- 把官方内容大段复制到仓库而不做解释或归纳。

## 4. 必须行为

必须：

- 每篇文档说明状态：Draft / Verified / Needs Test / Inference。
- 不确定的地方写“待确认”。
- 关键结论标注来源类型。
- 每篇文档至少提供一个后续 TODO。
- 每次提交只围绕一个主题。
- Commit message 使用 `.ai/STYLE_GUIDE.md` 的格式。

## 5. 推荐工作流

### Step 1：选择任务

从 `.ai/TASKS.md` 选择一个任务。

### Step 2：读取相关文档

例如写 ESP32-S3 Component Card 时，先读取：

- `docs/04-enhanced-bom.md`
- `docs/01-overview.md`
- `.ai/DOC_TEMPLATE.md`

### Step 3：生成内容

使用模板生成完整初稿。

### Step 4：自检

检查：

- 是否有内容？
- 是否有 Why？
- 是否区分事实和推测？
- 是否有 TODO？
- 是否符合文件命名规则？

### Step 5：提交

使用规范 commit message。

## 6. 内容深度要求

### 不合格示例

```markdown
# SPI

SPI 是一种通信协议。
```

### 合格示例

```markdown
# Knowledge: SPI

SPI 是一种同步串行总线。在 SparkBot 中，它主要用于 LCD 显示屏通信。

相比 I2C，SPI 更适合屏幕，因为屏幕需要持续传输大量像素数据。代价是占用更多引脚，并且需要关注 DMA、刷新率和总线竞争。

状态：Draft
来源：通用嵌入式知识，待补 ESP-IDF 官方文档链接
```

## 7. 任务粒度

一个任务建议控制在 30~60 分钟内。

如果任务过大，应拆分。

例如不要一次写：

```text
完成所有 Component Cards
```

应该拆成：

```text
T0201: add ESP32-S3 component card
T0202: add ES8311 component card
T0203: add BMI270 component card
```

## 8. Review 标准

提交前确认：

- [ ] 文件路径正确。
- [ ] 文件名小写英文连字符。
- [ ] 没有编造事实。
- [ ] 没有过度空泛。
- [ ] 能帮助读者完成实际复刻或理解。
- [ ] 与已有文档不冲突。
- [ ] 有后续 TODO。

## 9. 如何处理不确定资料

不要停止写作。

可以这样写：

```text
官方页面提到 V1.2 修改了 ES8311 相关电路，但当前文档尚未核对原理图差异。
状态：Needs Test
来源：Official，待原理图验证
```

不要这样写：

```text
V1.2 一定是因为电源噪声导致的。
```

## 10. 推荐优先级

优先补：

1. P0 项目规范和资料索引。
2. P1 增强版 BOM 和高风险器件。
3. P1 Component Cards。
4. P2 首次上电检查。
5. P2 Failure Cases。
6. P3 固件编译与烧录。
7. P4 自定义固件和桌面端。