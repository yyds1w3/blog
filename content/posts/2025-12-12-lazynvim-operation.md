---
title: Lazynvim operation
date: 2025-12-12T20:33:00.000+08:00
draft: false
tags:
  - Linux
---
```
<Space> + s + k 内置搜索快捷键
```
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
Ctrl + o从库函数退回来， Ctrl + i退到库函数
<Space> + s + s, 当前文件符号表搜索
<Space> + s + S, 当前项目符号表搜索
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

# ⚡ Neovim 硬核操作手册 (ACM/CP 极速版)

> "手中无剑，和有剑不用，是两码事。" —— Neovim 进阶笔记

## 1. 核心编辑魔法 (Editing Magic)

### 🔮 上帝之手与宏
| 按键/命令 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`.` (点)** | 重复上一次修改 | 给多行末尾加分号：`A; <Esc> j . j .` |
| **`qa`** ... **`q`** | 录制宏到寄存器 a | 批量处理复杂格式 |
| **`@a`** | 执行宏 a | `100@a` 执行 100 次 |
| **`@@`** | 重复上一次宏 | 懒人连发 |

### 🧱 影分身 (Visual Block)
*进入方式：`<C-v>` (WSL 下可能是 `<C-q>`)
| 操作 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`<C-v>` + `j/k` + `I`** | **多行行首插入** | 批量把 `int` 改成 `vector<int>` |
| **`<C-v>` + `j/k` + `A`** | **多行行尾追加** | 批量添加注释 `// TODO` |
| **`<C-v>` + `g<C-a>`** | **生成递增序列** | 把一列 `0` 变成 `1, 2, 3...` |

### ✂️ 文本对象 (Text Objects)
*公式：`操作(d/c/y/v)` + `范围(i/a)` + `对象`*
| 命令 | 含义 | 场景 |
| :--- | :--- | :--- |
| **`ciw`** | Change Inner Word | 修改当前单词（不管光标在单词哪里） |
| **`ci{`** / **`ci(`** | Change Inner `{` / `(` | 清空大括号/小括号内容并重写 |
| **`yi{`** | Yank Inner `{` | 复制整个函数体（不含大括号） |
| **`via`** | Select Inner Argument | 选中函数参数里的某一项 (需插件支持) |
| **`D`** / **`C`** | Delete/Change to End | 删/改到行尾 (等价于 `d$` / `c$`) |

---

## 2. 极速导航 (Navigation)

### 🚀 瞬移
| 按键 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`gd`** | Go Definition | 跳到变量/函数定义处 |
| **`<C-o>`** / **`<C-i>`** | Jump Back / Forward | 看了定义后跳回来，跳回去 |
| **`gi`** | Go Insert | 跳回**最后一次退出插入模式**的地方并进入插入模式 |
| **`g;`** | Go Change | 跳回**上一次修改**的地方（案发现场） |
| **`%`** | Match Bracket | 在 `()`、`{}`、`[]` 之间反复横跳 |
| **`s`** + `字母` | Flash Jump (LazyVim) | 屏幕任意位置两键到达 |

### 🎥 视角调整
| 按键 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`zz`** | Center View | 把当前行挪到屏幕**中间** (护颈椎神器) |
| **`zt`** / **`zb`** | Top / Bottom | 把当前行挪到屏幕**顶部 / 底部** |

---

## 3. 剪贴板与寄存器 (Registers)

| 按键 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`"+p`** | **系统粘贴** | 把 Windows 浏览器里的样例粘贴进 WSL |
| **`"0p`** | **防覆盖粘贴** | 刚刚用了 `dd` 删东西，想粘之前 `y` 复制的内容 |
| **`<C-r>"`** | **插入模式粘贴** | 写注释时，直接粘入刚复制的变量名 |
| **`<C-r>=`** | **计算器** | 插入模式下输入 `1024*1024` 回车自动填结果 |

---

## 4. 批量自动化 (Batch & Command)

### 🤖 命令行黑魔法
| 命令 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`:%s/old/new/gc`** | 确认式替换 | 全局替换，每次都问你 `y/n` |
| **`:g/debug/d`** | 全局清洗 | 删掉所有包含 `debug` 的行 |
| **`:10,20norm A;`** | 范围 Normal 命令 | 给 10-20 行末尾执行 `A;` (加分号) |
| **`:sort u`** | 去重排序 | 把头文件排序并去重 |
| **`:g/.../m 0`** | 全局搬运 | 把所有 `#include` 移动到文件开头 |

### 🐚 外部命令联动
| 命令 | 描述 | 场景 |
| :--- | :--- | :--- |
| **`:%!jq .`** | 格式化 JSON | 把乱糟糟的 JSON 数据变漂亮 |
| **`:r !cat in.txt`** | 读取命令输出 | 把 `in.txt` 的内容插入到代码注释里 |
| **`q:`** | 命令历史窗口 | 手滑输错命令，不用重打，像改代码一样改命令 |

---

## 5. ACM/CP 专属配置 (Snippets)

### ⌨️ 自动补全整行
* **`<C-x><C-l>`**：在插入模式下，自动补全与当前文件里已有的**整行**相同的代码（写 DP 状态转移神器）。

### 🔢 快速调整数字
* **`<C-a>`** / **`<C-x>`**：光标下的数字 +1 / -1。

### 🔨 一键编译运行 (keymaps.lua)
```lua
vim.keymap.set("n", "<F5>", function()
  vim.cmd("w") -- 保存
  local file = vim.fn.expand("%")
  local out = vim.fn.expand("%:r")
  -- 编译并从 in.txt 输入
  local cmd = "g++ -std=c++17 -O2 -Wall " .. file .. " -o " .. out .. " && ./" .. out .. " < in.txt"
  vim.cmd("vsplit | term " .. cmd) -- 分屏运行
end, { desc = "Compile and Run C++" })
