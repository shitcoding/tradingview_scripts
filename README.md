# TradingView Scripts Collection

A collection of Pine Script indicators and strategies for cryptocurrency trading, focused on short setup detection and trade analysis.

## 📁 Repository Structure

```
tradingview_scripts/
├── short_setup_finder/
│   ├── short_setup_finder_script.pine     # Main signal detection indicator
│   ├── short_setup_audit_script.pine      # Historical performance auditor
│   └── short_strategy_backtest_SL+TP.pine # Strategy backtester with SL/TP
└── spot_buy_marker.pine                   # Spot trading position tracker
```

## 🎯 Scripts Overview

### 1. Short Setup Finder (`short_setup_finder_script.pine`)

**Purpose**: Identifies potential short entry points using multiple technical confluence factors.

**Key Features**:
- **Surge Detection**: Identifies momentum exhaustion after significant price increases
- **RSI Overbought**: Detects overbought conditions with rollover confirmation
- **Bollinger Bands**: Filters based on price exhaustion near upper bands
- **Volume Confirmation**: Optional volume spike validation
- **Trend Filtering**: Configurable trend-based entry filtering
- **Dynamic Alerts**: Real-time alerts with suggested SL/TP levels

**Signal Types**:
- **BASE**: 2+ confluence factors (default)
- **STRONG**: 3+ confluence factors (default)

### 2. Short Setup Auditor (`short_setup_audit_script.pine`)

**Purpose**: Backtests and analyzes the historical performance of short setup signals.

**Key Features**:
- **Outcome Tracking**: Monitors TP hit rates and timing
- **Performance Statistics**: Hit rates, average bars to TP, ROI analysis
- **Visual Feedback**: Color-coded labels showing trade results
- **Summary Table**: Real-time statistics display

### 3. Short Strategy Backtest (`short_strategy_backtest_SL+TP.pine`)

**Purpose**: Full strategy implementation with position sizing and risk management.

**Key Features**:
- **Automated Trading**: Strategy-based entries and exits
- **Risk Management**: ATR-based stop loss and take profit
- **Performance Metrics**: Built-in strategy performance analysis
- **Commission Modeling**: Realistic backtesting with fees

### 4. Spot Buy Marker (`spot_buy_marker.pine`)

**Purpose**: Track and analyze spot trading positions with P&L monitoring.

**Key Features**:
- **Position Tracking**: Manual entry price and quantity input
- **Real-time P&L**: Live profit/loss calculation and display
- **Visual Elements**: Entry markers, horizontal price lines, summary tables
- **Flexible Input**: Support for quantity or total investment amount

## ⚙️ Configuration Parameters

### Common Settings Across Scripts

| Parameter | Description | Default | Range |
|-----------|-------------|---------|-------|
| **Surge Lookback** | Bars to check for momentum exhaustion | 72 | 1+ |
| **Surge Threshold** | Minimum price increase % | 10.0% | 0.1%+ |
| **RSI Length** | RSI calculation period | 14 | 2+ |
| **RSI Overbought** | Overbought threshold level | 70 | 50-100 |
| **BB Length** | Bollinger Bands period | 20 | 2+ |
| **BB Multiplier** | Standard deviation multiplier | 2.0 | 0.5+ |
| **ATR Length** | ATR calculation period | 14 | 1+ |
| **SL Multiplier** | Stop loss = ATR × multiplier | 1.5 | 0.1+ |
| **TP Multiplier** | Take profit = ATR × multiplier | 1.0 | 0.1+ |

## 🚀 Quick Start Guide

### Setting Up Short Setup Detection

1. **Load the Finder Script**:
   - Add `short_setup_finder_script.pine` to your TradingView chart
   - Configure confluence parameters based on your risk tolerance
   - Enable alerts for "Any alert() function call"

2. **Validate with Auditor**:
   - Add `short_setup_audit_script.pine` with identical settings
   - Review historical hit rates and performance metrics
   - Adjust parameters based on backtest results

