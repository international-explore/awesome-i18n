- [时区变更新闻](#时区变更新闻)
    - [2023c](#2023c)
    - [2023b](#2023b)
    - [2023a](#2023a)
    - [2022g](#2022g)
    - [2022f](#2022f)
    - [2022b](#2022b)

## 时区变更新闻
原文地址：https://github.com/eggert/tz/blob/main/NEWS

参考地址：https://mm.icann.org/pipermail/tz-announce/

#### 2023c
时间：2023-03-28 12:42:14 -0700

主要变更：回滚到2023a版本

原文：
```
Changes to past and future timestamps
Model Lebanon's DST chaos by reverting data to tzdb 2023a.
(Thanks to Rany Hany for the heads-up.)
```


#### 2023b
时间：2023-03-23 19:50:38 -0700

主要变更：今年黎巴嫩的夏令时调时将在4月20日/21日进行，而不是3月25日/26日。

原文：
```
Changes to future timestamps
This year Lebanon springs forward April 20/21 not March 25/26.
(Thanks to Saadallah Itani.)  [This was reverted in 2023c.]
```

#### 2023a
时间：2023-03-22 12:39:33 -0700

主要变更:
- **埃及恢复夏令时**：现在再次从4月至10月使用夏令时。
- 今年摩洛哥的夏令时调时将在4月23日，而不是4月30日。
- 巴勒斯坦推迟了今年夏令时的开始。
- 格陵兰岛的大部分地区从2024年起仍然使用夏令时。
- "America/Yellowknife"的时区链接（关联）到"America/Edmonton"。两个地区的时区设置是一致的，它们共享相同的标准时间和夏令时规则。
- tzselect现在可以使用当前时间来帮助推断时区。
- 代码现在默认使用C99或更新的版本。
- 修复了对C23属性的使用问题。

原文：
```
    Egypt now uses DST again, from April through October.
    This year Morocco springs forward April 23, not April 30.
    Palestine delays the start of DST this year.
    Much of Greenland still uses DST from 2024 on.
    America/Yellowknife now links to America/Edmonton.
    tzselect can now use current time to help infer timezone.
    The code now defaults to C99 or later.
    Fix use of C23 attributes.
```


#### 2022g
时间：2022-11-29 08:58:31 -0800

主要变更:
- **墨西哥奇瓦瓦州的北部边界将改为使用美国的时间制度。**
- 格陵兰岛的大部分地区将在2023年3月后停止调整时钟。
- 修复了加拿大北部部分1996年之前的时间戳问题。
- 不再推荐使用C89，请使用C99或更高版本。
- 增加了对AIX、libintl、MS-Windows、musl和z/OS的可移植性修复。
- 在C代码中，如果可用，尽量使用更多C23的特性。
- 默认支持C23的timegm函数。
- 修复了一些不太可能发生的整数溢出问题。

详细变更：
```
1. 墨西哥Chihuahua从2个时区变为3个时区

2. 其中 America/Ojinaga时区拆分为2个时区, 分别是 America/Ojinaga, America/Ciudad_Juarez

3. 墨西哥 Chihuahua洲的时区状态是:
  - America/Chihuahua, 取消夏令时, 永久保持GMT-6
  - America/Ojinaga, 恢复夏令时, 基准时区是GMT-6, 夏令时规则和US一致
  - America/Ciudad_Juarez, 恢复夏令时,基准时区是GMT-7, 夏令时规则和US一致

当地新闻：http://puentelibre.mx/noticia/oficial_tres_horarios_estado_de_chihuahua_propuesta_noviembre_2022/

Central time (GMT-6):
The entire state of Chihuahua, excluding border municipalities, will remain with the GMT-6 time zone.
That is, the same time zone as the center of the country and without setting the clock back or forward throughout the year.

Juarez time (GMT-7 in winter, GMT-6 in summer):
The municipalities of Ascensión, Juárez, Praxedis G. Guerrero, Guadalupe and Janos will adopt a seasonal time based on the 105° meridian to be tied with their neighbors in New Mexico and El Paso (Texas).
When the reform is approved, they will set their clocks back one hour and will be on GMT-7 in the winter. When daylight saving time arrives, they will move their clocks forward to GMT-6, tied with Central Standard Time.

Ojinaga time (GMT-6 in winter, GMT-5 in summer):
The municipalities of Ojinaga, Manuel Benavides and Coyame will adopt seasonal time based on the 90° meridian to become tied with Presidio, Texas time.
Upon approval of the reform, they will not change their time this winter and will remain on GMT-6, the same as Central Standard Time.
When summer arrives, they will move their clocks forward one hour to GMT-5, the same as the state of Texas.
```

#### 2022f
时间：2022-10-28 18:04:57 -0700

主要变更：
- **墨西哥除了靠近美国边境的地区外，将不再观察夏令时。**奇瓦瓦州将于2022年10月30日转为全年使用-06时区。
- 斐济将不再观察夏令时。

原文：
```
    Mexico will no longer observe DST except near the US border.
    Chihuahua moves to year-round -06 on 2022-10-30.
    Fiji no longer observes DST.
    Move links to 'backward'.
    In vanguard form, GMT is now a Zone and Etc/GMT a link.
    zic now supports links to links, and vanguard form uses this.
    Simplify four Ontario zones.
    Fix a Y2438 bug when reading TZif data.
    Enable 64-bit time_t on 32-bit glibc platforms.
    Omit large-file support when no longer needed.
    In C code, use some C23 features if available.
    Remove no-longer-needed workaround for Qt bug 53071.
```
    

#### 2022b
时间： 2022-08-10 15:38:32 -0700

主要变更：
- **智利在2022年9月推迟一周开始夏令时。**
- 伊朗在2022年后不再观察夏令时。
- 将"Europe/Kiev"重命名为"Europe/Kyiv"。
- 新增了zic命令的-R选项。
- 最新版本中，使用了%z格式代替以前的格式。
- 完成了将自1970年以来重复的时区移动到"backzone"文件夹的工作。
- 新增了PACKRATLIST编译选项。
- 新增了tailored_tarballs目标，取代了rearguard_tarballs目标。

原文：
```
    Chile's DST is delayed by a week in September 2022.
    Iran no longer observes DST after 2022.
    Rename Europe/Kiev to Europe/Kyiv.
    New zic -R option
    Vanguard form now uses %z.
    Finish moving duplicate-since-1970 zones to 'backzone'.
    New build option PACKRATLIST
    New tailored_tarballs target, replacing rearguard_tarballs
```
