# 3NDM1N15T4T0R — Endfield 设计语言

> 3NDM1N15T4T0R = **ENDMINISTRATOR**（《明日方舟：终末地》中的管理员）。
> 本仓库沉淀一套「终末地」气质的 Web 设计语言：令牌、排版、组件、装饰与动效规范，
> 目标是**任何 agent 或人 clone 之后照着就能做出同一风格**的界面。

## 怎么用这份仓库

| 文件 | 用途 |
| --- | --- |
| `DESIGN-LANGUAGE.md` | 本文件。完整规范与"为什么" |
| `tokens.json` | **唯一数值来源**。所有颜色/字号/间距/时序的机器可读版本 |
| `AGENTS.md` | 给 AI agent 的硬约束与自检清单（先读它再动手） |
| `examples/index.html` | 可运行样例：单文件，双击即看整套风格 |
| `assets/covers/` | 官方主视觉参考图（气质校准用，版权见 `CREDITS.md`） |
| `assets/fonts/` | HarmonyOS Sans SC 子集 woff2（含华为授权文本） |

两份文件冲突时以 `tokens.json` 的数值为准。

---

## 1. 一句话风格

**工业编辑风（industrial editorial）**：中性纸底 + 墨黑文字，全直角，1px 发丝线，
**单一信号色小面积点缀**，编号双语标签，超粗实心大字硬压背景。

四条支柱，每条都可被验证：

1. **中性底** —— 背景只有纸白与近黑两档，从不出现彩色大面积铺底（唯一例外见 §6）。
2. **单信号色 ≤5%** —— 强调色只允许出现在：标题局部、1px 线、小几何符号、单一色块。
   绝不用于正文段落。
3. **全直角** —— `border-radius: 0`。圆形只作为"母题"出现（圆点、唱片式圆形）。
4. **靠字重与字距分层，不靠阴影与圆角** —— 阴影仅用于 `0 1px 0 <hairline>`，
   不做悬浮投影。

---

## 2. 色彩

### 2.1 令牌（亮/暗双态）

| 令牌 | 亮色 | 暗色 | 用途 |
| --- | --- | --- | --- |
| `--paper` | `#e8e8e2` | `#101110` | 页面底 |
| `--panel` | `#f2f2ec` | `#181a18` | 面板底 |
| `--card` | `#dcddd6` | `#1e201d` | 内嵌块/代码底 |
| `--ink` | `#101110` | `#f5f5f0` | 主文字 |
| `--muted` | `#4a4c48` | `#898d89` | 元信息文字 |
| `--line` | `#d8d9d5` | `#343633` | 发丝线与边框 |
| `--accent` | `#6b5d00` | `#fff500` | 信号色 |
| `--shadow` | `rgba(16,17,16,.10)` | `rgba(0,0,0,.5)` | 唯一允许的 1px 投影 |

暗色态声明 `color-scheme: dark`，亮色态 `color-scheme: light`。

### 2.2 信号色二选一

- **谷地黄 `#fff500`**（默认，终末地主视觉的黄）
- **武陵青 `#14d0d0`**（备选）

### 2.3 亮底强调色"下潜"规则（关键）

信号色在**暗色**态可直接点亮；在**亮色**态若用于**文字**，必须下潜为深色以保证对比度：
`#fff500 → #6b5d00`。用于色块/线条时可以保留原色（`#fff500` 块 + 墨色文字，
对比度反而极高）。这条规则是亮暗两态观感一致的关键。

### 2.4 配额（硬性）

- 强调色覆盖面积目标 **< 5% / 屏**
- 正文永不着色；着色只允许四类落点：①标题局部 ②1px 线 ③小几何符号 ④一个色块
- 明暗对比：任何文字与其底色 ≥ **4.5:1**

### 2.5 语义映射（来自官方主视觉的用色习惯）

| 色 | 语义 |
| --- | --- |
| 黄 | 测试 / 公测 / 主信号 |
| 青 | 备选信号 |
| 红 | 事件 / 前瞻（在本语言中仅用于状态警示，如 `overdue`） |
| 绿 | 版本 / 自然主题（不用于状态） |

---

## 3. 字体与排版

### 3.1 字体家族（最多两种 + 一种等宽）

| 角色 | 字体栈 |
| --- | --- |
| 中文正文 | `"HarmonyOS Sans SC", MiSans, ui-monospace, "Cascadia Mono", Consolas, Menlo, monospace` |
| 展示（拉丁大标题/大数字） | `"Arial Black", "HarmonyOS Sans SC", Arial, sans-serif`，`font-weight: 900`，`letter-spacing: .02em` |
| 元信息 / 标签 | `ui-monospace, "Cascadia Mono", "SF Mono", Consolas, Menlo, monospace` |

`assets/fonts/` 内的 HarmonyOS Sans SC 为 **GB2312 子集**（6763 汉字 + ASCII + 常用符号，
woff2 各 < 1MB）；子集外字符由浏览器**按字符**回退到栈内下一字体，不会缺字空白。

### 3.2 字号阶梯

