# 🦞 Whale Guardian Copier

> **Binance OpenClaw AI Competition 2026** — Built with Claude AI + 11 Binance Skills

[![Binance Skills](https://img.shields.io/badge/Binance%20Skills-11%2F11-F0B90B?style=flat-square&logo=binance)](https://github.com/binance/binance-skills-hub)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-2026-00d4aa?style=flat-square)](https://openclaw.ai)
[![Claude AI](https://img.shields.io/badge/Claude-Sonnet%204-7c3aed?style=flat-square)](https://anthropic.com)
[![Multi-Chain](https://img.shields.io/badge/Chains-CEX%20%7C%20BSC%20%7C%20ETH%20%7C%20SOL%20%7C%20Base%20%7C%20Pump.fun-627EEA?style=flat-square)]()
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)]()

---

## 🎯 What is Whale Guardian Copier?

**Whale Guardian Copier** is an AI-powered trading agent that automatically detects whale transactions, audits smart contracts for safety, and executes copy trades in under 0.1 seconds — all powered by Claude AI and all 11 official Binance Skills.

> *"Stop watching whales make money. Let the guardian copy them for you — safely."*

---

## ✨ Core Features

### 🐋 Auto Whale Alert Feed
- Real-time detection of large transactions (>$500K) across BSC, Base, and Solana
- Displays whale wallet address, win rate, token, and transaction size instantly
- New alerts appear automatically every 25 seconds

### ⚡ One-Click Copy Trade
- Single button triggers a full 8-step analysis pipeline:
  `Address Info → Token Info → Market Rankings → Contract Audit → Trading Signal → Spot Skill → Simulate → Square Post`
- Entire flow completes in under 3 seconds
- Position size capped at **0.5% of portfolio** for risk management

### 🎯 Take Profit / Stop Loss
- Configurable TP/SL per trade (e.g. TP +15% / SL -5%)
- Quick preset buttons: +5% / +10% / +20% / +50% for TP, -3% / -5% / -10% / -15% for SL
- Live PNL monitor bar showing real-time position movement
- **Auto-executes Flash Order** when TP or SL level is hit

### 🌐 Flash Order — Multi-Chain (0.1s)
Trade across 6 venues in under 0.1 seconds:

| Chain | DEX/CEX | Native Token |
|-------|---------|-------------|
| 🏦 Binance | Spot Skill (CEX) | USDT |
| 🟡 BSC | PancakeSwap V3 | BNB |
| 💎 Ethereum | Uniswap V3 | ETH |
| 🟣 Solana | Jupiter / Raydium | SOL |
| 🔵 Base | Aerodrome | ETH |
| 🔥 Pump.fun | Bonding Curve AMM | SOL |

### 📊 PNL Dashboard
- 30-day portfolio growth chart (Canvas)
- Trade history with per-trade PNL, risk score, and execution time
- Win rate, total PNL, best trade stats

### 📢 Binance Square Auto-Post
- After every successful copy trade, auto-generates a viral Square post
- Includes token, PNL, risk score, and CTA — ready to publish

### 🌍 Multi-Language (i18n)
- Auto-detects browser language: 🇻🇳 Vietnamese / 🇺🇸 English / 🇨🇳 Chinese
- All UI strings, alerts, and Claude AI responses switch language automatically

---

## 🛠️ Tech Stack

```
Frontend      →  Vanilla HTML/CSS/JS (single file, zero dependencies)
AI Engine     →  Claude Sonnet 4 (claude-sonnet-4-20250514) via Anthropic API
Live Prices   →  Binance WebSocket (wss://stream.binance.com) — no CORS
AI Skills     →  11 Official Binance Skills from binance-skills-hub
Multi-Chain   →  CEX (Binance Spot) + DEX (BSC/ETH/SOL/Base/Pump.fun)
```

---

## ⚡ 11 Binance Skills Used

| # | Skill | Usage in Agent |
|---|-------|----------------|
| 1 | **Binance Spot Skill** | Flash Order execution, market data |
| 2 | **Query Address Info** | Whale wallet analysis, win rate |
| 3 | **Query Token Info** | Token metadata, holder count |
| 4 | **Crypto Market Rankings** | Volume, trending, net flow |
| 5 | **Meme Rush** | Meme coin narrative detection |
| 6 | **Trading Signal** | Entry price, confidence %, stop loss |
| 7 | **Token Contract Audit** | Risk score 0–100, rug/honeypot detection |
| 8 | **Binance Square Skill** | Auto-generate and post viral content |
| 9 | **Binance Alpha** *(NEW)* | On-chain trending assets BSC/Base/Solana |
| 10 | **USD-M Futures** *(NEW)* | Funding rate, OI, long/short strategy |
| 11 | **Margin Trading** *(NEW)* | Collateral ratio, liquidation price |

---

## 🚀 Quick Start (Demo Mode)

```bash
# No installation required — runs as a single HTML file
git clone https://github.com/YOUR_USERNAME/whale-guardian-copier
cd whale-guardian-copier
open whale-guardian-v7.html
```

> ⚠️ **Demo Mode**: All trades are simulated. To enable real trading, see [Production Setup](#production-setup) below.

---

## 🔧 Production Setup

### 1. Install Binance Skills Hub

```
# In your OpenClaw agent, send:
Install these Skills: https://github.com/binance/binance-skills-hub
```

### 2. Configure Binance API Key

1. Go to [Binance API Management](https://www.binance.com/en/my/settings/api-management)
2. Create API → select **System-generated key**
3. Enable: ✅ Read Access, ✅ Spot Trading
4. **NEVER enable Withdrawals** ← critical security rule
5. Bind trusted IP address

### 3. Environment Variables

```bash
ANTHROPIC_API_KEY=your_claude_api_key
BINANCE_API_KEY=your_binance_api_key
BINANCE_SECRET_KEY=your_binance_secret_key   # ← kept server-side only
```

### 4. Backend (Required for Real Trading)

A minimal Node.js backend is needed to sign HMAC-SHA256 requests (Secret Key must never be exposed in frontend):

```bash
cd backend
npm install
node server.js
```

### 5. For DEX / Web3

- **EVM chains** (BSC, ETH, Base): Connect MetaMask
- **Solana** (Jupiter, Pump.fun): Connect Phantom Wallet

---

## 📁 Project Structure

```
whale-guardian-copier/
├── whale-guardian-v7.html    # Main app (single file, all-in-one)
├── backend/
│   ├── server.js             # HMAC signing proxy for Binance API
│   └── package.json
├── README.md
└── LICENSE
```

---

## 🔄 How It Works — Copy Trade Flow

```
1. 🐋  Whale Alert detected (on-chain large tx > $500K)
         ↓
2. 🔍  [Skill #2] Address Info → analyze wallet win rate & history
         ↓
3. 🪙  [Skill #3] Token Info → liquidity, holders, 24h volume
         ↓
4. 🏆  [Skill #4] Market Rankings → trending rank, net inflow
         ↓
5. 🛡️  [Skill #7] Contract Audit → risk score 0-100
         ↓ (abort if score > 30)
6. 📡  [Skill #6] Trading Signal → entry price, confidence %
         ↓
7. ⚡  [Skill #1] Spot Skill → calculate 0.5% position size
         ↓
8. 🎯  TP/SL set → Flash Order executed in 0.1s
         ↓
9. 📢  [Skill #8] Square → auto-post viral content
```

---

## 🛡️ Safety First

- **Max position size**: 0.5% of portfolio per trade
- **Contract audit**: Auto-rejects any token scoring > 30/100
- **Honeypot detection**: Blocks trades on contracts that can't be sold
- **Rug pull scan**: Checks for mintable, freeze authority, top holder concentration
- **Demo mode by default**: No real funds at risk without explicit API key setup

---

## 🏆 Competition Details

- **Event**: Binance OpenClaw AI Innovation Contest 2026
- **Category**: AI Trading Agent
- **Skills used**: All 11 official Binance Skills
- **Unique angle**: Whale copy trading + AI safety audit + multi-chain + auto Square posting

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">

**Built with 🦞 by Whale Guardian Team**

*Powered by Claude AI × Binance Skills Hub × OpenClaw 2026*

</div>
