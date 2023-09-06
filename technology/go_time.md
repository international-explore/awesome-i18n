- [Constants](#constants)
  - [时间格式化、反解析用到的layout常量](#时间格式化反解析用到的layout常量)
  - [常见的时间段 common duration](#常见的时间段-common-duration)
- [type Time](#type-time)
  - [time结构](#time结构)
  - [time操作](#time操作)
    - [获取time对象](#获取time对象)
    - [时间加减比较](#时间加减比较)
    - [获取日历信息](#获取日历信息)
    - [时间格式化](#时间格式化)
    - [时间转时间戳](#时间转时间戳)
    - [其他](#其他)
- [type Location](#type-location)
  - [Location结构](#location结构)
  - [Location的常量](#location的常量)
  - [Location的函数](#location的函数)
    - [1、 FixedZone 固定时区](#1-fixedzone-固定时区)
    - [2、LoadLocation 根据时区名获取时区](#2loadlocation-根据时区名获取时区)
    - [3、LoadLocationFromTZData 从二进制字节流中加载时区](#3loadlocationfromtzdata-从二进制字节流中加载时区)


## Constants

### 时间格式化、反解析用到的layout常量

Time.Format and time.Parse
```
const (
	Layout      = "01/02 03:04:05PM '06 -0700" // The reference time, in numerical order.
	ANSIC       = "Mon Jan _2 15:04:05 2006"
	UnixDate    = "Mon Jan _2 15:04:05 MST 2006"
	RubyDate    = "Mon Jan 02 15:04:05 -0700 2006"
	RFC822      = "02 Jan 06 15:04 MST"
	RFC822Z     = "02 Jan 06 15:04 -0700" // RFC822 with numeric zone
	RFC850      = "Monday, 02-Jan-06 15:04:05 MST"
	RFC1123     = "Mon, 02 Jan 2006 15:04:05 MST"
	RFC1123Z    = "Mon, 02 Jan 2006 15:04:05 -0700" // RFC1123 with numeric zone
	RFC3339     = "2006-01-02T15:04:05Z07:00"
	RFC3339Nano = "2006-01-02T15:04:05.999999999Z07:00"
	Kitchen     = "3:04PM"
	// Handy time stamps.
	Stamp      = "Jan _2 15:04:05"
	StampMilli = "Jan _2 15:04:05.000"
	StampMicro = "Jan _2 15:04:05.000000"
	StampNano  = "Jan _2 15:04:05.000000000"
	DateTime   = "2006-01-02 15:04:05"
	DateOnly   = "2006-01-02"
	TimeOnly   = "15:04:05"
)
```

如果要自定义一些格式，可以参考：

```
Year: "2006" "06"
Month: "Jan" "January" "01" "1"
Day of the week: "Mon" "Monday"
Day of the month: "2" "_2" "02"
Day of the year: "__2" "002"
Hour: "15" "3" "03" (PM or AM)
Minute: "4" "04"
Second: "5" "05"
AM/PM mark: "PM"

格式化offset：
"-0700"     ±hhmm
"-07:00"    ±hh:mm
"-07"       ±hh
"-070000"   ±hhmmss
"-07:00:00" ±hh:mm:ss
```

### 常见的时间段 common duration

```
const (
	Nanosecond  Duration = 1
	Microsecond          = 1000 * Nanosecond
	Millisecond          = 1000 * Microsecond
	Second               = 1000 * Millisecond
	Minute               = 60 * Second
	Hour                 = 60 * Minute
)
```


## type Time

### time结构

```
type Time struct {
    //wall：这是一个表示时间的uint64字段，它包含纳秒和秒的信息。
    //wall的低30位存储纳秒信息，接下来的34位存储秒信息。
    //如果需要存储超过这个范围的时间，那么 wall 字段的最高位会被设置为1，并且使用下面的 ext 字段来存储。
	wall uint64
	//当wall字段的最高位被设置为1时，这个字段会被用来存储时间信息。这主要用于存储超过wall字段能表示的时间范围。
	ext  int64

    //时间的时区信息
	loc *Location
}
```

这些字段一般不直接使用，而是通过time.Time类型提供的方法进行操作

### time操作

#### 获取time对象

1、根据时间字符串/年月日时分秒 获取时间对象

```
func Date(year int, month Month, day, hour, min, sec, nsec int, loc *Location) Time

func Parse(layout, value string) (Time, error)
func ParseInLocation(layout, value string, loc *Location) (Time, error)

```

2、 根据时间戳获取时间对象

```
func Unix(sec int64, nsec int64) Time
func UnixMicro(usec int64) Time
func UnixMilli(msec int64) Time
```

3、 其他

```
func Now() Time
```

#### 时间加减比较

1、 时间加减

```

func (t Time) Add(d Duration) Time
func (t Time) AddDate(years int, months int, days int) Time

func (t Time) Sub(u Time) Duration


```

2、时间比较

```
func (t Time) After(u Time) bool
func (t Time) Before(u Time) bool
func (t Time) Compare(u Time) int
func (t Time) Equal(u Time) bool
```

#### 获取日历信息
1、获取年月日


```
func (t Time) Date() (year int, month Month, day int)

func (t Time) Year() int
func (t Time) Month() Month
func (t Time) Day() int

//获取是一年的第几天
func (t Time) YearDay() int

//获取是周几
func (Time) Weekday

```

2、获取时分秒

```
func (t Time) Clock() (hour, min, sec int)

func (t Time) Hour() int
func (t Time) Minute() int
func (t Time) Second() int
func (t Time) Second() int
func (t Time) Nanosecond() int


```

#### 时间格式化

```
func (t Time) Format(layout string) string
```

#### 时间转时间戳

```
func (t Time) Unix() int64
func (t Time) UnixMicro() int64
func (t Time) UnixMilli() int64
func (t Time) UnixNano() int64
```

#### 其他

```
//获取时区信息
func (t Time) Zone() (name string, offset int)

//看是否在夏令时内
func (t Time) IsDST() bool


```

## type Location

### Location结构
表示一个时区

```
type Location struct {
    //时区的名称，如"UTC"、"America/New_York"。
    name string
    //每个元素表示该时区的一个规则
    zone []zone
    //每个元素表示一个时区转换的时间点，即在什么时间切换到什么规则
    tx   []zoneTrans
    //表示扩展规则，用于计算超出已知转换时间点的时间
    extend string
    
    //cacheStart、cacheEnd：表示缓存的时间范围，用于提高查找效率
    cacheStart int64
    cacheEnd   int64
    //表示缓存的时区规则，也是为了提高查找效率。
    cacheZone  *zone
}

// A zone represents a single time zone such as CET.
type zone struct {
	name   string // abbreviated name, "CET"
	offset int    // seconds east of UTC
	isDST  bool   // is this zone Daylight Savings Time?
}

// A zoneTrans represents a single time zone transition.
type zoneTrans struct {
	when         int64 // transition time, in seconds since 1970 GMT
	index        uint8 // the index of the zone that goes into effect at that time
	isstd, isutc bool  // ignored - no idea what these mean
}
```

### Location的常量

1、UTC：代表协调世界时，也就是我们常说的格林尼治标准时间（Greenwich Mean Time，GMT）。它不受夏令时的影响。
```
// UTC represents Universal Coordinated Time (UTC).
var UTC *Location = &utcLoc
var utcLoc = Location{name: "UTC"}
```

2、Local：代表当前系统的本地时区。Local实际上是一个Location的实例，它会在程序运行的时候初始化为运行该程序的系统的本地时区。因此，它会根据你的系统设置以及是否启用了夏令时来变化。

优先级：
- 优先使用$TZ的环境变量。
    - 如果"TZ"的值以斜杠"/"开头，说明它是一个绝对路径，函数会尝试从这个路径加载时区信息。如果成功，就将这个时区设为本地时区并返回。
    - 如果"TZ"的值不是以斜杠开头并且不等于"UTC"，那么函数会尝试从"/usr/share/zoneinfo/"查找对应的时区文件来加载时区信息。如果成功，就将这个时区设为本地时区并返回。
- 没有$TZ的环境变量，那么会尝试从系统默认位置"/etc"加载"localtime"文件来获取时区信息。
```
var Local *Location = &localLoc
var localLoc Location
var localOnce sync.Once

func initLocal() {
	// consult $TZ to find the time zone to use.
	// no $TZ means use the system default /etc/localtime.
	// $TZ="" means use UTC.
	// $TZ="foo" or $TZ=":foo" if foo is an absolute path, then the file pointed
	// by foo will be used to initialize timezone; otherwise, file
	// /usr/share/zoneinfo/foo will be used.

	tz, ok := syscall.Getenv("TZ")
	switch {
	case !ok:
		z, err := loadLocation("localtime", []string{"/etc"})
		if err == nil {
			localLoc = *z
			localLoc.name = "Local"
			return
		}
	case tz != "":
		if tz[0] == ':' {
			tz = tz[1:]
		}
		if tz != "" && tz[0] == '/' {
			if z, err := loadLocation(tz, []string{""}); err == nil {
				localLoc = *z
				if tz == "/etc/localtime" {
					localLoc.name = "Local"
				} else {
					localLoc.name = tz
				}
				return
			}
		} else if tz != "" && tz != "UTC" {
			if z, err := loadLocation(tz, zoneSources); err == nil {
				localLoc = *z
				return
			}
		}
	}

	// Fall back to UTC.
	localLoc.name = "UTC"
}
```


### Location的函数
#### 1、 FixedZone 固定时区

```
func FixedZone(name string, offset int) *Location
```
固定使用 某个时区和偏移量

example：

```
package main

import (
	"fmt"
	"time"
)

func main() {
	loc := time.FixedZone("UTC-8", -8*60*60)
	t := time.Date(2009, time.November, 10, 23, 0, 0, 0, loc)
	fmt.Println("The time is:", t.Format(time.RFC822))
}
```


#### 2、LoadLocation 根据时区名获取时区


```
func LoadLocation(name string) (*Location, error)
```
这个函数接收一个字符串作为参数，代表一个地理时区的名称，然后返回对应的Location对象。

- 如果函数参数是空字符串""或者"UTC"，LoadLocation会返回UTC时区。
- 如果函数参数是"Local"，LoadLocation会返回当前系统的本地时区。
- 其他的参数，例如"America/New_York"，会被视为IANA（互联网号码分配机构）时区数据库中的一个地理时区名称。

LoadLocation函数在查找时区数据时，会按照以下顺序依次尝试：

- 首先，函数会检查**环境变量ZONEINFO**。如果它存在且有效，函数会从这个环境变量指定的目录或未压缩的zip文件中加载时区数据。
- 如果ZONEINFO环境变量不存在或无效，且当前系统是Unix系统，函数会尝试从 **系统的标准安装位置/usr/share/zoneinfo/** 加载时区数据。
- 如果前两步都失败，函数会尝试从 **$GOROOT/lib/time/zoneinfo.zip** 加载时区数据。
- 最后，如果前面的步骤都失败， 且**time/tzdata包** 被导入，函数会从这个包中加载时区数据。

上述的顺序就是LoadLocation函数查找时区数据的优先级。



#### 3、LoadLocationFromTZData 从二进制字节流中加载时区

```
func LoadLocationFromTZData(name string, data []byte) (*Location, error)
```
用于从提供的IANA Time Zone数据库的TZ数据中加载指定时区。

具体的执行原理如下：
1、函数首先会将提供的TZ数据解析为一个zoneinfo结构，这个结构包含了一系列的时区转换规则。数据应该是标准的IANA时区文件的格式，例如，Unix系统上/etc/localtime文件的内容。
2、然后，函数会在这个zoneinfo结构中查找指定的时区名称。如果找到了，就使用这些时区转换规则创建一个新的Location对象。
3、最后，函数返回这个新创建的Location对象。

这个函数非常有用，它允许你从自定义的数据源加载时区信息，而不仅仅是从系统默认的位置或者环境变量定义的位置。例如，你可以将TZ数据嵌入到你的应用程序中，然后使用LoadLocationFromTZData函数从这些嵌入的数据中加载时区信息。这对于那些需要在没有文件系统或环境变量支持的环境中运行的应用程序非常有用。
