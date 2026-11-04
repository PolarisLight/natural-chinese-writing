# 自然中文写作

一个用于中文去AI味、自然表达和成稿语言审校的 AI 技能。按明确规则做最小修改，保留作者的事实、判断强度、体裁和文章框架。

技能名称：`natural-chinese-writing`。可用于 Codex 和 Claude Code。

## 关注的问题

- 冗余的自我辩护、免责声明、空泛谦辞和叠加对冲。
- 相邻句反复使用相同骨架，或合句后动作与对象的对应关系变得含混。
- 主语、中心名词或主要动作出现过晚，长前置定语与前置从句集中堆积。
- 动作之间缺少自然衔接，或末项连接导致并列层次不清。
- 揭晓式破折号、空转提示语、同义复述和聊天套话。

未命中规则的句子逐字保留。自然的“当……时”“对于……来说”和有作用的前后连接词继续保留，必要清单保留完整项目与原有关系。

本技能处理句内和原段内的语言表达。论文叙事、贡献定位、实验安排与章节重组，应另行指定相应写作任务和授权。

## 安装

### Codex

将仓库放入个人技能目录：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/PolarisLight/natural-chinese-writing.git ~/.codex/skills/natural-chinese-writing
```

### Claude Code

使用同一份 `SKILL.md` 和参考文件，将仓库放入 Claude Code 的个人技能目录：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/PolarisLight/natural-chinese-writing.git ~/.claude/skills/natural-chinese-writing
```

目录规则见 [Claude Code 官方技能文档](https://code.claude.com/docs/en/skills#choose-where-skills-load)。`agents/openai.yaml` 提供 Codex 的界面配置；Claude Code 从 `SKILL.md` 读取技能说明和参考文件入口。

## 使用

| 工具 | 显式调用 |
| --- | --- |
| Codex | `$natural-chinese-writing` |
| Claude Code | `/natural-chinese-writing` |

随后附上需要审校的文字，例如：

```text
请审校以下文字，保留事实、判断强度和文章框架，只输出审校后的全文：

〔待审校文字〕
```

需要查看修改依据时，可以要求输出“原文、改稿、对应规则”的对照表。

## 审校示例

例句为规则说明而自拟，覆盖论文、软件、工程操作、项目报告和一般表达。

| 场景 | 原文 | 审校结果 |
| --- | --- | --- |
| 软件排查 | 系统记录错误，便于后续排查。系统归档日志，便于后续排查。 | 系统记录错误，并归档日志，便于后续排查。 |
| 研究工具 | 能够帮助研究人员按实验条件检索已有数据的分析工具已完成部署。 | 分析工具能够帮助研究人员按实验条件检索已有数据，现已完成部署。 |
| 项目报告 | 新流程有助于减少重复录入，缩短审核时间，提高记录完整性。 | 新流程有助于减少重复录入，缩短审核时间，并提高记录完整性。 |
| 故障分析 | 问题不在于缓存容量，而在于失效策略。 | 问题出在失效策略，缓存容量没有造成这一问题。 |
| 研究范围 | 本研究仅分析三个数据集的评测结果，并不试图涵盖所有数据集。 | 本研究仅分析三个数据集的评测结果。 |
| 操作条件 | 当设备温度超过80℃时，停止运行。 | 当设备温度超过80℃时，停止运行。 |
| 一般表达 | 对于经常出差的人来说，行李重量也是需要考虑的因素。 | 对于经常出差的人来说，行李重量也是需要考虑的因素。 |

合并句架时，每个动作继续对应原来的对象。三个动宾短语并列时，可以用“并”或“以及”衔接末项，避免误读。名词并列则按语义选用“和”“或”等连接词。

## 文件

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | 技能入口、优先级、修改边界和执行要求 |
| [references/rules-and-examples.md](references/rules-and-examples.md) | 完整规则、触发条件、例外与原文／改稿对照 |
| [agents/openai.yaml](agents/openai.yaml) | Codex 显示名称和默认调用提示 |
| [LICENSE](LICENSE) | 本项目新增内容的 MIT 许可 |
| [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) | 上游来源版本、版权与完整许可声明 |

## 规则来源与许可

规则整理参考了 `lieflat-less-ai-tone`、`anti-defensive-writing`、`humanizer`、`humanizer-cn` 和 `humanize-writing` 的语言审校部分，并通过逐条例句审阅，补充了中文语序、动作与对象的对应关系、衔接和并列表达规则。

本项目新增内容采用 [MIT 许可](LICENSE)。上游改编部分保留各自版权与许可声明，详见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。其中 lieflat 以已核验的 [MIT 历史版本](https://github.com/larashero3-dotcom/lieflat-less-ai-tone/tree/27d29232f10124db904ca9c0536d0b67cb3b2833) 为来源。
