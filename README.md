# mcporter-railway-query

An OpenClaw skill for querying Chinese railway tickets via 12306 using mcporter CLI.

## Overview

This skill provides tools to search for G/D/C train tickets, check train schedules, query seat availability, and plan rail travel between Chinese cities. It supports filtering by date, time range, train type, and sorting results.

## Prerequisites

1. Install mcporter CLI: `npm install -g mcporter`
2. Configure 12306 MCP server in `~/.mcporter/mcporter.json`
3. Ensure MCP server is running

## Installation

This is an OpenClaw skill. Install using:

```bash
openclaw skills install mcporter-railway-query.skill
```

## Usage

The skill provides several helper scripts:

### Query afternoon trains (12:00-18:00)
```bash
./scripts/query-afternoon.sh 2026-02-18 SHH KYH
```

### Query all-day trains
```bash
./scripts/query-tickets.sh 2026-02-18 AOH HZH
```

### Get station codes
```bash
./scripts/get-station-code.sh "上海虹桥"
```

### Direct mcporter commands
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

## Features

- Query train tickets with departure time filtering
- Support for G (high-speed), D (bullet train), and C (city train) trains
- Seat availability checking (商务座, 一等座, 二等座, etc.)
- Station code lookup
- Comprehensive station code reference table

## Common Station Codes

| Station | Code | Notes |
|---------|------|-------|
| 上海 | SHH | Shanghai Station |
| 上海虹桥 | AOH | Shanghai Hongqiao Station |
| 杭州东 | HZH | Hangzhou East Station |
| 江阴 | KYH | Jiangyin Station |

See `references/station-codes.md` for the complete list.

## License

MIT