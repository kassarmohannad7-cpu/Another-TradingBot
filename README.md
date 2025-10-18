RSI Trading Bot
A sophisticated automated trading bot for MetaTrader 5 that implements multiple RSI-based strategies with advanced risk management.

Features
Multiple RSI Strategies

Overbought/Oversold detection

RSI Divergence identification

Swing Failure Pattern recognition

Advanced Risk Management

ATR-based Stop Loss and Take Profit

2% maximum risk per trade

Trailing stop loss support

Position size calculation

Trend Confirmation

EMA-based trend filtering

Configurable fast/slow EMA periods

Live Trading

MT5 integration for live execution

Supports EURUSD and XAUUSD (extensible)

Maximum 1 position at a time

Notifications

Telegram alerts for bot start/stop

Trade open/close notifications

Error alerts

Fully Configurable

YAML-based configuration

All parameters adjustable without code changes

Robust Logging

Rotating log files

Configurable log levels

Console and file output

Installation
Clone or download the project

Install Python dependencies

pip install -r requirements.txt
Configure the bot

Edit config/config.yaml

Add your MT5 credentials

Add your Telegram bot token and chat ID (optional)

Adjust trading parameters as needed

Configuration
All settings are in config/config.yaml:

Trading Settings: Symbols, timeframe, scan interval

Risk Management: Risk percentage, ATR multipliers, trailing stops

RSI Strategies: Enable/disable strategies, adjust weights

Trend Confirmation: EMA settings

MT5 Connection: Login credentials and server

Telegram: Bot token and notification preferences

Logging: Log levels and rotation settings

Usage
Windows (Git Bash/WSL)
./script.sh
Direct Python
python src/main.py
Project Structure
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
Strategy Logic
The bot combines multiple RSI strategies:

Overbought/Oversold: Traditional RSI levels (70/30)

Divergence: Price vs RSI divergence detection

Swing Failure: Failed breakout patterns

When multiple strategies confirm the same direction, the bot can increase position size (configurable multiplier).

Risk Management
Maximum 2% account risk per trade

ATR-based dynamic stop loss and take profit

Trailing stop loss to lock in profits

Position size automatically calculated based on account balance and risk

Safety Features
Maximum 1 open position at a time

Graceful shutdown handling

Error notifications via Telegram

Comprehensive logging for audit trail

Requirements
Python 3.8+

MetaTrader 5 terminal

Active MT5 trading account

Telegram bot (optional, for notifications)

Disclaimer
This bot is for educational purposes. Trading involves risk. Always test thoroughly on a demo account before live trading.

Support
For issues or questions, refer to the project documentation or contact supp
