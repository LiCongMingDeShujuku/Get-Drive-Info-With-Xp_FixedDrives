![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 使用Xp_FixedDrives获取驱动器信息
#### Get Drive Info With Xp_FixedDrives
**发布-日期: 2015年06月16日 (评论)**

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这是一些从xp_fixed驱动器获取结果，并将其放在一个表中的快速逻辑。然后对该表的快速查询显示还有多少GB可用空间量。这个逻辑快速而简单。


## English
Here’s some quick logic which takes the results from xp_fixed drives, and puts it in a table. Then a quick query against that tables shows the amount of free space in GB. It’s quick, and simple. Those are the best ones.

---
## Logic
```SQL
use master;
set nocount on
if exists (select object_id('tempdb..#get_drive_info'))
drop table #get_drive_info
 
create table #get_drive_info
(
  drive char(1) not null
, mbfree int not null
)
insert into #get_drive_info
exec xp_fixeddrives
 
select
  'drive' = drive
, 'gb free' = mbfree / 1024
from
#get_drive_info
order by
drive asc


```

![#](images/get-drive-info-wiith-sql-xp-fixeddrives-a.png?raw=true "#")


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

