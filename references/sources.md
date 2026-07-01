# 千星奇域 · 信息来源与检索指南

> 本文件记录可用的信息来源和检索策略。

## 一、官方来源

| 来源 | 地址 | 内容说明 |
|------|------|----------|
| 千星奇域官网 | https://ys.mihoyo.com/miliastra_wonderland/ | 公告、新闻、版本更新 |
| 官方综合指南（文档&更新日志） | **内容文件（AI读取用）**：`https://act-webstatic.mihoyo.com/ugc-tutorial/knowledge/cn/zh-cn/{path_id}/content.html?game_biz=hk4eugc_cn&lang=zh-cn`<br>**目录（在线）**：`https://act-webstatic.mihoyo.com/ugc-tutorial/knowledge/cn/zh-cn/catalog.json?game_biz=hk4eugc_cn&lang=zh-cn`<br>**文本映射（在线）**：`https://act-webstatic.mihoyo.com/ugc-tutorial/knowledge/cn/zh-cn/textMap.json?game_biz=hk4eugc_cn&lang=zh-cn`<br>**目录+文本映射（本地）**：`references/milistar-index/`<br>**SPA页面（用户查看用）**：`https://act.mihoyo.com/ys/ugc/tutorial/detail/{path_id}` | 见下方动态页面处理规则说明 |
| 官方教程首页 | https://act.mihoyo.com/ys/ugc/tutorial/course/home | 分步创作教程（新手入口） |
| 奇匠学院 / 创作者中心 | https://act.mihoyo.com/ys/ugc/tutorial/course/home | 同一页面不同模块：奇匠学院=进阶教程 / 创作者中心=创作入口 |
| 千星奇域B站官号 | https://space.bilibili.com/3546889200863460 | ⚠️ 需手动访问。官方视频教程、版本演示 |
| 千星奇域米游社官号 | https://www.miyoushe.com/ys/accountCenter/postList?id=378227958 | ⚠️ 需手动访问。官方公告、活动资讯 |
| 米游社专区 | https://www.miyoushe.com/ys/topicDetail/2168 | 社区讨论、作品分享 |

> **动态页面处理规则**：标记 ⚠️ 的页面为纯前端渲染页面（SPA），传统的网页抓取工具无法获取其内容。但综合指南的内容文件本身是静态 JSON/HTML，可通过规律 URL 直接访问，无需浏览器渲染。处理方式优先级如下：
> 0. **本地索引优先** — `references/milistar-index/` 下已缓存 `catalog.json`（目录结构）和 `textMap.json`（章节全文），可直接读取本地文件实现目录查询和关键词检索，无需网络请求。若需要最新版本，再走在线来源。
> 1. **内容文件直接访问** — 综合指南的内容托管在 `act-webstatic.mihoyo.com`，URL 模式为 `https://act-webstatic.mihoyo.com/ugc-tutorial/knowledge/cn/zh-cn/{path_id}/content.html?game_biz=hk4eugc_cn&lang=zh-cn`。从 `catalog.json` 获取文档的 `path_id` 后即可直接拼出 URL，用普通抓取工具即可获取全文。不带 `v=` 参数时返回最新版本。<br>> **⚠️ 获取 `catalog.json` 时务必设足够大的 `max_length`（建议不低于 30000），避免截断导致漏掉文档条目。**
> 1.1 **文本映射检索** — `textMap.json` 包含各章节的全文文本，配合 `catalog.json` 的目录结构，可直接实现跨章节关键词检索，无需逐个读取内容文件。是检索已知关键词的首选方案。
> 2. **无头浏览器（兜底）** — 若需要检索（搜索关键词）而非读取已知文档，使用 agent-browser 打开 SPA 入口页面并执行 JavaScript（操作步骤见 §六）
> 3. **MHTML 导出（最终兜底）** — 若当前环境无无头浏览器，引导用户在浏览器中打开页面，另存为「单个网页文件(.mhtml)」后发送给 AI 处理
>
> ⚠️ **输出约定**：向用户输出综合指南链接时，一律使用 SPA 页面地址（`https://act.mihoyo.com/ys/ugc/tutorial/detail/{path_id}`），不要使用静态内容文件 URL（`act-webstatic.mihoyo.com`），后者在浏览器中打开可能显示乱码。

