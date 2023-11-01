# 时间日期

## 1、时间日期相关的配置

#### [时间日期字段](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/dateFields.json)

比如 年月日 时分秒 季度 周 纪元 时区

#### [公历的时间日期展示](https://github.com/unicode-org/cldr-json/blob/main/cldr-json/cldr-dates-modern/main/zh/ca-gregorian.json)

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

## 2、相关代码解读

### 2.1 **ICU4J日历类解读**
com.ibm.icu.util.Calendar

```
1、日历类的定义
Calendar是一个抽象基类，用于在Date对象和一组整数字段（如YEAR、MONTH、DAY、HOUR等）之间进行转换。（Date对象是毫秒精度表示特定的时间瞬间）

ICU4J包含几个实现不同国际日历系统的子类。比如
buddhist 佛教历法
chinese 农历
japanese 日本历，也叫和历
Gregorian 格里高利历，也就是公历，或者说阳历


2、日历类中的数据流
在日历中表示当前时间有2种方式：
一种是时间戳，一种是当地的年月日时分秒的字段值（当然这种方式需要知道时区timezone或者utcOffset）。
    //   local fields (YEAR, MONTH, DATE, HOUR, MINUTE, etc.)
    //           |
    //           | Using Calendar-specific algorithm
    //           V
    //   local standard millis
    //           |
    //           | Using TimeZone or user-set ZONE_OFFSET / DST_OFFSET
    //           V
    //   UTC millis (in time data member)
private transient int fields[]; //当地的年月日时分秒的字段值数组
private long time; //时间戳

3、日历类的构造函数
就是设置时区和locale信息（没传的话使用默认值）,设置时间戳为当前时间
默认使用公历

public static Calendar getInstance(TimeZone zone, ULocale locale) {
    return getInstanceInternal(zone, locale);
}
private static Calendar getInstanceInternal(TimeZone tz, ULocale locale) {
    if (locale == null) {
        locale = ULocale.getDefault(Category.FORMAT);
    }
    if (tz == null) {
        tz = TimeZone.getDefault();
    }

    Calendar cal = createInstance(locale);
    cal.setTimeZone(tz);
    cal.setTimeInMillis(System.currentTimeMillis());
    return cal;
}   


4、核心字段
public final static int ERA = 0;
public final static int YEAR = 1;
public final static int MONTH = 2;
public final static int WEEK_OF_YEAR = 3;
public final static int WEEK_OF_MONTH = 4;
public final static int DATE = 5;//和DAY_OF_MONTH一样
public final static int DAY_OF_MONTH = 5;
public final static int DAY_OF_YEAR = 6;
public final static int DAY_OF_WEEK = 7;
public final static int DAY_OF_WEEK_IN_MONTH = 8;

public final static int AM_PM = 9;
public final static int HOUR = 10;
public final static int HOUR_OF_DAY = 11;
public final static int MINUTE = 12;
public final static int SECOND = 13;
public final static int MILLISECOND = 14;


5、核心方法
set(), add(), and roll()这三个方法用来更改日历字段值
get(int field)用来获取日历值

5.1、核心方法1：set
set(int field, int value) 将字段f设置为value
此外，它还设置一个内部成员变量，以指示字段f已更改。
尽管字段f会立即更改，但在下一次调用get()、getTime()或getTimeInMillis()之前，不会重新计算日历的毫秒数。
因此，多次调用set()不会触发多次不必要的计算。
由于使用set()更改字段，其他字段也可能会更改，具体取决于字段、字段值和日历系统。

示例：比如日历最初设置为1999年8月31日。调用set(Calendar.MONTH，Calendar.SEPTEMBER)将日历设置为1999年9月31日。
这是一个临时的内部表示，如果随后调用getTime()，则解析为1999年10月1日。
但是，在调用getTime()之前调用set(Calendar.DAY_OF_MONTH，30)会将日历设置为1999年9月30日，因为set()本身之后不会进行重新计算。


5.2、核心方法2：add
add（f，delta）将delta添加到字段f。这相当于调用set(f,get(f)+delta)并进行两次调整：

add规则1:调用后的字段f值减去调用前的字段f的值是delta，对字段f中发生的任何溢出会进行取模运算。
当字段值超出其范围时，会发生溢出，因此，下一个较大的字段会递增或递减，字段值会调整回其范围。

add规则2:由于字段f改变后，较小的字段其最小值或最大值可能发生变化，因此它可能会调整，会将其值调整为尽可能接近其期望值。比如加1个月，可能会导致DAY_OF_MONTH变化

此外，与set()不同，add()强制立即重新计算日历的毫秒和所有字段。

示例：考虑一个最初设置为1999年8月31日的公历GregorianLendar。调用add（Calendar.MONTH，13）将日历设置为2000年9月30日。
按照add规则1：将MONTH字段设置为9月，因为将8月加13个月，即为下一年的9月。由于在公历中DAY_OF_MONTH在9月份不能为31，
因此根据add规则2：将DAY_OF-MONTH设置为30，这是最接近的值。

> go原生的addDate函数规则跟ICU不一致。它与规则2不一样，它会进行溢出。比如10月31号加一个月，先变成11.31（不存在），然后变成了12.1。
> 参考：https://pkg.go.dev/time#Time.AddDate

5.3、核心方法3：roll
roll(f, delta) adds delta to field f without changing larger fields. 
Roll规则：Larger fields are unchanged after the call. A larger field represents a larger unit of time. DAY_OF_MONTH is a larger field than HOUR.
更大的字段不会被更改，比如+13小时，相当于是+1小时，不会改变天

6、使用模型
考虑一个用户界面组件，该组件包含月份、日期和年份的递增和递减按钮。
如果界面显示的是1999年1月31日，用户按下月份递增按钮，那么应该显示什么？
如果底层实现使用set()，它可能会读取1999年3月3日。
更好的结果是1999年2月28日。
此外，如果用户再次按下月份递增按钮，则应显示为1999年3月31日，而不是1999年3日28日。
通过保存原始日期并使用add()或roll()（取决于较大的字段是否会受到影响），用户界面可以按照大多数用户的直觉进行操作。

注意：您应该始终使用roll和add，而不是尝试直接对Calendar的字段执行算术运算。日历子类很可能具有具有非线性行为的字段，例如在非闰年期间缺少月份或天数。子类的add和roll方法将考虑到这一点，而简单的算术操作可能会产生无效的结果。

```


