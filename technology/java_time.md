- [一、JDK8之前，旧的日期时间API](#一jdk8之前旧的日期时间api)
  - [1、日期时间 java.util.Date](#1日期时间-javautildate)
    - [（1）介绍](#1介绍)
    - [（2）成员变量](#2成员变量)
    - [（3）常用函数](#3常用函数)
  - [2、日历 java.util.Calendar](#2日历-javautilcalendar)
    - [（1）介绍](#1介绍-1)
    - [（2）成员变量](#2成员变量-1)
    - [（3）使用示例](#3使用示例)
  - [3、格式化 java.text.SimpleDateFormat](#3格式化-javatextsimpledateformat)
    - [（1）介绍](#1介绍-2)
    - [（2）使用示例](#2使用示例)
    - [（3）注意事项](#3注意事项)
  - [4、时区 java.util.TimeZone](#4时区-javautiltimezone)
    - [（1）简介](#1简介)
    - [（2）常用函数](#2常用函数)
    - [（3）存在的问题](#3存在的问题)
  - [5、老的日期时间处理类存在一些问题和缺点](#5老的日期时间处理类存在一些问题和缺点)
- [二、JDK8之后，新的日期和时间API](#二jdk8之后新的日期和时间api)
  - [1、日期时间](#1日期时间)
    - [（1）LocalDate](#1localdate)
    - [（2）LocalTime](#2localtime)
    - [（3）LocalDateTime](#3localdatetime)
    - [（4）ZonedDateTime](#4zoneddatetime)
  - [2、时间戳Instant](#2时间戳instant)
  - [3、格式化DateTimeFormatter](#3格式化datetimeformatter)
    - [（1）简介](#1简介-1)
    - [（2）常用函数](#2常用函数-1)
    - [（3）使用示例](#3使用示例-1)
  - [4、时区ZoneId](#4时区zoneid)
    - [（1）简介](#1简介-2)
    - [（2）常用函数](#2常用函数-2)
    - [（3）实现原理](#3实现原理)


脑图：https://mm.tt/app/map/2960894425?t=2fn031Wv0C
![image](https://github.com/international-explore/awesome-i18n/assets/104364356/c04bf1cc-88b3-46d1-969e-88951ddd4281)


## 一、JDK8之前，旧的日期时间API
### 1、日期时间 java.util.Date
#### （1）介绍
这个类表示一个特定的瞬间，精确到毫秒。你可以用它来获取时间戳，也可以将时间戳转换为人类可读的日期和时间格式。但是，Date类并不包含时区信息，它默认使用系统的默认时区。

#### （2）成员变量
```
//从1970年1月1日00:00:00 GMT（格林尼治标准时间）以来的毫秒数
private transient long fastTime;
```

#### （3）常用函数
```
//构造函数
//根据毫秒时间戳，创建一个时间对象
public Date(long date) {
    fastTime = date;
}
//创建表示now的时间对象
public Date() {
    this(System.currentTimeMillis());
}

//根据Date获取毫秒时间戳
public long getTime() {
    //xxx
}

//toString方法不建议使用，因为返回的时间字符串，是依赖系统默认的时区

```

### 2、日历 java.util.Calendar
#### （1）介绍
这个类是一个抽象类，它提供了一些方法用于操作日期和时间字段，例如年、月、日、小时、分钟和秒。
Calendar类比Date类更强大，因为它可以处理更复杂的日期和时间操作，例如日期的加减、日期字段的获取和设置等。此外，Calendar类还支持时区。
#### （2）成员变量
[参考icu4j日历类解读](https://github.com/international-explore/awesome-i18n/blob/main/technology/problem_domain/standard/datetime.md#21-icu4j%E6%97%A5%E5%8E%86%E7%B1%BB%E8%A7%A3%E8%AF%BB)

#### （3）使用示例
```
import java.util.Calendar;

public class Main {
    public static void main(String[] args) {
        Calendar calendar = Calendar.getInstance(); // 获取当前日期和时间
        int year = calendar.get(Calendar.YEAR); // 获取年份
        int month = calendar.get(Calendar.MONTH); // 获取月份，注意月份是从0开始的，所以实际月份需要加1
        int day = calendar.get(Calendar.DAY_OF_MONTH); // 获取日期
        int hour = calendar.get(Calendar.HOUR_OF_DAY); // 获取小时
        int minute = calendar.get(Calendar.MINUTE); // 获取分钟
        int second = calendar.get(Calendar.SECOND); // 获取秒
        System.out.println(year + "-" + (month + 1) + "-" + day + " " + hour + ":" + minute + ":" + second);
    }
}
```

### 3、格式化 java.text.SimpleDateFormat
#### （1）介绍
这个类是一个可以将日期和时间格式化为字符串，或者将字符串解析为日期和时间的工具。
它可以处理各种复杂的日期和时间格式。例如，你可以定义一个日期格式为"yyyy-MM-dd HH:mm:ss"，然后使用SimpleDateFormat将一个Date对象格式化为这种格式的字符串，或者将这种格式的字符串解析为一个Date对象。
#### （2）使用示例
```
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.TimeZone;

public class Main {
    public static void main(String[] args) {
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        formatter.setTimeZone(TimeZone.getTimeZone("Asia/Shanghai")); // 设置时区为上海

        // 格式化日期
        Date date = new Date();
        String dateString = formatter.format(date);
        System.out.println(dateString);
        
        // 解析日期字符串
        Date parsedDate = formatter.parse("2022-01-01 12:00:00");
        System.out.println(parsedDate);
    }
}
```

#### （3）注意事项
SimpleDateFormat不是线程安全的。如果你在多线程环境中使用SimpleDateFormat，你需要为每个线程创建一个新的实例，或者使用同步来保证线程


### 4、时区 java.util.TimeZone
#### （1）简介
抽象类，用来处理时区问题
TimeZone类本身是一个抽象类，它的具体实现依赖于子类。在Java SE平台上，它的一种常见实现是sun.util.calendar.ZoneInfo，这个类使用tzdata（一个包含全球所有时区信息的数据库）来获取时区信息。
#### （2）常用函数
```
getDefault()：获取默认的时区。
getID()：获取时区的ID。时区的ID是一个字符串，它唯一标识了世界上的一个特定时区。这个字符串通常由区域和城市组成，以“/”分隔，例如"America/New_York"，"Asia/Shanghai"。
这些ID主要遵循tz database的命名规则，tz database（也称为IANA时区数据库）是一个包含了世界各地从1970年以来的夏令时（daylight saving time，DST）转变信息的数据库。
TimeZone getTimeZone(String ID) 根据时区名称，获取时区对象
getOffset(long date)：获取指定日期的UTC偏移量。
getRawOffset()：获取原始的UTC偏移量。
setDefault(TimeZone zone)：设置默认的时区。
setRawOffset(int offsetMillis)：设置原始的UTC偏移量。
```
#### （3）存在的问题
TimeZone类是Java早期版本中的日期和时间API的一部分，虽然它可以用来处理时区，但存在一些问题：
- 非线程安全：
TimeZone实例是可变的，这就意味着它们在多线程环境下可能存在问题。如果多个线程同时修改一个TimeZone实例，可能会导致不可预料的结果。
- API设计不直观：
TimeZone的API设计让人感到困惑。比如，要获取一个特定的时区，你需要使用TimeZone.getTimeZone(String ID)方法，而不是一个构造函数。此外，这个方法在无法识别ID时并不会抛出异常，而是返回GMT时区，这可能会导致错误。
- 缺少功能：
TimeZone类无法处理日期和时间的许多复杂情况，比如夏令时、历法变更等。
基于这些原因，Java 8在java.time包中引入了新的日期和时间API，包括ZoneId类。ZoneId类设计得更为直观，功能也更为强大，而且它是不可变的，因此是线程安全的。所以，如果你正在使用Java 8或更高版本，推荐使用ZoneId和新的日期和时间API，而不是TimeZone和旧的日期和时间API。

### 5、老的日期时间处理类存在一些问题和缺点
- 可变性：Date是一个可变类，这意味着它的值可以被改变。这在多线程环境中可能会导致问题，因为你需要额外的同步来确保数据的一致性。
- 引用透明性：由于Date是可变的，所以它违反了函数式编程原则中的引用透明性。例如，如果你有一个返回Date的方法，调用者可能会改变返回的Date对象的值，这可能导致意想不到的结果。
- 时区处理：Date本身并不包含时区信息，但是其toString方法却依赖于系统默认的时区，这可能导致混淆和错误。
- 一致性：Calendar的月份是从0开始的，而天数是从1开始的，这种不一致使得Calendar很难使用且容易出错。
- 效率：Date和Calendar的部分方法（尤其是Calendar）效率低下，这在处理大量的日期和时间时可能成为问题。


举例来说，如果你想要设置一个特定的日期，比如2022年1月1日，你可能会这么做：
```
Calendar calendar = Calendar.getInstance();
calendar.set(2022, 0, 1);  // 0代表一月
```
这段代码看起来很奇怪，因为我们通常会认为1代表一月，而不是0。这就是Calendar设计的一个问题。而在新的日期和时间API中，你可以这么做：
```
LocalDate date = LocalDate.of(2022, 1, 1);  // 1代表一月
```
这段代码更直观，更易于理解。

## 二、JDK8之后，新的日期和时间API
### 1、日期时间
#### （1）LocalDate
表示一个日期（年/月/日），没有时间的部分，也没有时区（使用系统默认时区）。例如，可以使用它来存储生日或者纪念日。
```
LocalDate date = LocalDate.now(); // 获取当前日期
LocalDate birthday = LocalDate.of(1990, Month.JANUARY, 1); // 创建一个指定日期
```
#### （2）LocalTime
表示一天中的某个时间（小时/分钟/秒），没有日期部分，也没有时区（使用系统默认时区）。
```
LocalTime time = LocalTime.now(); // 获取当前时间
LocalTime midnight = LocalTime.MIDNIGHT; // 获取午夜时间
```
#### （3）LocalDateTime
表示一个日期和时间，没有时区（使用系统默认时区）。这是一个常用的类，适用于大部分日期和时间的处理。
```
LocalDateTime dateTime = LocalDateTime.now(); // 获取当前日期和时间
LocalDateTime customDateTime = LocalDateTime.of(1990, Month.JANUARY, 1, 10, 10, 30); // 创建一个指定的日期和时间
```
#### （4）ZonedDateTime
表示一个日期和时间，包含了时区。用于处理时区相关的日期和时间。
```
ZonedDateTime zonedDateTime = ZonedDateTime.now(); // 获取当前的日期、时间和时区
ZonedDateTime customZonedDateTime = ZonedDateTime.of(customDateTime, ZoneId.of("Asia/Shanghai")); // 创建一个指定的日期、时间和时区
```

### 2、时间戳Instant
Instant表示一个时间戳，通常用于记录事件的发生时间。

```
Instant now = Instant.now(); // 获取当前的时间戳
Instant fromEpochMilli = Instant.ofEpochMilli(System.currentTimeMillis()); // 从毫秒数创建一个时间戳
```

### 3、格式化DateTimeFormatter
#### （1）简介
用于日期时间的格式化和解析
#### （2）常用函数
ofPattern(String pattern)：根据给定的模式字符串创建一个DateTimeFormatter。
format(TemporalAccessor temporal)：使用此DateTimeFormatter来格式化一个日期和时间。
parse(String text)：使用此DateTimeFormatter来解析一个日期和时间字符串。
#### （3）使用示例

```
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
LocalDateTime dateTime = LocalDateTime.now();
String dateTimeString = formatter.format(dateTime); // 格式化日期和时间
System.out.println(dateTimeString);
LocalDateTime parsedDateTime = LocalDateTime.parse(dateTimeString, formatter); // 解析日期和时间字符串
System.out.println(parsedDateTime);
```

### 4、时区ZoneId
#### （1）简介
Java 8引入的新的日期时间API的一部分，表示一个时区标识符。它用于在日期和时间中包含时区信息。

#### （2）常用函数
```
of(String zoneId)：根据给定的时区ID创建一个ZoneId实例。
getAvailableZoneIds()：返回所有可用的时区ID。
getId()：返回此ZoneId的ID。
systemDefault()：返回系统默认的ZoneId。
```

#### （3）实现原理
ZoneId类是一个抽象类，它的具体实现依赖于它的两个子类ZoneOffset和ZoneRegion。
ZoneOffset表示一个固定的时区偏移量，而ZoneRegion则表示一个由tz database定义的时区。
ZoneId.of(String zoneId)方法会尝试先根据给定的ID创建一个ZoneOffset，如果失败，再尝试创建一个ZoneRegion。
