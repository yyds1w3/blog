---
title: Lazynvim operation
date: 2025-12-12T20:33:00.000+08:00
draft: false
tags:
  - Linux
---
```
<Space> + e,打开/关闭左侧文件树 (Explorer),Explorer
<Space> + f + f,查找文件 (Find Files),Find Files
<Space> + f + r,打开最近的文件 (Recent),Find Recent
<Space> + s + g,全局搜索代码内容 (Grep),Search Grep
<Space> + q + q,退出 Neovim,Quit Quit
<Ctrl> + s,保存文件 (Save),(和 Windows 一样)
```
```
<Space> + -,水平分屏 (上下切开),减号就是横线
<Space> |,垂直分屏 (左右切开)
<Ctrl> + h/j/k/l,在不同窗口间跳转,左/下/上/右
<Space> + w + d,关闭当前分屏窗口,Window Delete
<Shift> + h,切换到左边的标签页 (Buffer),Previous Buffer
<Shift> + l,切换到右边的标签页 (Buffer),Next Buffer
<Space> + b + d,关闭当前标签页,Buffer Delete
```
```
g + d,跳转到定义 (Go Definition),想看这个函数是怎么写的
g + r,查找引用 (References),想看这个变量哪里用到了
K (大写K),查看文档/悬浮提示,忘了 std::vector 怎么用？按一下
<Space> + c + r,重命名变量 (Rename),把 cnt 全局改成 count，智能的！
<Space> + c + a,代码修复 (Code Action),代码报红了？按这个自动修
<Space> + c + f,格式化代码 (Format),代码写乱了？一键美化
```
```
<Ctrl> + /,打开/关闭悬浮终端 (Terminal)
<Space> + l,打开 Lazy 插件管理器 (升级插件用)
<Space> + c + m,打开 Mason 管理器 (装 LSP 用)
<Space> + u + w,自动换行开关 (Wrap)
```
