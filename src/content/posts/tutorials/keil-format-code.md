---
title: Keil 使用 clang-format 的完整教程：实现 STM32 代码一键格式化
published: 2025-04-15
description: "在 Keil 中开发 STM32 工程时，CubeMX 生成的代码缩进和格式常常不统一。本文将详细讲解如何在 Keil 中集成 clang-format，配置快捷键，实现类似 VSCode 的一键自动格式化，让代码始终保持整洁一致。"
image: ""
tags: [STM32, 嵌入式开发]
category: "开发环境"
draft: false
lang: "zh_CN"
---

> 在使用 Keil 作为 STM32 开发环境时，每次通过 STM32CubeMX 更新代码后，自动生成的代码都会变成 2 空格缩进格式，严重影响代码可读性。本文将介绍如何通过 clang-format 工具实现 Keil 环境下的一键代码格式化。

## 环境准备

### 必要组件

1. Keil uVision IDE
2. clang-format 工具

### clang-format 获取方式

**Keil V6 用户(armclang 编译器)**：
工具已内置在安装目录中：

```
<Keil安装路径>\ARM\ARMCLANG\bin\clang-format.exe
```

**Keil V5 用户(armcc 编译器)**：

1. 从[Arm 官网](https://developer.arm.com/downloads/view/ACOMPE?sortBy=availableBy&revision=r6p24-00rel0)下载 V6 编译器包`Arm Compiler for Embedded 6.24 (for Keil® MDK)`
2. 解压至 Keil 安装目录下的 ARM 文件夹
3. 确保最终路径为：

```
<Keil安装路径>\ARM\ARMCLANG\bin\clang-format.exe
```

## 配置步骤

### 1. 添加自定义工具

1. 打开 Keil → Tools → Customize Tools Menu...

   ![Customize Tools Menu](https://img.hanzogenji.cn/i/2025/07/08/686d0aa7413c7.png)

2. 点击 Add 添加新工具

3. 配置参数：

   - **名称**：clang format

   - **路径**：clang-format.exe 的完整路径

   - **参数**：

     ```
     -verbose -sort-includes -style=Microsoft -i !E
     ```

   - `!E`表示当前文件

   - `-i`表示直接修改文件

### 2. 设置快捷键

1. 进入 Edit → Configuration → Shortcut Keys

2. 找到"Tools:clang format"项

   ![Shortcut_keys](https://img.hanzogenji.cn/i/2025/07/08/686d0aa830915.png)

3. 设置喜欢的快捷键组合，我使用 VSCode 同款`Alt + Shift + F`。

## 使用技巧

1. **使用前务必保存文件**，因为工具会直接修改源文件
2. 格式化后会按照 Microsoft 风格自动调整：
   - 代码缩进
   - #include 排序
   - 代码对齐等

## 高级定制

clang-format 支持高度自定义配置，可通过修改参数调整：

- 缩进宽度
- 大括号风格
- 换行规则等

如需特定格式要求，可参考 clang-format 官方文档或咨询相关技术支持。

> 提示：该方案特别适合需要频繁使用 STM32CubeMX 生成代码的开发者，能有效保持代码风格统一。
