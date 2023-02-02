# 国际化出海技术交流

旨在收集和分享出海i18n相关的一些领域知识和技术工具。
内容上包括重要标准、开发工具、经典文章、相关书籍、白皮书、出海创业企业、英文词汇和重要新闻等。
范围整体分为两大部分
- i18n - internationalization：主要包括货币、时间、度量衡等本地化因素的适配技术
- l10n - localization：主要包括翻译、多语言等本地化文案适配技术


# 内容目录
* [i18n-internationalization](#i18n-internationalization) 
    * [LOCALE - LOCALE、CLDR等通用部分](#通用标准)
    * [CURRENCY - 货币相关问题](#货币部分-currency)
    * [TIME - 时间相关问题](#时间部分-time)
    * [MEASURE - 度量衡相关问题](#度量衡相关)
    * [NUMBER - 数字相关问题]()
    * [PHONE - 电话相关问题]()
    * [MESSAGE - 信息相关问题，涵盖标题、标签、错误信息等]()
    * [COLLATE - 比较习惯相关问题]()
    * [NAME - 姓名相关问题]()
    * [ADDRESS - 地址相关问题]()
    * [PAPER - 纸张相关问题]()
    * [POSTCODE - 邮编相关问题]()
    * [IDIOM - 习惯语相关问题]()
    * [TABOO - 禁忌语相关问题]()
    * [BRAND - 品牌相关问题]()
    * [EVENT - 各地重大事件相关]()
    * [WEATHER - 天气重大事件相关]()
* [l10n-localization](#l10n-localization)
    * [文案相关问题](#文案相关问题)
* [出海企业和新闻](#出海企业和新闻)
  
## i18n-internationalization 
#### 通用标准

#### 权威组织
#### 开发工具
[icu](https://unicode-org.github.io/icu/)ICU：international components for unicode，国际化unicode组件。ICU是一个开源的C/C++、java类库，它给程序提供unicode和全球化支持。它是跨平台的，在所有平台都可以给出相同的结果。ICU是**library**

[cldr](https://github.com/unicode-org/cldr) The Unicode Common Locale Data Repository,Unicode通用语言环境数据存储库。CLDR是**数据集**

[icu4x](https://github.com/unicode-org/icu4x) - CU4X提供了支持广泛软件国际化的组件。它深刻借鉴了ICU4C、ICU4J和ECMA-402的经验，并依赖于CLDR项目的数据。
#### 相关站点
#### 经典文章

### 货币部分-currency

#### 货币标准
[iso 4217 表示货币或资金名称](https://www.iso.org/iso-4217-currency-codes.html)

#### 国家使用的币种

#### 货币展示样式
CLDR数据集：
[货币displayname和symbol示例](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-numbers-modern/main/zh/currencies.json)
[货币展示样式示例](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-numbers-modern/main/zh/numbers.json#L143)

#### 货币精度

#### 汇率
相关api站点工具

| 站点链接      | 特性 |
| ----------- | ----------- |
| [fixer](https://fixer.io/documentation)      | 小时更新, eur基准|
| [Currency API](https://currencylayer.com/documentation)   | 每日更新、usd基准 |
| [openexchangerates](https://docs.openexchangerates.org/reference/api-introduction) | 小时更新、usd为基准 |

#### 货币权威组织
#### 货币开发工具
#### 货币相关站点
#### 货币经典文章

### 时间部分-time
#### 时间展示样式
[时间字段](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/dateFields.json) 包括纪元、年、季度、月、周、日、时分秒等
[展示样式](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/ca-gregorian.json)包括日期格式化、时间格式化、时间段格式化


#### 日历相关
各种历法
[维基百科历法说明](https://zh.wikipedia.org/zh-hans/%E5%8E%86%E6%B3%95)
[国际通用公历](https://zh.wikipedia.org/wiki/%E5%85%AC%E5%8E%86)
[CLDR中的历法数据](https://github.com/unicode-org/cldr-json/tree/main/cldr-json) cldr-cal开头的文件

节假日
- 节假日查询工具网站：https://www.timeanddate.com/holidays/

#### 时区
[IANA时区数据库](https://www.iana.org/time-zones)

时区查看工具，基于IANA发布的TZDB数据制作：https://nodatime.org/TimeZones
#### 时间标准
[ISO 8601](https://zh.wikipedia.org/zh-hans/ISO_8601) 国际标准化组织的日期和时间的表示方法

#### 时间权威组织
#### 时间开发工具

#### 时间相关站点
[时间戳转换](https://tool.chinaz.com/Tools/unixtime.aspx)

#### 时间经典文章
[欧美地区的夏令时有什么意义？](https://www.zhihu.com/question/37097917)
[时标和历法](http://www.fmddlmyy.cn/text8.html)

### 度量衡相关
[度量衡系统类型](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-units-modern/main/zh/measurementSystemNames.json) 公制、英制、美制

[单位](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-units-modern/main/zh/units.json)

常见度量衡类型：
- 长度
- 面积
- 体积
- 重量
- 温度
- 坐标
参考：[度量衡](technology/problem_domain/standard/unit.md)

## l10n-localization 
#### 文案相关问题

## 出海企业新闻和文章
### 出海企业
#### 字节
- tiktok：海外版抖音
- IfYooou：对标SHEIN的快时尚跨境独立站
#### 拼多多
- Temu：海外版拼多多
#### 阿里
- 速卖通：To C的跨境零售电商平台
- 阿里国际站：和To B的数字化跨境贸易平台

#### 快手
- Kwai：快手短视频国际版
  
#### SHEIN
希音SHEIN是一家全球领先的时尚和生活方式在线零售商。服务全球超过150个国家的消费者。

### 新闻和文章
#### 2023年1月
[出海，互联网大厂必修课](https://letschuhai.com/ecommerce-overseas-tiktok-temu-shein?utm_source=wechat&utm_medium=banner&utm_campaign=event&utm_id=weekly31)

[京东国际收缩，海外业务退守供应链服务](https://mp.weixin.qq.com/s/_WyrMr25orea8AjDzVSmRw)


 * i18n
   * [行业标准](/technology/industry_standard.md)
 * l10n
   * [成熟度标准](https://blog.andovar.com/localization-maturity-model-how-does-your-company-measure-up)
   *  
## 核心问题域
 * 标准本地化（有很强的规律，或其本身就遵循某个国际标准）
   * [locale](technology/problem_domain/standard/locale.md)
   * [时间](technology/problem_domain/standard/datetime.md)
   * [数字](technology/problem_domain/standard/number.md)
   * [度量衡](technology/problem_domain/standard/unit.md)
   * [电话]
 * 非标本地化（是突发或实时变化的，用标准化技术无法生成或业界尚未有权威的数据源，它们的本地化过程就依赖于人工创作或公司外系统）
   * [节假日]
   * [天气]
   * [事故]

   
## 开发工具
 * i18n
   * [ICU](https://github.com/unicode-org/icu) - 全球化支持权威的组件库，目前提供c语言和java版本
     * [icu4x](https://github.com/unicode-org/icu4x) - CU4X提供了支持广泛软件国际化的组件。它深刻借鉴了ICU4C、ICU4J和ECMA-402的经验，并依赖于CLDR项目的数据。
   * [CLDR](https://cldr.unicode.org/index) - ICU使用的核心数据集，也是i18n的核心数据集
     * 加工工具

## 出海白皮书
* [2020中国互联网企业出海白皮书](http://www.d-long.com/eWebEditor/uploadfile/202006202334

## 书籍

* 视频课程：
* * 谷歌同学的一个教程： https://www.udacity.com/course/localization-essentials--ud610 

## 微信公众号
* 36氪出海 - 提供出海企业相关的新闻
* RWS语言翻译和内容管理 - RWS(语言服务提供商)中国的官方微信
  
## 网站外链
 * [W3C international](https://www.w3.org/blog/international/) - W3C international网站，涵盖w3c在international方向的标准、手册、工具等。
 * [ICU 官网](https://icu.unicode.org/) - 为应用提供Unicode和全球化支持的一套成熟、广泛使用的组件库
 * 本地化服务供应商
   * [RWS](https://www.rws.com/cn/localization/)
   * [translations.com](https://zh_cn.translations.com/)
   * [lionbridge](https://www.lionbridge.com/zh-hans/)
   * [welocalize](https://www.welocalize.com/zh-hans/)
 * 翻译相关平台
   * [字节国际化翻译平台](https://www.volcengine.com/products/starling)