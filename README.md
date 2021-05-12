# 自用scoop仓库

## Scoop安装

### 环境需求

- Windows 7 SP1+ / Windows Server 2008+
- PowerShell 5（或更高版本，包括PowerShell Core）和.NET Framework 4.5（或更高版本）
- 必须为您的用户启用PowerShell脚本执行的策略，例如 Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser， 选择`Y`

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 配置自定义安装目录`SCOOP`环境变量

```
$env:SCOOP='D:\Scoop\Applications'
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
# run the installer
```

### 配置自定义全局安装目录 `SCOOP_GLOBAL`环境变量

```powershell
$env:SCOOP_GLOBAL='D:\Scoop\GlobalScoopApps'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
# run the installer
```

### 安装

> 在PowerShell中运行以下命令，如果没有配置`SCOOP`环境变量，其会安装在默认位置(`C:\Users\<user>\scoop`)

```powershell
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')

# or shorter
iwr -useb get.scoop.sh | iex
```

### 添加软件库

```powershell
scoop bucket add win-bucket https://github.com/tanzl/scoop-bucket
```
### 软件下载

输入如下命令即可安装需要的软件：

```powershell
scoop install win-bucket/<软件名>
```
如果是安装到global目录，命令如下：

```powershell
sudo scoop install 7zip git openssh --global
sudo scoop install win-bucket/<软件名> -g
```
> -g --global 需要管理员权限  
>
> 安装scoop install sudo

## 软件列表

| 软件                                                         | 简介                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [AdGuardHome](https://adguard.com/adguard-home.html)         | AdGuard Home 是一款全网广告拦截与反跟踪软件                  |
| [navicat-premium](http://www.navicat.com.cn/products/navicat-premium) | Navicat Premium 是一套数据库开发工具，让你从单一应用程序中同时连接 MySQL、MariaDB、MongoDB、SQL Server、Oracle、PostgreSQL 和 SQLite 数据库 |
| [Netpiao](http://www.bhdata.com/program.asp?action=view&id=39) | 心蓝12306订票助手是由心蓝数据(BHData.Com)开发，基于铁路客户服务中心官网(12306.Cn)的一个网上购买火车票实用客户端程序 |
| [NoSQLBooster-for-MongoDB](https://nosqlbooster.com/)        | NoSQLBooster for MongoDB是针对MongoDB v2.6-4.4的跨平台GUI工具 |
| [dev-sidecar](https://github.com/docmirror/dev-sidecar)      | 开发者边车，github打不开，github加速，git clone加速，git release下载加速，stackoverflow加速 |
| [oraclejdk8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html) | Oracle JDK 8 Java开发工具包                                  |

