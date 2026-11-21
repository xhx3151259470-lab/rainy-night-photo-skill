# AI Skill 合集

一组可直接安装到 Trae 的 Skill，用于把重复的创作流程沉淀成可复用的能力。

## Skill 列表

| Skill | 用途 |
|---|---|
| [day-to-night-rain](skills/day-to-night-rain/) | 把白天实景照片改造成电影级夜景 / 雨夜照片，含完整提示词与各工具参数 |

---

## 安装

Skill 是「一个文件夹 + 一个 `SKILL.md`」。安装即把文件夹放进 Trae 的 skills 目录。

### 方式一：项目级（只对当前项目生效）

只影响一个项目，适合团队共享同一套约定。

```bash
git clone https://github.com/xhx3151259470-lab/AI-skill.git
cd <你的项目根目录>
mkdir -p .trae/skills
cp -r <clone路径>/skills/* .trae/skills/
```

Windows PowerShell：

```powershell
git clone https://github.com/xhx3151259470-lab/AI-skill.git
# 假设克隆到了 D:\AI-skill
New-Item -ItemType Directory -Force -Path "<你的项目>\.trae\skills" | Out-Null
Copy-Item -Recurse "D:\AI-skill\skills\*" "<你的项目>\.trae\skills\"
```

### 方式二：全局级（所有项目都能用）

| 系统 | Trae CN | Trae 国际版 |
|---|---|---|
| Windows | `C:\Users\<用户名>\.trae-cn\skills\` | `C:\Users\<用户名>\.trae\skills\` |
| macOS / Linux | `~/.trae-cn/skills/` | `~/.trae/skills/` |

```bash
# macOS / Linux 示例（CN 版）
mkdir -p ~/.trae-cn/skills
cp -r ./AI-skill/skills/* ~/.trae-cn/skills/
```

```powershell
# Windows 示例（CN 版）
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.trae-cn\skills" | Out-Null
Copy-Item -Recurse ".\AI-skill\skills\*" "$env:USERPROFILE\.trae-cn\skills\"
```

### 方式三：只装某一个 Skill

复制对应文件夹即可，`references/` 要跟着一起复制：

```text
skills/day-to-night-rain/
├── SKILL.md
└── references/
    └── prompt-templates.md
```

---

## 使用

安装后无需配置，直接用自然语言触发。

| 说法 | 是否命中 |
|---|---|
| 「把这张照片改成夜景」 | 命中 |
| 「给这张图加雨」 | 命中 |
| 「用电影感调色重做这张照片」 | 命中 |
| 「生成一张夜景照片」 | 不命中（这是文生图，不是改造现有照片） |

也可以显式调用：`/day-to-night-rain`

## 两个安装注意事项

1. **目录名必须与 `SKILL.md` 里的 `name` 字段完全一致**，否则加载失败。
   例如 `day-to-night-rain/` 目录里必须是 `name: day-to-night-rain`。

2. **不要把 `skills/` 这一层也复制进去**。
   正确：`.trae/skills/day-to-night-rain/SKILL.md`
   错误：`.trae/skills/skills/day-to-night-rain/SKILL.md`

## 目录结构

```text
AI-skill/
└── skills/
    └── day-to-night-rain/
        ├── SKILL.md                        # 触发描述 + 工作流 + 失败修复
        └── references/
            └── prompt-templates.md         # 完整提示词模板，按需加载
```

每个 Skill 的 `SKILL.md` 只放决策流程与检查项，长文本模板放 `references/`，按需读取，避免占用上下文。
