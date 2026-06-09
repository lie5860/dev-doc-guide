# Dev Doc Guide

`dev-doc-guide` 是一个 Codex 技能，用于编写或评审中文研发文档。

它的核心职责不是直接充当某一份模板，而是先判断用户要的文档类型，再路由到对应的写作指南，确保文档的层级、边界和内容深度正确。

## 覆盖范围

本技能覆盖四类常见研发文档：

| 文档类型 | 指南文件 | 主要回答的问题 |
| --- | --- | --- |
| 需求分析 | `requirements-analysis.md` | 为什么要做、做什么、边界是什么、用户如何使用、怎样验收。 |
| 概要设计 | `summary-design.md` | 总体怎么做、分成哪些模块、模块之间如何协作、关键决策是什么。 |
| 详细设计 | `detailed-design.md` | 工程师如何按文档实现、联调和验证。 |
| 架构文档 | `architecture-design.md` | 系统为什么这样组织、关键组件如何分工、如何满足质量属性、未来如何演进。 |

## 适用场景

当用户要求编写或评审以下内容时，适合使用本技能：

- 需求分析、需求规格说明、需求说明书、PRD
- 概要设计、总体方案、系统概要设计
- 详细设计、接口设计、模块设计、代码实现方案
- 架构文档、应用架构、系统架构、架构设计
- “技术方案”“按我的文档风格”“帮我写一份研发文档”等文档类型不明确的请求

## 工作方式

`SKILL.md` 是技能入口，只负责文档类型判定、路由和边界提醒。

真正写作或评审时，Codex 需要根据文档类型读取对应子指南：

- `requirements-analysis.md`
- `summary-design.md`
- `detailed-design.md`
- `architecture-design.md`

每份输出文档应先声明：

```text
本文档类型：<需求分析 / 概要设计 / 详细设计 / 架构文档>。使用子指南：<对应子指南文件名>。
```

## 安装

克隆到 Codex 用户级技能目录：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/lie5860/dev-doc-guide.git ~/.codex/skills/dev-doc-guide
```

然后重启 Codex 或开启新会话，使技能元信息重新加载。

## 仓库结构

```text
dev-doc-guide/
├── SKILL.md
├── requirements-analysis.md
├── summary-design.md
├── detailed-design.md
├── architecture-design.md
└── README.md
```

## 维护原则

本技能保持项目无关，只沉淀通用的中文研发文档分类、边界和写作指南。

团队专属模板、产品术语、仓库约定、业务背景和项目流程，应放在目标项目自己的文档、规范或本地技能里。
