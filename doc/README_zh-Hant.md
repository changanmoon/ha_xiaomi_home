# Home Assistant 米家集成

[English](../README.md) | [简体中文](./README_zh.md) | [繁體中文](./README_zh-Hant.md)

米家集成是一個由小米官方提供支援的 Home Assistant 的集成組件，它可以讓您在 Home Assistant 中使用小米 IoT 智能裝置。

## 安裝

> Home Assistant 版本要求：
>
> - Core $\geq$ 2024.4.4
> - Operating System $\geq$ 13.0

### 方法 1：使用 git clone 命令透過 GitHub 下載

```bash
cd config
git clone https://github.com/XiaoMi/ha_xiaomi_home.git
cd ha_xiaomi_home
./install.sh /config
```

推薦使用此方法安裝米家集成。如果您想要更新到指定版本，只需切換至相應的 Tag 。

例如，更新米家集成版本至 v1.0.0

```bash
cd config/ha_xiaomi_home
git checkout v1.0.0
./install.sh /config
```

### 方法 2: [HACS](https://hacs.xyz/)

HACS > 右上角三個點 > Custom repositories > Repository: https://github.com/XiaoMi/ha_xiaomi_home.git & Category: Integration > ADD > 按一下 HACS 的 New 或 Available for download 分類下的 Xiaomi Home，進入集成詳情頁 > DOWNLOAD

> 米家集成暫時沒有加入到 HACS 商店，敬請期待。

### 方法 3：透過 [Samba](https://github.com/home-assistant/addons/tree/master/samba) 或者 [FTPS](https://github.com/hassio-addons/addon-ftp) 手動安裝

下載並將 `custom_components/xiaomi_home` 資料夾複製到 Home Assistant 的 `config/custom_components` 資料夾下。

## 配置

### 登入

