# 貢獻指南

[English](../CONTRIBUTING.md) | [简体中文](./CONTRIBUTING_zh.md) | [繁體中文](./CONTRIBUTING_zh-Hant.md)

感謝您考慮為我們的項目做出貢獻！您的努力將使我們的項目變得更好。

在您開始貢獻之前，請花一點時間閱讀以下准則：

## 我可以如何貢獻？

### 報告問題

如果您在項目中遇到錯誤，請在 GitHub 上[報告問題](https://github.com/XiaoMi/ha_xiaomi_home/issues/new/)，並提供關於錯誤的詳細資訊，包括復現步驟、debug 級日誌以及錯誤出現的時間。

集成啟用 debug 級日誌的[方法](https://www.home-assistant.io/integrations/logger/#log-filters)：

```
# configuration.yaml 設定列印日誌等級

logger:
  default: critical
  logs:
    custom_components.xiaomi_home: debug
```

### 建議增強功能

如果您有增強或新功能的想法，歡迎您在 GitHub 討論區[創建想法](https://github.com/XiaoMi/ha_xiaomi_home/discussions/new?category=ideas) 。我們期待您的建議！

### 貢獻代碼

1. Fork 該倉庫並從 `main` 創建您的分支。
2. 確保您的代碼符合項目的編碼規範。
3. 確保您的提交消息描述清晰。
4. 提交請求應附有明確的問題描述和解決方案。
5. 如果必要，請更新文檔。
6. 請運行測試並確保測試通過。

## 拉取請求准則

在提交拉取請求之前，請確保滿足以下要求：

- 您的拉取請求解決了單個問題或功能。
- 您已在本地測試過您的更改。
- 您的程式碼遵循項目的[代碼規範](#代碼規範)，已運行 [`pylint`](https://github.com/google/pyink) 搭配本項目的 [pylintrc](../.pylintrc) 檢查代碼。
- 所有現有測試都通過，並且如果適用，您已添加了新的測試。
- 任何依賴更改都有文檔說明。

## 代碼規範

本項目的代碼格式遵循 [Google Style](https://google.github.io/styleguide/pyguide.html) 。請確保您的貢獻符合該指南。

## Commit Message 格式

```
<type>: <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

type ：有以下幾種變更類型

- feat：新增功能。
- fix：修復問題。
- docs：僅僅修改了文檔。
- style：僅僅是對格式進行修改，如逗號、縮進、空格等，不改變代碼邏輯。
- refactor：代碼重構，沒有新增功能或修復問題。
- perf：優化性能。
- test：增加或修改測試用例。
- chore：修改編譯流程，或變更依賴庫和工具等。
- revert：版本回滾。

subject ：簡潔的標題，描述本次提交的概要。使用祈使句、現在時態，首字母小寫，結尾不加句號。

body ：描述本次提交的詳細內容，解釋為什麼需要這些變更。除 docs 之外的變更類型必須包含 body。

footer ：（可選）關聯的 issue 或 pull request 編號。

## 命名規範

### 米家命名規範

- 描述“小米”時必須使用“Xiaomi”，變數名稱可以使用“xiaomi”或“mi”。
- 描述“米家”時必須使用“Xiaomi Home”，變數名稱可以使用“mihome”或“MiHome”。
- 描述“小米IoT”時必須使用“MIoT”，變數名稱可以使用“miot”或“MIoT”。

### 第三方平台命名規範

- 描述“Home Assistant”時必須使用“Home Assistant”，變數可以使用“hass”或“hass_xxx”。

### 其它命名規範

- 文檔中的中文語句包含英文時，如果英文沒有被中文引號括起來，那麼中文與英文之間必須有一個空格。（最好代碼注釋也這麼寫）

## 許可

在為本項目做出貢獻時，您同意您的貢獻遵循本項目的[許可證](../LICENSE.md) 。

## 獲取幫助

如果您需要協助或有疑問，可在 GitHub 的[討論區](https://github.com/XiaoMi/ha_xiaomi_home/discussions/)詢問。

您還可以聯繫 ha_xiaomi_home@xiaomi.com
