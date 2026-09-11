# 参考：社区项目与索引站

本文件登记本设计语言的**外部来源**，说明各自许可、我们取了什么、刻意没取什么。
原则：**只吸收设计事实与许可允许的代码；AGPL 项目只做参考、零代码复制。**

---

## 1. ReEnd-Components —— 已采纳（MIT）

- **仓库**：https://github.com/VBeatDead/ReEnd-Components
- **自述**：Arknights: Endfield Design System — React 组件库（Tailwind CSS + TypeScript + Radix UI）
- **许可**：**MIT**，© 2025 VBeatDead（许可原文见 `assets/ui-kits/reend-components/LICENSE`）
- **采纳内容**：`tailwind-preset.ts`（Tailwind 预设与令牌）、`index.css`（语义令牌与工业风样式），
  原样保留于 `assets/ui-kits/reend-components/`，供对照取用。
- **它的令牌与本仓库的印证**：
  - `--bracket-color`（方括号标题色）↔ 我们的 §5.3 方括号标题
  - `--bg-grid-color: rgba(255,255,255,0.03)`（暗底）/ `rgba(0,0,0,0.04)`（浅底）↔ 我们 §6 暗色网格 **alpha .03**
  - 字体栈 `Orbitron`（展示）/ `Bender` / `JetBrains Mono`（等宽）/ `Source Han Sans · Noto Sans SC`（中文）
    ↔ 我们的"展示字 + 等宽元信息 + 中文无衬线"三分法
  - 语义色标 `--text-primary/secondary/tertiary/muted/placeholder/disabled` 六级灰阶
    ↔ 我们的 `--ink / --muted` 两档（他们的粒度更细，可作扩展参考）

## 2. endfield-gacha-app —— 已采纳（MIT）

- **仓库**：https://github.com/RoLingG/endfield-gacha-app
- **自述**：明日方舟：终末地 寻访记录终端（Wails + Go/JavaScript 桌面端）
- **许可**：**MIT**（许可原文见 `assets/ui-kits/endfield-gacha-app/LICENSE`）
- **采纳内容**：`frontend/src/theme.js`（亮/暗双态令牌），原样保留于 `assets/ui-kits/endfield-gacha-app/`。
- **它的令牌与本仓库的印证（重要）**：
  - 亮色态强调色 `#d9b500`（深黄）／暗色态 `#fffa00`（亮黄）
    ↔ 我们 `tokens.json` 的 **accentSinkRule**（亮底强调色下潜）。**两个独立项目各自得出同一规律**。
  - `--ef-chip-border/--ef-chip-text: #d45a2a`（橙）作状态色 ↔ 我们的状态色语义分工
  - 未采纳：其 `assets/icons/*.ico`（托盘图标，非设计语言）、`assets/images/logo.jpg`（792KB，游戏美术）
    与其字体 `nunito`（OFL，但与终末地观感无关）

## 3. Talos-Pioneers/ui —— 仅参考，零代码（AGPL-3.0）

- **仓库**：https://github.com/Talos-Pioneers/ui
- **自述**：Arknights Endfield Blueprints UI Components（Vue）
- **许可**：**AGPL-3.0** —— 强著佐权 + 网络分发条款。
- **处理方式**：**不复制任何代码、不 vendor、不做目录级混放**。原因：
  1. 本仓库文档/代码以 MIT 提供，混入 AGPL 会给所有使用者带来合规负担；
  2. AGPL 的网络条款对"以服务形式提供"场景有额外义务，而设计规范仓库的用途是**被自由取用**；
  3. 若确实要用它的组件，正确姿势是**由使用方以依赖形式接入**（`npm install`），许可责任随之转移。
- 如需吸收其**实现思路**，应做 clean-room 重写（看思路、自己写），不要改写量名式搬运。
- 提示：此类社区 UI 仓库常内置游戏美术资源——那是鹰角 IP，与 AGPL 是两套权利，即便代码可用美术也不可随搬。

## 4. Endfield Wiki（wiki.gg）—— 仅参考链接

- **站点**：https://endfield.wiki.gg/ （主页面 `/wiki/Main_Page`；用户给出的带追踪参数的 URL 会 404）
- **定位**：游戏**数据与术语**索引（角色、道具、剧情），非 UI 设计资源。
- **实测**：其图片库以角色立绘/封面为主（`456_Endfield_*.png`，单张 4–6MB），**对界面设计语言参考价值低**，
  故未采图，仅登记为术语/文案对照来源。
- 文字内容为 CC BY-SA（署名—相同方式共享），图像多为游戏版权素材——**引用时请核实各自页脚标注**。

## 5. 相关但不属于本仓库素材的其他来源

- 官方封面六图（`assets/covers/`）：经 ignoredone.space 归档整理，出处与版权见根目录 `CREDITS.md`。
- 官方站点素材（`assets/official-site/`）：取自官网 CDN，分析结论见 `reference/official-site.md`。
