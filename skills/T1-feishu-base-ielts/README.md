# T1 · 雅思口语 Part 2 题卡 AI 批量生成系统

> AI PM 训练 W1 · 提示词工程 + AI 嵌入企业工作流 demo
> Tags: `prompt-engineering` `feishu-base` `lark-bitable` `ielts` `ai-education` `enterprise-ai-workflow`

## 一句话

在新航道集团内部，用飞书多维表格 + AI 字段把 Part 2 题卡备课流程做成可批量跑的 AI 生产线——输入话题，AI 自动产出题卡 + 4 维评分要点 + 7.5-8.0 范文 + 5 条常见错误。教师备 20 道题从 5 小时压到 30 分钟。

**两个层次的价值**：
1. **教研生产力**：教师/教研组真实可用的内部工具
2. **求职作品集**：证明能把 AI 嵌进真实企业工作流（不是 toy demo）

## 部署环境

- 平台：**飞书多维表格**（Lark Bitable）+ AI 字段捷径
- 租户：**新航道国际教育集团**企业飞书
- 模型：豆包 Pro / DeepSeek-R1（飞书内置）
- 用户：教师 / 教研组（内部工具，非学员前台）

> ⚠️ 应用本身在企业租户内，外部账号无法直接访问。本 repo 以截图 + 配置文档形式归档。

## 截图

| 文件 | 内容 |
|---|---|
| `screenshots/feishu-base-overview.png` | 表格全貌 + 新航道企业飞书租户面包屑（证明企业内部场景） |
| `screenshots/feishu-ai-field-config.png` | AI 字段「评分要点」配置面板，含完整 prompt 文本（核心工程证据） |
| `screenshots/feishu-output-detail-essay.png` | 第 1 行「科技」范文完整展开（180-220 词 + 自然口语化痕迹） |
| `screenshots/feishu-output-detail-errors.png` | 第 1 行「科技」常见错误完整展开（5 条具体到语法/词汇点）|

## 技术要点

- **System Role**：BC 认证考官口径，12 年带考经验设定
- **Prompt 链式调用**：4 个 AI 字段分工 + 跨字段引用
  - 字段 2「题卡」← 引用「话题」
  - 字段 3「评分要点」← 引用「话题」+「题卡」
  - 字段 4「范文」← 引用「话题」+「题卡」
  - 字段 5「常见错误」← 引用「话题」
- **Few-Shot**：3 个不同话题类型（物品 / 人物 / 地点）的完整范例做 in-context learning
- **关键约束设计**：
  - 范文目标 7.5-8.0（不要 9.0，避免 AI 痕迹）
  - 强制自然口语化特征（well / you know / I mean）
  - 禁中文字符（防止跨语种幻觉）
  - 错误库强制"话题特异性"（禁通用错误模板）

## 文件结构

```
T1-staging/
├── README.md                       ← 本文件
├── feishu-config.md                ← 飞书 4 字段拆解 prompt（生产版）
├── prompt.md                       ← Coze 单 prompt 版（参考，未启用）
├── examples/
│   ├── 01-technology.json
│   ├── 02-person.json
│   └── 03-place.json
├── screenshots/                    ← 4 张飞书截图
├── T1-prompts-v2.html              ← v2 prompt 升级（针对 v1 问题）
├── T1-rebuild-5steps.html          ← 手动重建 5 步走（备用）
├── T1-one-prompt-build.html        ← 飞书 AI 助手一键搭建 prompt
├── T1-reframe-analysis.html        ← T1 路径决策（A/B/C）
├── T1-path-decision-v2.html        ← 查证飞书官方文档后的路径选型
├── T1-final-plan-v3.html           ← Aily 权限确认后的最终方案
└── T1-final-screenshot-and-archive.html  ← 截图 + 归档指南
```

## 学到了什么

**v1 → v2 prompt 迭代过程的 4 个关键发现**：

1. **字数硬约束需要"自查清单"**才能压住模型。v1 prompt 只说"180-220 词"，结果 4/5 行写到 250-290 词；v2 加了"写完前数词数 + 删冗余"的强制自查流程，才把长度压到合规。**模型的默认倾向是"多写"，必须用结构化约束反向施压**。

2. **跨语种环境的 prompt 必须显式禁字符**。v1 在英文范文里偶发出现中文字符"观察"（AI 幻觉）。v2 加"100% 英文，禁止任何中文字符"硬约束后消除。**多语种企业环境的 prompt 工程必须把"输出语言纯度"作为一类显式约束**。

3. **通用错误库会被模型当万金油塞进每个话题**。v1 5 个话题里"用 effect 代替 affect""漏掉 how-feel bullet"这两条错误重复出现 3-5 次——模型在用"安全通用答案"偷懒。v2 加"话题特异性原则 + 通用错误黑名单"后强制每个话题输出独家错误库。**Prompt 工程要主动识别并切断模型的"懒惰路径"**。

4. **段落格式塌陷需要显式换行约束**。v1 某些行输出把 4 段评分要点挤在一起；v2 加"段落标题必须各自独立成行 + 段落间空一行"后解决。**Markdown 格式不是模型默认遵守的，要显式声明**。

**最大的体感**：

> **Prompt 工程的本质是和模型"反 over-helping"博弈**——它倾向于给你更长、更通用、更安全的输出。Prompt 工程师的工作不是"写出能跑的指令"，而是"写出能让 AI 不越界的约束"。这套思维在任何 AI 产品的 prompt 调优场景都通用。

## 路径选型说明

| 阶段 | 选择 | 原因 |
|---|---|---|
| 最初计划 | Coze 单 bot | 个人版无权限，企业版需付费/申请 |
| 实际 v1 | 飞书多维表格 + AI 字段 | 企业账号现成，可批处理，业务工作流原生 |
| W5+ 升级路径 | 飞书 Aily 智能体（同租户，原生调 Bitable 数据）| 学生端对话入口，端到端企业 AI 产品故事完整 |

## 和其他项目的关系

- **同领域 Part 3 工具**（消费侧）：[ielts-flashcard](https://github.com/yflg2569096112-star/ielts-flashcard)
- **下游升级路径 E1**：W5-W8 用飞书 Aily 搭学生端对话 bot，调用本表 Bitable 数据，组成完整双端 AI 教育产品

## 完成状态

- [x] Prompt 设计 v1（4 字段拆解）
- [x] Few-shot 范例（3 个完整 JSON）
- [x] 飞书多维表格搭建（新航道企业租户）
- [x] 5 主题 × 4 字段 v1 测试运行
- [x] v1 输出诊断（识别 4 类问题）
- [x] Prompt v2 升级（针对性修复 4 类问题）
- [x] 截图归档（4 张）
- [x] 复盘填入 README
- [ ] Push GitHub（待 gh CLI 安装 + ai-pm-portfolio monorepo 创建）

## 简历可写 Bullet

> 在新航道集团内部以飞书生态搭建端到端 AI 教研工具：用多维表格 AI 字段做 4 段 prompt 链式调用，批量生产 Part 2 题卡+评分+范文+错误库，单次处理 5 话题 × 4 字段 = 20 个 AI 单元。完整双端产品全栈在企业内部 IT 完成，符合教育行业 PII 合规要求。Prompt 经过 v1→v2 迭代，针对长度失控、跨语种幻觉、通用错误堆砌、格式塌陷四类问题设计硬约束。
