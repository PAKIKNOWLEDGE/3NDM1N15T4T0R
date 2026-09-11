# 3NDM1N15T4T0R

> **ENDMINISTRATOR** —— 《明日方舟：终末地》气质的 Web 设计语言规范。

一套可被 agent 直接套用的工业编辑风设计语言：中性纸底 + 墨黑文字、全直角、
1px 发丝线、**单一信号色小面积点缀**、编号双语标签、超粗实心大字硬压背景，
外加一个招牌的启动加载动画。

## 从这里开始

| 想要 | 去看 |
| --- | --- |
| 直接看效果 | [`examples/index.html`](examples/index.html)（单文件，双击打开） |
| 理解规范与理由 | [`DESIGN-LANGUAGE.md`](DESIGN-LANGUAGE.md) |
| 拿到精确数值 | [`tokens.json`](tokens.json)（颜色/字号/间距/时序，唯一来源） |
| 让 AI agent 照做 | [`AGENTS.md`](AGENTS.md)（硬约束 + 自检清单） |
| 校准气质 | [`assets/covers/`](assets/covers/)（六张官方主视觉） |
| 看官方站的做法 | [`reference/official-site.md`](reference/official-site.md)（含像素采样配色 + 5 条可迁移做法） |
| 看社区项目印证 | [`reference/community-projects.md`](reference/community-projects.md)（MIT 令牌已收录，AGPL 项目仅参考） |

## 风格一览

- **四条支柱**：中性底 · 单信号色 ≤5% · 全直角 · 靠字重与字距分层（不用阴影圆角）
- **两个配色方案**：谷地黄 `#fff500`（默认）/ 武陵青 `#14d0d0`（备选），亮暗双态
- **亮色态下潜规则**：强调色当文字用时 `#fff500 → #6b5d00`，当色块用时保留原色
- **装饰三件套**：左缘刻度尺、底边裁切幽灵大字、底部 3px 信号色收边带
- **招牌动效**：1500ms 启动加载动画（10px 信号色轨自上而下填充 → 横向铺满 → 淡出），
  工程上要求墙钟推导 + 双时钟 + 保险丝 + 幂等 + `reduced-motion` 跳过

## 目录

```
DESIGN-LANGUAGE.md   完整规范（含布局/组件/动效/反面清单/自检清单）
AGENTS.md            给 AI agent 的执行说明与硬约束
tokens.json          机器可读的设计令牌与规则
examples/index.html  可运行样例（内联样式与 loader 实现）
assets/covers/       官方主视觉参考（版权见 CREDITS.md）
assets/official-site/ 官网素材（分享图 + 公告横幅，分析见 reference/official-site.md）
assets/ui-kits/      社区设计系统的令牌文件（MIT，含许可原文与出处说明）
assets/fonts/        HarmonyOS Sans SC 子集 woff2 + 授权文本
reference/           外部来源分析：官网做法、社区项目许可与印证
CREDITS.md           来源、版权与许可
```

## 外部印证

本规范不是凭空推演：两套独立的社区实现分别得出了相同的结论——
[ReEnd-Components](https://github.com/VBeatDead/ReEnd-Components)（MIT）定义了 `--bracket-color`
与 `--bg-grid-color: rgba(255,255,255,.03)`，与我们的方括号标题、暗色网格 alpha `.03` 一致；
[endfield-gacha-app](https://github.com/RoLingG/endfield-gacha-app)（MIT）在亮色态用深黄 `#d9b500`、
暗色态用亮黄 `#fffa00`，正是本仓库的 **accentSinkRule**。详见
[`reference/community-projects.md`](reference/community-projects.md)。

## 许可

本仓库的**文档、代码与示例**以 MIT 许可提供（见 [LICENSE](LICENSE)）。
`assets/` 下的封面图与字体为第三方素材，**不适用** MIT，其版权与使用限制见
[CREDITS.md](CREDITS.md)。
