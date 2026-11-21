# Rainy Night Photo Skill

把白天的实景照片改造成**电影级夜景 / 雨夜**照片。核心约束是「锁定构图，只改光照」，所以成果不会变成另一栋楼。

> 这不是插件，也不是代码。它是一个 Markdown 格式的 **Agent Skill** —— 任何能读取指令文件的 AI Agent 都能用，不绑定 Trae。

---

## 能力

| 输入 | 输出 |
|---|---|
| 白天实景照片 | 电影级夜景（蓝紫夜空 + 暖金窗光 + 湿地反射） |
| 夜景成片 | 雨夜版（雨丝 + 积水涟漪 + 雾气光晕） |
| 任意照片 | 青橙分离调色、胶片颗粒、自然暗角 |

内置 5 类常见故障的修复方案：构图被重画、多出月亮、玻璃变黑、像滤镜、雨夜双重曝光。

---

## 安装

Skill 的本质是「一个文件夹 + 一个 `SKILL.md`」。放到对应平台能识别的位置即可。

| 平台 | 放置位置 |
|---|---|
| Trae（项目级） | `<项目>/.trae/skills/day-to-night-rain/` |
| Trae（全局） | `~/.trae-cn/skills/day-to-night-rain/`（国际版为 `~/.trae/skills/`） |
| Claude Code | `~/.claude/skills/day-to-night-rain/` |
| Cursor | 放入 `.cursor/rules/`，或将 `SKILL.md` 内容并入 `AGENTS.md` |
| Codex CLI / 其他支持 AGENTS.md 的工具 | 将 `SKILL.md` 内容并入项目根的 `AGENTS.md` |
| 无技能机制的 Agent | 直接把 `SKILL.md` 全文粘进系统提示词或自定义指令 |

> 各平台的技能目录仍在演进，若上表路径失效，以对应平台的官方文档为准。规则本身与平台无关。

### 命令安装

```bash
git clone https://github.com/xhx3151259470-lab/rainy-night-photo-skill.git

# 以 Trae 全局安装为例
mkdir -p ~/.trae-cn/skills
cp -r rainy-night-photo-skill/skills/day-to-night-rain ~/.trae-cn/skills/
```

```powershell
git clone https://github.com/xhx3151259470-lab/rainy-night-photo-skill.git

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.trae-cn\skills" | Out-Null
Copy-Item -Recurse ".\rainy-night-photo-skill\skills\day-to-night-rain" "$env:USERPROFILE\.trae-cn\skills\"
```

---

## 不安装也能用

这个仓库的价值有一半在提示词本身。直接打开 [references/prompt-templates.md](skills/day-to-night-rain/references/prompt-templates.md)，复制对应段落，粘进任何生图工具即可：

- 即梦 / 通义万相 / 可灵
- Midjourney / Flux / SDXL
- GPT-Image / Nano Banana

文档里给了各工具的参考强度与 denoise 建议。

---

## 使用

安装后用自然语言触发，也可以显式调用 `/day-to-night-rain`。

| 说法 | 是否命中 |
|---|---|
| 「把这张照片改成夜景」 | 命中 |
| 「给这张图加雨」 | 命中 |
| 「用电影感调色重做这张照片」 | 命中 |
| 「生成一张夜景照片」 | 不命中（这是文生图，不是改造现有照片） |

底层要求：Agent 需要具备**图像生成 + 参考图输入**能力。只有文本能力的模型无法执行。

---

## 目录结构

```text
rainy-night-photo-skill/
├── README.md
└── skills/
    └── day-to-night-rain/
        ├── SKILL.md                        # 触发描述 + 工作流 + 失败修复
        └── references/
            └── prompt-templates.md         # 完整提示词模板，按需加载
```

`SKILL.md` 只放决策流程与检查项，长文本模板放在 `references/`，按需读取，避免占用上下文。

---

## 两个安装注意

1. **目录名必须与 `SKILL.md` 的 `name` 字段一致**，即 `day-to-night-rain`，否则加载失败。
2. **不要把 `skills/` 这一层也复制进去**。
   正确：`.trae/skills/day-to-night-rain/SKILL.md`
   错误：`.trae/skills/skills/day-to-night-rain/SKILL.md`

## License

MIT
