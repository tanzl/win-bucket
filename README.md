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
scoop bucket add win-bucket https://github.com/tanzl/win-bucket
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

