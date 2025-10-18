# RSI Trading Bot

A sophisticated automated trading bot for MetaTrader 5 that implements multiple RSI-based strategies with advanced risk management.

---

## Features

- Multiple RSI strategies
  - Overbought / Oversold detection (traditional RSI levels 70 / 30)
  - RSI Divergence identification
  - Swing Failure Pattern recognition
- Advanced risk management
  - ATR-based Stop Loss and Take Profit
  - Maximum 2% risk per trade (configurable)
  - Trailing stop loss support
  - Automatic position size calculation
- Trend confirmation
  - EMA-based trend filtering
  - Configurable fast/slow EMA periods
- Live trading
  - MT5 integration for live execution
  - Supports EURUSD and XAUUSD (extensible)
  - Maximum 1 position at a time (safety limit)
- Notifications
  - Telegram alerts for bot start/stop
  - Trade open/close notifications
  - Error alerts
- Fully configurable
  - YAML-based configuration (no code changes required)
- Robust logging
  - Rotating log files
  - Configurable log levels
  - Console and file output

---

## Installation

1. Clone or download the project:
   ```bash
   git clone https://github.com/kassarmohannad7-cpu/Another-TradingBot.git
   cd Another-TradingBot
   ```
2. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure the bot (see Configuration section).

---

## Configuration

All settings are stored in `config/config.yaml`. Main configuration areas:

- Trading Settings: symbols, timeframe, scan interval
- Risk Management: risk percentage, ATR multipliers, trailing stops
- RSI Strategies: enable/disable strategies, adjust weights
- Trend Confirmation: EMA settings
- MT5 Connection: login credentials and server
- Telegram: bot token and chat ID (optional)
- Logging: log levels and rotation settings

Edit `config/config.yaml` to:
- Add your MT5 credentials
- Add your Telegram bot token and chat ID (optional)
- Adjust trading and risk parameters as needed

---

## Usage

- Using the provided script (Windows / Git Bash / WSL):
  ```bash
  ./script.sh
  ```
- Run directly with Python:
  ```bash
  python src/main.py
  ```

---

## Project Structure

```
rsi_trading_bot/
├── config/
│   └── config.yaml              # Configuration file
├── src/
│   ├── main.py                  # Entry point
│   ├── bot.py                   # Main orchestrator
│   ├── strategies/              # RSI strategy implementations
│   ├── indicators/              # Technical indicators
│   ├── trading/                 # MT5 connection & execution
│   ├── notifications/           # Telegram notifications
│   └── utils/                   # Utilities (config, logging)
├── logs/                        # Log files
├── script.sh                    # Startup script
└── requirements.txt             # Python dependencies
```

---

## Strategy Logic

The bot combines multiple RSI-based strategies:

- Overbought/Oversold: Traditional RSI levels (70 / 30)
- Divergence: Price vs RSI divergence detection
- Swing Failure: Failed breakout patterns

When multiple strategies confirm the same direction, the bot can increase position size using a configurable multiplier.

---

## Risk Management

- Maximum 2% account risk per trade (configurable)
- ATR-based dynamic stop loss and take profit
- Trailing stop loss to lock in profits
- Position size automatically calculated based on account balance and configured risk

---

## Safety Features

- Maximum 1 open position at a time
- Graceful shutdown handling
- Error notifications via Telegram
- Comprehensive logging for audit trail

---

## Requirements

- Python 3.8+
- MetaTrader 5 terminal
- Active MT5 trading account
- Telegram bot (optional, for notifications)

---

## Disclaimer

This bot is provided for educational purposes only. Trading involves risk. Always test thoroughly on a demo account before running on a live account.

---

## Support

For issues or questions, refer to the project documentation or contact the project maintainer.
