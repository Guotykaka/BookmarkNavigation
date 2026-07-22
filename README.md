# Ergulum · BookmarkNavigation

个人浏览器起始页 / 书签导航。单文件实现，打开即用。

在线仓库：[Guotykaka/BookmarkNavigation](https://github.com/Guotykaka/BookmarkNavigation)

## 功能

- **多引擎搜索**：百度、Google、必应、Perplexity、ChatGPT、秘塔、Gemini、Copilot、Felo
- **分类快捷导航**：快捷导航 / 外网 / 个人 / 讯息（彩色首写图标）
- **深浅色主题**：左上角切换，偏好写入 `localStorage`
- **页脚信息**：北京时间（多源网络对时）、日期、IP 定位天气
- **足球赛况**：左侧曼联英超 + 拜仁德甲（上场比分 / 下场预告，北京时间）
- **邮箱入口**：右上角 Gmail、QQ邮箱、163邮箱
- **站点图标**：`favicon.ico`

## 使用

直接用浏览器打开：

```bash
index.html
```

或本地起一个静态服务：

```bash
npx serve .
```

也可设为浏览器「新标签页 / 主页」。

## 结构

```
BookmarkNavigation/
├── index.html      # 页面与全部逻辑
├── favicon.ico     # 站点图标
└── README.md
```

## 数据来源

| 模块            | 接口                                                        |
| --------------- | ----------------------------------------------------------- |
| 英超 / 德甲赛程 | ESPN 公开接口 `site.api.espn.com`（`eng.1` / `ger.1`）      |
| 天气            | Open-Meteo                                                  |
| IP 定位         | 腾讯位置服务                                                |
| 网络时间        | 苏宁 / maketimestamp / 拼多多 / 小米 等时间戳源（取中位数） |

赛程时间统一按 **北京时间（UTC+8）** 显示，约每 15 分钟刷新。

## 自定义

编辑 `index.html` 中的配置即可：

- `ENGINES`：搜索引擎列表
- `NAV_GROUPS`：导航分组与链接（`name` / `text` / `color` / `url`）
- `CLUBS`：左侧足球球队（队 ID、联赛代码、DOM 节点）

主题存储键：`ergulum_theme`（`dark` / `light`）  
定位缓存键：`ergulum_location`

## 字体

- 界面正文：Manrope、Noto Sans SC、Outfit（Google Fonts）
- 站点图标（favicon）：**Just Another Hand**（Google Fonts 手写体，用于生成 `favicon.ico` 中的字母造型）

## 说明

- 左侧赛况在窄屏（宽度 &lt; 1100px）会自动隐藏
- 「外网」类站点可能需要代理访问
- 腾讯地图 Key 写在页面内，仅供个人使用；公开部署请换成自己的 Key
