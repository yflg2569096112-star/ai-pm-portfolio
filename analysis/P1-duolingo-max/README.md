# P1 · Duolingo Max 深度拆解

> AI PM 转型 16 周训练 · W1 案例库 #1 · 2026-05-24

## 核心判断

**30 美金月费的 AI 老师，正在被 Duolingo 自己降级。**

2026 Q1 财报里 Duolingo 把 Max 独占的 Video Call 下放到便宜的 Super 层——这是 LLM-as-product 商业模式被市场用脚投票的结构性教训，比任何成功案例都值钱。

## 文件导览

| 文件 | 内容 |
|---|---|
| [`P1-duolingo-max-v1.html`](./P1-duolingo-max-v1.html) | **主拆解** · 2856 字 · 战略变阵 / 功能矩阵 / AI 架构 / 商业拷问 / 移植雅思 / 5 教训 |
| [`P1-duolingo-101.html`](./P1-duolingo-101.html) | 小白入门科普 · 模拟手机界面演示 Duolingo / Roleplay / Video Call 是什么样 |

> 下载后用浏览器打开效果最佳（GitHub 网页不直接渲染 HTML 样式）

## 3 个最值钱发现

1. **战略变阵信号**：Max 占付费用户仅 9%（约 98 万人），CEO 主动把 Video Call 撤回 Super，理由是"让 10 倍多人用上"——官方撤退信号
2. **护城河之问**：所有差评指向同一句话——"ChatGPT 免费能做"。LLM-as-product 没有结构性护城河
3. **雅思赛道空白**：搜遍中英文，雅思圈没有 Max 级别的整合产品，全是 GPT 套壳小工具——这是集团级 AI 解决方案的明确机会点

## 移植到雅思 · 5 条产品路径

| # | 动作 | 对接资产 |
|---|---|---|
| 1 | Roleplay → 雅思 Part 2 题卡对话演练 | 口语 Flashcard 工具（E3 升级方向） |
| 2 | Explain My Answer → 写作错题语法卡 | Task1 写作工具（E1 升级方向） |
| 3 | Video Call → AI 雅思考官（**需绑名师 IP**，慎做） | 集团方案而非 indie |
| 4 | Birdbrain 自适应层 → 学员画像 + 错题档案 | 集团已有学员数据（最被低估的资产） |
| 5 | **不做 Max 层，做 Super 层** | 集团网课 + AI 增强能力 |

## 5 个教训（给 AI 教育产品的判断）

1. **LLM-as-product 没有护城河** — 用户付 $20/月用 ChatGPT 能解决你 80% 功能
2. **AI 反馈的"可看完率"比"准确率"重要** — Explain My Answer 是 Max 投入产出比最高的功能
3. **语音对话要么做到 Realtime 级别，要么不如不做** — Lily 被吐槽"无聊、慢"的根源
4. **定价层级是教学法的承诺，不是营销话术** — 把功能撤回 Super 等于公开承认错估
5. **有学员数据的玩家有不公平优势** — Birdbrain 是 Duolingo 真正抄不动的东西

## 证据强度梯队

| 主题 | 强度 | 来源 |
|---|---|---|
| 定价 / Q1 FY26 财报 | 🟢 强 | SEC 8-K（一手） |
| 功能矩阵 / DuoCon 2024-25 | 🟢 强 | Duolingo 官方博客 + 投资者公告 |
| GPT-4 + Birdbrain 架构 | 🟢 强 | SEC 申报 + OpenAI 官方 |
| Max 渗透率 9% | 🟡 中 | Q1 FY26 earnings call 二手转述 |
| 用户反馈正负面 | 🟡 中 | 评测博客拼凑（Reddit 原帖未抓） |
| Video Call 技术链路 | 🔴 弱 | 评测者推测，Duolingo 未公开 |
| 雅思赛道空白 | 🟡 中 | 反向证据——搜不到本身就是信号 |

完整 source 列表（强 / 中 / 弱 三梯队）→ 见 v1 文末

## 元信息

- **训练任务 ID**：`P1` · W1 案例库第 1 篇
- **配套技术任务**：[T1 · 雅思口语题卡 AI 系统](../../skills/T1-feishu-base-ielts/)
- **下一篇**：P2 · Speak（speak.com）— 同赛道竞品对标，对接 E3 口语 Flashcard 升级
