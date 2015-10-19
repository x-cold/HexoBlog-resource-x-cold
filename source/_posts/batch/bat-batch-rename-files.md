title: 批处理实现批量文件重命名
date: 2015-1-18
tags: [cmd,bat]
categories: bat
---
模拟一下这样的情景，假设我有一个文件夹用于保存各种下载的文本文件（自然也可以是其他格式的文件），当这个文件夹文件数量达到一定规模时，我需要将这些文件的名字序列化，那么下面这个批处理文件便横空出世了。

![title](/img/title/2.jpg)

###实现代码：

```Bash
@echo off
setlocal EnableDelayedExpansion
::下面这个语句要请改成你要处理的文件夹路径如“pushd %~dp0^\text”改成"pushd "c:\text""
pushd %~dp0^\text
::计数
set /a index = 0
for /f %%i in ('dir /b /a-d *.*') do (
set /a index += 1
ren %%~nxi !index!%%~xi
)
echo 共扫描到!index!个文件。
pause>nul
```

ps：请将以上代码用任意文本编辑器保存为后缀名为"bat"或者"cmd"的文件。
<!--more-->