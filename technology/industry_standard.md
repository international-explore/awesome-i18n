# 行业标准
在此列出事实上的行业标准或者规范

## 一、ICU
ICU：international components for unicode，国际化unicode组件。

ICU是**library**


ICU是一个开源的C/C++、java类库，它给程序提供unicode和全球化支持。它是跨平台的，在所有平台都可以给出相同的结果。

[icu文档](https://unicode-org.github.io/icu/)

[icu的github](https://github.com/unicode-org/icu)

[icu的数据](https://github.com/unicode-org/icu-data)

官方的两个库：
- ICU4C：ICU for C/C++
  
https://github.com/unicode-org/icu/tree/main/icu4c

- ICU4J：ICU for Java
  
https://github.com/unicode-org/icu/tree/main/icu4j

## 二、CLDR
CLDR:The Unicode Common Locale Data Repository,Unicode通用语言环境数据存储库

CLDR是**数据集**，ICU以及其他众多I18N libary，数据源都是从CLDR取的。

[官方github](https://github.com/unicode-org/cldr)

举个例子：[中国的通用信息](https://github.com/unicode-org/cldr/blob/main/common/main/zh.xml)

[json形式的CLDR](https://github.com/unicode-org/cldr-json)

## 三、i18n的其他语言库

[icu4x](https://github.com/unicode-org/icu4x)
rust编写的icu组件，旨在解决跨平台问题，使用轻量

[globalize](https://github.com/globalizejs/globalize)
js版本的i18n库，star数近5千

[icu4go](https://github.com/uber-go/icu4go)
uber实现的icu for go，但是已5年没有维护了


## 四、时区数据库
i18n标准本地化内容中，时间是最复杂的一部分，因为包含了时间戳和当地时间的转换、时区、夏令时、历法等一系列问题。而且由于有各地夏令时的不定期调整，导致时间相关的数据或者代码会有变化。

为了解决相关的问题，专门有一个时区数据库，提供时间相关的 **数据**和**代码**

- [iana时区数据库官网](https://www.iana.org/time-zones)
- [时区数据库原始c代码github](https://github.com/eggert/tz)
- [时区数据库变更新闻](https://github.com/eggert/tz/blob/main/NEWS)
- [icu使用的tzdata数据](https://github.com/unicode-org/icu-data/tree/main/tzdata)

