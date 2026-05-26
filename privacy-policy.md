# 拾光旅行 隐私政策

**生效日期：** 2026年5月26日  
**最后更新：** 2026年5月26日

本隐私政策说明 macOS 应用 **拾光旅行**（Bundle ID：`com.nex.timetrace`）如何收集、使用、存储与保护信息。本文件托管于开源数据仓库 [nex-calendar-data](https://github.com/EverEcho/nex-calendar-data)，供应用内展示及 App Store 等渠道引用。

使用本应用即表示您理解并同意本政策。若不同意，请停止使用并可在系统设置中撤销相关权限。

---

## 1. 我们是谁

拾光旅行是一款运行在您 Mac 本地的菜单栏日历应用，由独立开发者维护。我们**不运营**用于识别个人身份的在线账户系统，也**不会**将您的日历内容上传至我们自有的服务器进行分析或出售。

如有隐私相关问题，请通过 GitHub 提交 Issue：

- 应用仓库：[nex-calendar/nex-calendar](https://github.com/nex-calendar/nex-calendar)（以实际发布仓库为准）
- 数据仓库：[EverEcho/nex-calendar-data](https://github.com/EverEcho/nex-calendar-data)

---

## 2. 我们处理哪些信息

### 2.1 完全在您的设备上处理的数据

在获得您授权的前提下，应用可能访问并仅在本地使用以下信息：

| 类型 | 用途 | 存储位置 |
|------|------|----------|
| **系统日历与日程** | 读取、展示、创建或编辑您选择的日历事件 | 由 macOS「日历」/ EventKit 管理；应用内存中仅保留展示所需的摘要 |
| **系统提醒事项** | 读取、展示、创建或编辑提醒 | 由 macOS「提醒事项」/ EventKit 管理 |
| **应用内创建的本地日程与任务** | 在应用内新建、编辑、删除的日程与待办 | `~/Library/Application Support/拾光旅行/`（`nex_events.json`、`nex_tasks.json`） |
| **应用设置与偏好** | 语言、周起始日、节假日地区、订阅列表、快捷键等 | macOS `UserDefaults`（应用沙盒内） |
| **ICS 订阅缓存** | 加速展示您添加的外部日历订阅 | `~/Library/Application Support/拾光旅行/ics_cache/` |

上述数据**默认不会**发送给开发者。您可在「系统设置 → 隐私与安全性」中随时关闭日历、提醒事项等权限。

### 2.2 可选的 iCloud 同步

若您已登录 iCloud 并在系统中启用本应用的 iCloud 能力，应用可将**本地创建的日程与任务**（`nex_events.json`、`nex_tasks.json`）同步至您 Apple ID 名下的 iCloud 容器（`iCloud.com.nex.timetrace`）。该数据由 **Apple** 根据 [Apple 隐私政策](https://www.apple.com/legal/privacy/) 处理，我们无法访问您的 iCloud 账户内容。

### 2.3 您主动配置的网络请求

应用仅在以下情况发起出站网络连接，且**不附带**可识别您身份的开发者侧用户 ID：

1. **公共日历数据更新**  
   从 GitHub 拉取开源节假日、调休、农历等 JSON 数据（默认源：`https://raw.githubusercontent.com/EverEcho/nex-calendar-data/main/`）。请求内容为公开的静态数据文件；**不会**上传您的姓名、日历事件或设备标识给该仓库。

2. **ICS 日历订阅**  
   当您添加 `.ics` 订阅 URL 时，应用会向**您指定的第三方地址**发起 HTTP(S) 请求以下载日历数据，并在本地解析与缓存。该第三方服务的隐私实践由其运营方负责，请仅订阅您信任的来源。

除上述情形外，应用**不包含**广告、第三方统计 SDK、崩溃上报服务或向开发者服务器的遥测上传。

### 2.4 系统功能相关

- **登录时打开**：若您开启，将通过 macOS `SMAppService` 注册登录项，由系统管理，不向开发者发送额外数据。
- **全局快捷键**：仅在本地注册热键以显示/隐藏面板，不上传按键记录。

---

## 3. 我们如何使用信息

我们使用上述信息的唯一目的是提供日历相关功能，例如：

- 在界面中展示月历、农历、节假日与调休标记  
- 同步并显示系统日历、提醒事项及 ICS 订阅  
- 记住您的显示偏好与订阅配置  
- 在离线时回退到内置或已缓存的公共日历数据  

**我们不会**将您的个人日历内容用于广告投放、用户画像或出售给第三方。

---

## 4. 数据共享与披露

我们不会向第三方出售您的个人数据。仅在以下有限情形下可能涉及数据离开您的设备：

- 您配置的 **ICS 订阅 URL** 所指向的服务器  
- **Apple iCloud**（若您启用同步）  
- **GitHub** 等托管公共 JSON 的 CDN（仅下载公共文件，无个人内容上传）  
- 法律法规要求或保护合法权益所必需时  

---

## 5. 数据保留与删除

- **系统日历/提醒事项**：由 macOS 与您自行管理；卸载应用不会删除系统日历中的数据。  
- **应用本地文件**：删除 `~/Library/Application Support/拾光旅行/` 可清除应用创建的本地日程、任务及 ICS 缓存。  
- **应用设置**：卸载应用后，`UserDefaults` 中相关项通常随应用移除；亦可在「系统设置 → 通用 → 存储空间」中管理。  
- **iCloud 数据**：请在 iCloud 管理或 Apple 账户设置中处理。  

---

## 6. 权限说明（macOS）

应用可能请求以下权限，均在系统弹窗中说明用途：

| 权限 | 用途 |
|------|------|
| 日历（完全访问） | 读取与写入您授权的日历事件 |
| 提醒事项（完全访问） | 读取与写入提醒 |
| 网络客户端 | 下载公共日历数据及 ICS 订阅 |
| iCloud | 可选同步本地创建的日程与任务 |
| Apple 事件（如适用） | 与系统自动化相关的必要能力 |

您可随时在「系统设置 → 隐私与安全性」中撤销授权。

---

## 7. 儿童隐私

本应用面向一般用户，不会故意收集 13 周岁以下儿童的个人信息。若您认为我们无意中处理了儿童数据，请通过上述 GitHub Issue 联系我们。

---

## 8. 国际用户

应用主要在您的 Mac 本地运行。公共日历数据可能从位于不同国家/地区的服务器（如 GitHub）下载。使用 ICS 订阅时，数据可能传输至订阅服务所在地区。

---

## 9. 政策变更

我们可能更新本政策以反映功能或法律要求的变化。更新后的版本将发布于本仓库；重大变更时，我们会在应用或发布说明中提示。继续使用应用即视为接受更新后的政策。

---

## 10. 适用法律与联系

本政策的解释与适用以您所在地强制性法律为准。  
联系与申诉渠道：通过 [EverEcho/nex-calendar-data Issues](https://github.com/EverEcho/nex-calendar-data/issues) 或应用主仓库 Issues 与我们联系。

---

# 拾光旅行 Privacy Policy (English)

**Effective date:** May 26, 2026  
**Last updated:** May 26, 2026

**拾光旅行** (Bundle ID: `com.nex.timetrace`) is a macOS menu bar calendar app. This policy describes what data the app processes and how.

## Summary

- **Local-first:** Calendar/reminder access uses Apple EventKit on your Mac. Locally created events/tasks are stored under `~/Library/Application Support/拾光旅行/`. Preferences use UserDefaults.
- **Optional iCloud:** Local JSON event/task files may sync to your Apple ID via `iCloud.com.nex.timetrace` (handled by Apple).
- **Network:** (1) Downloads **public** holiday/lunar JSON from GitHub (`EverEcho/nex-calendar-data`) — no personal calendar data is uploaded. (2) Fetches **ICS URLs you configure** — third-party privacy policies apply.
- **No ads, no analytics SDK, no sale of personal data** to the developer.
- **Permissions:** Calendar, Reminders, network client, optional iCloud — revocable in System Settings.
- **Contact:** [GitHub Issues](https://github.com/EverEcho/nex-calendar-data/issues) on this data repo or the main app repository.

For the full Chinese version (authoritative for zh locales), see sections 1–10 above.

---

*This document is MIT-licensed like the rest of nex-calendar-data; the app itself may be distributed under separate terms.*