## 二、专用知识库 Skill（miliastra-knowledge）

| 来源 | 地址 | 说明 |
|------|------|------|
| miliastra-knowledge Skill | skillhub `miliastra-toolbox` v1.0.3 | 专用千星沙箱知识库查询 Skill，通过 API 直接查节点说明、文档全文与语义检索 |
| API 端点 | `https://ugc.070077.xyz/` | 后端知识库 API |
| 可用工具 | `get_node_info` `list_documents` `get_document` `rag_search` | 支持批量查询，优先于浏览器搜索使用 |

> 来源：skillhub 市场（https://skillhub.cn/）安装的 `miliastra-toolbox` 包。该 Skill 在 P-AI 中注册名为 `miliastra-knowledge`，应优先于网页搜索使用，因为其直接查询结构化知识库，比浏览器检索更精准高效。

## 三、社区来源

| 来源 | 地址 | 特点 |
|------|------|------|
| BWIKI | https://wiki.biligame.com/ys/千星奇域 | 结构化百科，系统数据完整 |
| B站教程 | 搜索关键词：千星奇域 + 教程/沙箱/节点图 | 视频教学，实操演示 |
| NGA论坛 | https://ngabbs.com/ 搜索千星奇域 | 深度讨论和FAQ |
| 17173 | 搜索千星奇域 | 攻略和界面详解 |
| 知乎 | 搜索千星奇域 | 评测和解读 |
| 本地更新日志 | `references/milistar-updatelog.md` | 月之三~月之八版本更新记录（手动保存） |

## 四、搜索关键词模板

### 按玩法类型
- `千星 [类型名] 关卡 制作`
- `千星 [玩法] 实现`
- `千星 教程 [玩法]`

### 按编辑器功能
- `千星 节点图 [功能名]`
- `千星 触发器 [条件]`
- `千星 变量 [用法]`

### 按问题类型
- `千星 能不能 [功能]`
- `千星 [问题] 怎么解决`
- `千星 [功能] 限制 上限`

## 五、版本信息

当前版本号通过以下方式确认：
- 米游社公告
- 游戏内版本号
- BWIKI版本标注

已知版本节点：
- v6.1：千星奇域首次上线
- v6.6（月之七）
- v6.7（月之八）：当前版本（2026-07-01）

## 六、无头浏览器搜索米游社官方教程

> **注意**：综合指南的文档内容已可通过静态 URL 直接访问（见上方「动态页面处理规则」），无需浏览器。无头浏览器仅在下述场景仍需使用：
> - 需要在综合指南首页搜索关键词（无法通过静态 URL 实现）
> - 需要交互式操作（如翻页、点击展开等）
> - 内容文件 URL 模式失效时的兜底

当需要查询千星奇域编辑器的最新官方文档时，使用 agent-browser 搜索米游社综合指南页面。

### 操作流程

```bash
# 打开综合指南页面
agent-browser open "https://act.mihoyo.com/ys/ugc/tutorial/detail/mhs2w008wf14"

# 获取页面快照，找到搜索框的 ref（如 e20）
agent-browser snapshot -i -c

# 填入搜索关键词并按 Enter
agent-browser fill @e20 "小地图"
agent-browser press Enter

# 等待搜索结果加载
agent-browser wait 2000

# 获取搜索结果快照
agent-browser snapshot -i -c
```

> ⚠️ ref 编号（如 e20）每次页面加载后会变化，必须先用 snapshot 确认当前 ref。所有步骤应在同一链式命令中完成：`open && snapshot && fill && press Enter && wait && snapshot`。

### 搜索技巧

- 使用具体的编辑器功能名（如"小地图标识""执行节点""界面控件"）效果最好
- 搜索后结果会展示匹配的文档标题和内容摘要，可直接点开对应的 link 获取全文