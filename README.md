# nex-calendar-data

NexCalendar 开源日历数据仓库。包含法定节假日、调休安排、农历标签、二十四节气等，供 [NexCalendar](https://github.com/nex-calendar/nex-calendar) 及其他日历应用使用。

## 目录结构

```
manifest.json                    # 数据索引与版本信息
regions/
  cn/
    holidays.json                # 中国：固定节日、农历节日、节气规则（清明等）
    adjustments.json             # 中国：国务院发布的休/班调休（按年更新）
  jp.json                        # 日本：固定节日、Happy Monday 规则
  us.json                        # 美国：联邦固定节日与浮动规则
lunar/
  labels.json                    # 农历月日、天干地支、生肖（多语言）
  solar-terms.json               # 二十四节气名称与计算常数
```

## 通过 GitHub Raw 访问

仓库地址：[EverEcho/nex-calendar-data](https://github.com/EverEcho/nex-calendar-data)

```
https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/manifest.json
https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/regions/cn/holidays.json
https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/regions/cn/adjustments.json
https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/regions/jp.json
https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/regions/us.json
https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/lunar/solar-terms.json
```

NexCalendar 客户端启动时会从远程拉取最新数据，并缓存到本地；离线时使用内置副本。

**中国数据拆分为两个文件**：节日名称与规则变化较少，可长期缓存；调休安排每年由国务院发布，单独更新 `adjustments.json` 即可，无需重下节日数据。

## 数据格式

### 名称语言优先级 `nameLocales`（可选）

按地区配置节日名称的 locale 回退顺序，再与用户界面语言合并：

```json
"nameLocales": ["ja", "en"]
```

### 固定节日 `fixedHolidays`

按公历 `MMdd` 匹配：

```json
{ "mmdd": "1001", "names": { "zh": "国庆节", "en": "National Day" } }
```

### 农历节日 `lunarHolidays`（仅 cn）

与固定节日相同，使用农历 `mmdd`（正月初一 = `0101`），由 Chinese calendar 匹配：

```json
{ "mmdd": "0101", "names": { "zh": "春节", "en": "Spring Festival" } }
```

### 节气节日规则 `rules`（cn 清明等）

按 `lunar/solar-terms.json` 中的节气索引匹配当日：

```json
{ "type": "solarTerm", "termIndex": 6, "names": { "zh": "清明节", "en": "Qingming Festival" } }
```

### 调休安排 `schedules`（`regions/cn/adjustments.json`）

按公历年份分组，值为该年休/班的 `MMDD` 列表（无重复年份前缀，体积更小）：

```json
"2025": {
  "rest": ["0101", "0128"],
  "work": ["0126"]
}
```

跨年日期归入日期所在年（如 2022-12-31 记在 `"2022".rest` 的 `"1231"`）。

### 浮动节日规则 `rules`（jp / us）

- `weekdayInRange`：某月某星期几，且日期落在 `[dayMin, dayMax]`
- `weekdayAfter`：某月某星期几，且日期 > `afterDay`

## 贡献

- **调休**：每年国务院通知发布后，向 `regions/cn/adjustments.json` 追加该年条目，并更新 `years` 与 `manifest.json` 的 `updatedAt`。
- **节日/翻译**：修改 `regions/cn/holidays.json` 或对应地区文件。

## 许可

MIT
