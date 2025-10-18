# **RSI Trading Bot**

A sophisticated automated trading bot for MetaTrader 5 that implements multiple RSI-based strategies with advanced risk management. Supports **EURUSD** and **XAUUSD** out of the box.

---

## **Features**

- **Multiple RSI Strategies**
  - Overbought/Oversold detection
  - RSI Divergence identification
  - Swing Failure Pattern recognition
- **Advanced Risk Management**
  - ATR-based Stop Loss and Take Profit
  - 2% maximum risk per trade
  - Trailing stop loss support
  - Position size calculation
- **Trend Confirmation**
  - EMA-based trend filtering
  - Configurable fast/slow EMA periods
- **Live Trading**
  - MT5 integration for live execution
  - Supports **EURUSD** and **XAUUSD** (extensible)
  - Maximum 1 position at a time
- **Notifications**
  - Telegram alerts for bot start/stop
  - Trade open/close notifications
  - Error alerts
- **Fully Configurable**
  - YAML-based configuration
  - All parameters adjustable without code changes
- **Robust Logging**
  - Rotating log files
  - Configurable log levels
  - Console and file output

---

## **Requirements**

- Python 3.8+
- MetaTrader 5 terminal installed and logged in
- Active MT5 trading account
- Telegram bot (optional, for notifications)

---

## **Installation**

1. **Clone or download the project**
    ```bash
    git clone https://github.com/your-org/rsi_trading_bot.git
    cd rsi_trading_bot
    ```
    Or download the ZIP and extract.

2. **Create and activate a virtual environment (recommended)**
    ```bash
    python -m venv .venv
    # Windows
    .venv\Scripts\activate
    # macOS/Linux
    source .venv/bin/activate
    ```

3. **Install Python dependencies**
    ```bash
    pip install -r requirements.txt
    ```

4. **Configure the bot**
    - Edit the configuration:
      ```bash
      nano config/config.yaml
      ```
    - Provide:
      - MT5 login, server, and (if needed) password
      - Telegram bot token and chat ID (optional)
      - Symbols: **EURUSD**, **XAUUSD**; timeframe; risk settings; ATR multipliers; EMA periods

---

## **Configuration**

All settings are in `config/config.yaml`. Pre-configured for **EURUSD** and **XAUUSD**:

```yaml
trading:
  symbols: ["EURUSD", "XAUUSD"]   # Supported symbols
  timeframe: "M15"
  scan_interval_sec: 30
  max_open_positions: 1

risk:
  risk_pct: 2.0
  atr_period: 14
  sl_atr_mult: 2.0
  tp_atr_mult: 3.0
  trailing_stop:
    enabled: true
    activation_atr_mult: 1.5
    step_atr_mult: 0.5

rsi_strategies:
  overbought_oversold:
    enabled: true
    rsi_period: 14
    overbought: 70
    oversold: 30
    weight: 1.0
  divergence:
    enabled: true
    swing_lookback: 5
    min_strength: 0.6
    weight: 1.0
  swing_failure:
    enabled: true
    lookback_bars: 10
    weight: 1.0
  confirmation:
    min_total_weight: 1.5
    size_multiplier_on_multi_confirm: 1.5

trend_filter:
  enabled: true
  ema_fast: 21
  ema_slow: 50

mt5:
  login: 12345678
  server: "YourBroker-Server"
  password: "YOUR_PASSWORD"

telegram:
  enabled: false
  bot_token: "123456:ABC-DEF..."
  chat_id: "123456789"
  notify:
    startup: true
    shutdown: true
    trade_open: true
    trade_close: true
    errors: true

logging:
  level: "INFO"
  file: "logs/bot.log"
  rotate:
    max_bytes: 10485760
    backup_count: 5
