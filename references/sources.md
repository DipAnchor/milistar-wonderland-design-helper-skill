# 千星奇域 · 检索与查询指南

> 信息来源优先级：**知识库 API** > 本地索引 > 综合指南内容文件 > 社区来源。

## 一、知识库 API（miliastra-knowledge）⭐ 最高优先级

端点：`https://ugc.070077.xyz/`。PAI 注册 Skill：`miliastra-knowledge`。

### SVG 图表检索（组件配置图）⭐ 优先

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/v1/svg/index` | GET | SVG 目录结构 |
| `/api/v1/svg/search` | GET | 按名称模糊搜索 SVG（`?png=true` 渲染为 PNG） |
| `/api/v1/svg/raw/{filename}` | GET | 精确获取 SVG 原始内容或 PNG |
| `/api/v1/svg/resolve` | GET | 解析 SVG 的可浏览 URL |

### 节点检索（全文匹配）

| 接口 | 方法 | 说明 |
|------|------|------|
| `/api/v1/skills/miliastra-knowledge/tools/get_node_info` | POST | 查节点信息 |
| `/api/v1/skills/miliastra-knowledge/tools/list_documents` | POST | 列出文档 |
| `/api/v1/skills/miliastra-knowledge/tools/get_document` | POST | 获取文档全文 |
| `/api/v1/skills/miliastra-knowledge/tools/rag_search` | POST | 语义检索 |

### 结构化数据查询

| 接口 | 方法 | 查询参数 | 说明 |
|------|------|----------|------|
| `/api/v1/data/gadgets` | GET | `id`, `name`(模糊), `limit`, `offset` | 物件 ID/中文名/尺寸 |
| `/api/v1/data/effects` | GET | `id`, `name`(模糊), `limit`, `offset` | 特效 ID/名/时长/半径 |
| `/api/v1/data/bgm` | GET | `id`, `name`(模糊), `limit`, `offset` | 音乐 ID/名/时长/类别 |

## 二、官方综合指南（兜底）

| 方式 | 说明 |
|------|------|
| **本地索引** | `references/milistar-index/` 下 `catalog.json`（目录）+ `textMap.json`（全文），直接关键词检索，无需网络 |
| **内容文件直读** | `https://act-webstatic.mihoyo.com/ugc-tutorial/knowledge/cn/zh-cn/{path_id}/content.html?game_biz=hk4eugc_cn&lang=zh-cn`，从 `catalog.json` 取 path_id 拼 URL |
| **文本映射检索** | `textMap.json` 跨章节关键词检索 |
| **SPA 用户链接** | `https://act.mihoyo.com/ys/ugc/tutorial/detail/{path_id}`（给用户看别用静态 URL） |

> 获取 `catalog.json` 时 `max_length` 建议不低于 30000，避免截断漏条目。

## 三、社区来源

| 来源 | 检索方式 |
|------|----------|
| BWIKI | `https://wiki.biligame.com/ys/千星奇域` — 结构化百科 |
| B站教程 | 搜索 `千星奇域 + 教程/沙箱/节点图` |
| NGA论坛 | `https://ngabbs.com/` 搜索千星奇域 |
| 本地更新日志 | `references/milistar-updatelog.md` |

## 四、搜索关键词模板

- `千星 [类型] 关卡 制作` / `千星 [玩法] 实现` / `千星 教程 [玩法]`
- `千星 节点图 [功能]` / `千星 触发器 [条件]` / `千星 变量 [用法]`
- `千星 能不能 [功能]` / `千星 [问题] 怎么解决` / `千星 [功能] 限制 上限`
