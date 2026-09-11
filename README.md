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
assets/fonts/        HarmonyOS Sans SC 子集 woff2 + 授权文本
CREDITS.md           来源、版权与许可
```

## 许可

本仓库的**文档、代码与示例**以 MIT 许可提供（见 [LICENSE](LICENSE)）。
`assets/` 下的封面图与字体为第三方素材，**不适用** MIT，其版权与使用限制见
[CREDITS.md](CREDITS.md)。
