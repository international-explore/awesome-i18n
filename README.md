- [1. **项目简介**](#1-项目简介)
- [2. **基础概念**](#2-基础概念)
  - [2.1国际化和本地化的概念解释](#21国际化和本地化的概念解释)
  - [2.2 国际化和本地化的范围](#22-国际化和本地化的范围)
    - [语言](#语言)
    - [货币](#货币)
    - [时间](#时间)
    - [数字](#数字)
    - [度量衡：公制、英制、美制等](#度量衡公制英制美制等)
    - [电话、邮编、地址等](#电话邮编地址等)
    - [名字和称谓](#名字和称谓)
    - [法律法规等](#法律法规等)
  - [2.3 locale(语言标记和区域标识)的解释](#23-locale语言标记和区域标识的解释)
      - [维基百科的解释](#维基百科的解释)
      - [ICU中locale的解释](#icu中locale的解释)
      - [locale的组成](#locale的组成)
  - [2.4 时间相关概念](#24-时间相关概念)
  - [2.5 字符编码和字符集的基础知识](#25-字符编码和字符集的基础知识)
- [3. **相关标准**](#3-相关标准)
  - [Unicode和UTF-8编码](#unicode和utf-8编码)
  - [CLDR（Common Locale Data Repository）](#cldrcommon-locale-data-repository)
  - [时区标准](#时区标准)
  - [BCP 47标准介绍（语言标记和区域标识）](#bcp-47标准介绍语言标记和区域标识)
  - [ISO标准](#iso标准)
    - [国家代码标准](#国家代码标准)
      - [ISO 3166](#iso-3166)
    - [货币代码标准](#货币代码标准)
      - [ISO 4217 三个字母货币代码](#iso-4217-三个字母货币代码)
      - [ISO 10916 货币金额表示法](#iso-10916-货币金额表示法)
    - [时间相关标准](#时间相关标准)
      - [ISO 8601 日期和时间的表示方法](#iso-8601-日期和时间的表示方法)
- [4. **最佳实践**](#4-最佳实践)
  - [4.1 多语言文案](#41-多语言文案)
  - [4.2 货币](#42-货币)
  - [4.3 时间](#43-时间)
- [5. **工具集合**](#5-工具集合)
  - [5.1 时间](#51-时间)
    - [5.1.1 时区工具](#511-时区工具)
    - [5.1.2 时间格式化](#512-时间格式化)
    - [5.1.3 日历](#513-日历)
  - [5.2 货币](#52-货币)
      - [5.2.1 汇率](#521-汇率)
- [6. **知名开源项目**](#6-知名开源项目)
  - [6.1 I18N通用项目](#61-i18n通用项目)
    - [ICU](#icu)
    - [icu4x](#icu4x)
  - [6.2 翻译](#62-翻译)
  - [6.3 时间](#63-时间)
  - [6.4 数字+货币](#64-数字货币)
- [7. i18n典型代码和实现原理](#7-i18n典型代码和实现原理)
  - [java](#java)
  - [go](#go)
- [8. 大厂i18n实现方式案例](#8-大厂i18n实现方式案例)
- [9. **贡献指南**](#9-贡献指南)
- [10. **其他资源**](#10-其他资源)
  - [10.1 书籍、论文、博客和教程](#101-书籍论文博客和教程)
  - [10.2 网站外链](#102-网站外链)


# 1. **项目简介**

awesome-i18n，旨在收集和分享出海i18n相关的一些领域知识和技术工具。
包括基础概念、相关标准、最佳实践、工具集合等

# 2. **基础概念**

## 2.1国际化和本地化的概念解释

*   i18n - internationalization：国际化，是指在设计软件，将软件与特定语言及地区脱钩的过程。当软件被移植到不同的语言及地区时，软件本身不用做内部工程上的改变或修正。主要包括货币、时间、度量衡等本地化因素的适配技术。
*   l10n - localization：本地化，是指当移植软件时，加上与特定区域设置有关的信息和翻译文件的过程。主要包括翻译、多语言等本地化文案适配技术。

[维基百科对国际化和本地化的解释](https://zh.wikipedia.org/zh-cn/%E5%9B%BD%E9%99%85%E5%8C%96%E4%B8%8E%E6%9C%AC%E5%9C%B0%E5%8C%96)

国际化和本地化之间的区别虽然微妙，但却很重要。国际化意味着产品有适用于任何地方的“潜力”；本地化则是为了更适合于“特定”地方的使用，而另外增添的特色。用一项产品来说，国际化只需做一次，但本地化则要针对不同的区域各做一次。这两者之间是互补的，并且两者合起来才能让一个系统适用于各地。

## 2.2 国际化和本地化的范围
### 语言
    - 字母编码：unicode编码
    - 书写方向：从左到右、从右到左
    - 文案翻译：中到英、英到多语，机器翻译、人工翻译、chatGPT翻译
    - 图片、音频
    - 文化差异：禁忌语、大小写、单复数等
### 货币
- 国家使用的货币币种
- 货币码（字母代码、数字代码）、货币精度
- 货币格式化（货币三要素：金额、币种、单位）
- 汇率

### 时间
- 时区：时区名称、时区偏移、夏令时规则、国家城市的时区等   
- 日期时间：
    - 格式化（年月日时分秒、上下午、24小时制或者12小时制）
    - 获取时间戳
    - 倒计时
    - 时间段格式化
- 日历：
    - 获取年月日、星期几等日历信息
    - 周末、节假日
    - 时间加减

### 数字
- 数字命名系统
- 小数点、千分位的符号
- 数字舍入方式：四舍五入、银行家取整、向上、向下取整
- 百分比数字
- 短格式数字，如5K

### 度量衡：公制、英制、美制等
- 长度：千米、米、厘米等的格式化
- 温度：华氏度、摄氏度
- 重量：吨、千克、克等
- 容量：升、毫升等
- 面积：平方公里、平方米
- 坐标：经纬度

### 电话、邮编、地址等
- 电话：区号、手机号验证、报警电话
- 邮编
- 地址

### 名字和称谓
- fullName、shortName
- 昵称

### 法律法规等

## 2.3 locale(语言标记和区域标识)的解释

#### 维基百科的解释
计算机中一套定义用户的语言、国家和用于定义用户希望在其用户界面上看到的各种可以改变的选择的参数集合。通常一个区域设置标识符至少包括一个语言标识符和一个区域标识符。

[维基百科中的locale解释](https://zh.wikipedia.org/wiki/%E5%8C%BA%E5%9F%9F%E8%AE%BE%E7%BD%AE)

#### ICU中locale的解释
lcaole标识了一个特定的用户社区——一群具有相似文化和语言期望的用户。
[icu中的locale解释](https://unicode-org.github.io/icu/userguide/locale/#the-locale-concept)

#### locale的组成
一般由 **语言码** 和 **地区码** 组成。
```
zh-CN 中文+中国大陆
en-US 英文+美国
pt-BR 葡语+巴西
es-MX 西语+墨西哥
```


## 2.4 时间相关概念

## 2.5 字符编码和字符集的基础知识

unicode

# 3. **相关标准**

## Unicode和UTF-8编码

## CLDR（Common Locale Data Repository）

## 时区标准

[IANA时区数据库](https://www.iana.org/time-zones)

数据标准和文件解读：<https://mp.weixin.qq.com/s/joZdNPbGPJMPs67yzyrlvg>

## BCP 47标准介绍（语言标记和区域标识）
## ISO标准

### 国家代码标准

#### ISO 3166

该标准定义了所有国家和地区的代码，用于在国际交流、商务和政府间合作等方面的标识。
[ISO官网链接](https://www.iso.org/iso-3166-country-codes.html)
[wiki链接](https://zh.wikipedia.org/zh/ISO_3166-1)

ISO 3166-1 国家代码标准：该标准定义了全球所有国家和地区的代码和名称，共包括249个国家和地区。其中，国家代码由2个字母组成，地区代码由3个字母组成。例如，中国的国家代码是“CN”，美国的国家代码是“US”，而英国的地区代码是“GB-ENG”。

ISO 3166-2 国家行政区划代码标准：该标准定义了各个国家的行政区划代码和名称。这些代码可以用于政府、商业和其他领域中进行国家和地区的标识和分类。例如，中国的行政区划代码包括“CN-11”（北京市）、“CN-44”（广东省）等。

ISO 3166-3 国家名称变更标准：该标准定义了国家和地区名称变更时的处理方式和规则。该标准主要用于处理国家和地区名称的历史变更，以确保标准的连续性和一致性。

### 货币代码标准

#### ISO 4217 三个字母货币代码

这是一份国际标准，定义了三个字母的货币代码，例如 USD 表示美元。此标准还定义了每个货币的小数点位置和格式等信息。
[ISO 4217的官方链接](https://www.iso.org/iso-4217-currency-codes.html)
[维基百科链接](https://zh.wikipedia.org/zh-hans/ISO_4217)

#### ISO 10916 货币金额表示法

这是一份国际标准，规定了货币金额表示法的基本原则，包括货币符号、金额表示方式、货币小数点分隔符等。
[ISO 10916的官方链接](https://www.iso.org/standard/57248.html)

ISO 15022 - 这是一份国际标准，规定了金融电报和电子交换数据的格式和内容规则。ISO 15022定义了用于表示货币的代码和符号，以及货币金额的表示方法。ISO 15022的官方链接为：<https://www.iso.org/standard/31443.html>

ISO 20022 - 这是一份国际标准，为金融机构提供了一种统一的数据模型和通信方式。该标准定义了一个用于交换财务信息的XML格式，其中包括用于表示货币的代码和符号，以及货币金额的表示方法。ISO 20022的官方链接为：<https://www.iso20022.org/>

### 时间相关标准
#### [ISO 8601](https://zh.wikipedia.org/zh-hans/ISO_8601) 日期和时间的表示方法

ISO 8601：该标准规定了日期和时间的表示方法，包括年、月、日、小时、分钟和秒等信息，也可以表示带时区偏移量的日期和时间。该标准适用于各种应用场景，如数据交换、文件存储、电子邮件等等。
ISO 8601标准官网链接：https://www.iso.org/iso-8601-date-and-time-format.html
维基百科链接：(https://zh.wikipedia.org/zh-hans/ISO_8601)

# 4. **最佳实践**

## 4.1 多语言文案

## 4.2 货币
"Internationalizing Currency Display" (Unicode Consortium)：介绍了国际化中货币显示的标准和最佳实践。
链接：https://unicode.org/reports/tr35/tr35-numbers.html#Currency_Display


## 4.3 时间


# 5. **工具集合**

## 5.1 时间

### 5.1.1 时区工具

时区查看工具，基于IANA发布的TZDB数据制作：<https://nodatime.org/TimeZones>

时区的一些说明和工具网站链接：<https://data.iana.org/time-zones/tz-link.html>

### 5.1.2 时间格式化
[时间戳转换](https://tool.chinaz.com/Tools/unixtime.aspx)

### 5.1.3 日历
网站：
- Time and Date (https://www.timeanddate.com/holidays/) - 提供全球节假日的信息和日期计算工具。
- Holiday API (https://www.holidayapi.com/) - 提供全球节假日信息和日期查询功能。
- Office Holidays (https://www.officeholidays.com/) - 提供全球节假日信息，按国家和地区分类。

API接口：
- Calendarific (https://calendarific.com/) - 提供全球节假日和工作日的API接口，支持按国家和地区查询。
- Holiday API (https://www.holidayapi.com/) - 上述网站也提供了API接口，可以查询全球节假日信息。

## 5.2 货币

#### 5.2.1 汇率

相关api站点工具

| 站点链接                                                                               | 特性          |
| ---------------------------------------------------------------------------------- | ----------- |
| [fixer](https://fixer.io/documentation)                                            | 小时更新, eur基准 |
| [Currency API](https://currencylayer.com/documentation)                            | 每日更新、usd基准  |
| [openexchangerates](https://docs.openexchangerates.org/reference/api-introduction) | 小时更新、usd为基准 |

*   语言资源管理工具和平台
*   字符编码转换工具和库

# 6. **知名开源项目**

## 6.1 I18N通用项目

### ICU

介绍

*   [ICU](https://unicode-org.github.io/icu/) international components for unicode，国际化unicode组件库。ICU是一个开源的C/C++、java类库，提供unicode和全球化支持。它是跨平台的，在所有平台都可以给出相同的结果。

[icu文档](https://unicode-org.github.io/icu/)

[icu的github](https://github.com/unicode-org/icu)

[icu的数据](https://github.com/unicode-org/icu-data)

### icu4x

*   [icu4x](https://github.com/unicode-org/icu4x) - CU4X提供了支持广泛软件国际化的组件。它深刻借鉴了ICU4C、ICU4J和ECMA-402的经验，并依赖于CLDR项目的数据。

## 6.2 翻译
- gettext: https://www.gnu.org/software/gettext/, 是GNU国际化与本地化（i18n）函数库，获取多语言文案

## 6.3 时间
Moment.js - 一个JavaScript库，用于解析、验证、操作和显示日期和时间，支持本地化和国际化。Github链接：https://github.com/moment/moment

date-fns - 另一个用于处理日期和时间的JavaScript库，它强调了函数式编程和不可变性，也支持本地化和国际化。Github链接：https://github.com/date-fns/date-fns

Chrono - 一个用于解析和格式化自然语言日期和时间的JavaScript库，支持多种语言和时区。Github链接：https://github.com/wanasit/chrono

pytz - Python的时区处理库，可以轻松地处理不同时区的时间转换。Github链接：https://github.com/stub42/pytz

## 6.4 数字+货币

*   accounting.js: 一个用于格式化和处理货币、数字和货币的 JavaScript 库，支持多种货币格式和货币计算。它可以在浏览器端和 Node.js 中使用。Github链接：<https://github.com/josscrowcroft/accounting.js/>
*   big.js: 一个用于处理大数字和货币计算的 JavaScript 库。它支持多种货币，可以在浏览器端和 Node.js 中使用。Github链接：<https://github.com/MikeMcl/big.js/>
*   MoneyPHP: 一个 PHP 库，可以格式化和处理货币，支持各种货币和货币计算。Github链接：<https://github.com/moneyphp/money>
*   django-money: 一个 Django 库，可以在 Django 应用程序中处理货币，支持多种货币格式和货币计算。Github链接：<https://github.com/django-money/django-money>
*   Numeral.js: 一个用于格式化和处理数字的 JavaScript 库，支持各种数字格式、货币和货币计算。它可以在浏览器端和 Node.js 中使用。Github链接：<https://github.com/adamwdraper/Numeral-js>
*   jpmorganchase/number: 一个 Java 库，可以格式化货币金额、执行货币计算，支持多种货币和货币格式。Github链接：<https://github.com/jpmorganchase/number>

# 7. i18n典型代码和实现原理

## java

## go

*   逐个列举主流编程语言，介绍它们的i18n实现原理和特点
*   比较不同语言的i18n实践差异和注意事项

# 8. 大厂i18n实现方式案例

*   收集和介绍一些知名互联网公司（如Google、Facebook、Netflix等）的i18n实现方式和经验分享
*   分享大厂在多语言应用和本地化方面的最佳实践

# 9. **贡献指南**

*   如何贡献到"awesome-i18n"项目
*   提交问题和建议的指南
*   鼓励贡献者分享自己的经验和知识

# 10. **其他资源**

## 10.1 书籍、论文、博客和教程
* 视频课程：
     * 谷歌同学的一个教程： https://www.udacity.com/course/localization-essentials--ud610 
* [l10n成熟度标准](https://blog.andovar.com/localization-maturity-model-how-does-your-company-measure-up)

## 10.2 网站外链

 * [W3C international](https://www.w3.org/blog/international/) - W3C international网站，涵盖w3c在international方向的标准、手册、工具等。
 * [ICU 官网](https://icu.unicode.org/) - 为应用提供Unicode和全球化支持的一套成熟、广泛使用的组件库
 * 本地化服务供应商
   * [RWS](https://www.rws.com/cn/localization/)
   * [translations.com](https://zh_cn.translations.com/)
   * [lionbridge](https://www.lionbridge.com/zh-hans/)
   * [welocalize](https://www.welocalize.com/zh-hans/)
 * 翻译相关平台
   * [字节国际化翻译平台](https://www.volcengine.com/products/starling)
