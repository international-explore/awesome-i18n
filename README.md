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
      - [Unicode](#unicode)
      - [UTF-8编码](#utf-8编码)
  - [2.6 电话相关基础知识](#26-电话相关基础知识)
      - [电话号码的组成](#电话号码的组成)
      - [电话号码的格式](#电话号码的格式)
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
    - [golang.org/x/text](#golangorgxtext)
    - [go-playground/locales](#go-playgroundlocales)
  - [6.2 翻译](#62-翻译)
  - [6.3 时间](#63-时间)
  - [6.4 数字+货币](#64-数字货币)
  - [6.5 电话](#65-电话)
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
- 数字格式化
- 小数点、千分位的符号
- 数字舍入方式：四舍五入、银行家取整、向上、向下取整
- 百分比数字
- 短格式数字，如5K
- 数字本地化书写，如 零、壹、贰、叁

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
#### Unicode
Unicode 是一种**字符编码标准**，它为世界上几乎所有的字符和文本元素提供了唯一的标识符，包括字母、数字、符号、标点符号、特殊符号和各种文字。Unicode 旨在解决不同字符集和编码的混乱，为全球范围内的文字和符号提供一致的表示和交换方式。

Unicode 使用数字来表示每个字符，这些数字称为码点（Code Point）。每个字符都有一个唯一的码点，例如，拉丁字母 "A" 的码点为 U+0041，中文汉字 "你" 的码点为 U+4F60。Unicode 支持超过一百万个码点，以涵盖各种语言、符号和文字系统。

Unicode 还定义了字符编码方案，最常用的是 UTF-8、UTF-16 和 UTF-32。这些编码方案将码点转换为字节序列，以便在计算机系统中存储和传输文本数据。

通过使用 Unicode，人们能够更容易地在不同的语言和文化之间进行文本交流，确保字符的正确显示和处理，以实现全球化和国际化的支持。

#### UTF-8编码
UTF-8（Unicode Transformation Format - 8-bit）是一种变长字符编码方案，用于将 Unicode 中的字符编码转换为字节序列以进行存储和传输。

UTF-8 的设计灵感来自 ASCII 编码，它采用了与 ASCII 兼容的编码方式，使得 ASCII 字符在 UTF-8 中的表示与 ASCII 编码相同。对于非 ASCII 字符（即 Unicode 码点大于 127 的字符），UTF-8 使用多字节序列进行编码，字节数的长度取决于字符的 Unicode 码点。

UTF-8 的编码规则如下：

对于单字节字符（Unicode 码点范围：U+0000 至 U+007F），使用一个字节表示，最高位固定为 0。
对于多字节字符，首字节的高位表示字节数，后续字节的高位都以 10 开头，用于标识该字节属于多字节字符的一部分。
UTF-8 的优势在于它兼容 ASCII 编码，并且能够表示几乎所有的 Unicode 字符，包括国际文字、符号和表情符号等。它在互联网、操作系统和各种应用程序中得到广泛支持，成为一种常用的字符编码方案。

## 2.6 电话相关基础知识
#### 电话号码的组成
国际电话号码 一般由  **国际冠码 + 国际电话区号 + 电话号码** 组成。
比如 00 86 2150504740、+86 13112345678。
- **国际冠码** ：拨出电话时候，由**拨出地区**确定的一个前缀，不同国家使用不同的标准，比如中国大陆使用 “00” 为国际冠码，拨打国际电话的时候要根据拨出地区确定国际冠码，同时，由于这个冠码太繁琐，可以使用“+”来代替任何国家的国家冠码。
- **国际电话区号**： 表示你要 **拨到哪里** ，每个国家分配的一个代码，我们熟悉的 ”86“ 是中国大陆， ”852“是中国香港，”1“ 是美国。“+86”就是由国际冠码与国际电话区号组成的。
- **电话号码**：有了上述两个部分，电话号码就确定了国家（地区），剩下的部分就是内部的电话号码了，每个不同国家、不同地区，都有可能有自己内部的电话号码格式，不过这个部分就是日常生活中最常用的部分，大家会熟悉很多。
  
举例： 假设我香港的朋友，告诉我他的电话号码是 51231234，我要给他打电话： 
1. 我需要确定我是从中国大陆拨打电话，中国大陆的国际冠码是 00，或者我不知道我的国际冠码，直接用通用的冠码 +；
2. 我需要确定香港地区的电话区号，是 852； 
3. 在朋友给我的号码前面加上上述号码，拨打 0085251231234 或者 +85251231234 才能正确拨打。

各个国家的电话区号：https://zh.wikipedia.org/zh-hans/%E5%9B%BD%E9%99%85%E7%94%B5%E8%AF%9D%E5%8C%BA%E5%8F%B7%E5%88%97%E8%A1%A8

#### 电话号码的格式
1、有哪些格式？每个格式是怎么样的？

- E.164：是国际电联推荐的国际公共电信号码计划，没有任何格式化符号，例如"+41446681800"。
- INTERNATIONAL：国际格式，包含国际前缀和国家代码，以及区号和电话号码，可以有空格或其他分隔符，例如"+41 44 668 1800"。
- NATIONAL：国内格式，一般不包含国家代码，可以有空格或其他分隔符，例如"044 668 1800"。
- RFC3966：是一种网络电话URI的格式，包含"tel:"的前缀，所有的空格和其他分隔符都被连字符替换，电话号码的扩展部分以";ext="附加，例如"tel:+41-44-668-1800"。

总的来说，这些格式的主要区别在于是否包含国家代码，是否有分隔符，以及是否包含特定的前缀或后缀。

2、每种格式的使用场景
- E.164：这种格式主要用于国际通信，目的是在全球范围内唯一地标识电话号码。这种格式用于电话系统的路由和计费，以及一些网络协议，如SIP。
- INTERNATIONAL：这种格式主要用于需要跨国家和地区显示或录入电话号码的场合，比如国际旅行者需要拨打或记录电话号码，或者在国际环境中交流电话号码。
- NATIONAL：这种格式主要用于国内通信，比如在同一国家或地区内拨打或记录电话号码。这种格式是最常见的，因为大多数电话号码都在国内使用。
- RFC3966：这种格式主要用于网络上的电话号码，比如在网页或电子邮件中链接电话号码，或者在网络协议和应用程序中使用电话号码。这种格式允许在电话号码中包含额外的信息，如分机号码。
# 3. **相关标准**

## Unicode和UTF-8编码
- Unicode官网：https://home.unicode.org/
- UTF-8：https://zh.wikipedia.org/zh-hans/UTF-8


## CLDR（Common Locale Data Repository）

CLDR是一个由 Unicode 组织维护的开源项目，旨在提供全球范围内的语言和文化相关数据，用于软件国际化和本地化。

CLDR 提供了丰富的**数据**，包括各个国家和地区的**语言、时区、日期和时间格式、货币符号、数字格式、排序规则、单位、国家/地区名称等信息**。这些数据是按照 BCP 47 标准（语言标签）进行分类和组织的，使得开发人员可以轻松地获取并使用与特定语言和地区相关的本地化数据。

通过使用 CLDR，开发人员可以实现更准确和一致的本地化体验，确保软件在不同语言和文化环境中正确地显示和处理文本、日期、时间、数字和其他本地化元素。CLDR 数据可以在各种软件平台和应用程序中使用，如操作系统、数据库、网站、移动应用等。

官网：https://cldr.unicode.org/

cldr的github（xml数据格式）：https://github.com/unicode-org/cldr
其中重要数据都放在https://github.com/unicode-org/cldr/tree/main/common/main中，优先可以看root.xml文件

json版本的CLDR数据：https://github.com/unicode-org/cldr-json


## 时区标准

[IANA时区数据库](https://www.iana.org/time-zones)

数据标准和文件解读：<https://mp.weixin.qq.com/s/joZdNPbGPJMPs67yzyrlvg>

[时区变更历史新闻](news/timezone_news.md)
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

### golang.org/x/text
github地址： https://github.com/golang/text/

golang.org/x/text是Go语言的一个子项目，它提供了文本处理的相关功能。它包含了很多有用的子包，可以用于本地化、字符集转换、文本处理与格式化、数字格式化、货币处理等。

下面是一些golang.org/x/text包中常用子包的介绍：
- currency：提供了ISO 4217标准中定义的各种货币的常量和货币相关的函数。
- language：定义了标准的ISO语言和区域代码，并提供了与语言相关的函数。
- message：用于格式化多语言消息的包，支持参数化输出和本地化处理。
- number：用于数字格式化和解析的包，提供了更高级和可定制的数字格式化功能。
- plural：用于处理复数形式的包，可以根据不同的语言和规则返回正确的复数形式。
- runes：提供了一些有用的函数和工具，用于对Unicode字符进行操作和处理。
- transform：提供了字符集转换和编码转换的功能，可以轻松处理不同编码之间的转换。
- unicode：提供了Unicode字符的相关信息和函数，可以用于字符类别、大小写转换、宽字符处理等。
- date：**对日期时间暂时没有支持**

核心逻辑是下载cldr的数据，然后解析生成对应的二进制数据，放到代码中。

使用示例
```go
func TestForCurrency(t *testing.T) {
	//使用locale获取对应的tag标识符
	tag, err := language.Parse("zh-CN")
	if err != nil {
		fmt.Println(err)
		return
	}

	//根据tag获取对应的 用来格式化的指针
	p := message.NewPrinter(tag)

	//进行格式化，里面指明进行货币的格式化，货币码为CNY，数字为1234.56
	s := p.Sprint(currency.Symbol(currency.CNY.Amount(1234.56)))
	fmt.Println(s) // 输出：¥ 1,234.56
	fmt.Println()

	//进行格式化，里面指明进行货币的格式化，货币码为CNY，数字为1234.56，并且使用符号模式而不是用iso代码
	//在特定的上下文中，如格式化或显示信息时，可以使用符号来代替ISO代码。这一请求通常适用于表示货币和其他符号的情况。
	//使用符号而不是ISO代码可能具有以下几个好处：
	//1.更清晰和熟悉：符号通常比ISO代码对用户来说更容易识别和熟悉。例如，使用"$"代表美元或"€"代表欧元可以使货币值对用户更容易理解。
	//2.本地化和文化背景：符号可以更轻松地在不同的文化和语言环境中进行适应和理解。ISO代码可能对非英语用户来说不够直观或普遍认可。
	//3.用户界面设计和美学：符号可以增强用户界面的设计和美学，特别是在有限的空间可用或使用图标和视觉元素时。
	s = p.Sprint(currency.Symbol(currency.USD.Amount(1234.56)))
	fmt.Println(s) // 输出：US$ 1,234.56
	s = p.Sprint(currency.ISO(currency.USD.Amount(1234.56)))
	fmt.Println(s)                                                    // 输出：USD 1,234.56
	s = p.Sprint(currency.NarrowSymbol(currency.USD.Amount(1234.56))) //使用窄符号模式，用于在有限空间或需要更紧凑显示的情况下
	fmt.Println(s)                                                    // 输出：$ 1,234.56

	fmt.Println()
	s = p.Sprint(currency.USD.Amount(1234.56))
	fmt.Println(s) // 输出：USD 1,234.56

	fmt.Println()
	s = p.Sprint(currency.ISO.Kind(currency.Cash)(currency.JPY.Amount(1234.56))) //使用现金模式
	fmt.Println(s)                                                               // 输出：JPY 1,235
	s = p.Sprint(currency.Symbol.Kind(currency.Cash)(currency.JPY.Amount(1234.56)))
	fmt.Println(s) // 输出：JP¥ 1,235
	s = p.Sprint(currency.NarrowSymbol.Kind(currency.Cash)(currency.JPY.Amount(1234.56)))
	fmt.Println(s) // 输出：¥ 1,235
}

```

### go-playground/locales
github地址：https://github.com/go-playground/locales

用于提供本地化（locales）支持。它提供了一组用于处理不同语言和地区的数据，例如日期，时间，数字格式化和翻译等。


核心逻辑见：https://github.com/go-playground/locales/blob/master/cmd/generate_resources.go
依赖golang.org/x/text生成原始数据，然后根据数据自动生成对应的配置和代码。

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

## 6.5 电话
- Java/C++/JavaScript: https://github.com/google/libphonenumber
- C#: https://github.com/twcclegg/libphonenumber-csharp
- Go: https://github.com/nyaruka/phonenumbers
- Objective-c: https://github.com/iziz/libPhoneNumber-iOS
- PHP: https://github.com/giggsey/libphonenumber-for-php
- PostgreSQL in-database types: https://github.com/blm768/pg-libphonenumber
- Python: https://github.com/daviddrysdale/python-phonenumbers
- Ruby: https://github.com/mobi/telephone_number
- Rust: https://github.com/1aim/rust-phonenumber
- Erlang: https://github.com/marinakr/libphonenumber_erlang
- Clojure: https://github.com/randomseed-io/phone-number
   
# 7. i18n典型代码和实现原理

## java

## go

在 Go 中，标准库已经提供了一些本地化相关的包，可以满足一般的本地化需求。以下是一些常用的标准库包：
- time 包：提供时间和日期的处理，包括格式化、解析、时区转换等功能。
- strconv 包：用于数字和字符串之间的转换，例如数字格式化和解析。
- text/template 和 html/template 包：用于模板引擎，支持本地化的文本替换和格式化。

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
