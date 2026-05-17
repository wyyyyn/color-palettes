---
name: color-palettes
description: Use when building UI, choosing or applying a visual style to a frontend project, theming, or the user asks about palettes / fonts / layout / tone. A combinable design system — 30 color palettes × 8 font pairings × 6 layouts × 6 tones × 6 moods — previewed live in preview.html. Use the "Replicate into a project" workflow to apply a chosen combo (or one cloned from a site) as CSS variables into any codebase.
---

# Color Palettes — Combinable Design System

This is not just a color list. It is a **5-axis combinable design system** with a live playground (`preview.html`): pick one option from each menu and the mock site re-renders the full combination. Any combo can be **replicated into a real project** as CSS variables.

```
COLOR (30) × FONT (8) × LAYOUT (6) × TONE (6) × MOOD (6)
```

- **Open `preview.html`** in a browser to explore combos, shuffle (Space), lock axes, and **Copy / Export** the current combo (CSS variables + Google Fonts link + JSON config).
- The 30 color palettes (data below) are the canonical color source and are unchanged from the original collection.

## 设计原则

构建 UI 时遵循克制的编辑风：

- **大量留白**：`padding`/`margin` 宁多勿少，每屏只讲一件事
- **克制用色**：主色 + 点缀色足矣，别把 7 个角色色全堆上
- **语义化**：颜色映射到角色（bg/text/accent…）而非裸 hex；字号/圆角/阴影也走变量
- **去装饰化**：不用渐变按钮、不堆阴影；靠背景色与描边分层（除非 TONE 明确选了 elevated/bold）
- **动效克制**：`transition` 150–400ms，由 MOOD 的 `--transition` 决定

---

## 五个轴 (The 5 Axes)

### 1. COLOR · 配色 (30) — `--color-*`

7 个语义色彩角色。完整 hex 见下方「快速参考」表与「JS 数据」。

| 角色 | CSS 变量 | 用途 |
|------|----------|------|
| bg | `--color-bg` | 页面背景 |
| card | `--color-card` | 卡片 / 区块背景 |
| text | `--color-text` | 标题、主要文字 |
| text2 | `--color-text2` | 正文、次要文字 |
| accent | `--color-accent` | 按钮、链接、交互元素 |
| accent2 | `--color-accent2` | 标签、高亮、次要点缀 |
| btn-text | `--color-btn-text` | 按钮上的文字颜色 |

### 2. FONT · 字体 (8) — `--font-display / --font-body / --font-mono`

| id | 名称 | display / body / mono |
|----|------|------------------------|
| claude | Claude 编辑 | Fraunces / Inter / IBM Plex Mono |
| mag | 杂志大衬线 | Playfair Display / Source Serif 4 / IBM Plex Mono |
| swiss | 瑞士中性 | Inter / Inter / IBM Plex Mono |
| literary | 文学衬线 | Newsreader / Newsreader / IBM Plex Mono |
| terminal | 终端极客 | Space Grotesk / IBM Plex Mono / IBM Plex Mono |
| humanist | 人文混排 | Spectral / Inter / IBM Plex Mono |
| contrast | 编辑反差 | Fraunces / Source Serif 4 / IBM Plex Mono |
| modern | 现代无衬线 | Space Grotesk / Inter / IBM Plex Mono |

CJK 回退统一加 `'Noto Serif SC'`（衬线）/ `'Noto Sans SC'`（无衬线）。

### 3. LAYOUT · 排版 (6) — `--fs1/2/b/s --line-height --measure --tracking --space-* --gap --cols`

`editorial`(大字距宽留白) · `tight`(紧凑高密度) · `centered`(居中极简) · `magazine`(巨标题叙事) · `dense`(仪表盘) · `poster`(海报巨字)。控制字号阶梯、行距、字距、版心宽、栅格列数、对齐与间距节奏。

### 4. TONE · 调性 (6) — `--radius --border-width --shadow --btn-radius --btn-padding --weight-*`

`sharp`(方角描边无影) · `soft`(圆角胶囊) · `minimal`(细线几乎无形) · `editorial`(下划线印刷感) · `elevated`(阴影立体) · `bold`(粗边硬投影)。形语言：圆角、描边 vs 阴影、按钮形、字重对比。

