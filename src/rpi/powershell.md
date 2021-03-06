# 使用Powershell

```admonish info
官方文档：[powershell](https://docs.microsoft.com/en-us/powershell/scripting/install/install-raspbian?view=powershell-7.2)
```

## 一、安装Powershell

32位和64位系统的唯一的区别就是32位需要安装依赖，而64位不需要。

### 32位操作系统

安装依赖：

```bash
sudo apt-get update
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y
```

下载解压文件，在我写此文档时powershell最新版本是7.2.5，你可以前往官网下载更新的[版本](https://github.com/PowerShell/PowerShell/releases)：

```bash
wget https://github.com/PowerShell/PowerShell/releases/download/v7.2.5/powershell-7.2.5-linux-arm32.tar.gz
mkdir ~/Powershell
tar -xvf ./powershell-7.2.5-linux-arm32.tar.gz -C ~/Powershell
```

### 64位操作系统

直接下载解压文件：

```bash
wget https://github.com/PowerShell/PowerShell/releases/download/v7.2.5/powershell-7.2.5-linux-arm64.tar.gz
mkdir ~/Powershell
tar -xvf ./powershell-7.2.5-linux-arm64.tar.gz -C ~/Powershell
```

## 二、配置Powershell：

```bash
sudo ~/Powershell/pwsh -command 'New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force'
```

## 三、使用Powershell：

```bash
pwsh
```