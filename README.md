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
    ├── sources.md                    # 信息来源与检索指南（含无头浏览器操作流程）
    ├── milistar-updatelog.md         # 月之三~月之八版本更新记录
    └── milistar-index/               # 综合指南本地索引（catalog.json + textMap.json）

> 另有 miliastra-knowledge Skill（skillhub 市场 `miliastra-toolbox` v1.0.3）
> 作为专用知识库 API 数据源，通过 `https://ugc.070077.xyz/` 提供节点/文档查询。
```

## 使用场景

当需要回答以下问题时，应调用本 Skill：

- 「千星奇域能不能做XX玩法？」
- 「我想做一个XX类型的地图，技术路径是什么？」
- 「千星沙箱编辑器支持XX功能吗？」
- 「XX机制有没有社区实现案例？」

## 数据来源

| 来源 | 用途 |
|------|------|
| 本地综合指南索引（references/milistar-index/） | 目录+章节全文，本地快速检索官方综合指南，优先于在线搜索源 |
| miliastra-knowledge API | 专用千星沙箱知识库查询（节点说明/文档/语义检索） |
| 米游社官方综合指南 | 最新编辑器官网文档（无头浏览器实时检索） |
| B站搜索 API | 社区视频教程与实机案例 |
| 米游社千星奇域专区 | 社区讨论与作品分享 |
| BWIKI | 系统数据百科 |
| 本地更新日志 | 月之三~月之八版本变更汇总 |

## 前置依赖

本 Skill 配套使用 **miliastra-knowledge** 知识库 API（来自 skillhub 市场 `miliastra-toolbox` v1.0.3），无需额外安装即可查询千星沙箱节点与文档。

使用无头浏览器搜索米游社功能需要安装 `agent-browser`：

```bash
npm install -g agent-browser
agent-browser install  # 下载 Chromium
```

若环境无无头浏览器，仍可通过用户导出的 MHTML 文件获取官方文档内容。

## 维护说明

千星奇域随版本持续更新。当出现以下情况时，建议更新本 Skill：

- 新版本新增编辑器能力
- 已知限制被突破
- 社区发现新的实现技巧

更新时主要关注 官方更新公告和社区教程新发现。

能力验证优先调用 miliastra-knowledge 知识库 API 查证，其次搜索社区和官网。
