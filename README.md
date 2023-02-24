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
* [出海企业新闻和文章](#出海企业新闻和文章)
* [出海白皮书](#出海白皮书)
* [书籍](#书籍)
* [微信公众号](#微信公众号)
* [网站外链](#网站外链)
  
## i18n-internationalization 
#### 开发工具
- [icu](https://unicode-org.github.io/icu/)ICU：international components for unicode，国际化unicode组件。ICU是一个开源的C/C++、java类库，它给程序提供unicode和全球化支持。它是跨平台的，在所有平台都可以给出相同的结果。ICU是**library**
- [cldr](https://github.com/unicode-org/cldr) The Unicode Common Locale Data Repository,Unicode通用语言环境数据存储库。CLDR是**数据集**
- [icu4x](https://github.com/unicode-org/icu4x) - CU4X提供了支持广泛软件国际化的组件。它深刻借鉴了ICU4C、ICU4J和ECMA-402的经验，并依赖于CLDR项目的数据。
#### 相关站点
W3C国际化活动小组 (Internationalization Activity)：W3C国际化活动小组提供了一系列国际化和本地化的技术规范，包括HTML、CSS、XML等，旨在为Web开发者提供标准化的国际化方案。

Mozilla开发者网络 (MDN Web Docs)：Mozilla开发者网络提供了很多关于i18n的文档和教程，包括国际化和本地化的指南、多语言网站的实现等。

i18n资源库 (i18n-resource-repo)：这是一个公共的i18n资源库，包括了很多翻译好的文本资源，可以帮助开发者快速构建多语言网站。

Google开发者中心 (Google Developers)：Google开发者中心提供了许多有关国际化和本地化的文档和教程，包括如何构建跨文化的应用程序等。

阮一峰的网络日志 (ruanyifeng.com)：阮一峰的网络日志是一位知名技术博主，他的博客中提供了许多有关i18n的文章，包括如何处理多语言字符串、如何进行本地化等。

Unicode Consortium：Unicode Consortium是一个非营利性组织，它维护了Unicode标准，为数字、字母、符号和其他字符提供唯一的标识符，从而使得跨语言和跨文化的通信和交互成为可能。

Internationalization and Localization Industry Standards Association (ILISA)：ILISA是一个致力于推动国际化和本地化行业标准化的非营利组织，其官方网站提供了有关国际化和本地化的文章、新闻、博客等信息。

IBM Globalization (IBM Globalization)：IBM Globalization提供了各种与国际化和本地化相关的产品和服务，其官方网站还提供了许多与国际化和本地化相关的文档和教程。

Java Internationalization (Java i18n)：Java Internationalization是Java语言中处理国际化和本地化的工具和库，其官方网站提供了各种与Java国际化和本地化相关的教程、文档和代码示例。

Gettext (GNU gettext)：Gettext是一个开源的国际化和本地化工具，支持各种编程语言，包括C/C++、Python、Ruby等，其官方网站提供了有关Gettext的文档和教程。
#### 经典文章
"Unicode and Internationalization" by Mark Davis and Markus Scherer - 该文章介绍了Unicode标准及其在国际化方面的应用。链接：http://unicode.org/reports/tr26/

"Internationalization Best Practices: Specifying Language in XHTML and HTML Content" by Richard Ishida - 该文章讲述了在XHTML和HTML内容中指定语言的最佳实践。链接：https://www.w3.org/International/articles/language-tags/

"Character Sets and Encodings" by Mark Pilgrim - 该文章介绍了字符集和编码的概念，并介绍了在Web开发中如何正确处理它们。链接：https://diveinto.html5doctor.com/encoding.html

"The importance of language tags in HTML and XML" by Geert Van Damme - 该文章讨论了在HTML和XML中使用语言标记的重要性，以及如何正确使用它们来支持国际化。链接：https://www.w3.org/International/articles/language-tags/

"Internationalization: The Multi-Lingual Web" by Richard Ishida - 该文章涵盖了各种Web国际化问题的概述，包括语言标记、字符集和编码、本地化资源、文本排序和其他相关问题。链接：https://www.w3.org/International/tutorials/internationalization/


### 国家/地区-country/region
#### 相关标准
ISO 3166 国家代码标准：该标准定义了所有国家和地区的代码，用于在国际交流、商务和政府间合作等方面的标识。ISO官网链接：https://www.iso.org/iso-3166-country-codes.html wiki链接：https://zh.wikipedia.org/zh/ISO_3166-1

ISO 3166-1 国家代码标准：该标准定义了全球所有国家和地区的代码和名称，共包括249个国家和地区。其中，国家代码由2个字母组成，地区代码由3个字母组成。例如，中国的国家代码是“CN”，美国的国家代码是“US”，而英国的地区代码是“GB-ENG”。

ISO 3166-2 国家行政区划代码标准：该标准定义了各个国家的行政区划代码和名称。这些代码可以用于政府、商业和其他领域中进行国家和地区的标识和分类。例如，中国的行政区划代码包括“CN-11”（北京市）、“CN-44”（广东省）等。

ISO 3166-3 国家名称变更标准：该标准定义了国家和地区名称变更时的处理方式和规则。该标准主要用于处理国家和地区名称的历史变更，以确保标准的连续性和一致性。


### 货币部分-currency

#### 货币标准

ISO 4217 - 这是一份国际标准，定义了三个字母的货币代码，例如 USD 表示美元。此标准还定义了每个货币的小数点位置和格式等信息。ISO 4217的官方链接为：https://www.iso.org/iso-4217-currency-codes.html 维基百科的链接：https://zh.wikipedia.org/zh-hans/ISO_4217

ISO 10916 - 这是一份国际标准，规定了货币金额表示法的基本原则，包括货币符号、金额表示方式、货币小数点分隔符等。ISO 10916的官方链接为：https://www.iso.org/standard/57248.html

ISO 15022 - 这是一份国际标准，规定了金融电报和电子交换数据的格式和内容规则。ISO 15022定义了用于表示货币的代码和符号，以及货币金额的表示方法。ISO 15022的官方链接为：https://www.iso.org/standard/31443.html

ISO 20022 - 这是一份国际标准，为金融机构提供了一种统一的数据模型和通信方式。该标准定义了一个用于交换财务信息的XML格式，其中包括用于表示货币的代码和符号，以及货币金额的表示方法。ISO 20022的官方链接为：https://www.iso20022.org/


#### 货币展示样式
CLDR数据集：
- [货币displayname和symbol示例](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-numbers-modern/main/zh/currencies.json)
- [货币展示样式示例](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-numbers-modern/main/zh/numbers.json#L143)


#### 汇率
相关api站点工具

| 站点链接      | 特性 |
| ----------- | ----------- |
| [fixer](https://fixer.io/documentation)      | 小时更新, eur基准|
| [Currency API](https://currencylayer.com/documentation)   | 每日更新、usd基准 |
| [openexchangerates](https://docs.openexchangerates.org/reference/api-introduction) | 小时更新、usd为基准 |

#### 货币开发工具
money.js: 一个简单的 JavaScript 货币库，可以格式化货币金额、执行货币计算，支持各种货币，包括自定义货币。它可以在浏览器端和 Node.js 中使用。Github链接：https://github.com/openexchangerates/money.js/

accounting.js: 一个用于格式化和处理货币、数字和货币的 JavaScript 库，支持多种货币格式和货币计算。它可以在浏览器端和 Node.js 中使用。Github链接：https://github.com/josscrowcroft/accounting.js/

big.js: 一个用于处理大数字和货币计算的 JavaScript 库。它支持多种货币，可以在浏览器端和 Node.js 中使用。Github链接：https://github.com/MikeMcl/big.js/

MoneyPHP: 一个 PHP 库，可以格式化和处理货币，支持各种货币和货币计算。Github链接：https://github.com/moneyphp/money

django-money: 一个 Django 库，可以在 Django 应用程序中处理货币，支持多种货币格式和货币计算。Github链接：https://github.com/django-money/django-money

Numeral.js: 一个用于格式化和处理数字的 JavaScript 库，支持各种数字格式、货币和货币计算。它可以在浏览器端和 Node.js 中使用。Github链接：https://github.com/adamwdraper/Numeral-js

jpmorganchase/number: 一个 Java 库，可以格式化货币金额、执行货币计算，支持多种货币和货币格式。Github链接：https://github.com/jpmorganchase/number

#### 货币经典文章
"Internationalizing Currency Display" (Unicode Consortium)：介绍了国际化中货币显示的标准和最佳实践。
链接：https://unicode.org/reports/tr35/tr35-numbers.html#Currency_Display


"Currency Formatting Best Practices" (Globalization Partners International)：介绍了货币格式化的最佳实践。
链接：https://www.globalizationpartners.com/2018/09/05/currency-formatting-best-practices/

### 时间部分-time
#### 时间展示样式
- [时间字段](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/dateFields.json) 包括纪元、年、季度、月、周、日、时分秒等
- [展示样式](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/ca-gregorian.json)包括日期格式化、时间格式化、时间段格式化


#### 日历相关
各种历法
- [维基百科历法说明](https://zh.wikipedia.org/zh-hans/%E5%8E%86%E6%B3%95)
- [国际通用公历](https://zh.wikipedia.org/wiki/%E5%85%AC%E5%8E%86)
- [CLDR中的历法数据](https://github.com/unicode-org/cldr-json/tree/main/cldr-json) cldr-cal开头的文件

节假日
- 节假日查询工具网站：https://www.timeanddate.com/holidays/

#### 时区
- [IANA时区数据库](https://www.iana.org/time-zones)
- 时区查看工具，基于IANA发布的TZDB数据制作：https://nodatime.org/TimeZones
#### 时间标准
- [ISO 8601](https://zh.wikipedia.org/zh-hans/ISO_8601) 国际标准化组织的日期和时间的表示方法

ISO 8601：该标准规定了日期和时间的表示方法，包括年、月、日、小时、分钟和秒等信息，也可以表示带时区偏移量的日期和时间。该标准适用于各种应用场景，如数据交换、文件存储、电子邮件等等。ISO 8601标准的具体内容可以在以下链接中查看：https://www.iso.org/iso-8601-date-and-time-format.html 维基百科链接：(https://zh.wikipedia.org/zh-hans/ISO_8601)

POSIX时间：该标准定义了一个以1970年1月1日00:00:00 UTC为起点的时间系统，以秒为单位表示时间。POSIX时间主要用于Unix系统中，也是许多编程语言中表示时间的标准。该标准的具体内容可以在以下链接中查看：https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap04.html#tag_04_15

RFC 3339：该标准基于ISO 8601标准，规定了一种日期和时间的表示方法，同时也支持带时区偏移量的日期和时间。RFC 3339主要用于互联网协议中，如XML、JSON等格式中的时间表示。该标准的具体内容可以在以下链接中查看：https://datatracker.ietf.org/doc/html/rfc3339

Unicode CLDR：该标准是针对不同地区和语言的本地化需求而制定的，定义了各种日期和时间格式的模式和规则。Unicode CLDR包含了全球各地的日期、时间、时区和节假日等信息，是很多国际化软件和网站中常用的时间标准之一。该标准的具体内容可以在以下链接中查看：https://cldr.unicode.org/index/cldr-spec/dates-times


#### 时间开发工具
Moment.js - 一个JavaScript库，用于解析、验证、操作和显示日期和时间，支持本地化和国际化。Github链接：https://github.com/moment/moment

date-fns - 另一个用于处理日期和时间的JavaScript库，它强调了函数式编程和不可变性，也支持本地化和国际化。Github链接：https://github.com/date-fns/date-fns

ICU - 国际组件库，包括一个日期和时间格式化工具，可以格式化和解析各种日期和时间格式，并支持本地化和国际化。Github链接：https://github.com/unicode-org/icu

Chrono - 一个用于解析和格式化自然语言日期和时间的JavaScript库，支持多种语言和时区。Github链接：https://github.com/wanasit/chrono

pytz - Python的时区处理库，可以轻松地处理不同时区的时间转换。Github链接：https://github.com/stub42/pytz
#### 时间相关站点
- [时间戳转换](https://tool.chinaz.com/Tools/unixtime.aspx)

timeanddate.com: 这个网站提供了丰富的时间和日期工具，包括世界时钟、日出日落时间、时区转换、会议计算器等等。链接：https://www.timeanddate.com/

worldtimebuddy.com: 这个网站可以帮助你快速地查看不同城市之间的时间差，并支持定制化的时区列表和时间格式。链接：https://www.worldtimebuddy.com/

thetimenow.com: 这个网站提供了全球各地的实时时钟、日出日落时间、时区地图等工具。链接：https://www.thetimenow.com/

Every Time Zone: 这个网站提供了一个简单易用的界面，可以轻松查看世界各地的时间、日期和时区。链接：https://everytimezone.com/

#### 时间经典文章
- [欧美地区的夏令时有什么意义？](https://www.zhihu.com/question/37097917)
- [时标和历法](http://www.fmddlmyy.cn/text8.html)
- 时间是怎么来的]https://mp.weixin.qq.com/s/SlL040FjK90_TF7pd2lkGg

### 度量衡相关
- [度量衡系统类型](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-units-modern/main/zh/measurementSystemNames.json) 公制、英制、美制
- [单位](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-units-modern/main/zh/units.json)

常见度量衡类型：
- 长度
- 面积
- 体积
- 重量
- 温度
- 坐标

参考：[度量衡](technology/problem_domain/standard/unit.md)

## l10n-localization 
- [l10n成熟度标准](https://blog.andovar.com/localization-maturity-model-how-does-your-company-measure-up)


## 出海企业新闻和文章
### 出海企业
#### 字节
- tiktok：海外版抖音
- IfYooou：对标SHEIN的快时尚跨境独立站

#### 腾讯
海外市场业务主要包括游戏、社交网络、数字内容、金融科技等领域，拥有海外用户超过十亿。
#### 华为
在海外市场主要是手机、通信设备、云计算等领域，是全球最大的电信设备供应商之一。
#### 小米
在印度、东南亚等地区市场表现优异，业务主要涵盖智能手机、智能家居、智能电视等领域。
#### 拼多多
- Temu：海外版拼多多
#### 阿里
- 阿里国际站：和To B的数字化跨境贸易平台
- 速卖通：B2C 跨境零售电商平台,覆盖超过 200 个国家
- 收购了本土电商平台 Trendyol
- 东南亚电商平台 Lazada
- 阿里在西班牙的新电商平台 Miravia 
#### 快手
- Kwai：快手短视频国际版
  
#### SHEIN
- 希音SHEIN是一家全球领先的时尚和生活方式在线零售商。服务全球超过150个国家的消费者。

### 新闻和文章


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