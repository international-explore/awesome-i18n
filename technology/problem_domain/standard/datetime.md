# 时间日期

## 时间日期相关的配置

#### [时间日期字段](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/dateFields.json)

比如 年月日 时分秒 季度 周 纪元 时区

#### [公历的时间日期展示](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/ca-gregorian.json)

- 日期格式化
- 时间格式化
- 时间间隔格式化

#### [时区信息](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/timeZoneNames.json)

```json
{
    "main":{
        "zh":{
            "identity":{
                "version":{
                    "_cldrVersion":"41"
                },
                "language":"zh"
            },
            "dates":{
                "timeZoneNames":{
                    "hourFormat":"+HH:mm;-HH:mm",
                    "gmtFormat":"GMT{0}",
                    "gmtZeroFormat":"GMT",
                    "regionFormat":"{0}时间",
                    "regionFormat-type-daylight":"{0}夏令时间",
                    "regionFormat-type-standard":"{0}标准时间",
                    "fallbackFormat":"{1}（{0}）",
                    "zone":Object{...},
                    "metazone":Object{...}
                }
            }
        }
    }
}
```