# BottomClaw 🦞 抄底龙虾

多信号驱动的自动建仓 OpenClaw Skill。追踪实时价格与市场情绪，根据你的阶梯规则自动提醒或执行 DCA。

## 快速开始

```bash
# 1. 克隆项目
git clone https://github.com/nobita1998/deepClaw.git
cd deepClaw

# 2. 启动 Claude Code
claude

# 3. 龙虾自动开始引导设置（无需输入任何命令）
```

`CLAUDE.md` 会自动加载，龙虾会检测到 config.json 不存在，直接进入 setup 引导。

## 首次设置

龙虾会一步步问你：

1. **选币** — 你想定投哪些币？
2. **预算** — 总投入上限多少？
3. **阈值** — 什么价格开始加仓？
4. **确认** — 生成配置，你确认后保存到 `config.json`

全程对话式，不需要手编 JSON。

## 日常使用

每天打开项目，启动 Claude Code，龙虾自动输出状态报告。

也可以直接对话：

```
"BTC 什么阶段"        → 单币查询
"执行"               → 执行今日建仓（提醒模式下为模拟）
"今天不买了"          → 跳过，记录到 state.json
"刚买了 8.8U BTC"     → 补录手动交易
"复盘"               → 月度复盘报告
"切换到实盘"          → 开启自动下单（需配置 API Key）
"把 BTC 加仓线改成 6万" → 修改配置
```

如果昨天龙虾提醒了但你没回复，下次启动会先问你："昨天那笔你买了吗？"

## 两种模式

| 模式 | 说明 | 需要 API Key |
|------|------|:---:|
| `alert_only`（默认） | 只提醒，你手动去 Binance 买 | ❌ |
| `live` | 自动下单 | ✅ |

默认提醒模式，零配置可用。信任后说「切换到实盘」，龙虾会引导你安全配置 API Key（关闭提币权限 + IP 限制）。

## 文件结构

```
deepClaw/
├── CLAUDE.md                  ← Claude Code 自动加载的入口
├── README.md                  ← 你正在看的这个
└── skill/bottomclaw/
    ├── SKILL.md               ← 龙虾的大脑（逻辑定义）
    ├── config.json            ← 你的规则（setup 时生成）
    └── state.json             ← 交易记录（自动维护）
```

## 数据源

全部公开 API，无需鉴权：

- **Binance** — 实时价格
- **Alternative.me** — Fear & Greed Index
- **CoinGecko** — BTC Dominance

## License

MIT
