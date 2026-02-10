# mcporter-railway-query

一个用于通过 12306 查询中国铁路车票的 OpenClaw 技能。

## 概述

此技能提供了查询 G/D/C 字头列车车票、查看列车时刻表、查询座位可用性以及规划城市间铁路旅行的工具。支持按日期、时间段、列车类型过滤以及结果排序。

## 先决条件

1. 安装 mcporter CLI: `npm install -g mcporter`
2. 在 `~/.mcporter/mcporter.json` 中配置 12306 MCP 服务器
3. 确保 MCP 服务器正在运行

## 安装

这是一个 OpenClaw 技能，使用以下命令安装：

```bash
openclaw skills install mcporter-railway-query.skill
```

## 使用方法

技能提供了几个辅助脚本：

### 查询下午班次 (12:00-18:00)
```bash
./scripts/query-afternoon.sh 2026-02-18 SHH KYH
```

### 查询全天班次
```bash
./scripts/query-tickets.sh 2026-02-18 AOH HZH
```

### 获取车站代码
```bash
./scripts/get-station-code.sh "上海虹桥"
```

### 直接使用 mcporter 命令
```bash
mcporter call 12306.get-tickets \
  date="2026-02-18" \
  fromStation="AOH" \
  toStation="HZH" \
  trainFilterFlags="GD" \
  earliestStartTime=12 \
  latestStartTime=18 \
  sortFlag="startTime" \
  --config ~/.mcporter/mcporter.json
```

## 功能

- 按出发时间过滤查询列车
- 支持 G (高铁), D (动车), 和 C (城际) 列车
- 座位可用性检查 (商务座, 一等座, 二等座, 等)
- 车站代码查询
- 全面的车站代码参考表

## 常用车站代码

| 车站 | 代码 | 备注 |
|------|------|------|
| 上海 | SHH | 上海站 |
| 上海虹桥 | AOH | 上海虹桥站 |
| 杭州东 | HZH | 杭州东站 |
| 江阴 | KYH | 江阴站 |

完整列表请参见 `references/station-codes.md`。

## 许可证

MIT