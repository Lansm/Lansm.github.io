---
title: Windows Terminal个人设置
categories:
  - Windows
tags:
  - Windows Terminal
description: 基本对着微软官方文档就行
cover: 'https://img.thaddeus.ink/self_images/anime_imgs/a035.jpg'
abbrlink: 82a5ec21
date: 2020-12-23 16:02:57
---

win10 1903+
安装/自行编译 [Windows Terminal](https://docs.microsoft.com/zh-cn/windows/terminal/)

u1s1，微软官方的文档是真的全

---

### [配置文件设置](https://docs.microsoft.com/zh-cn/windows/terminal/customize-settings/profile-settings)



#### [Cascadia Code PL](https://docs.microsoft.com/zh-cn/windows/terminal/cascadia-code)

所有版本的 `Cascadia Code` 都可以从 [Cascadia Code GitHub 发布页](https://github.com/microsoft/cascadia-code/releases)下载

使用 `PowerShell`，安装 `Posh-Git` 和 `Oh-My-Posh`：

```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```

[Posh-Git](https://github.com/dahlbyk/posh-git) 将 Git 状态信息添加到提示，并为 Git 命令、参数、远程和分支名称添加 tab 自动补全。 [Oh-My-Posh](https://github.com/JanDeDobbeleer/oh-my-posh) 为 PowerShell 提示符提供主题功能。


若要在当前 PowerShell 主机应用程序中创建当前用户的配置文件，请使用以下命令：

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

`notepad $PROFILE`任意编辑器对配置文件进行编辑

```powershell
Import-Module posh-git
Import-Module oh-my-posh
# Start the default settings
Set-Prompt
# Alternatively set the desired theme:
Set-Theme Agnoster
```

如果`PowerShell`提示执行脚本不安全的问题，更新执行策略

> Set-ExecutionPolicy <policy-name>
> Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
> policy-name可能的值
> Unrestricted、RemoteSigned、AllSigned、Restricted、Default、Bypass、Undefined

安装含[Powerline](https://docs.microsoft.com/zh-cn/windows/terminal/tutorials/powerline-setup)版本PL字体后，在`Setting.json`中添加进`powershell`中

```json
"fontFace": "Cascadia Code PL",
```

#### 背景和配色

1. `acrylic` 背景和透明度设置，默认关闭

   ```json
   "useAcrylic": false,
   "acrylicOpacity": 0.15,
   ```

2. 设置背景图像及透明度

   ```json
   "backgroundImage":"...",
   "backgroundImageOpacity":0.4,
   ```

3. 根据自己的背景搭配自带的[配色方案](https://docs.microsoft.com/zh-cn/windows/terminal/customize-settings/color-schemes)多试试搭配，毕竟懒得自定义配色

   ```json
   "colorScheme": "Tango Dark",
   ```

   



