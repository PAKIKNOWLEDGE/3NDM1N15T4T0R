# CREDITS — 来源、版权与许可

本仓库分三类内容，许可各不相同。

## 1. 文档、代码与示例（MIT）

`DESIGN-LANGUAGE.md`、`AGENTS.md`、`tokens.json`、`examples/`、`README.md`
以及本设计语言本身的实现思路，以 **MIT** 许可提供，可自由使用、修改、再分发。
参见 [LICENSE](LICENSE)。

设计语言的部分思路参考了 **[dsh-theme-endfield](https://github.com/ymh0000123/dsh-theme-endfield)**
（© 2026 ymh0000123，MIT）——该系统化的主题令牌组织方式、设置开关分层，
以及"加载动画与遮罩层是一个决定、让它动是另一个决定"的设计哲学来自该项目。
本项目未复制其源代码。

## 2. 封面素材（`assets/covers/`）—— 版权归鹰角网络所有

六张图片为《明日方舟：终末地》官方宣传主视觉，**版权归上海鹰角网络科技有限公司
（HYPERGRYPH）所有**，此处仅作设计风格研究与参考之用：

| 文件 | 来源版本 |
| --- | --- |
| `0716.jpg` | 「向渊行」前瞻 |
| `0522.jpg` | 「寻遗散记」电台 |
| `0411.jpg` | 「春晓时」版本 PV |
| `0301.jpg` | 「新潮起 故渊离」版本 PV |
| `0128.jpg` | BACK TO ENDFIELD 公测 PV |
| `0101.png` | 全面测试 III PV |

图片经 [ignoredone.space · 终末地美术资源系统](https://www.ignoredone.space/index.php/endfield_design/)
整理与转存，本站为个人美术资源归档站，非官方站点。

**使用限制**：不得用于商业用途，不得声称版权归属自己，不得用于二次分发的素材包。
若权利人要求，应立即移除。若你 fork 本仓库用于公开项目，建议自行移除此目录
（文档中对这些图片的分析结论已完整写入 `DESIGN-LANGUAGE.md`，不依赖原图也能执行）。

## 3. 字体（`assets/fonts/`）—— 华为授权

**HarmonyOS Sans SC**（© 2021 Huawei Device Co., Ltd.），授权文本全文见
[`assets/fonts/LICENSE-HarmonyOS-Sans.txt`](assets/fonts/LICENSE-HarmonyOS-Sans.txt)。

关键条款摘要（以授权原文为准）：

- 允许免费使用，**含商业用途**；
- 允许将字体**嵌入应用软件等作品**中随之分发，并自由分发/销售该作品；
- **不得**将字体本体或其中任何组件作为**独立商品**再分发或销售；
- 任何副本中必须保留版权声明与授权协议文本（本仓库已保留 `LICENSE-HarmonyOS-Sans.txt`）。

此处提供的是 **GB2312 子集** woff2（Regular / Bold，各 < 1MB），
用于本设计语言的预览与落地；字符集外的字符会回退到系统字体。

## 4. 其他第三方内容

| 内容 | 位置 | 许可 | 说明 |
| --- | --- | --- | --- |
| ReEnd-Components 令牌文件 | `assets/ui-kits/reend-components/` | **MIT**（© 2025 VBeatDead） | `tailwind-preset.ts`、`index.css` 原样收录，许可原文随附 |
| endfield-gacha-app 令牌文件 | `assets/ui-kits/endfield-gacha-app/` | **MIT** | `theme.js` 原样收录，许可原文随附 |
| 官网素材 | `assets/official-site/` | 版权归鹰角网络 | 取自官网 CDN；分析结论见 `reference/official-site.md` |
| Talos-Pioneers/ui | 仅 `reference/` 中的**文字引用** | **AGPL-3.0** | **未复制任何代码**；理由见 `reference/community-projects.md` |
| Endfield Wiki（wiki.gg） | 仅 `reference/` 中的**链接引用** | 文字 CC BY-SA / 图像游戏版权 | 未收录其图片 |

## 5. 致谢

- 原始设计：**HYPERGRYPH / 鹰角网络** ——《明日方舟：终末地》视觉设计
- 令牌化组织参考：**[ymh0000123/dsh-theme-endfield](https://github.com/ymh0000123/dsh-theme-endfield)**（MIT）
- 设计系统印证：**[VBeatDead/ReEnd-Components](https://github.com/VBeatDead/ReEnd-Components)**（MIT）、
  **[RoLingG/endfield-gacha-app](https://github.com/RoLingG/endfield-gacha-app)**（MIT）
- 界面实现参考（未取代码）：**[Talos-Pioneers/ui](https://github.com/Talos-Pioneers/ui)**（AGPL-3.0）
- 素材归档：[ignoredone.space](https://www.ignoredone.space/index.php/endfield_design/)
- 资料索引：[Endfield Wiki](https://endfield.wiki.gg/)
- 字体：**Huawei Device Co., Ltd.**
