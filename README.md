# 国际化出海技术交流

旨在收集和分享出海i18n相关的一些领域知识和技术工具。
内容上包括重要标准、开发工具、经典文章、相关书籍、白皮书、出海创业企业、英文词汇和重要新闻等。
范围整体分为两大部分
- i18n - internationalization：主要包括货币、时间、度量衡等本地化因素的适配技术
- l10n - localization：主要包括翻译、多语言等本地化文案适配技术


# 内容目录
* [i18n-internationalization](#i18n-internationalization) 
    * [LOCALE - LOCALE、CLDR等通用部分](#通用部分)
    * [CURRENCY - 货币相关问题](#货币部分-currency)
    * [TIME - 时间相关问题](#时间部分-time)
      * [TIMEZONE - 时区相关问题]()
      * [HOLIDAY - 节假日相关问题]()
    * [MEASURE - 度量衡相关问题]()
    * [NUMBER - 数字相关问题]()
    * [PHONE - 电话相关问题]()
    * [MESSAGE - 信息相关问题，涵盖标题、标签、错误信息等]()
    * [COLLATE - 比较习惯相关问题]()
    * [NAME - 姓名相关问题]()
    * [ADDRESS - 地址相关问题]()
    * [PAPER - 纸张相关问题]()
* [l10n-localization](#l10n-localization)
  
  
## i18n-internationalization 
#### 通用标准
#### 权威组织
#### 开发工具
#### 相关站点
#### 经典文章

### 货币部分-currency
#### 货币标准
#### 货币权威组织
#### 货币开发工具
#### 货币相关站点
#### 货币经典文章

### 时间部分-time
#### 时间标准
#### 时间权威组织
#### 时间开发工具
#### 时间相关站点
#### 时间经典文章
 
### 度量衡部分-time
#### 时间标准
#### 时间权威组织
#### 时间开发工具
#### 时间相关站点
#### 时间经典文章


## l10n-localization 


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
* [2020中国互联网企业出海白皮书](http://www.d-long.com/eWebEditor/uploadfile/2020062023345840113526.pdf)




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