---
name: day-to-night-rain
description: Restyle daytime real photos into cinematic night or rainy images with reference-locked prompts. Use for turning a photo into a night scene, adding rain, or reusing this grading recipe. Do not use for from-scratch generation.
---

# Day to Night / Rain Restyle

把白天实景照片改造成电影级夜景或雨夜照片。核心矛盾是「改光照但不改构图」，所以提示词必须先锁定构图，再描述光照。

## 工作流

1. 确认源照片路径，读取图片，确认主体元素（建筑形态、前景、地面类型）。这些名词后面要写进锁定句。
2. **夜景第一遍**：以源照片为参考图，使用 `references/prompt-templates.md` 的夜景主提示词，参考强度 0.55–0.65。
3. **检查**：构图是否被重画、是否多出月亮、玻璃是否被刷成纯黑。任一失败按下方「失败修复」处理后再进下一步。
4. **雨夜第二遍**（仅在用户要求雨夜时）：以夜景结果为参考图，追加雨夜增量提示词，参考强度降到 0.35，只加天气层，不改建筑。
5. 批量处理时逐张串行调用，不要并行，避免参考图串位。

## 失败修复

| 症状 | 处理 |
|---|---|
| 建筑被重画、机位变了 | 参考强度提到 0.7，并在开头补「仅改变光照与天气，建筑轮廓与元素位置完全不动」 |
| 多出月亮 | 正向和负向都加 `no moon`。正向必须显式写，只写负向不够 |
| 玻璃变成纯黑块 | 加 `glass lit from inside with cool cyan-white light`，这是唯一有效的修法 |
| 画面像滤镜、不像夜景 | 补「纵向亮度渐变」：天空暗、天际线亮、前景暗。这是最常被漏掉的一层 |
| 雨夜出现双重曝光 | 说明做成了「原图直接加雨」，应改为以夜景成片为参考的第二遍生成 |

## 工具参数

| 工具 | 设置 |
|---|---|
| 即梦 / 万相 | 图生图，参考强度 0.55–0.65 |
| Midjourney | `--iw 1.4` 到 `--iw 1.8`，`--ar 16:9 --style raw --s 100` |
| Flux / SDXL | denoise 0.45–0.55，CFG 3.5–4.5；二次加雨 denoise 0.35 |
| GPT-Image / Nano Banana | 先传原图，第一句写「保持构图，只改光照」 |

## 提示词模板

完整英文版、中文版、负向提示词、变量替换表见 `references/prompt-templates.md`。按需读取，不要全文复述给用户。

## 交付检查

- 原图机位、透视、主体元素位置一致
- 无新增月亮、无新增前景植被、无新增人物
- 玻璃内部有冷色内光，不是纯黑
- 地面倒影为竖向拉长，不是镜面平铺
- 若用户后续要把成图做成 2.5D 推镜视频，提醒每张图的灭点需要单独设，不能共用一个值
