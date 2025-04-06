---
title: Onlinetime-endstone文档 | docs
---

# Endstone 在线时间插件

一个用于显示玩家在线时间的 Minecraft 基岩版 [Endstone](https://endstone.dev/latest/) 插件。

### 命令

- /onlinetime : 查看你的在线时间
- /onlinetimetop : 查看所有玩家的在线时间排行榜

### 启用玩家名下方在线时间显示

- 打开 `config.json` 文件，将 `"onlinetime_belowname_enable"` 的值修改为 1 或 0。1 表示启用，0 表示禁用。
- 保存文件并重启服务器。

### 切换语言

- 打开 `config.json` 文件，修改 `"lang"` 为你的目标语言并保存文件。
- 执行命令 `scoreboard objectives remove onlinetime` 然后重启服务器。

## 安装

- 从[发布页面](https://github.com/ljh938527/onlinetime-endstone/releases)下载 .whl 文件
- 将其放入 `plugins` 文件夹
- 重启服务器，即刻体验！

## 系统要求

Python: 3.10+

Endstone: 0.5+
