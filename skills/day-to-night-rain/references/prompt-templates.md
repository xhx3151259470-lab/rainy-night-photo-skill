# 提示词模板

`{}` 为待替换槽位，替换表在文末。

## 1. 快速版（先做一次试生成）

```
cinematic night photography, same composition as reference, deep blue-violet sky, warm golden windows, wet reflective ground, teal and orange grade, film grain, no moon, no added people
```

## 2. 夜景主提示词（第一遍，英文）

```
{用途，如：校园夜景底图}：以<图片1>为唯一构图参考，严格保留原照片的机位、透视、建筑轮廓与所有元素位置（{主体元素1}、{主体元素2}、{前景元素}），仅把白天改为夜晚，不新增月亮，不新增前景植被。

Cinematic night photography: deep blue-violet twilight sky occupying the upper third, {窗户光形态} glowing warm golden in irregular rows, {玻璃/幕墙} lit from inside with cool cyan-white light, warm amber street lamps and path lights, {地面} dark and wet with long vertical stretched reflections, distant city lights as small warm points along the horizon.

Teal-and-orange color grade, cool blue shadows against warm amber highlights, vertical brightness gradient from dark sky to bright skyline to dark foreground, medium-high contrast, rich but controlled saturation, subtle film grain, soft natural vignette (bright center, darker edges), slight bloom around every light source. Realistic architectural photography, full-frame camera 24-70mm f/2.8, high detail, photorealistic, no text, no watermark, no added people.
```

## 3. 雨夜增量（第二遍，英文）

```
Heavy steady rain: dense fine diagonal rain streaks across the whole frame, raindrops lit gold as they pass in front of the glowing windows; the ground is completely soaked into a dark mirror with long amber light streaks smeared across it, shallow puddles showing concentric ripple rings; every surface is glossy — water runs down the glass panels, beads on branches, streaks down the metal skin; low mist drifting near the ground, each lamp wrapped in a warm halo, distant skyline blurred into scattered warm bokeh through the rain haze.
```

## 4. 中文夜景版

```
电影级夜景摄影，以参考图为准严格保留机位、透视与建筑轮廓，只把白天改为夜晚。画面上部是深蓝紫色夜空，中部建筑窗户成排透出暖金色灯光，玻璃幕墙内部透出冷青白光，路灯与庭院灯为暖琥珀色，地面深色湿亮并拉出竖向长条倒影，远处城市灯带点点散落。青橙分离调色，冷蓝阴影对暖琥珀高光，纵向由暗到亮再到暗的亮度渐变，中高对比，色彩浓郁但不过饱和，轻微胶片颗粒，自然暗角，灯光带柔和辉光。真实建筑摄影质感，全画幅 24-70mm f/2.8，高清细节，不出现文字、水印、新增人物。
```

## 5. 中文雨夜增量

```
叠加密集细雨：全画面斜向细密雨丝，经过灯光处被染成金色；地面被雨水浸透成深色镜面，拉出细长的暖色倒影，浅积水中有同心涟漪；所有表面湿亮，玻璃挂水痕，树枝挂水珠；地面浮着薄雾，每盏灯带柔和光晕，远处天际线在雨雾中化成散落的暖色光斑。
```

## 6. 负向提示词

```
cartoon, anime, illustration, 3d render, plastic look, oversaturated, flat lighting, daytime, blue sky, blown highlights, double exposure, ghosting, blurred architecture, distorted perspective, fisheye, extra moon, added people, text, watermark, logo
```

## 7. 变量替换表

| 槽位 | 可选内容 |
|---|---|
| 窗户光形态 | glowing warm golden in irregular rows / in continuous horizontal bands / only a few scattered rooms lit |
| 玻璃 幕墙 | central glass curtain wall / glass tower / arched glass corridor |
| 地面 | calm lake water / wet asphalt / wet stone paving / long staircase treads |
| 前景元素 | bare tree branches silhouetted / window frame with rain droplets / flagpole |
