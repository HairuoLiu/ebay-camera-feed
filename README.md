# eBay 相机新上架日报（加拿大）

每天自动抓取 eBay 加拿大站新上架的相机、镜头与胶片器材，去重后识别型号、与市场成交价比对，生成可搜索、可筛选、可下载的在线日报。

- **站点**：https://hairuoliu.github.io/ebay-camera-feed/
- **RSS 订阅**：https://hairuoliu.github.io/ebay-camera-feed/feed.xml

## 怎么看

| 入口 | 内容 |
| --- | --- |
| 首页 `index.html` | 当天精华 Top 60 + 寻宝 Top 30，带搜索、筛选、排序 |
| `ca/YYYY-MM-DD.html` | 当日完整日报（全部条目） |
| `ca/YYYY-MM-DD-treasure.html` | 捡漏页：抄底 / 超值 + 残件寻宝 |
| `ca/YYYY-MM-DD.csv` | 当日精华数据，Excel 可直接打开 |
| `ca/YYYY-MM-DD-treasure.csv` | 当日寻宝数据 |

页面顶部可切换「精华排序」与「寻宝捡漏」两个标签页。

## 价值等级怎么读

每条商品带一枚彩色标签，表示它相对于市场均价的位置：

**抄底 · 超值 · 偏低 · 合理 · 偏高 · 高价 · 无基准**

- **抄底 / 超值**：明显低于市场均价，建议优先看
- **无基准**：缺少可比的市场成交价，需自行判断
- 价格区同时显示「均价」与「省 / 贵百分比」

## 数据说明

- 数据源：eBay Browse API（加拿大站 `EBAY_CA`）
- 更新频率：每天一次
- 保留策略：**只保留最近 30 天**，过期文件自动清理
- 商品图片为 eBay 原图远程链接，本仓库不存储任何图片
- 仅供参考，成交前请自行核验卖家信誉与实物成色

## 仓库结构

```
.
├─ index.html          首页：当天摘要 + 历史归档入口
├─ manifest.json       日报索引（按日期倒序，最多 30 条）
├─ feed.xml            RSS 订阅源（最近 40 条）
├─ ca/                 加拿大区按日文件
│  ├─ YYYY-MM-DD.html / .csv
│  └─ YYYY-MM-DD-treasure.html / .csv
└─ .github/
   └─ workflows/pages.yml   推送到 main 后自动部署 GitHub Pages
```

## 自动化

推送到 `main` 分支即自动触发 GitHub Actions 部署到 GitHub Pages，无需手动操作。
每日数据的抓取、建站与清理由本机的定时任务完成，全程不产生任何 AI 调用成本。
