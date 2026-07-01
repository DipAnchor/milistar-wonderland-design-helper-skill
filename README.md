# 千星奇域·玩法边界与实现查询助手

> 一个为 AI 设计的 Skill，用于查询原神「千星奇域」UGC 系统的玩法边界、系统能力与实现可行性。

## 概述

本 Skill 不存储具体的教程步骤或节点图配置细节，而是提供一套**检索方法论**，让 AI 能自行判断某个玩法在千星奇域沙箱编辑器中是否可行、以及如何找到实现参考。

核心工作流：
1. 拆解玩法核心机制
2. 搜索社区现有案例
3. 对照系统能力拓扑
4. 实时检索确认不确定性
5. 给出可行性结论

## 目录结构

```
milistar-wonderland-design-helper/
├── SKILL.md                          # 技能主文件：玩法可行性判定流程
├── README.md                         # 本文件
└── references/
    ├── sources.md                    # 检索与查询指南（含各 API 接口说明与优先级）
    ├── milistar-updatelog.md         # 月之三~月之八版本更新记录
    └── milistar-index/               # 综合指南本地索引（catalog.json + textMap.json）
```

## 使用场景

当需要回答以下问题时，应调用本 Skill：

- 「千星奇域能不能做XX玩法？」
- 「我想做一个XX类型的地图，技术路径是什么？」
- 「千星沙箱编辑器支持XX功能吗？」
- 「XX机制有没有社区实现案例？」

## 数据来源优先级

完整检索接口与说明详见 [`references/sources.md`](references/sources.md)，检索优先级从高到低：

| 优先级 | 来源 | 说明 |
|--------|------|------|
| ⭐1 | **知识库 API — SVG 图表检索** | 查组件配置图、参数枚举、操作步骤。端点 `https://ugc.070077.xyz/api/v1/svg/search` |
| ⭐2 | **知识库 API — Skill 工具** | `get_node_info`/`list_documents`/`get_document`/`rag_search`，查节点/文档/语义 |
| 3 | **知识库 API — 结构化数据** | 查物件、特效、音乐信息 |
| 4 | **知识库 API — 术语翻译** | 查 15 国翻译 |
| 5 | **知识库 API — 社区笔记** | 查社区笔记 |
| 6 | **官方综合指南** | 本地索引或内容文件直读 |
| 7 | **网页搜索** | B站、米游社、BWIKI、通用搜索（兜底） |

知识库 API 端点：`https://ugc.070077.xyz/`，PAI Skill 注册名：`miliastra-knowledge`。

## 前置依赖

本 Skill 配套使用 **miliastra-knowledge** 知识库 API（来自 skillhub 市场 `miliastra-toolbox`），无需额外配置即可查询千星沙箱节点、文档与编辑器图示。

## 维护说明

千星奇域随版本持续更新。当出现以下情况时，建议更新本 Skill：

- 新版本新增编辑器能力
- 已知限制被突破
- 社区发现新的实现技巧

更新时主要关注 官方更新公告和社区教程新发现。

能力验证优先调用 miliastra-knowledge 知识库 API 查证，其次搜索社区和官网。