[設定 > 裝置與服務 > 加入集成](https://my.home-assistant.io/redirect/brand/?brand=xiaomi_home) > 搜尋“`Xiaomi Home`” > 下一步 > 請按一下這裡進行登入 > 使用小米賬戶登入

[![Open your Home Assistant instance and start setting up a new integration.](https://my.home-assistant.io/badges/config_flow_start.svg)](https://my.home-assistant.io/redirect/config_flow_start/?domain=xiaomi_home)

### 加入 MIoT 裝置

登入成功後，會彈出會話框“選擇家庭與裝置”。您可以選擇需要加入的米家家庭，該家庭內的所有裝置將匯入 Home Assistant 。

### 多賬戶登入

用一個小米賬戶登入並配置完成後，您可以在 Xiaomi Home Integration 頁面中繼續加入其他小米賬戶。

方法：[設定 > 裝置與服務 > 已配置 > Xiaomi Home](https://my.home-assistant.io/redirect/integration/?domain=xiaomi_home) > 加入中樞 > 下一步 > 請按一下這裡進行登入 > 使用小米賬戶登入

[![Open your Home Assistant instance and show an integration.](https://my.home-assistant.io/badges/integration.svg)](https://my.home-assistant.io/redirect/integration/?domain=xiaomi_home)

### 修改配置項

在會話框“配置選項”中，可選擇需要變更的配置項。您可以修改用戶暱稱或更新從米家 APP 匯入的裝置列表。

方法：[設定 > 裝置與服務 > 已配置 > Xiaomi Home](https://my.home-assistant.io/redirect/integration/?domain=xiaomi_home) > 配置 > 選擇需要變更的配置項

### Action 除錯模式

啟用該模式後，您可手動向裝置發送帶引數的 Action 控制指令。發送帶引數的 Action 控制指令的用戶入口顯示為一個文本實體。

方法：[設定 > 裝置與服務 > 已配置 > Xiaomi Home](https://my.home-assistant.io/redirect/integration/?domain=xiaomi_home) > 配置 > Action 除錯模式

## 安全性

米家集成及其使用的雲端介面由小米官方提供。您需要使用小米賬戶登入以獲取裝置列表。米家集成使用 OAuth 2.0 的登入方式，不會在 Home Assistant 中保存您的小米賬戶密碼。但由於 Home Assistant 平台的限制，登入成功後，您的小米用戶信息（包括裝置信息、證書、 token 等）會明文保存在 Home Assistant 的配置檔案中。因此，您需要保管好自己 Home Assistant 配置檔案。一旦該檔案洩露，其他人可能會冒用您的身份登入。

> 如果您懷疑您的 OAuth 2.0 令牌已洩露，您可以透過以下步驟取消小米賬戶的登入授權：米家 APP -> 我的 -> 按一下用戶名稱進入小米賬戶頁面 -> 應用授權 -> Xiaomi Home (Home Assistant Integration) -> 取消授權

## 常見問題

- 米家集成是否支援所有的小米米家裝置？

  米家集成目前支援大部分米家裝置品類，但仍有一小部分裝置品類（藍牙、紅外及虛擬裝置）並不支援。

- 米家集成是否可以同時使用多個小米賬戶？

  是的，米家集成支援多個小米賬戶同時登入。另外，米家集成還支援不同賬戶的米家裝置加入到同一個 Home Assistant 區域。

- 米家集成是否支援本地化控制？

  米家集成支援透過[小米中樞閘道](https://www.mi.com/shop/buy/detail?product_id=15755&cfrom=search)（韌體版本 3.4.0_000 以上）或內置中樞閘道（軟體版本 0.8.0 以上）的米家裝置實現本地化控制。如果沒有小米中樞閘道或其他帶中樞閘道功能的裝置，那麼所有控制指令都會透過小米雲發送。支援 Home Assistant 本地化控制的小米中樞閘道（含內置中樞閘道）的韌體尚未發佈，韌體升級計劃請參閱 MIoT 團隊的通知。

  小米中樞閘道僅在中國大陸可用，在其他地區不可用。

  米家集成也能透過啟用小米局域網控制功能實現部分本地化控制效果。小米局域網控制功能只能控制與 Home Assistant 處於同一局域網內的 IP 裝置（使用 WiFi、網線連接路由器的裝置），無法控制藍牙 Mesh、ZigBee 等協議接入的裝置。該功能可能會引起一些異常，我們建議不要使用該功能。小米局域網控制功能啟用方法：[設定 > 裝置與服務 > 已配置 > Xiaomi Home](https://my.home-assistant.io/redirect/integration/?domain=xiaomi_home) > 配置 > 更新局域網控制配置

  小米局域網控制功能不受地區限制，在全球範圍內均可用。如果 Home Assistant 所在的局域網內存在中樞閘道，那麼即便米家集成啟用了小米局域網控制功能，該功能也不會生效。

- 米家集成在哪些地區可用？

  米家集成所用的雲服務介面已部署在中國大陸、歐洲、印度、俄羅斯、新加坡、美國共六個地區的機房。由於用戶數據在不同地區的小米雲上相互隔離，您需要在配置 Home Assistant 時選擇用戶所在地區，才能匯入相應的米家裝置。米家集成支援將不同地區的米家裝置加入到同一個 Home Assistant 區域。

## 消息收發原理

### 雲端控制

<div align=center>
<img src="./images/cloud_control_zh.jpg" width=300>

圖 1：雲端控制架構

</div>

米家集成向小米雲 MQTT Broker 訂閱關注的裝置消息。當裝置屬性發生改變或產生裝置事件時，裝置向小米雲發送上行消息， MQTT Broker 向米家集成推送訂閱的裝置消息。由於米家集成不需要向雲端輪詢以獲取裝置當前的屬性值，因此米家集成能第一時間獲知裝置屬性變化或事件發生。得益於消息訂閱機制，米家集成只在配置完成時向雲端查詢一次所有的裝置屬性，對雲端產生的訪問壓力很小。

米家集成需要控制裝置時，透過小米雲 HTTP 介面向裝置發送控制消息。裝置收到小米雲發來的下行消息後做出響應。

### 本地控制

<div align=center>
<img src="./images/local_control_zh.jpg" width=300>

圖 2：本地控制架構

</div>

小米中樞閘道內包含一個標準的 MQTT Broker ，實現了完整的訂閱發佈機制。米家集成向小米中樞閘道訂閱關注的裝置消息。當裝置屬性發生改變或產生裝置事件時，裝置向小米中樞閘道發送上行消息， MQTT Broker 向米家集成推送訂閱的裝置消息。

米家集成需要控制裝置時，向 MQTT Broker 發佈裝置控制消息，再經由小米中樞閘道轉發給裝置。裝置收到小米中樞閘道發來的下行消息後做出響應。

## MIoT-Spec-V2 與 Home Assistant 實體的映射關係

[MIoT-Spec-V2](https://iot.mi.com/v2/new/doc/introduction/knowledge/spec) 的全稱為 MIoT Specification Version 2 ，是小米 IoT 平台制訂的物聯網協議，用於對 IoT 裝置進行規範化的功能性描述，其中包含功能定義（其他 IoT 平台稱之為物模型）、交互模型、消息格式以及編碼。

在 MIoT-Spec-V2 中，一個產品定義為一個裝置，一個裝置包含若干服務，一個服務包含若干屬性、方法和事件。米家集成根據 MIoT-Spec-V2 生成對應的 Home Assistant 實體。

具體的轉換關係如下：

### 一般轉換規則

- 屬性（Property）

| access（訪問方式） | format（數據格式） | value-list（取值列表） | value-range（取值範圍） | 轉換後的實體 |
| ------------------ | ------------------ | ---------------------- | ----------------------- | ------------ |
| 可寫               | string             | -                      | -                       | Text         |
| 可寫               | bool               | -                      | -                       | Switch       |
| 可寫               | 非 string、非 bool | 有                     | -                       | Select       |
| 可寫               | 非 string、非 bool | 無                     | 有                      | Number       |
| 不可寫             | -                  | -                      | -                       | Sensor       |

- 事件（Event）

轉換後的實體為 Event，事件引數同時傳遞給實體的 `_trigger_event` 。

- 方法（Action）

| in（輸入引數列表） | 轉換後的實體 |
| ------------------ | ------------ |
| 空                 | Button       |
| 非空               | Notify       |

如果啟用了“Action 除錯模式”，方法的 in 字段為非空時，還會生成 Text 實體。

Notify 實體詳情頁中 Attributes 會顯示輸入引數的格式。輸入引數為有序的列表，英文中括號[]包括。字符串元素由英文雙引號""包括。

例如， xiaomi.wifispeaker.s12 siid=5 aiid=5 方法（ Intelligent Speaker Execute Text Directive ）在 Notify 實體詳情頁顯示的輸入引數格式為 `[Text Content(str), Silent Execution(bool)]` ，使用的輸入引數可以是 `["Hello", true]` 。

### 特殊轉換規則

MIoT-Spec-V2 定義類型使用的 URN 格式為 `urn:<namespace>:<type>:<name>:<value>[:<vendor-product>:<version>]`，其中 `name` 是用於描述實例（裝置、服務、屬性、事件、方法）的有意義的單詞或詞組。米家集成先用實例名稱（ name ）判斷是否將 MIoT-Spec-V2 實例轉換成特定的 Home Assistant 實體。對於不符合特殊轉換規則的 MIoT-Spec-V2 實例，再使用一般轉換規則進行轉換。

`namespace` 用於描述實例所屬的命名空間，取值為“miot-spec-v2”表示小米定義的規範， 取值為“bluetooth-spec”表示藍牙聯盟定義的規範，其他則為廠商自定義的規範。當 `namespace` 不是“miot-spec-v2”時，轉換後的實體名稱前會顯示一個星號\*。

- 裝置（Device）

轉換規則為 `SPEC_DEVICE_TRANS_MAP` ：

```
{
    '<device instance name>':{
        'required':{
            '<service instance name>':{
                'required':{
                    'properties': {
                        '<property instance name>': set<property access: str>
                    },
                    'events': set<event instance name: str>,
                    'actions': set<action instance name: str>
                },
                'optional':{
                    'properties': set<property instance name: str>,
                    'events': set<event instance name: str>,
                    'actions': set<action instance name: str>
                }
            }
        },
        'optional':{
            '<service instance name>':{
                'required':{
                    'properties': {
                        '<property instance name>': set<property access: str>
                    },
                    'events': set<event instance name: str>,
                    'actions': set<action instance name: str>
                },
                'optional':{
                    'properties': set<property instance name: str>,
                    'events': set<event instance name: str>,
                    'actions': set<action instance name: str>
                }
            }
        },
        'entity': str
    }
}
```

device instance name 下的 required 表示必須包含的服務， optional 表示可選的服務， entity 表示轉換後的實體。 service instance name 下的 required 表示必須包含的屬性、事件、方法，optional 表示可選的屬性、事件、方法。 required 、 properties 域下的 property instance name 的值表示屬性的訪問方式，匹配成功的條件是 property instance name 的值是相應 MIoT-Spec-V2 屬性實例的訪問方式的子集。

如果 MIoT-Spec-V2 裝置實例缺少必選的服務、屬性、事件、方法，則不會生成 Home Assistant 實體。

- 服務（Service）

轉換規則為 `SPEC_SERVICE_TRANS_MAP` ：

```
{
    '<service instance name>':{
        'required':{
            'properties': {
                '<property instance name>': set<property access: str>
            },
            'events': set<event instance name: str>,
            'actions': set<action instance name: str>
        },
        'optional':{
            'properties': set<property instance name: str>,
            'events': set<event instance name: str>,
            'actions': set<action instance name: str>
        },
        'entity': str
    }
}
```

service instance name 下的 required 表示必須包含的屬性、事件、方法，optional 表示可選的屬性、事件、方法， entity 表示轉換後的實體。 required 、 properties 域下的 property instance name 的值表示屬性的訪問方式，匹配成功的條件是 property instance name 的值是相應 MIoT-Spec-V2 屬性實例的訪問方式的子集。

如果 MIoT-Spec-V2 服務實例缺少必選的屬性、事件、方法，則不會生成 Home Assistant 實體。

- 屬性（Property）

轉換規則為 `SPEC_PROP_TRANS_MAP` ：

```
{
    'entities':{
        '<entity name>':{
            'format': set<str>,
            'access': set<str>
        }
    },
    'properties': {
        '<property instance name>':{
            'device_class': str,
            'entity': str
        }
    }
}
```

entity name 下的 format 表示屬性的數據格式，匹配上一個值即為匹配成功； access 表示屬性的訪問方式，匹配上所有值才算匹配成功。

property instance name 下的 entity 表示轉換後的實體，取值為 entities 下的 entity name ； device_class 表示轉換後實體所用的 `_attr_device_class` 。

- 事件（Event）

轉換規則為 `SPEC_EVENT_TRANS_MAP` ：

```
{
    '<event instance name>': str
}
```

event instance name 下的值表示轉換後實體所用的 `_attr_device_class` 。

### MIoT-Spec-V2 過濾規則

`spec_filter.json` 用於過濾掉不需要的 MIoT-Spec-V2 實例，過濾掉的實例不會轉換成 Home Assistant 實體。

`spec_filter.json`的格式如下：

```
{
    "<MIoT-Spec-V2 device instance>":{
        "services": list<service_iid: str>,
        "properties": list<service_iid.property_iid: str>,
        "events": list<service_iid.event_iid: str>,
        "actions": list<service_iid.action_iid: str>,
    }
}
```

`spec_filter.json` 的鍵值為 MIoT-Spec-V2 裝置實例的 urn （不含版本號“version”字段）。一個產品的不同版本的韌體可能會關聯不同版本的 MIoT-Spec-V2 裝置實例。 MIoT 平台要求廠商定義產品的 MIoT-Spec-V2 時，高版本的 MIoT-Spec-V2 實例必須包含全部低版本的 MIoT-Spec-V2 實例。因此， `spec_filter.json` 的鍵值不需要指定裝置實例的版本號。

裝置實例下的 services 、 properties 、 events 、 actions 域的值表示需要過濾掉的服務、屬性、事件、方法的實例號（ iid ，即 instance id ）。支援通配符匹配。

示例：

```
{
    "urn:miot-spec-v2:device:television:0000A010:xiaomi-rmi1":{
        "services": ["*"]   # Filter out all services. It is equivalent to completely ignoring the device with such MIoT-Spec-V2 device instance.
    },
    "urn:miot-spec-v2:device:gateway:0000A019:xiaomi-hub1": {
        "services": ["3"],  # Filter out the service whose iid=3.
        "properties": ["4.*"]   # Filter out all properties in the service whose iid=4.
        "events": ["4.1"],  # Filter out the iid=1 event in the iid=4 service.
        "actions": ["4.1"]  # Filter out the iid=1 action in the iid=4 service.
    }
}
```

所有裝置的裝置信息服務（ urn:miot-spec-v2:service:device-information:00007801 ）均不會生成 Home Assistant 實體。

## 多語言支援

米家集成配置選項中可選擇的集成使用的語言有簡體中文、繁體中文、英文、西班牙語、俄語、法語、德語、日語這八種語言。目前，米家集成配置頁面的簡體中文和英文已經過人工校審，其他語言由機器翻譯。如果您希望修改配置頁面的詞句，則需要修改 `custom_components/xiaomi_home/translations/` 以及 `custom_components/xiaomi_home/miot/i18n/` 目錄下相應語言的 json 檔案。

在顯示 Home Assistant 實體名稱時，米家集成會從小米雲下載裝置廠商為裝置配置的多語言檔案，該檔案包含裝置 MIoT-Spec-V2 實例的多語言翻譯。 `multi_lang.json` 是本地維護的多語言配置字典，其優先級高於從雲端獲取的多語言檔案，可用於補充或修改裝置的多語言翻譯。

`multi_lang.json` 的格式如下：

```
{
    "<MIoT-Spec-V2 device instance>": {
        "<language code>": {
            "<instance code>": <translation: str>
        }
    }
}
```

`multi_lang.json` 的鍵值為 MIoT-Spec-V2 裝置實例的 urn （不含版本號“version”字段）。

language code 為語言代碼，取值為 zh-Hans、zh-Hant、en、es、ru、fr、de、ja （對應上述米家集成可選的八種語言）。

instance code 為 MIoT-Spec-V2 實例代碼，格式如下：

```
service:<siid>                  # 服務
service:<siid>:property:<piid>  # 屬性
service:<siid>:property:<piid>:valuelist:<value> # 屬性取值列表的值
service:<siid>:event:<eiid>     # 事件
service:<siid>:action:<aiid>    # 方法
```

siid、piid、eiid、aiid、value 均為十進制三位整數。

示例：

```
{
    "urn:miot-spec-v2:device:health-pot:0000A051:chunmi-a1": {
        "zh-Hant": {
            "service:002": "養生壺",
            "service:002:property:001": "工作狀態",
            "service:002:property:001:valuelist:000": "待機中",
            "service:002:action:002": "停止烹飪",
            "service:005:event:001": "烹飪完成"
        }
    }
}
```

> 在 Home Assistant 中修改了 `custom_components/xiaomi_home/translations/` 路徑下的 `specv2entity.py`、`spec_filter.json`、`multi_lang.json` 檔案的內容，需要在集成配置中更新實體轉換規則才能生效。方法：[設定 > 裝置與服務 > 已配置 > Xiaomi Home](https://my.home-assistant.io/redirect/integration/?domain=xiaomi_home) > 配置 > 更新實體轉換規則

## 文檔

- [許可證](../LICENSE.md)
- 貢獻指南： [English](../CONTRIBUTING.md) | [简体中文](./CONTRIBUTING_zh.md) | [繁體中文](./CONTRIBUTING_zh.md)
- [更新日誌](../CHANGELOG.md)
- 開發文檔： https://developers.home-assistant.io/docs/creating_component_index

## 目錄結構

- miot：核心代碼。
- miot/miot_client：每加入一個用戶需要增加一個 miot_client 實例。
- miot/miot_cloud：雲服務相關功能，包括 OAuth 登入、 HTTP 介面功能（獲取用戶信息、發送裝置控制指令等）。
- miot/miot_device：裝置實體，包含裝置信息以及屬性、事件、方法的處理邏輯。
- miot/miot_mips：消息總線，用於訂閱和發佈消息。
- miot/miot_spec：解析 MIoT-Spec-V2 。
- miot/miot_lan: 裝置局域網控制，包括裝置發現、裝置控制等。
- miot/miot_mdns: 中樞閘道服務局域網發現。
- miot/miot_network：獲取網路狀態和網路信息。
- miot/miot_storage: 集成檔案存儲。
- miot/test：測試腳本。
- config_flow：配置流程。