### 5. MOOD · 氛围 (6) — `--transition` + `data-tex / data-motif / data-rule` + 密度系数

`paper`(纸纹·✻标记) · `gallery`(极致留白·无饰) · `terminal`(扫描线·$ 提示符) · `magazine`(分隔线·节奏) · `nocturne`(晕影·圆点饰) · `clean`(零纹理·即时)。控制纹理、装饰母题、信息密度、微交互速度。

> 数据真值在 `preview.html` 的 `T / FONTS / LAYOUTS / TONES / MOODS` 数组。要新增选项就往对应数组追加一个对象，UI 自动渲染。

---

## 复刻进项目 (Replicate a Combo Into Your Project)

**核心能力**：把 playground 选好的一套组合（或从某网站复刻来的气质，见下节），作为 CSS 变量落进用户的真实代码。

### Step 0 — 拿到组合

从 `preview.html` 右上「复制 / 导出」拿到 bundle（或用户口述「配色 D + 字体 terminal + 排版 dense + 调性 sharp + 氛围 terminal」即可自行查上表组装）。导出 bundle 形如：

```
/* color-palettes · D Teal & Gold / Terminal Geek / Dense Dashboard / Sharp / Terminal */
:root{
  --color-bg:#004643; --color-card:rgba(171,209,198,.15);
  --color-text:#fffffe; --color-text2:#abd1c6;
  --color-accent:#f9bc60; --color-accent2:#e16162; --color-btn-text:#001e1d;
  --font-display:'Space Grotesk','Noto Sans SC',sans-serif;
  --font-body:'IBM Plex Mono','Noto Sans SC',monospace;
  --font-mono:'IBM Plex Mono',monospace;
  --fs-h1:26px; --fs-h2:16px; --fs-body:13.5px; --fs-small:10.5px;
  --line-height:1.5; --measure:880px; --tracking:0px;
  --space-section:21px; --space-inline:28px; --gap:7px;
  --radius:0px; --border-width:1px; --shadow:none;
  --btn-radius:0px; --btn-padding:10px 22px;
  --weight-display:600; --weight-body:400;
  --transition:140ms;
}
/* + Google Fonts <link> + JSON config { palette, font, layout, tone, mood } */
```

### Step 1 — 探测目标项目

读 `package.json` / 配置判断技术栈：Tailwind v4、shadcn/ui、Next.js、Vite、纯 CSS、单 HTML 等。找到主样式入口（`globals.css` / `index.css` / `app.css` / `:root`）。

### Step 2 — 落地 CSS 变量（按栈选一种）

- **纯 CSS / 单 HTML**：把 bundle 的 `:root{…}` 整段写进主样式表；元素改用 `var(--color-*)`、`font-family:var(--font-body)`、`border-radius:var(--radius)` 等。
- **Tailwind v4**：把变量放进 `@theme { --color-bg: …; --font-display: … }`，类名引用 `bg-bg text-text font-display rounded-[var(--radius)]`。
- **shadcn/ui**：写 `theme.css`，在 `@layer base :root{…}` 覆盖；把 `--color-accent`→`--primary`、`--color-bg`→`--background`、`--color-text`→`--foreground` 做语义映射。
- **Next.js / Vite**：新建 `styles/design-system.css`，在入口 import 一次。

### Step 3 — 引入字体

把 bundle 里的 Google Fonts `<link>` 加进 `<head>`（或框架的 fonts 配置 / `next/font`）。只引用到的家族，`display=swap`。

### Step 4 — 验证（不可跳过）

1. 起项目，按 [[CLAUDE.md 渲染必截图]] 原则**截图**与 playground 比对一致。
2. 校验对比度：`text` on `bg`、`btn-text` on `accent` 至少过 WCAG AA（4.5:1 正文）。不达标提示用户换 COLOR 或调 text2。
3. 列出改了哪些文件 + 一段 before/after 示例 + 跑起来的命令。

### Step 5 — 留痕（可选但推荐）

