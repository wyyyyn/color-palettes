# 设计实验室 · color-palettes

一个八维可组合的设计系统，配一个零构建的实时预览页 `preview.html`。每个菜单各选一项，模拟站点会即时合成整套组合。任意一套组合都能作为 CSS 变量（连同自带字体 / 图标 / 花纹）复刻进真实项目，全程离线。

```
配色(40) × 字体(24) × 排版(6) × 调性(6) × 氛围(6) × 图标(13) × 花纹(17) × 元件(8)
```

## 在线预览

- **本地**：克隆后直接用浏览器打开 `preview.html`，无需安装、无需构建。
- **GitHub Pages**：仓库 Settings → Pages 指向 `main` 根目录后，访问 `https://wyyyyn.github.io/color-palettes/`（根 `index.html` 会自动跳到 `preview.html`）。

## 怎么用

在 `preview.html` 里：

- 每个菜单点选一项，预览区实时合成整套视觉。
- `空格` 随机洗牌，需要固定某一维时点该轴的锁。
- 支持中 / EN 切换，全程键盘可操作。
- 右上「复制 / 导出」拿到当前组合的 CSS 变量、Google Fonts 链接与 JSON 配置；URL hash 可分享，快照可做 A·B 对比。

## 八个轴

| 轴 | 数量 | 控制什么 | 关键变量 |
|----|------|----------|----------|
| 配色 COLOR | 40 | 7 个语义色彩角色，低饱和基调，全库无高饱和紫 | `--color-bg/card/text/text2/accent/accent2/btn-text` |
| 字体 FONT | 24 | display / body / mono 三件套策展配对 | `--font-display / --font-body / --font-mono` |
| 排版 LAYOUT | 6 | 字号阶梯、行距、字距、版心宽、栅格、间距节奏 | `--fs* --line-height --measure --space-* --cols` |
| 调性 TONE | 6 | 圆角、描边对阴影、按钮形、字重对比 | `--radius --border-width --shadow --btn-* --weight-*` |
| 氛围 MOOD | 6 | 纹理、装饰母题、信息密度、微交互速度 | `--transition` + `data-tex/-motif/-rule` |
| 图标 ICON | 13 | 切风格不切内容，4 个恒定概念 × 13 套风格 | `assets/icons/styles/<id>/` |
| 花纹 PATTERN | 17 | 复古 / 现代可平铺底纹 + 装饰分隔花纹 | `--pat / --orn` |
| 元件 ELEMENT | 8 | 按钮 / 卡片 / 标签的具体配方，叠在调性之上 | `data-el` |

数据真值都在 `preview.html` 内的 `T / FONTS / LAYOUTS / TONES / MOODS / ICONS / PATTERNS / ELEMENTS` 数组，由 `AXES` 统一驱动，菜单 / 随机 / 锁定 / 分享 URL / 快照 / A·B 对比 / 导出全部自动覆盖新轴。详细轴说明与选色建议见 [`SKILL.md`](./SKILL.md)。

## 复刻进项目

1. 在预览页选好组合，从「复制 / 导出」拿到 bundle（CSS 变量 + 字体 link + JSON）。
2. 探测目标项目技术栈（纯 CSS / Tailwind v4 / shadcn/ui / Next.js / Vite），把 `:root{…}` 落进主样式入口或 `@theme`。
3. 引入用到的字体，校验对比度过 WCAG AA，截图与预览页比对一致。

完整 Step 0–5 流程、按技术栈的落地写法、以及「反向复刻已有网站到最近组合」的流程，见 [`SKILL.md`](./SKILL.md)。

## 离线资源库

`assets/` 内置开源资源，复刻时无需联网、无需 CDN，整目录拷进目标项目即可用：

| 目录 | 内容 | 许可 |
|------|------|------|
| `assets/fonts/` | 自托管 woff2 字族（含 Noto Serif/Sans SC）+ `fonts.css` | SIL OFL 1.1 |
| `assets/icons/styles/` | 13 风格 × 4 概念 SVG | Lucide ISC · Phosphor/Tabler/Heroicons MIT · Remix Apache-2.0 |
| `assets/icons/lucide/` | 完整 Lucide（`sprite.svg`、`tags.json`） | ISC |
| `assets/patterns/` | 16 套可平铺底纹 + 6 装饰花纹 | CC0（原创） |

许可汇总见 [`THIRD_PARTY_LICENSES.md`](./THIRD_PARTY_LICENSES.md)，各目录内保留 `OFL.txt / LICENSE / _licenses/*` 即可合法再分发。

## 目录结构

```
preview.html             实时预览页（单文件，零构建，全部数据与逻辑内联）
index.html               根入口，自动跳转到 preview.html
SKILL.md                 八轴详解 + 复刻工作流 + 配色快速参考表
THIRD_PARTY_LICENSES.md  第三方资源许可汇总
assets/                  离线字体 / 图标 / 花纹
```

## 设计原则

构建 UI 时遵循克制的编辑风：大量留白、克制用色、颜色映射到语义角色而非裸 hex、去装饰化、动效克制。全库以低饱和为基调，禁用高饱和紫色。

## 许可

代码与预览页归仓库作者所有。`assets/` 下第三方字体 / 图标按各自许可（OFL / MIT / ISC / Apache-2.0）分发，原创花纹为 CC0。再分发请保留对应许可文件。
