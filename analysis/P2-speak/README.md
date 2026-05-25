# P2 · Speak (speak.com) 深度拆解

> AI PM 转型 16 周训练 · W1 案例库 #2（提前到 W1 完成） · 2026-05-24

## 核心判断

**Realtime API 是分水岭——没切的 AI 口语产品都会被淘汰。**

Speak 在过去 18 个月做对了 Duolingo Max 没做的一件事：第一时间切到 OpenAI Realtime API，把 AI 口语对话做成端到端 speech-to-speech 体验。结果是：$1B 独角兽估值、ARR 一年从 $50M 翻到 $100M+、**韩国市场营收已超过 Duolingo**。

## 文件导览

| 文件 | 内容 |
|---|---|
| [`P2-speak-v1.html`](./P2-speak-v1.html) | **主拆解** · 2702 字 · 商业奇迹 / 功能矩阵 / AI 架构对比 / 反馈机制弱点 / 移植雅思 / 5 教训 |
| [`P2-speak-101.html`](./P2-speak-101.html) | 小白入门科普 · 模拟手机界面 + 接力赛 vs 直传类比 + 间隔重复曲线图 |

> 下载后用浏览器打开效果最佳（GitHub 网页不直接渲染 HTML 样式）

## 3 个最值钱发现

1. **🎯 Realtime API 官方案例**：Live Roleplays 用 GPT-4o 端到端 speech-to-speech，OpenAI 官方点名为早期合作伙伴——**正是 P1 推测 Duolingo Max 没切的同一个 API**
2. **🦄 商业表现碾压**：$1B 独角兽，ARR 一年翻倍（$50M→$100M+），B 端 500+ 企业（KPMG / 现代汽车），员工 adoption 85%
3. **🕳️ 雅思赛道再次空白**：Speak 没有 IELTS 专门模块——和 P1 一致信号，**头部 AI 口语产品都不做雅思**，集团方案空间持续验证

## 关键技术差异 · Speak ↔ Duolingo Max

| 维度 | Duolingo Max | Speak |
|---|---|---|
| Voice 技术 | STT→GPT-4→TTS（推测） | ✅ **Realtime API 端到端** |
| 延迟 | 1-2 秒 | **< 200 ms** |
| ASR | 第三方 | 自研 Conformer-CTC |
| 主战场 | 美国大本营 | 亚洲优先（韩国 #1） |
| 商业 | $30/月 撤退 9% | $20/月 + B 端 500+ |
| 反馈机制 | Explain My Answer（强） | ⚠️ "最弱的部分" |

## 移植到雅思 · 5 条产品路径

| # | 动作 | 对接 |
|---|---|---|
| 1 | 优先切 Realtime API（不再做三段式） | E3 口语 Flashcard 升级的<strong>第一技术决策</strong> |
| 2 | 把反馈机制做深（Speak 留给后来者的礼物） | 错题语法卡 + spaced repetition + 月度叙事报告 |
| 3 | STT 严判 + 雅思级发音评分 | 反 Speak 的"宽容"，集团差异化点 |
| 4 | 严格场景化 Part 1/2/3（反 Speak 的 Free Talk） | E3 升级方向 |
| 5 | B 端集团方案（Speak 已验证可行） | 新航道集团已有学员 + 教师 + 课程 |

## 5 个教训

1. **Realtime API 是分水岭，不是优化项** — 2026 还在做三段式的产品都会被淘汰
2. **自研 ASR 是被低估的护城河** — Speak 用 Conformer-CTC fine-tune 甩开第三方 40-60% WER
3. **反馈机制是"对话量"产品的反向护城河** — Speak 弱在这，留给后来者明确空间
4. **亚洲市场 ARPU 不输欧美** — Speak 韩国营收超 Duolingo，但定价逻辑要本地化重写
5. **通用 AI 口语产品天花板有限** — 考试 / 雅思 / 职场专项细分仍有空间，集团有不公平优势

## 证据强度

| 主题 | 强度 |
|---|---|
| 融资 / 估值 / ARR | 🟢 强（TechCrunch + Crunchbase + 官方 Series C 公告） |
| Realtime API 用法 | 🟢 强（OpenAI + Speak 双方官方确认） |
| 自研 ASR Conformer-CTC | 🟢 强（Speak 官方技术博客） |
| 韩国营收超 Duolingo | 🟡 中（CEO 访谈二手转述） |
| Premium Plus 定价 | 🔴 弱（多评测说不透明） |
| 用户反馈"feedback 最弱" | 🟢 强（多源一致） |
| Speak 没有 IELTS 模块 | 🟢 强（反证多源） |

完整 source 列表 → 见 v1 文末

## 元信息

- **训练任务 ID**：`P2` · W1 案例库第 2 篇（提前到 W1 完成）
- **配套技术任务**：[T1 · 雅思口语题卡 AI 系统](../../skills/T1-feishu-base-ielts/)
- **上一篇**：[P1 · Duolingo Max](../P1-duolingo-max/) — 行业旗舰失败教训
- **下一篇**：P3 · Khanmigo（Khan Academy）— AI 导师范式