在目标项目根写一份 `DESIGN.md`（沿用 bundle 注释行的组合名 + 各 token），方便下一个 AI 理解这套系统。

---

## 复刻已有网站 (Clone a Site → Nearest Combo)

反向流程，借助已安装的开源 skill **`clone-website`**（`~/.claude/skills/clone-website`，网站逆向/复刻）：

1. 用 `clone-website` 抓取目标站，拿到它的实际配色、字体、圆角、阴影、间距（computed styles）。
2. 把抓到的特征**映射到本系统最接近的组合**：
   - 主色/底色 → 最近的 COLOR（按 bg+accent 色距）
   - 字体族 → 最近的 FONT（衬线/无衬线/等宽 + 调性）
   - 圆角/阴影/描边 → TONE；字号阶梯/版心 → LAYOUT；纹理/密度 → MOOD
3. 在 `preview.html` 里选中该组合让用户确认/微调，再走上面「复刻进项目」Step 1–5 落地。

这样既能 1:1 复刻，也能把外站气质收敛进这套可控的语义系统。

---

## 快速参考 (Palette Hex)

| ID | Name | BG | Card | Text | Text2 | Accent | Accent2 | BtnText | 氛围 |
|----|------|----|------|------|-------|--------|---------|---------|------|
| A | Earthy Scholar | #f9f4ef | #eaddcf | #020826 | #716040 | #8c7851 | #f25042 | #fff | 旧书店温润 |
| B | Rose Petal | #faeee7 | #fff | #33272a | #594a4e | #ff8ba7 | #c3f0ca | #33272a | 柔和浪漫 |
| C | Cream & Navy | #fef6e4 | #f3d2c1 | #001858 | #172c66 | #f582ae | #8bd3dd | #001858 | 杂志高级感 |
| D | Teal & Gold | #004643 | rgba(171,209,198,.12) | #fffffe | #abd1c6 | #f9bc60 | #e16162 | #001e1d | 东方美学 |
| E | Forest & Gold | #f2f7f5 | #e8f0ec | #00473e | #475d5b | #faae2b | #ffa8ba | #00473e | 自然清新 |
| F | Paper & Teal | #f8f5f2 | #feefe8 | #232323 | #222525 | #078080 | #f45d48 | #f8f5f2 | 知性干净 |
| G | Silver & Orange | #eff0f3 | #fffffe | #0d0d0d | #2a2a2a | #ff8e3c | #d9376e | #0d0d0d | 现代极简 |
| H | Midnight Rose | #232946 | rgba(184,193,236,.1) | #fffffe | #b8c1ec | #eebbc3 | #d4d8f0 | #232946 | 深夜书房 |
| I | Chocolate Rose | #55423d | rgba(255,243,236,.1) | #fffffe | #fff3ec | #ffc0ad | #e78fb3 | #271c19 | 复古奢华 |
| J | Blush Latte | #F7E6E1 | #f0d5cd | #4B332E | #A77A6E | #CFA59A | #A77A6E | #fff | 裸粉渐变 |
| K | Champagne Smoke | #FBF6EE | #f2ebe0 | #2A2A2B | #7B746B | #2A2A2B | #C8B89E | #FBF6EE | 画廊烛光 |
| L | Vanilla Sage | #F6F0E6 | #e8eed5 | #2F3E3A | #6F8A78 | #6F8A78 | #A8BDA3 | #F6F0E6 | 疗愈自然 |
| M | Sunset Gradient | #355C7D | rgba(248,177,149,.12) | #F8B195 | #dda090 | #F67280 | #F8B195 | #355C7D | 日落浪漫 |
| N | Peach & Forest | #2A363B | rgba(153,184,152,.1) | #FECEAB | #99B898 | #FF847C | #99B898 | #2A363B | 对比张力 |
| O | Pastel Bloom | #fff8f5 | #fff | #444 | #888 | #FFAAA6 | #A8E6CE | #444 | 糖果轻快 |
| P | Coral Garden | #fdf0e6 | #fff | #3a2020 | #6b4a4a | #FE4365 | #83AF9B | #fff | 明快浪漫 |
| Q | Lavender Dusk | #f6efef | #f0e2e1 | #181818 | #555 | #994ff3 | #fbdd74 | #fff | 紫黄出挑 |
| R | Mocha Mousse | #FAF7F2 | #f0ebe3 | #2C1810 | #6B4C3B | #A47864 | #d4a58a | #FAF7F2 | Pantone年度 |
| S | Warm Clay | #FAF2E8 | #f3ebe0 | #2F201B | #8B5A44 | #C89A7C | #8B5A44 | #fff | 手作质朴 |
| T | Dark Ember | #0f0e17 | rgba(167,169,190,.08) | #fffffe | #a7a9be | #ff8906 | #f25f4c | #0f0e17 | 暗黑炽烈 |
| U | Neon Dusk | #16161a | rgba(127,90,240,.08) | #fffffe | #94a1b2 | #7f5af0 | #2cb67d | #fffffe | 赛博黄昏 |
| V | Violet Pop | #fffffe | #d1d1e9 | #2b2c34 | #2b2c34 | #6246ea | #e45858 | #fffffe | 紫电惊鸿 |
| W | Sunshine Mint | #fffffe | #e3f6f5 | #272343 | #2d334a | #ffd803 | #bae8e8 | #272343 | 柠檬薄荷 |
| X | Cotton Candy | #fec7d7 | #d9d4e7 | #0e172c | #322f49 | #a786df | #f9f8fc | #fffffe | 棉花糖 |
| Y | Coastal Linen | #F3EFE7 | #e8e4db | #2C3D45 | #6C8A96 | #6C8A96 | #AFC1C7 | #F3EFE7 | 海岸亚麻 |
| Z | Terracotta Whisper | #F5E7DB | #f0ddd0 | #3A2A25 | #A55A43 | #D48B6A | #A55A43 | #fff | 陶语轻声 |
| AA | Retro Mint Soda | #F8F1E6 | #CDEBDD | #2B3A3F | #4a5c5f | #72C7B7 | #F2A65A | #2B3A3F | 薄荷汽水 |
| AB | Iced Blueberry | #F7F8FC | #DCE6FA | #2D3354 | #6E83C7 | #6E83C7 | #AFC3F2 | #F7F8FC | 蓝莓冰沙 |
| AC | Olive Ink | #F2F0E6 | #e6e3d5 | #141A14 | #3F4B39 | #9AA27E | #3F4B39 | #F2F0E6 | 橄榄墨香 |
| AD | Cherry Mocha | #F6EEE9 | #f0e5de | #1C1214 | #5B2A2A | #B24A4A | #E7B9B2 | #fff | 樱桃摩卡 |