3. **Strategy Testing**:
   - Load `short_strategy_backtest_SL+TP.pine` for full backtesting
   - Analyze strategy performance metrics
   - Optimize parameters using TradingView's strategy tester

### Using Spot Buy Marker

1. **Position Setup**:
   - Input your actual buy price and time
   - Choose between quantity or total investment input
   - Customize visual elements (colors, labels, tables)

2. **Monitoring**:
   - Track real-time P&L in the top-right table
   - View entry marker and horizontal price line
   - Monitor percentage and absolute returns

## 📊 Alert Configuration

### Setting up Dynamic Alerts

1. **Create Alert**:
   - Condition: "Any alert() function call"
   - Message: Use default (script generates dynamic content)
   - Frequency: "Once Per Bar Close"

2. **Alert Content**:
   ```
   Short BTCUSDT (STRONG)
   15.10.25 14:30
   CFL: 3/4
   RSI: 75.2
   Price: 67425.50
   SL: 68890.75
   TP: 66450.25
   ```

## 🎯 Trading Methodology

### Short Setup Confluence Factors

1. **Momentum Exhaustion** (Surge): Price has increased significantly over lookback period
2. **Overbought Conditions** (RSI): RSI above threshold with rollover confirmation
3. **Bollinger Exhaustion** (BB): Price interaction with upper Bollinger Band
4. **Volume Confirmation** (Optional): Above-average volume supporting the move

### Risk Management

- **Stop Loss**: ATR-based, typically 1.5× ATR above entry
- **Take Profit**: ATR-based, typically 1.0× ATR below entry
- **Position Sizing**: Based on account risk tolerance
- **Confluence Requirement**: Minimum 2-3 factors for signal validity

## 📈 Performance Analysis

### Key Metrics to Monitor

- **Hit Rate**: Percentage of signals reaching TP before SL
- **Average Bars to TP**: Time efficiency of signals
- **Risk/Reward Ratio**: Based on ATR multipliers
- **Confluence Impact**: Performance difference between BASE and STRONG signals

### Optimization Tips

1. **Backtest Period**: Use sufficient historical data (6+ months)
2. **Market Conditions**: Consider different market environments
3. **Parameter Sensitivity**: Test robustness across parameter ranges
4. **Commission Impact**: Include realistic trading costs

## ⚠️ Important Notes

### Risk Disclaimers

- **Educational Purpose**: These scripts are for educational and research purposes
- **No Financial Advice**: Not intended as investment recommendations
- **Risk Management**: Always use proper position sizing and risk controls
- **Market Risk**: Cryptocurrency markets are highly volatile and risky

### Technical Considerations

- **Data Quality**: Ensure clean price and volume data
- **Timeframe**: Scripts optimized for 1-hour timeframes
- **Market Hours**: Consider 24/7 crypto market characteristics
- **Slippage**: Account for execution differences in live trading

## 🔧 Customization

### Modifying Parameters

1. **Confluence Thresholds**: Adjust `minConf` and `strongConf` for signal frequency
2. **Risk Ratios**: Modify ATR multipliers for different risk profiles
3. **Timeframe Adaptation**: Adjust lookback periods for different timeframes
4. **Market Specific**: Customize parameters for specific cryptocurrency pairs

### Adding New Conditions

1. **New Indicators**: Add additional technical indicators to confluence calculation
2. **Market Structure**: Include support/resistance or market structure filters
3. **Fundamental Filters**: Add macro or fundamental analysis filters
4. **Time Filters**: Include session or time-based entry restrictions

## 📝 Version History

- **v2.3**: Enhanced alert formatting and confluence display
- **v1.3**: Added comprehensive outcome auditing
- **v6**: Updated to Pine Script version 6
- Current: All scripts use latest Pine Script v6 syntax

## 🤝 Contributing

Feel free to modify and enhance these scripts for your own trading research. Consider sharing improvements that could benefit the trading community.

---

**Disclaimer**: These tools are for educational purposes only. Trading cryptocurrencies carries significant risk. Always conduct your own research and consider consulting with financial professionals before making investment decisions.