# BottomClaw 🦞 抄底龙虾

多信号驱动的自动建仓 OpenClaw Skill。追踪 BTC/BNB/HYPE 实时价格与市场情绪，根据你的阶梯规则自动提醒或执行 DCA。

## 一句话开始

克隆本项目后，在 Claude Code 中粘贴：

```
读取 skill/bottomclaw/SKILL.md，按照里面的 setup 引导流程跟我对话。
```

## 安装

### OpenClaw

```bash
# 安装 Skill
openclaw skill install github:nobita1998/deepClaw/skill/bottomclaw

# 使用
/bottomclaw
```

### Claude Code

将本项目克隆到本地，在 Claude Code 中使用 `/skill` 加载：

```bash
git clone https://github.com/nobita1998/deepClaw.git
cd deepClaw
```

启动 Claude Code 后，直接输入：

```
/bottomclaw
```

或者将 `skill/bottomclaw/` 目录复制到你的 Claude Code 项目中的 `.claude/skills/` 下：

```bash
mkdir -p .claude/skills
cp -r skill/bottomclaw .claude/skills/
```

然后在任意项目中使用 `/bottomclaw`。

## 首次使用

第一次运行 `/bottomclaw` 时，龙虾会引导你完成设置：

1. **选币** — 你想定投哪些币？
2. **预算** — 总投入上限多少？
3. **阈值** — 什么价格开始加仓？
4. **确认** — 生成配置，你确认后保存

全程对话式，不需要手编 JSON。

## 两种模式

| 模式 | 说明 | 需要 API Key |
|------|------|:---:|
| `alert_only`（默认） | 只提醒，你手动去 Binance 买 | ❌ |
| `live` | 自动下单 | ✅ |

装完就是提醒模式，零配置可用。信任后说「切换到实盘」开启自动下单。

## 日常使用

```
/bottomclaw          → 查看状态报告（价格 + 阶段 + 建议）
"BTC 什么阶段"        → 单币查询
"执行"               → 执行今日建仓
"今天不买了"          → 跳过
"刚买了 8.8U BTC"     → 补录交易
"复盘"               → 月度复盘报告
"切换到实盘"          → 开启自动下单
"把 BTC 加仓线改成 6万" → 修改配置
```

## 文件结构

```
skill/bottomclaw/
├── SKILL.md      ← Skill 逻辑定义（Agent 读这个）
├── config.json   ← 你的建仓规则（首次设置时生成）
└── state.json    ← 交易记录（自动维护）
```

## 数据源

全部公开 API，无需鉴权：

- **Binance** — 实时价格
- **Alternative.me** — Fear & Greed Index
- **CoinGecko** — BTC Dominance

## License

MIT
