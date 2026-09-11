# AGENTS.md — 给 AI Agent 的使用说明

你被要求用「终末地 / 3NDM1N15T4T0R」风格做界面时，按本文件执行。
**动手前先读完** `DESIGN-LANGUAGE.md`（规范与理由）与 `tokens.json`（数值唯一来源），
再打开 `examples/index.html` 看一遍实际效果。

## 最短路径（3 步）

1. 复制 `tokens.json` 的 `color.light` / `color.dark` 到 CSS 自定义属性（`--paper` … `--accent`）。
2. 按 `DESIGN-LANGUAGE.md` §4/§5 搭骨架：`topbar → nav → 三栏 grid → 面板 → statusbar`。
3. 跑 `DESIGN-LANGUAGE.md` §9 的十条自检清单，逐条给出结论再交付。

## 硬约束（违反即返工）

| # | 约束 |
| --- | --- |
| 1 | `border-radius: 0`，全局直角 |
| 2 | 背景只有 `--paper` 两档（亮/暗），不用彩色大面积铺底、不用渐变背景 |
| 3 | 强调色覆盖 < 5%/屏；只用于标题局部、1px 线、小几何符号、单一色块；**正文零着色** |
| 4 | 亮色态强调色用作文字必须下潜（`#fff500 → #6b5d00`） |
| 5 | 文字对比度 ≥ 4.5:1 |
| 6 | 字体家族 ≤ 3（正文/展示/等宽各一）；数字用 `tabular-nums` |
| 7 | 阴影只允许 `0 1px 0 var(--shadow)`；禁止悬浮投影、发光、毛玻璃 |
| 8 | 装饰每种只用一个，禁止纹理叠加 |
| 9 | 时间戳必须带标签（`LAST BUILD …`），不裸放 |
| 10 | 动效遵守 `prefers-reduced-motion`；loader 六条工程约束不可省 |

## 常用片段

**双态令牌**

```css
:root{--paper:#e8e8e2;--panel:#f2f2ec;--card:#dcddd6;--ink:#101110;
  --muted:#4a4c48;--line:#d8d9d5;--accent:#6b5d00;--shadow:rgba(16,17,16,.10);color-scheme:light}
@media (prefers-color-scheme: dark){:root{--paper:#101110;--panel:#181a18;--card:#1e201d;
  --ink:#f5f5f0;--muted:#898d89;--line:#343633;--accent:#fff500;--shadow:rgba(0,0,0,.5);color-scheme:dark}}
```

**内嵌字体**（若你的产物需要与官方气质一致的中文渲染）

```css
@font-face{font-family:"HarmonyOS Sans SC";
  src:url(assets/fonts/HarmonyOS_Sans_SC_Regular.woff2) format("woff2");font-weight:400;font-display:swap}
@font-face{font-family:"HarmonyOS Sans SC";
  src:url(assets/fonts/HarmonyOS_Sans_SC_Bold.woff2) format("woff2");font-weight:700;font-display:swap}
```

字体许可见 `assets/fonts/LICENSE-HarmonyOS-Sans.txt`：可自由商用、可嵌入作品分发，
但**不得将字体本体作为独立商品再分发**，且必须保留版权声明与授权文本。

**编号双语标签 + 方括号**

```html
<div class="label"><b>01</b> // VAULT</div>
```
```css
.label::before{content:"[";color:var(--accent);margin-right:5px}
.label::after {content:"]";color:var(--accent);margin-left:5px}
```

**面板三件套：刻度尺 + 幽灵大字 + 收边**

```css
.panel{position:relative;overflow:hidden;background:var(--panel);
  border:1px solid var(--line);box-shadow:0 1px 0 var(--shadow);padding:16px 18px}
.panel::before{content:"";position:absolute;left:0;top:0;bottom:0;width:5px;opacity:.75;
  background:repeating-linear-gradient(to bottom,var(--line) 0,var(--line) 1px,transparent 1px,transparent 10px)}
.panel::after{content:attr(data-word);position:absolute;right:12px;bottom:-.36em;
  font:900 46px/1 "Arial Black",Arial,sans-serif;letter-spacing:.04em;
  color:var(--ink);opacity:.055;pointer-events:none;white-space:nowrap}
.statusbar{border-bottom:3px solid var(--accent)}
```

**启动加载动画**：完整时序与六条工程约束见 `DESIGN-LANGUAGE.md` §7.1，
可运行实现见 `examples/index.html`（搜索 `playLoader`）。直接复用时注意：
墙钟推导、双时钟、保险丝、幂等、`pointer-events:none` + `aria-hidden`、
`prefers-reduced-motion` 跳过——六条缺一不可。

## 风格判断速查

- 想要"更炫"时：**不要**加发光/渐变/圆角。改为增加**结构性**手段——
  编号、刻度、发丝线、双语小字、底边裁切大字。
- 不确定颜色时：回 `tokens.json` 取值，不要新造色。
- 不确定该不该上强调色时：**不上**。这套语言的辨识度来自克制。
- 参考气质：`assets/covers/` 六张官方主视觉（黄底蓝图、纸白水墨、方括号标题、
  底部收边）。

## 自检输出格式（交付前贴给用户）

```
[ ] 强调色面积 <5%，正文零着色        → 结论/证据
[ ] 全直角、无渐变、无悬浮投影        → …
[ ] 亮色态强调文字已下潜             → …
[ ] 对比度 ≥4.5:1                    → …
[ ] tabular-nums + 11px 大写元信息    → …
[ ] [ ] 方括号 + 编号双语             → …
[ ] 装饰用满两种（刻度尺/幽灵字/收边） → …
[ ] loader 时序与六条约束（若用）      → …
[ ] prefers-reduced-motion 已处理     → …
[ ] 时间戳带标签                      → …
```