## CSS 变量模板 (单个配色)

```css
[data-theme="A"] {
  --color-bg: #f9f4ef;
  --color-card: #eaddcf;
  --color-text: #020826;
  --color-text2: #716040;
  --color-accent: #8c7851;
  --color-accent2: #f25042;
  --color-btn-text: #fff;
}
```

## JS 数据 (30 配色)

```js
const themes = [
  { id:'A', name:'Earthy Scholar', bg:'#f9f4ef', card:'#eaddcf', text:'#020826', text2:'#716040', accent:'#8c7851', accent2:'#f25042', btnText:'#fff' },
  { id:'B', name:'Rose Petal', bg:'#faeee7', card:'#fff', text:'#33272a', text2:'#594a4e', accent:'#ff8ba7', accent2:'#c3f0ca', btnText:'#33272a' },
  { id:'C', name:'Cream & Navy', bg:'#fef6e4', card:'#f3d2c1', text:'#001858', text2:'#172c66', accent:'#f582ae', accent2:'#8bd3dd', btnText:'#001858' },
  { id:'D', name:'Teal & Gold', bg:'#004643', card:'rgba(171,209,198,.12)', text:'#fffffe', text2:'#abd1c6', accent:'#f9bc60', accent2:'#e16162', btnText:'#001e1d' },
  { id:'E', name:'Forest & Gold', bg:'#f2f7f5', card:'#e8f0ec', text:'#00473e', text2:'#475d5b', accent:'#faae2b', accent2:'#ffa8ba', btnText:'#00473e' },
  { id:'F', name:'Paper & Teal', bg:'#f8f5f2', card:'#feefe8', text:'#232323', text2:'#222525', accent:'#078080', accent2:'#f45d48', btnText:'#f8f5f2' },
  { id:'G', name:'Silver & Orange', bg:'#eff0f3', card:'#fffffe', text:'#0d0d0d', text2:'#2a2a2a', accent:'#ff8e3c', accent2:'#d9376e', btnText:'#0d0d0d' },
  { id:'H', name:'Midnight Rose', bg:'#232946', card:'rgba(184,193,236,.1)', text:'#fffffe', text2:'#b8c1ec', accent:'#eebbc3', accent2:'#d4d8f0', btnText:'#232946' },
  { id:'I', name:'Chocolate Rose', bg:'#55423d', card:'rgba(255,243,236,.1)', text:'#fffffe', text2:'#fff3ec', accent:'#ffc0ad', accent2:'#e78fb3', btnText:'#271c19' },
  { id:'J', name:'Blush Latte', bg:'#F7E6E1', card:'#f0d5cd', text:'#4B332E', text2:'#A77A6E', accent:'#CFA59A', accent2:'#A77A6E', btnText:'#fff' },
  { id:'K', name:'Champagne Smoke', bg:'#FBF6EE', card:'#f2ebe0', text:'#2A2A2B', text2:'#7B746B', accent:'#2A2A2B', accent2:'#C8B89E', btnText:'#FBF6EE' },
  { id:'L', name:'Vanilla Sage', bg:'#F6F0E6', card:'#e8eed5', text:'#2F3E3A', text2:'#6F8A78', accent:'#6F8A78', accent2:'#A8BDA3', btnText:'#F6F0E6' },
  { id:'M', name:'Sunset Gradient', bg:'#355C7D', card:'rgba(248,177,149,.12)', text:'#F8B195', text2:'#dda090', accent:'#F67280', accent2:'#F8B195', btnText:'#355C7D' },
  { id:'N', name:'Peach & Forest', bg:'#2A363B', card:'rgba(153,184,152,.1)', text:'#FECEAB', text2:'#99B898', accent:'#FF847C', accent2:'#99B898', btnText:'#2A363B' },
  { id:'O', name:'Pastel Bloom', bg:'#fff8f5', card:'#fff', text:'#444', text2:'#888', accent:'#FFAAA6', accent2:'#A8E6CE', btnText:'#444' },
  { id:'P', name:'Coral Garden', bg:'#fdf0e6', card:'#fff', text:'#3a2020', text2:'#6b4a4a', accent:'#FE4365', accent2:'#83AF9B', btnText:'#fff' },
  { id:'Q', name:'Lavender Dusk', bg:'#f6efef', card:'#f0e2e1', text:'#181818', text2:'#555', accent:'#994ff3', accent2:'#fbdd74', btnText:'#fff' },
  { id:'R', name:'Mocha Mousse', bg:'#FAF7F2', card:'#f0ebe3', text:'#2C1810', text2:'#6B4C3B', accent:'#A47864', accent2:'#d4a58a', btnText:'#FAF7F2' },
  { id:'S', name:'Warm Clay', bg:'#FAF2E8', card:'#f3ebe0', text:'#2F201B', text2:'#8B5A44', accent:'#C89A7C', accent2:'#8B5A44', btnText:'#fff' },
  { id:'T', name:'Dark Ember', bg:'#0f0e17', card:'rgba(167,169,190,.08)', text:'#fffffe', text2:'#a7a9be', accent:'#ff8906', accent2:'#f25f4c', btnText:'#0f0e17' },
  { id:'U', name:'Neon Dusk', bg:'#16161a', card:'rgba(127,90,240,.08)', text:'#fffffe', text2:'#94a1b2', accent:'#7f5af0', accent2:'#2cb67d', btnText:'#fffffe' },
  { id:'V', name:'Violet Pop', bg:'#fffffe', card:'#d1d1e9', text:'#2b2c34', text2:'#2b2c34', accent:'#6246ea', accent2:'#e45858', btnText:'#fffffe' },
  { id:'W', name:'Sunshine Mint', bg:'#fffffe', card:'#e3f6f5', text:'#272343', text2:'#2d334a', accent:'#ffd803', accent2:'#bae8e8', btnText:'#272343' },
  { id:'X', name:'Cotton Candy', bg:'#fec7d7', card:'#d9d4e7', text:'#0e172c', text2:'#322f49', accent:'#a786df', accent2:'#f9f8fc', btnText:'#fffffe' },
  { id:'Y', name:'Coastal Linen', bg:'#F3EFE7', card:'#e8e4db', text:'#2C3D45', text2:'#6C8A96', accent:'#6C8A96', accent2:'#AFC1C7', btnText:'#F3EFE7' },
  { id:'Z', name:'Terracotta Whisper', bg:'#F5E7DB', card:'#f0ddd0', text:'#3A2A25', text2:'#A55A43', accent:'#D48B6A', accent2:'#A55A43', btnText:'#fff' },
  { id:'AA', name:'Retro Mint Soda', bg:'#F8F1E6', card:'#CDEBDD', text:'#2B3A3F', text2:'#4a5c5f', accent:'#72C7B7', accent2:'#F2A65A', btnText:'#2B3A3F' },
  { id:'AB', name:'Iced Blueberry', bg:'#F7F8FC', card:'#DCE6FA', text:'#2D3354', text2:'#6E83C7', accent:'#6E83C7', accent2:'#AFC3F2', btnText:'#F7F8FC' },
  { id:'AC', name:'Olive Ink', bg:'#F2F0E6', card:'#e6e3d5', text:'#141A14', text2:'#3F4B39', accent:'#9AA27E', accent2:'#3F4B39', btnText:'#F2F0E6' },
  { id:'AD', name:'Cherry Mocha', bg:'#F6EEE9', card:'#f0e5de', text:'#1C1214', text2:'#5B2A2A', accent:'#B24A4A', accent2:'#E7B9B2', btnText:'#fff' },
];
```

