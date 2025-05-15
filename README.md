
# Intraday Nifty Short Straddle Backtest (with Re-entries)

This project implements an intraday short straddle backtesting engine for NIFTY options, with support for re-entries after stop-loss hits. The strategy dynamically determines optimal entry points, manages trades through the day, and provides a complete performance summary.

---

## 📊 Strategy Overview

- **Instrument**: NIFTY Options (CE & PE)
- **Strategy**: Short Straddle
- **Entry Window**: 09:20 AM to 09:45 AM
- **Exit Time**: 03:15 PM
- **Stop Loss**: 10% of total premium
- **Re-entries**: Up to 3 re-entries allowed upon SL hit
- **Lot Size**: 375
- **Initial Capital**: ₹10,00,000
- **Slippage**: 0.5%
- **Brokerage**: ₹0.5 per leg per lot

---

## 📁 Folder Structure

```
project/
│
├── data/
│   └── APR_2021/                  # Folder with input CSV option data files
│
├── ShortStraddle_Backtest.py     # Main backtest script
├── ShortStraddle_Trades_*.csv    # Exported trade-level results
├── ShortStraddle_Daily_*.csv     # Exported daily capital and PnL
└── README.md                     # This file
```

---

## ⚙️ Configuration

Set your custom parameters at the top of the script:

```python
ENTRY_WINDOW_START = "09:20:00"
ENTRY_WINDOW_END = "09:45:00"
EXIT_TIME = "15:15:00"
SL_PCT = 0.1
LOTSIZE = 375
MAX_REENTRIES = 3
INITIAL_CAPITAL = 1000000
DATA_FOLDER = r"C:\path\to\your\data\APR_2021"
```

---

## ▶️ How to Run

```bash
python ShortStraddle_Backtest.py
```

> You can set the `start_date` and `end_date` at the bottom of the script.

---

## 📈 Output

After execution, two CSVs are generated:

1. **`ShortStraddle_Trades_<from>_to_<to>.csv`**  
   Detailed logs for each trade: entry/exit time, PnL, reason, ticker, etc.

2. **`ShortStraddle_Daily_<from>_to_<to>.csv`**  
   Daily summary: number of trades, daily PnL, capital progression.

---

## 🧮 Performance Metrics (Sample)

```
==== Performance Summary ====
Total Days     : 19
Total Trades   : 28
Avg Trades/Day : 1.47
Avg Entries/Day: 1.47
Win Rate (Days): 52.63%
Win Rate (Trades): 46.43%
Total Return   : ₹27056.25 (2.71%)
Max Drawdown   : ₹31575.00 (2.98%)
CAGR           : 39.94%
Sharpe Ratio   : 1.58
```

---

## 📌 Features

- ✅ Optimal ATM strike selection per day
- ✅ Time-window based entry strategy
- ✅ Support for multiple re-entries
- ✅ Stop-loss handling
- ✅ Daily and trade-wise PnL reports
- ✅ Drawdown, Sharpe, CAGR calculation

---

## 🛠 Dependencies

```bash
pip install pandas numpy
```
Note: 

- Make sure to update the DATA_FOLDER variable in the script to the path where your intraday options CSV files are stored locally before running the backtest     (e.g., DATA_FOLDER = r"your/local/path/to/APR_2021").

- Make sure your `APR_2021` folder contains intraday option CSVs with `Date`, `Time`, `Ticker`, `Open`, `High`, `Low`, `Close`.

---

## 🔍 Future Enhancements

- Add graphical reports (e.g., equity curve, drawdown)
- Integrate Telegram/email alert for daily report
- Automate multiple-month backtests
- Add transaction cost simulation (actual turnover)

---

## 📬 Contact

**Author:** Om Deshmukh
