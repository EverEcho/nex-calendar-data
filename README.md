# nex-calendar-data

NexCalendar 开源日历数据仓库。包含法定节假日、调休安排、农历标签、二十四节气等，供 [NexCalendar](https://github.com/nex-calendar/nex-calendar) 及其他日历应用使用。

## 目录结构

```
manifest.json          # 数据索引与版本信息
regions/
  cn.json              # 中国：固定节日、农历节日、国务院调休
  jp.json              # 日本：固定节日、Happy Monday 规则
  us.json              # 美国：联邦固定节日与浮动规则
lunar/
  labels.json          # 农历月日、天干地支、生肖（多语言）
  solar-terms.json     # 二十四节气名称与计算常数
```

## 通过 GitHub Raw 访问

将本仓库推送到 GitHub 后，可通过 raw URL 直接读取 JSON：

```
https://raw.githubusercontent.com/<你的用户名>/nex-calendar-data/main/manifest.json
https://raw.githubusercontent.com/<你的用户名>/nex-calendar-data/main/regions/cn.json
https://raw.githubusercontent.com/<你的用户名>/nex-calendar-data/main/lunar/solar-terms.json
```

NexCalendar 客户端启动时会从远程拉取最新数据，并缓存到本地；离线时使用内置副本。

## 数据格式

### 固定节日 `fixedHolidays`

按公历 `MMdd` 匹配：

```json
{ "mmdd": "1001", "names": { "zh": "国庆节", "en": "National Day" } }
```

### 农历节日 `lunarHolidays`（仅 cn）

按农历月日匹配（使用 Chinese calendar）：

```json
{ "month": 1, "day": 1, "names": { "zh": "春节", "en": "Spring Festival" } }
```

### 调休安排 `adjustments`（仅 cn）

国务院发布的「休 / 班」安排：

```json
{ "date": "2025-01-26", "type": "work" }
{ "date": "2025-01-28", "type": "rest" }
```

### 浮动节日规则 `rules`（jp / us）

- `weekdayInRange`：某月某星期几，且日期落在 `[dayMin, dayMax]`
- `weekdayAfter`：某月某星期几，且日期 > `afterDay`

## 贡献

欢迎提交 PR 更新调休安排、补充节日或修正翻译。修改 `manifest.json` 中的 `updatedAt` 字段即可。

## 许可

MIT
