# GitHub Store - Strategy Backtest Results

Export and store strategy backtest results.

## Structure

```
github-store/
├── index.json                      # Index of all strategies with stats
└── strategies/
    └── {strategy_id}/
        ├── stats.json              # Strategy statistics
        └── equity_curve.json       # Equity curve data points
```

## Usage

```bash
python tools/deploy.py \
  -sid tpsl \
  -bid example \
  -pair BTCUSD \
  -ex bybit \
  -tf 1h \
  -name "My Strategy" \
  -desc "Strategy description"
```

## Options

- `-sid, --strategy-id`: Strategy ID (required)
- `-bid, --input-id`: Input/Batch ID (required)
- `-pair, --pair`: Trading pair (required)
- `-ex, --exchange`: Exchange name (required)
- `-tf, --timeframe`: Timeframe (required)
- `-name, --name`: Display name (optional)
- `-desc, --description`: Description (optional)

## How It Works

1. Checks if backtest output exists in `strategies/{strategy_id}/outputs/`
2. Runs backtest automatically if output doesn't exist
3. Exports stats.json and equity_curve.json
4. Updates index.json with strategy entry

## Files

### stats.json
Complete performance statistics:
- Return, Sharpe ratio, Sortino ratio, Calmar ratio
- Max drawdown, win rate, profit factor
- Number of trades, avg trade %, exposure time

### equity_curve.json
Full equity curve data for visualization

### index.json
Index of all strategies with preview stats
