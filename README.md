# 国际化技术交流

旨在收集和分享国际化相关的一些信息。
内容上包括重要标准、开发工具、经典文章、相关书籍、白皮书、出海创业企业、英文词汇和重要新闻等。
范围上会涵盖i18n - internationalization、t9n - translation、l10n - localization、g11n - globalization、m17n - multilingualization等


# 内容目录
   * [🔭 基础概念](#基础概念) - 国际化的一些概念和常识。
   * [⚖️ 核心问题域](#核心问题域)-国际化通用的问题域
   * [📙 英语词汇](./i18nGlossary.md) - 国际化相关的一些重要英文词汇 
   * [🏛️ 业界标准](#业界标准) - 国际化方面的一些重要标准、规范。
   * [🏢 出海企业](#出海企业) - 服务企业出海的一些企业。
   * [🔨 开发工具](#开发工具) - 国际化重要的组件、工具、应用。
   * [⭐ 出海白皮书](#出海白皮书) - 一些出海的企业，白皮书等权威信息
   * [📘 书籍](#书籍) - 国际化相关的一些重要书籍
   * [💬 微信公众号](#微信公众号) - 国际化相关的微信公众号
   * [📎 网站外链](#网站外链) - 国际化相关重要新闻、资源外链
   * [🗞️ 相关新闻](./news.md) - 出海相关的一些重要新闻

## 基础概念
### 核心概念解释
* I18N - internationalization（国际化），i和n之间有18个字母所以叫做i18n。
  * 国际化是指在设计软体时，将软体与特定语言及地区脱钩的过程。当软体被移植到不同的语言及地区时，软体本身不用做内部工程上的改变或修正。
* L10N - localization（本地化） 
  * 本地化则是指当移植软体时，加上与特定区域设置有关的文字、图片和语音等资源的过程。 
* G11N - globalization(全球化)
  * 包括i18n、l10n以及其他所有使产品在全球更受欢迎的产品生产、推广、销售和售后活动。
* T9N - translation（翻译）
  * 将某种基准文字按语言和文化习惯翻译成符合当地习惯的文字的过程，属于l10n本地化创作中最重要的一类创作。l10n的其他本地化创作包括图片创作、语音创作和UI配色等。

### 相互的关系
![相关的关系](/image/relationship.png)
* I18N和L10N的关系
  * 国际化和在地化之间的区别虽然微妙，但却很重要。国际化意味着产品有适用于任何地方的 **“能力”** ；本地化则是为了更适合于 **“特定”** 地方的使用，而另外增添的特色。
  * 用一项产品来说，**国际化只需做一次**，但**本地化则要针对不同的区域各做一次**。这两者之间是**相辅相成**的，并且两者合起来才能让一个系统适用于各地。
*  G11N = I18N+L10N+其他
*  T9N属于L10N，但也需要I18N的能力
  
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



## 业界标准
 * i18n
   * [行业标准](/technology/industry_standard.md)
 * l10n
   * [成熟度标准](https://blog.andovar.com/localization-maturity-model-how-does-your-company-measure-up)
   * 

## 出海创业企业
* 国内出海企业
* * 字节
* * 华为
* * 阿里

* 国外出海企业
* * Google
* * Netflix
   
## 开发工具
 * i18n
   * [ICU](https://github.com/unicode-org/icu) - 全球化支持权威的组件库，目前提供c语言和java版本
     * [icu4x](https://github.com/unicode-org/icu4x) - CU4X提供了支持广泛软件国际化的组件。它深刻借鉴了ICU4C、ICU4J和ECMA-402的经验，并依赖于CLDR项目的数据。
   * [CLDR](https://cldr.unicode.org/index) - ICU使用的核心数据集，也是i18n的核心数据集
     * 加工工具

## 出海白皮书
* [2020中国互联网企业出海白皮书](http://www.d-long.com/eWebEditor/uploadfile/2020062023345840113526.pdf)




## 书籍

* 视频课程：
* * 谷歌同学的一个教程： https://www.udacity.com/course/localization-essentials--ud610 

## 微信公众号
* 36氪出海 - 提供出海企业相关的新闻

## 网站外链
 * [W3C international](https://www.w3.org/blog/international/) - W3C international网站，涵盖w3c在international方向的标准、手册、工具等。
 * [ICU 官网](https://icu.unicode.org/) - 为应用提供Unicode和全球化支持的一套成熟、广泛使用的组件库
 * 本地化服务供应商
 * * [RWS](https://www.rws.com/cn/localization/)
 * * [translations.com](https://zh_cn.translations.com/)
 * * [lionbridge](https://www.lionbridge.com/zh-hans/)
 * * [welocalize](https://www.welocalize.com/zh-hans/)
 * 翻译相关平台
 * * [字节国际化翻译平台](https://www.volcengine.com/products/starling)