## 选色建议

| 场景 | 推荐配色 |
|------|----------|
| 个人博客 / 写作站 | A、K、R、AC ｜ 字体 literary/humanist ｜ 排版 editorial ｜ 氛围 paper |
| 作品集 / Portfolio | F、G、E、Y ｜ 字体 claude/contrast ｜ 排版 magazine/poster ｜ 氛围 gallery |
| 暗色主题 | D、H、T、U ｜ 字体 terminal/modern ｜ 调性 sharp ｜ 氛围 terminal/nocturne |
| 女性化 / 柔和 | B、J、O、X ｜ 字体 humanist ｜ 调性 soft ｜ 氛围 paper |
| 高对比 / 张力 | C、N、Q、V ｜ 字体 mag ｜ 调性 bold ｜ 排版 magazine |
| SaaS / 开发者工具 | G、U、V、AB ｜ 字体 swiss/modern ｜ 调性 minimal/sharp ｜ 排版 dense |
| 暖色调 / 手工感 | S、Z、AD、R ｜ 字体 claude ｜ 调性 editorial ｜ 氛围 paper |
| 清新活力 | W、AA、E、O ｜ 字体 modern ｜ 调性 soft ｜ 氛围 clean |

## 来源

- 配色：[Happy Hues](https://www.happyhues.co) · [Digital Synopsis](https://digitalsynopsis.com/design/minimal-web-color-palettes-combination-hex-code/) · [Media.io](https://www.media.io/color-palette/aesthetic-color-palette.html) · Pantone 2025 (R)
- 字体：Google Fonts（Fraunces / Inter / Playfair Display / Source Serif 4 / Newsreader / Spectral / Space Grotesk / IBM Plex Mono）
- 调性/氛围：Anthropic / Claude 设计语言（cream + 黏土橙 + 方角无阴影 + ✻）、Realtime Colors、Radix、Open Props 等社区实践
- 复刻：配合已安装的开源 skill `clone-website`（网站逆向 → 最近组合 → 应用）