| 尺寸 | 用途 |
| --- | --- |
| 11px | 元信息、标签、导航、状态栏（`uppercase`，字距 `.12–.14em`） |
| 13px | 次要数据、表格 |
| 14px | 正文基准 |
| 15px | 长文阅读区 |
| 16px | 列表条目标题 |
| 24 / 34px | 区块大标题 / 时钟与详情页标题（展示字体 900） |
| 46px | 装饰用幽灵大字（§5.4） |

### 3.3 数字与双语

- 所有会变化的数字加 `font-variant-numeric: tabular-nums`（时钟、计数、日期对齐）。
- **双语双层**是这套语言的标识手法：中文大字 + 其下的英文小字（`uppercase`、
  字距 `.12em+`、`--muted` 色）。
- 行高：元信息 1.65，标题 `.95–1.3`。

---

## 4. 布局

- **三栏网格**：`250px / 1fr / 300px`，间距 `14px`；容器最大宽度 `1180px`。
- **窄屏**（≤920px）：单列，并把次要面板重排到主内容之后。
- **密度控制**：列数可为 `2 / 3 / 4`（CSS 变量 `--cols`，默认 3）——对应官方档案页
  的 `Column − 3 +` 仪表面板交互。
- **仪表控件语汇**：`Section` / `Column − 3 +` / `◎ ＋ − ✕`；按钮与控件一律方形、
  1px 描边、等宽大写小字。
- **四角信息位**：左上放标识（品牌/模块名），右下放版本号与构建时间
  （示例：`MIND v0.2.0` + `LAST BUILD 2026-09-06 21:58`）。时间必须带标签，
  裸时间戳隔月会被误读为故障。
- **上留白 + 下收边**：内容区底部压一条 **3px 信号色收边带**（来自官方主视觉的
  "底部渐变压暗收边"手法）。
- 面板内边距 `16px 18px`，面板间距 `14px`。

---

## 5. 组件规范

| 组件 | 规格 |
| --- | --- |
| 顶栏 `.topbar` | 1px 描边，11px 大写，`--muted` 文字，品牌名用信号色 |
| 导航 `nav` | 标签式：1px 描边、无下边框、当前项信号色文字 |
| 面板 `.panel` | `--panel` 底 + 1px `--line` 描边 + `0 1px 0 var(--shadow)` |
| 区块标签 `.label` | 11px 大写；形如 `[01 // VAULT]`——编号 + `//` + 双语名 |
| 统计行 `.stat` | 左右两端对齐，数值用信号色 |
| 列表行 `.row` | 底部 1px 头发丝线，末行无线；标题 16px；右侧元信息 `nowrap` 且不收缩 |
| 标签 `.tag` | 11px `--muted`，`::before` 自动加 `#` |
| 状态栏 `.statusbar` | 11px 大写，顶部 1px 线 + **底部 3px 信号色** |

### 5.1 交互态

```css
/* hover：信号色实心反白（首选） */
background: var(--accent); border-color: var(--accent); color: var(--ink);
::selection      { background: var(--accent); color: var(--paper); }
:focus-visible   { outline: 2px solid var(--accent); outline-offset: 2px; }
/* 滚动条：细，轨道透明 */
scrollbar-width: thin; scrollbar-color: var(--line) transparent;  /* + WebKit 6px 版本 */
```

### 5.2 左缘刻度尺（工业感最强的单品）

```css
.panel::before{content:"";position:absolute;left:0;top:0;bottom:0;width:5px;
  background:repeating-linear-gradient(to bottom,
    var(--line) 0,var(--line) 1px,transparent 1px,transparent 10px);opacity:.75}
```

### 5.3 方括号标题

区块标题（`.label`）两侧自动加 `[` `]` 伪元素，信号色。
官方主视觉 6 张封面里 4 张使用了方括号/角标包标题，这是该品牌最高频的符号。

### 5.4 底边裁切幽灵大字

面板右下的巨大英文模块名，被容器底边**裁掉下半截**：

```css
.panel{position:relative;overflow:hidden}
.panel::after{content:attr(data-word);position:absolute;right:12px;bottom:-.36em;
  font-family:"Arial Black",Arial,sans-serif;font-weight:900;font-size:46px;line-height:1;
  letter-spacing:.04em;color:var(--ink);opacity:.055;pointer-events:none;white-space:nowrap}
```

用法：给容器加 `data-word="VAULT"` 这类属性即可，纯装饰、零信息量。

---

## 6. 背景与纹理

- **亮底**：纯纸色，不加纹理。
- **暗底（可选）**：28px 工业网格，1px 线，透明度 `.03`，双轴：

```css
background-image:
  repeating-linear-gradient(0deg,rgba(245,245,240,.03) 0,rgba(245,245,240,.03) 1px,transparent 1px,transparent 28px),
  repeating-linear-gradient(90deg,rgba(245,245,240,.03) 0,rgba(245,245,240,.03) 1px,transparent 1px,transparent 28px);
```

- 官方封面里还出现过蓝图线稿、故障像素块、水墨纸纹、半调网点——这些属于**可选扩展**，
  一次只用一种，不要叠加。