### 2.2 时间类解读

DateFormat的parse方法的底层原理涉及以下步骤：
```
获取输入的日期字符串和DateFormat对象中定义的日期格式模式。
1、将日期字符串按照日期格式模式进行解析，将字符串中的各个字段（年、月、日、时、分、秒等）提取出来。
2、根据提取出来的字段值，构建一个Calendar对象，并将字段值设置到对应的Calendar字段中。
3、如果DateFormat对象定义了时区信息，将时区信息应用到Calendar对象中，以便正确地解析和处理时区相关的时间信息。
4、最后，根据Calendar对象中的字段值，计算出对应的时间戳（以毫秒为单位）。
```


计算时区偏移和夏令时偏移的过程中存在两个潜在的歧义。
```
以下讨论假设夏令时切换时间为凌晨2点（壁钟时间）。

1、正偏移变化，例如切换到夏令时。 在这种情况下，凌晨2点到2点59分之间的时间实际上不存在。对于这种情况，skippedWallTime选项指定了行为。例如，凌晨2点30分被解释为：
- WALLTIME_LAST（默认）：凌晨3点30分（夏令时）（将凌晨2点30分解释为离凌晨1点59分（标准时间）后31分钟）
- WALLTIME_FIRST：凌晨1点30分（标准时间）（将凌晨2点30分解释为离凌晨3点（夏令时）前30分钟）
- WALLTIME_NEXT_VALID：凌晨3点（夏令时）（壁钟上2点30分后的下一个有效时间）

2、负偏移变化，例如切换回标准时间。 在这种情况下，凌晨1点到1点59分之间的时间可以是标准时间或夏令时。两者都是有效的表示（表示从凌晨1点59分（夏令时）跳到凌晨1点（标准时间））。 对于这种情况，repeatedWallTime选项指定了行为。例如，凌晨1点30分被解释为：
- WALLTIME_LAST（默认）：凌晨1点30分（标准时间）- 后一次出现
- WALLTIME_FIRST：凌晨1点30分（夏令时）- 前一次出现
除了上述情况之外，当日历为严格模式时（非默认），落在被跳过的时间范围内的壁钟时间将被视为错误的情况。

```

- 日期格式化
- 时间格式化
- 时间间隔格式化

## 3、相关工具和网站
时区相关的工具网站：
https://nodatime.org/TimeZones