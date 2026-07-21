# 图像工具适配

工具语法变化快。先确认用户使用的平台和版本；无法确认时输出平台无关提示词，不猜测参数。

## Midjourney

- 把主体、空间和材料放在提示词前部。
- 仅在确认支持时追加宽高比、风格化和排除参数。
- 常见写法示例：`--ar 16:9`、`--style raw`、`--no text, watermark`。
- 不默认添加版本参数。用户指定版本时再使用对应语法。
- 参考图任务中说明图像承担的是构图、体量、材质还是风格参考。

## OpenAI Images

- 使用完整自然语言描述目标图像和编辑边界。
- 编辑任务明确列出必须保持不变的内容，例如相机、主体位置、开口和文字。
- 需要透明背景、指定尺寸或高保真编辑时，作为独立要求写明。
- 不附加 Midjourney 风格的双连字符参数。

## FLUX 与通用扩散模型

- 主提示词使用具体可见特征，负面提示词单独列出。
- 图生图任务说明结构保持强度、允许变化范围和目标材质。
- 采样器、步数、引导强度和尺寸属于运行环境参数；用户未说明界面或模型版本时不要编造推荐值。
- 使用 ControlNet、深度图或边缘控制时，明确控制的是体量、透视还是轮廓。

## 草图转效果图平台

把约束分成两类：

```text
必须保持：体量、层数、开口位置、道路边界、相机透视
允许变化：材料、植被、天空、人物、灯光、细部丰富度
```

输出前提醒用户检查平台是否会裁切输入图、重置宽高比或自动改变透视。

## 通用负面约束

按任务选择，不要全部堆叠：

```text
distorted perspective, warped structure, duplicate columns, floating elements,
impossible stairs, inconsistent window rhythm, excessive reflections,
oversaturated vegetation, illegible signage, watermark, text artifacts
```