---

## 7. 动效

### 7.1 启动加载动画（本语言的招牌动效）

整屏遮罩（`#0a0b0a`），左缘 **10px 信号色进度轨自上而下填充**，
刻度/百分比/状态行跟随填充端一起下移（下边界钳位 94%，接近 100% 不滑出屏幕）。

| 阶段 | 时长 | 表现 |
| --- | --- | --- |
| 进度 | 900ms（`easeOutCubic`） | 轨自上而下填充，读数跟随下移 |
| 横向铺满 | 300ms | 到 100% 后由 10px 宽横向展开至整屏 |
| 整屏淡出 | 300ms | 连同遮罩淡至透明，节点移除 |

- 总时长 **1500ms**，每次进页播放一次。
- 主题/皮肤切换进入时播放 **850ms 短版**（350/300/200）。
- 品牌块（如 `END` / `FIELD` 双行）**右置但内部左对齐**，字号
  `clamp(26px,5.2vh,64px)`，取较小轴，窗口矮或窄都不与进度轨相撞。

工程约束（照抄，别省）：

1. 进度由**墙钟时间**推导（`Date.now()`），不逐帧累加，不漂移。
2. `requestAnimationFrame` 负责平滑，`setInterval(50ms)` 兜底——后台标签页 rAF 会停摆。
3. 独立 `setTimeout(总时长+800ms)` **硬性保险丝**，任何情况下遮罩必定移除。
4. 重复触发幂等（已存在遮罩则跳过）。
5. `pointer-events: none`（动画中也不拦截点击）+ `aria-hidden="true"`（纯装饰不朗读）。
6. `prefers-reduced-motion: reduce` → **完全不播放**。

### 7.2 其他动效

基线是**没有 transition**：hover/focus 变化即时生效。不引入视差、滚动动画、
淡入队列。要加动效时，只加"状态切换"类，不加"入场表演"类（loader 是唯一例外）。

---

## 8. 反面清单（Don't）

- ❌ 圆角（`border-radius` 非 0）、胶囊按钮
- ❌ 彩色大面积铺底、渐变按钮、毛玻璃、霓虹发光
- ❌ 悬浮投影卡片（只允许 `0 1px 0` 发丝线式阴影）
- ❌ 强调色用于正文或长段落
- ❌ emoji 当图标；几何符号只用 `◯ ● ＋ − ✕ ◎ ▶ ◀`
- ❌ 同时叠加两种以上纹理
- ❌ 浅色文字压浅底（对比度 < 4.5:1）
- ❌ 超过两种字体家族（正文 + 展示）+ 一种等宽
- ❌ 裸时间戳（必须带 `LAST BUILD` 之类标签）

---

## 9. 落地自检清单（agent 交付前逐条核对）

1. 强调色面积是否 < 5%？正文是否零着色？
2. 是否存在非 0 圆角、彩色大底、渐变按钮？（应为否）
3. 亮色态下强调色**文字**是否已下潜（`#fff500 → #6b5d00`）？
4. 文字与底色对比度是否全部 ≥ 4.5:1？
5. 数字是否启用 `tabular-nums`？元信息是否 11px 大写 + 字距？
6. 区块标题是否带 `[ ]` 方括号与编号双语？
7. 是否用了刻度尺 / 幽灵大字 / 底部 3px 收边带中的至少两种装饰？
8. 若含 loader：时序是否符合 900/300/300（短版 350/300/200）？六条工程约束是否齐全？
9. 是否遵守 `prefers-reduced-motion`？
10. 时间戳是否带标签？

---

## 10. 来源与致谢

- 设计语言参考：**[dsh-theme-endfield](https://github.com/ymh0000123/dsh-theme-endfield)**
  （© 2026 ymh0000123，MIT）——奶油纸底/墨黑文字/信号色强调/全直角工业风的令牌思路、
  加载动画与"图层是一个决定、让它动是另一个决定"的开关设计哲学。
- 主视觉参考：`assets/covers/` 六张官方宣传封面（版权归鹰角网络所有，仅作风格参考，
  详见 `CREDITS.md`）。
- 字体：**HarmonyOS Sans SC**（© 2021 Huawei Device Co., Ltd.），授权文本见
  `assets/fonts/LICENSE-HarmonyOS-Sans.txt`。
- 构图手法提炼来源：[ignoredone.space · 终末地美术资源系统](https://www.ignoredone.space/index.php/endfield_design/)
  （封面走查得出方括号标题、底边裁切幽灵大字、左缘刻度尺、底边收边带四条手法）。
- 官方站做法：[`reference/official-site.md`](reference/official-site.md)（像素采样配色 + 5 条可迁移做法）。
- 社区实现印证：[`reference/community-projects.md`](reference/community-projects.md)——
  ReEnd-Components（MIT）的 `--bracket-color` 与网格 alpha `.03`、endfield-gacha-app（MIT）的
  亮/暗强调色 `#d9b500 / #fffa00`，分别与本仓库的方括号标题、暗色网格、accent 下潜规则一致。
