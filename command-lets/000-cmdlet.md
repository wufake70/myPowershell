## Cmdlet 是 PowerShell 中的一个轻量级命令，它是由一个动词和一个名词组成的，用于执行特定的操作。`不区分大小写`

- `Get-Command`：获取所有可用的 cmdlet 和函数。
```PowerShell
# 获取所有 cmdlet 和函数
Get-Command

# 获取所有 cmdlet
Get-Command -CommandType Cmdlet

# 获取所有与进程相关的 cmdlet
Get-Command -Noun Process
```
- `Get-Help`：获取 cmdlet 的帮助信息。
```PowerShell
# 获取 Get-Process cmdlet 的帮助信息
Get-Help Get-Process

# 获取 Get-Process cmdlet 的详细帮助信息
Get-Help Get-Process -Detailed

# 获取 Get-Process cmdlet 的示例
Get-Help Get-Process -Examples
```
- `Get-Process`：获取当前运行的进程信息。
```PowerShell
# 获取当前运行的所有进程信息
Get-Process

# 获取名称为 notepad 的进程信息
Get-Process -Name notepad

# 获取占用内存最多的 5 个进程信息
Get-Process | Sort-Object -Property WS -Descending | Select-Object -First 5
```
`Get-Process` 常用参数：
    - `-Name`：指定要获取的进程名称。
    - `-Id`：指定要获取的进程 ID。
    - `-IncludeUserName`：包括进程的用户名。

```PowerShell
# 获取名称为 notepad 的进程信息
Get-Process -Name notepad

# 获取 ID 为 1234 的进程信息
Get-Process -Id 1234

# 获取所有进程信息，并包括用户名
Get-Process -IncludeUserName
```
- `Stop-Process`：停止一个进程。
```PowerShell
# 停止名称为 notepad 的进程
Stop-Process -Name notepad

# 停止 ID 为 1234 的进程
Stop-Process -Id 1234

# 强制停止名称为 notepad 的进程
Stop-Process -Name notepad -Force
```
`Stop-Process` 常用参数：
    - `-Name`：指定要停止的进程名称。
    - `-Id`：指定要停止的进程 ID。
    - `-Force`：强制停止进程，即使它有关联的作业。

- `Get-Service`：获取计算机上的服务信息。
```PowerShell
# 获取计算机上的所有服务信息
Get-Service

# 获取名称为 wuauserv 的服务信息
Get-Service -Name wuauserv

# 获取所有已启动的服务信息
Get-Service | Where-Object {$_.Status -eq "Running"}
```
`Get-Service` 常用参数：
    - `-Name`：指定要获取的服务名称。
    - `-DisplayName`：指定要获取的服务显示名称。
    - `-DependentServices`：包括依赖于指定服务的服务。

```PowerShell
# 获取名称为 wuauserv 的服务信息
Get-Service -Name wuauserv

# 获取显示名称为 Windows Update 的服务信息
Get-Service -DisplayName "Windows Update"

# 获取名称为 wuauserv 的服务信息，以及依赖于它的服务信息
Get-Service -Name wuauserv -DependentServices
```