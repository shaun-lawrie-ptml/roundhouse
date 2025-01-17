> **Warning**
> This uses keywords.txt extracted from the 8.0.16 version of MySql.Data because this resource no longer exists in the newer versions but it was required for ILMerge. If there resource doesn't exist in the new version it's assumed that there is no reference to it so this doesn't cause any damage, it just includes it in one of the output dlls.
> This was built with the following command:
> ```cmd
> dotnet publish product/roundhouse.console -p:NoPackageAnalysis=true
>   -p:TargetFramework=netcoreapp3.1 -p:Version="1.3.1.1" -p:Configuration=Build
>   -p:Platform="Any CPU"
> ```

Project RoundhousE - Database Change Management done right
=======
<a href=https://ci.appveyor.com/project/chucknorris/roundhouse>
<img src="https://ci.appveyor.com/api/projects/status/github/chucknorris/roundhouse?branch=master&svg=true" alt="CI build status"/>
</a>
<p></p>

<img src="https://github.com/ferventcoder/roundhouse/raw/master/docs/logo/RoundhousE_Logo.jpg" height="200" alt="RoundhousE - Professional Database Management" />  

  
# LICENSE
[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0) - see docs\legal (just LEGAL in the zip folder)  
  
# Documentation
[WIKI](https://github.com/chucknorris/roundhouse/wiki)  

# INFO
## Overview
RoundhousE is an automated database deployment (change management) system that allows you to use your current idioms and gain much more. Currently works with Oracle<sup>[1](footnote1)</sup>, SQL Server (2000/2005/2008/Express), Access<sup>[1](footnote1)</sup>, MySQL, SQLite and PostgreSQL. There are future plans for other databases.  
  
It seeks to solve both maintenance concerns and ease of deployment. We follow some of the same idioms as other database management systems (SQL scripts), but we are different in that we think about future maintenance concerns. We want to always apply certain scripts (anything stateless like functions, views, stored procedures, and permissions), so we don't have to throw everything into our change scripts. This seeks to solves future source control concerns. How sweet is it when you can version the database according to your current source control version?  

<a name="footnote1">1</a>)  Only on full-framework on Windows, not on Cross-platform .NET Core global tool version.

  
## Getting started with RoundhousE
### Downloads
 You can download RoundhousE from [https://github.com/chucknorris/roundhouse/releases](https://github.com/chucknorris/roundhouse/releases)

 You can also obtain a copy from the build server at [https://ci.appveyor.com/project/chucknorris/roundhouse/build/artifacts](https://ci.appveyor.com/project/chucknorris/roundhouse/build/artifacts).  
  
### Gems (_Not updated for 0.9.0 and above, sorry_) 

![](https://img.shields.io/gem/dt/roundhouse.svg)

If you have Ruby 1.8.6+ (and Gems 1.3.7+) installed, you can get the current release of RoundhousE to your machine quickly!  
  
1. Type `gem install roundhouse`  
2. Then from anywhere you can type `rh [options]`  
  
### NuGet  

![](https://img.shields.io/nuget/dt/roundhouse.svg)

With NuGet you can get the current release of RoundhousE to your application quickly!  
  
1. In Visual Studio Package Manager Console type `install-package roundhouse`  
2. There is also `roundhouse.lib`, `roundhouse.msbuild`, and `roundhouse.refreshdatabase`  
  
### Chocolatey  
![](https://img.shields.io/chocolatey/dt/roundhouse.svg)

Chocolatey is like apt-get, but for Windows! This is an alternative method to get the current release of RoundhousE to your machine quickly!  

  
1. Type `cinst roundhouse`  
2. Then from anywhere you can type `rh [options]`  

### Dotnet core global tool (Windows, Linux, macOS, etc)
![](https://img.shields.io/nuget/dt/dotnet-roundhouse.svg)

1. Type `dotnet tool install -g dotnet-roundhouse` 
1. Then from anywhere you can type `rh [options]`  

You can read more about what happens in the background e.g. here:
https://natemcmaster.com/blog/2018/05/12/dotnet-global-tools/, but in short, it installs
the binaries to your `~/.dotnet/tools` folder. 

You will need dotnet core installed on your box for this to work. You can get it here: [https://dot.net](https://dot.net).


### Docker: Dotnet core global tool

You can easily integrate RoundhousE in your existing docker infrastructure. Use docker compose, or just pull it down directly and run it. You should probably build upon the image, and add your own customisations, as appropriate. The docker image has the dotnet core global tool distribution of RoundhousE in a Debian 10 Linux base image.

1. Type `docker pull dotnetroundhouse/roundhouse`
1. Type `docker run dotnetroundhouse/roundhouse`

 
### Source
This is the best way to get to the bleeding edge of what we are doing.  

1. Clone the source down to your machine.  
  `git clone git://github.com/chucknorris/roundhouse.git`  
1. Type `cd roundhouse`  
1. Type `git config core.autocrlf false` to leave line endings as they are.  
1. Type `git status`. You should not see any files to change.
1. Run `build.ps1`. NOTE: You must have git on the path (open a regular command line and type git).
 
### Developing

The build system has been using UppercuT, but this will probably not be maintained going forward. We will try to 
standardize on more "main stream" build tools like MSBuild and Powershell. There are still some remains of UppercuT in the 
source code (esp. in the `build` folder), but this is probably going to be removed in the near future.

To work with the command line, you will need the following in your path:
 - MS Build
 - GitVersion (easiest to run choco install gitversion.portable. You are running chocolatey aren't you?)
 - NuGet Command Line (easiest to run choco install nuget.commandline. You are running chocolatey aren't you?)

### IMPORTANT
NOTE: If you are looking at the source - please run build.ps1 before opening the solution. It extracts the `keywords.txt` files needed for ILMerge-ing MySql dlls, and build will complain without them.
  
  
# REQUIREMENTS
* .NET Framework 4.6.1 (for the full framework version), _or_
* .NET Core 2.1+ (for the dotnet core distribution)
* SA access to the sql server (for creation or deletion)  
* change access to the database (for everything else)  

# DONATE
Donations Accepted - If you enjoy using this product or it has saved you time and money in some way, please consider making a donation.  
It helps keep to the product updated, pays for site hosting, etc. https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2RA38UKSK6EZU

# RELEASE NOTES

_Please see [releases](../../releases) for the full release logs_

## [1.0.2](../../releases/tag/1.0.2)
**Bugfix release**

Fixed bug in packaging of dotnet core tool, and another bug with log folder paths and colon in connection string.

## [1.0.1](../../releases/tag/1.0.1)
**Merge-error release fix**


## [1.0.0](../../releases/tag/1.0.0)
**Cross-platform dotnet core and dotnet standard ++**

Big technological release. RoundhousE now runs on .NET Core in addition to the good, old .NET framework.

## [0.9.1](../../releases/tag/0.9.1)
 **Two Bugfixes**

After the 0.9.0 release, users identifed two significant bugs. These are fixed in a quick point release.

 (See release for the full release notes)

## [0.9.0](../../releases/tag/0.9.0)
 **Focus on modernising tooling**

 RoundhousE has had some catching-up to do tooling-wise. Dependency on .NET 3.5, old, NAnt-based build chain, etc. We are starting this work. It is not done yet, but on its way. Feature-wise not a lot to brag about, but RH.exe should now be able to run on Windows Server 2016 out-of-the-box, because it is no longer dependent on .NET 3.5.

 (See release for the full release notes)

## [0.8.8](../../releases/tag/0.8.8)
 **Catching up with Pull Requests**
 (See release for the release notes)

## [0.8.7](../../releases/tag/0.8.7)
 **OMG!! It's a RoundhousE release!!**

 *It's been a long time coming. I didn't want to get bogged down into writing 
 the perfect release notes, so I am summarizing the last four years of commit 
 history. I hope that no one that contributed feels slighted by my failure to 
 specifically acknowledge your contribution. I intend to do better in the 
 future.*

### Enhancements
 + Added option to run scripts outside of transaction scope
 + Handle Azure connection strings
 + Properly split files that start with a splitter
 + Respect Transaction flag
 + Improved Logging
 + Added switch --warnandignoreononetimescriptchanges

### Bug Fixes
 + Only retry on SQL Connection errors
 + Correctly handle postgres connection disposed error

## 0.8.6

### Enhancements

  + Use git as official repository. (mpareja)
  + Upgrade UpperCut to version 1.4.2. (ferventcoder)
  + Database Restore: use restore specific timeout value. (icetoast - [pull #90](https://github.com/chucknorris/roundhouse/pull/90))
  + Ignore EOL format changes when detecting script changes. (lahma - [pull #104](https://github.com/chucknorris/roundhouse/pull/104))
  + Include SQL Print statements in debug log. (ferventcoder - [issue #68](https://github.com/chucknorris/roundhouse/issues/68))
  + Include statement being run in log when an error occurs. (ferventcoder - [issue #66](https://github.com/chucknorris/roundhouse/issues/66))
  + Added 'runBeforeUp' anytime directory. (cdrexle - [pull #51](https://github.com/chucknorris/roundhouse/pull/51))
  + Support resolving version from a text file. (mpareja - [pull #50](https://github.com/chucknorris/roundhouse/pull/50), [pull #55](https://github.com/chucknorris/roundhouse/pull/55))
  + Add option to turn off copying scripts into 'itemsRan' directory. (lahma - [pull #47](https://github.com/chucknorris/roundhouse/pull/47))
  + WarnOnOneTimeScriptChange will now cause changed one-time scripts to be re-run. (BiggerNoise - [pull #35](https://github.com/chucknorris/roundhouse/pull/35))
  + Upgrade NHibernate to version 3.3.2. (drusellers)
  + Upgrade FubuCore, HtmlTags and StructureMap. (drusellers)

### Bug Fixes

  + SQL Batch Parser: handle training comments, single quotes. (mpareja - [pull #108](https://github.com/chucknorris/roundhouse/pull/108))
  + SQL Batch Parser: fix hang. (AndersMalmgren - [pull #100](https://github.com/chucknorris/roundhouse/pull/100))
  + Token Replacer: preserve case for unmatched tokens. (mpareja - [pull #65](https://github.com/chucknorris/roundhouse/pull/65))
  + SQL scripts no longer truncated to 4000 characters. (charoco, ferventcoder - [pull #61](https://github.com/chucknorris/roundhouse/pull/61))
  + Oracle: Fix handling of null values. (rdingwall - [pull #59](https://github.com/chucknorris/roundhouse/pull/59), [issue #58](https://github.com/chucknorris/roundhouse/issues/58))
  + Script File Versioner: fix exception. (Michael Kobaly - [issue #68 on Google Code](https://code.google.com/p/roundhouse/issues/detail?id=68))
  + Only change DB recovery mode if explicitly told to. (ferventcoder - [issue #69 on Google Code](https://code.google.com/p/roundhouse/issues/detail?id=69))
  + Fixed the debug command line switch. (ferventcoder - [issue #40](https://github.com/chucknorris/roundhouse/issues/40))
  + Ensure version 1.2.10 of log4net is used when installing NuGet packages. (ferventcoder - [issue #41](https://github.com/chucknorris/roundhouse/issues/41))
  + Fix: Improve logging of RH exceptions. (torkelo - [pull #60](https://github.com/chucknorris/roundhouse/pull/60))

### Breaking Changes

  + RoundhousE will change the DB recover mode if the `recoverymode` mode option is explicitly set to `simple` or `full`. In the past, RoundhousE would default to `full` but would only ever set the recovery mode while creating/restoring the database. If you depended on RoundhousE to create/restore the database for you and you don't want the database server default to be used, you should specify the recovery mode option.

## 0.8.5  
* FIX: KeyNotFoundException in NHibernateSessionFactoryBuilder. See [issue 59] (http://code.google.com/p/roundhouse/issues/detail?id=59) for details. (r361)  
* **SQLite Support!**. See details https://github.com/chucknorris/roundhouse/issues/21 (r360)  
* **PostgreSQL Support!** Thanks SiimV! See details https://github.com/chucknorris/roundhouse/issues/30 (r359)  
* **New Configuration Switch!** SearchAllSubdirectoriesInsteadOfTraverse - All migrations subfolders are traversed by default and run in order of each folder's scripts. This option runs all items in subfolders at same time. Thanks SiimV! See details https://github.com/chucknorris/roundhouse/issues/31 (r359)  
* FIX: Transactions not working with restore. See details https://github.com/chucknorris/roundhouse/issues/26 (r357)  
* FIX: Fixed a nasty bug with SQL Server where it tries to hold a connection (interferes with drop/create mode) and gives a transport error. See details https://github.com/chucknorris/roundhouse/issues/12 (r357)  
* **New Version Resolver!** - Script Number Versioning. See details https://github.com/chucknorris/roundhouse/pull/25 (r356)  
* FIX: Custom create script should split batch statements. See details https://github.com/chucknorris/roundhouse/issues/22 (r353)  
* **New Migrations Folder!** RunAfterCreateDatabaseFolder - Runs only one time and only after a database has been created. This works with a limited set of database types at the moment. Please test if you are planning on using. See details https://github.com/chucknorris/roundhouse/issues/20 (r351)  
* Almost everything is now ilmerged internalized. See details https://github.com/chucknorris/roundhouse/issues/8 and https://github.com/chucknorris/roundhouse/issues/15 (r350)  
* FIX: Cannot drop databases with snapshots. See details https://github.com/chucknorris/roundhouse/pull/13 (r349)  
* Create database custom script can handle file paths. See details https://github.com/chucknorris/roundhouse/pull/17 (r348)  
* FIX: SQL Server 2000 needs to create all of its tables. See details https://github.com/chucknorris/roundhouse/issues/18 (r346)  
* RH assemblies are now signed. See details https://github.com/chucknorris/roundhouse/issues/14 (r342)  
* FIX: Removed the temporary log location. See details https://github.com/chucknorris/roundhouse/issues/7 (r340)  
* **New Configuration Switch!** DisableTokenReplacement - Token replacement should be configurable. See [issue 56](http://code.google.com/p/roundhouse/issues/detail?id=56) for details. (r339)  
* FIX: Token replacer should only replace for items it finds. See [issue 56](http://code.google.com/p/roundhouse/issues/detail?id=56) for details. (r339)  
* **Possible Breaking Change!** File encoding will always try to read files as UTF-8, but fall back to ANSI. You can't go wrong if you encode in ANSI. See [issue 39](http://code.google.com/p/roundhouse/issues/detail?id=39) for details. (r337)  
* Restores are a bit smarter about moving files to a default location when one has not been specified. See details https://github.com/chucknorris/roundhouse/issues/9 or [issue 13](http://code.google.com/p/roundhouse/issues/detail?id=13) (r336)  
* FIX: Do not run token replacement on empty text. See details https://github.com/chucknorris/roundhouse/issues/10 (r330)  
* Custom Scripts also run token replacement (r321)  
* **New Configuration Switches!** Two new switches available - CommandTimeout and CommandTimeoutAdmin! (r329)  
* FIX: Migrate doesn't try to configure log4net now (causes issues w/libraries that do) (r326)  
* **New Migrations Folder!** Indexes folder now available (r327)  
* **New Migrations Folder!** AlterDatabase folder now available. See details https://github.com/chucknorris/roundhouse/issues/6 (r324)  
* FIX: Included sample for Oracle doesn't work. See [issue 55] (http://code.google.com/p/roundhouse/issues/detail?id=55) for details. (r322)  
* Custom Restore Options should use token replacement (r321)  
* **MySQL Support!**. Thanks Diyan. See details https://github.com/chucknorris/roundhouse/pull/3 (r320)  
  
## 0.8.0.300  
* RH now does token replacement in the sql files using '{{PropertyName}}'. See [issue 33] (http://code.google.com/p/roundhouse/issues/detail?id=33) for details. (r299)  
* Always run files that have '.EVERYTIME.' in the name. See [issue 51] (http://code.google.com/p/roundhouse/issues/detail?id=51) for details. (r299)  
* RoundhousE ships a DLL for embedding. See [issue 44] (http://code.google.com/p/roundhouse/issues/detail?id=44) for details. It has a semi-fluent interface - see (https://gist.github.com/977990) for details. (r299)  
* FIX: Environment Specific Files run other environments when other environments are part of the name (i.e. BOBTEST is run with TEST). See [issue 50] (http://code.google.com/p/roundhouse/issues/detail?id=50) for details. (r299)  
* A folder that runs after the other anytime scripts folders have run has been added. See https://github.com/chucknorris/roundhouse/pull/1 for details. (r297)  
* Fixing the script modified twice running each time bug. See https://github.com/chucknorris/roundhouse/pull/5 for details. (r296)  
* Sample is now a project in the release folder. (r287)  
* MSBuild is available again. (r288)  
  
## 0.7.0.281  
* Fixed a few issues with using the connection string. You should now be able to only supply the connection string and not server/database as well.  
  
## 0.7.0.276  
* Fixed a collation issue with RoundhousE id columns in its tracking tables. See [issue 46] (http://code.google.com/p/roundhouse/issues/detail?id=46) for details. (r274)  
* RestoreFromPath can take a relative path. (r269)  
* RH can now upgrade it's internals without user interaction. See [issue 40] (http://code.google.com/p/roundhouse/issues/detail?id=40) for details. (r268)  
* MSBuild / NAnt tasks are deprecated and no longer hooked up. Please use the console and call it from your tasks. (r268)  
* RH has differencing support with NHibernate Schema Generation/Updates (r267 - branch, r268)  
* FluentNhibernate and NHibernate are now being used for the internals (r267 - branch, r268)  
* SMO is deprecated and removed (r203 - branch, r268)  
* Gems and build upgrades, oh my! (r259)  
* SQL2000 to 2005 is now a smooth transition. (r221)  
* Fix: SQL2000 - ScriptsRun now correctly references Version for the foreign key. (r220)  
* Fix: Connection should be initialized before asking the database if it supports ddl transactions. (r215)  
* Fix: Uppercase User names when running with Oracle. (r200)  
* RH has differencing support with RedGate. See sample project for details. (r197)  
* Fix: Scrips run errors now updates version number and path w/out a dependency on scripts run. Allows for it to finish during transactional runs and still capture errors. (r196)  
* Fix: Capture errortastic changes to DDL/DML (up) files in the script run errors table. (r191)  
* Added admin connection string to do administrative tasks. (r190)  
  
## Prior Release Notes  
**Prior releases notes are on the [wiki](https://github.com/chucknorris/roundhouse/wiki/releasenotes).**  

  
# CREDITS
UppercuT - Automated Builds (automated build in 10 minutes or less?!) [http://projectuppercut.org](http://projectuppercut.org)
