![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Quickly Take An SQL Database Offline And Online With SQL
**Post Date: February 26, 2016**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Here's some quick SQL logic that will take the database offline, then online again. It's helpful for maintenance reference.</p>     


## SQL-Logic
```SQL
use master;
set nocount on
 
-- check if database is online.  if so proceed to take offline.  if not; do nothing.
if exists(select state_desc from sys.databases where name = 'MyDatabase' and state_desc = 'online')
    begin
        alter database [MyDatabase] set offline with rollback immediate;
    end
    else
        print 'The database is already offline. No changes will be made';
 
-- confirm the database is OFFLINE.
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';
 
-- set database online
alter database [MyDatabase] set online;
 
-- confirm the database is ONLINE.
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';

```



## SQL-Logic
```SQL

use master;
set nocount on
 
-- check if database is online.  if so proceed to take offline.  if not; do nothing.
if exists(select state_desc from sys.databases where name = 'MyDatabase' and state_desc = 'online')
    begin
        alter database [MyDatabase] set offline with rollback immediate;
    end
    else
        print 'The database is already offline. No changes will be made';
 
-- confirm the database is OFFLINE.
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';
 
-- set database online
alter database [MyDatabase] set online;
 
-- confirm the database is ONLINE.
select
    'server_name'       = upper(@@servername)
,   'database_name'     = upper(name)
,   'is_offline'        = state_desc
from
    sys.databases
where
    name = 'MyDatabase';
```


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

   
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

