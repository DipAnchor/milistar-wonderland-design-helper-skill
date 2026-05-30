# 千星奇域 · 信息来源与检索指南

> 本文件记录可用的信息来源和检索策略。

## 一、官方来源

| 来源 | 地址 | 内容说明 |
|------|------|----------|
| 千星奇域官网 | https://ys.mihoyo.com/miliastra_wonderland/ | 公告、新闻、版本更新 |
| 官方综合指南（更新日志） | https://act.mihoyo.com/ys/ugc/tutorial/detail/mhs2w008wf14 | ⚠️ SPA页面。可用无头浏览器检索关键词（见§五），或手动另存为MHTML作为兜底 |
| 官方教程首页 | https://act.mihoyo.com/ys/ugc/tutorial/course/home | 分步创作教程（新手入口） |
| 奇匠学院 / 创作者中心 | https://act.mihoyo.com/ys/ugc/tutorial/course/home | 同一页面不同模块：奇匠学院=进阶教程 / 创作者中心=创作入口 |
| 千星奇域B站官号 | https://space.bilibili.com/3546889200863460 | ⚠️ 需手动访问。官方视频教程、版本演示 |
| 千星奇域米游社官号 | https://www.miyoushe.com/ys/accountCenter/postList?id=378227958 | ⚠️ 需手动访问。官方公告、活动资讯 |
| 米游社专区 | https://www.miyoushe.com/ys/topicDetail/2168 | 社区讨论、作品分享 |

> **动态页面处理规则**：标记 ⚠️ 的页面为纯前端渲染页面（SPA），传统的网页抓取工具无法获取其内容。处理方式有两种：
> 1. **无头浏览器（优先）** — 使用 agent-browser 打开页面并执行 JavaScript，获取动态渲染后的完整内容（操作步骤见 §五）
> 2. **MHTML 导出（兜底）** — 若当前环境无无头浏览器，引导用户在浏览器中打开页面，另存为「单个网页文件(.mhtml)」后发送给 AI 处理

## 二、社区来源

| 来源 | 地址 | 特点 |
|------|------|------|
| BWIKI | https://wiki.biligame.com/ys/千星奇域 | 结构化百科，系统数据完整 |
| B站教程 | 搜索关键词：千星奇域 + 教程/沙箱/节点图 | 视频教学，实操演示 |
| NGA论坛 | https://ngabbs.com/ 搜索千星奇域 | 深度讨论和FAQ |
| 17173 | 搜索千星奇域 | 攻略和界面详解 |
| 知乎 | 搜索千星奇域 | 评测和解读 |
| 本地更新日志 | `references/milistar-updatelog.md` | 月之三~月之七版本更新记录（手动保存） |

## 三、搜索关键词模板

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

## 四、版本信息

当前版本号通过以下方式确认：
- 米游社公告
- 游戏内版本号
- BWIKI版本标注

已知版本节点：
- v6.1：千星奇域首次上线
- v6.6（月之七）：当前版本（2026-05-30）

## 五、无头浏览器搜索米游社官方教程

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