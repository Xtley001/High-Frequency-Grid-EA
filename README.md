# High-Frequency-Grid-EA

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Platform](https://img.shields.io/badge/Platform-MetaTrader%205-orange.svg)
![Language](https://img.shields.io/badge/Language-MQL5-red.svg)
![Status](https://img.shields.io/badge/Status-Active-green.svg)

## 🚀 Overview

A sophisticated High-Frequency Trading (HFT) Expert Advisor designed for MetaTrader 5 that implements an advanced grid-based trading strategy with dynamic spread monitoring, intelligent order management, and adaptive trailing stop mechanisms.

**Author**: Christley Olubela (@Xtley001)  
**Version**: 1.00  
**Platform**: MetaTrader 5

## 📋 Table of Contents

- [Features](#features)
- [Strategy Overview](#strategy-overview)
- [Installation](#installation)
- [Configuration](#configuration)
- [Parameters](#parameters)
- [Risk Management](#risk-management)
- [Performance Optimization](#performance-optimization)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Disclaimer](#disclaimer)

## ✨ Features

### Core Functionality
- **Dynamic Spread Monitoring**: Real-time spread analysis with configurable limits
- **Time-Based Trading**: Customizable trading hours for optimal market conditions
- **Intelligent Order Management**: Automatic order placement, modification, and deletion
- **Adaptive Trailing Stops**: Dynamic trailing stop adjustments based on market movement
- **Multiple Lot Sizing Methods**: Fixed lots, percentage of balance, equity, or free margin
- **Grid-Based Strategy**: Systematic order placement with configurable distances

### Advanced Features
- **Commission Integration**: Automatic commission calculation in trade decisions
- **Broker Compatibility Check**: Validates broker suitability for HFT strategies
- **Memory Efficient**: Optimized array handling for spread history
- **Multi-Timeframe Support**: Configurable timing parameters
- **Position Averaging**: Intelligent position averaging for grid trades

## 🎯 Strategy Overview

### Core Strategy Logic

The EA implements a **Grid-Based Mean Reversion Strategy** with the following principles:

1. **Market Assumption**: Prices tend to revert to their mean over time
2. **Grid Placement**: Places buy stops above current price and sell stops below
3. **Dynamic Adjustment**: Continuously adjusts order levels based on market conditions
4. **Risk Control**: Uses trailing stops and position sizing to manage risk

### Entry Logic
- **Buy Orders**: Placed when price moves up, expecting continuation or reversal
- **Sell Orders**: Placed when price moves down, expecting continuation or reversal
- **Distance Management**: Orders placed at calculated distances based on spread and volatility

### Exit Logic
- **Trailing Stops**: Dynamic trailing stops that adapt to market movement
- **Time-Based Exits**: Orders cancelled outside trading hours
- **Spread-Based Exits**: Orders cancelled when spread exceeds limits

### Position Management
- **Position Averaging**: Adds to winning positions at calculated intervals
- **Risk Scaling**: Adjusts position sizes based on account equity and risk parameters
- **Order Modification**: Continuously updates order levels based on market conditions

## 🛠 Installation

1. **Download**: Clone or download the repository
   ```bash
   git clone https://github.com/Xtley001/High-Frequency-Grid-EA.git
   ```

2. **Copy Files**: Copy `High-Frequency Grid EA.mq5` to your MetaTrader 5 `Experts` folder:
   ```
   MetaTrader 5/MQL5/Experts/
   ```

3. **Compile**: Open MetaEditor and compile the EA

4. **Attach**: Drag and drop the EA onto your desired chart

## ⚙️ Configuration

### General Settings
- **Magic Number**: Unique identifier for EA trades (default: 12345)
- **Slippage**: Maximum acceptable slippage in points (default: 1)

### Time Settings
- **Start Hour**: Trading start time (default: 16:00)
- **End Hour**: Trading end time (default: 17:00)
- **Seconds**: Order modification interval (default: 60)

### Money Management
- **Lot Type**: Choose from Fixed, % of Balance, % of Equity, or % of Free Margin
- **Fixed Lot**: Fixed lot size when using fixed lots method (default: 0.01)
- **Risk Percent**: Risk percentage for dynamic lot sizing (default: 0.5%)

### Trade Settings
- **Delta**: Base order distance multiplier (default: 0.5)
- **Max Distance**: Maximum order placement distance (default: 7.0)
- **Stop**: Stop loss size multiplier (default: 10.0)
- **Max Trailing**: Trailing stop activation level (default: 4.0)
- **Max Spread**: Maximum allowed spread in points (default: 9999)

## 📊 Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `InpMagic` | int | 12345 | Magic number for trade identification |
| `StartHour` | int | 00 | Trading start hour (24h format) |
| `EndHour` | int | 23 | Trading end hour (24h format) |
| `LotType` | enum | 0 | Lot calculation method |
| `FixedLot` | double | 1 | Fixed lot size |
| `RiskPercent` | double | 0.5 | Risk percentage for dynamic lots |
| `Delta` | double | 0.5 | Order distance multiplier |
| `MaxDistance` | double | 7.0 | Maximum order distance |
| `Stop` | double | 10.0 | Stop loss multiplier |
| `MaxTrailing` | double | 4.0 | Trailing stop activation |
| `MaxSpread` | int | 9999 | Maximum spread limit |

## 🛡️ Risk Management

### Built-in Risk Controls
- **Position Sizing**: Automatic lot calculation based on account size
- **Spread Filtering**: Trades only when spreads are within acceptable limits
- **Time Filtering**: Restricts trading to specified hours
- **Trailing Stops**: Dynamic stop loss adjustment for profit protection
- **Margin Checks**: Validates sufficient margin before placing orders

### Recommended Settings
- **Conservative**: Risk 0.5-1% per trade, tight spread limits
- **Moderate**: Risk 1-2% per trade, moderate spread limits
- **Aggressive**: Risk 2-5% per trade, wider spread limits

⚠️ **Warning**: This EA uses a grid strategy which can lead to significant drawdowns. Always test on demo accounts first.

## 🔧 Performance Optimization

### For Best Results
- **Low Latency VPS**: Use a VPS close to your broker's servers
- **ECN/STP Brokers**: Choose brokers with tight spreads and fast execution
- **Major Pairs**: Focus on liquid currency pairs (EUR/USD, GBP/USD, USD/JPY)
- **Proper Timing**: Trade during high-volume market hours

### Monitoring
- **Spread Conditions**: Monitor average spreads during trading hours
- **Execution Quality**: Check for slippage and requotes
- **Drawdown Levels**: Monitor maximum drawdown periods

## 🐛 Troubleshooting

### Common Issues

**EA Not Trading**
- Check trading hours settings
- Verify spread limits
- Ensure sufficient margin
- Confirm broker allows automated trading

**High Spread Errors**
- Adjust `MaxSpread` parameter
- Check broker's spread conditions
- Consider trading during high-volume hours

**Order Modification Errors**
- Verify broker allows order modifications
- Check minimum distance requirements
- Ensure orders are not too close to market

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

### Development Guidelines
- Follow MQL5 coding standards
- Test all changes on demo accounts
- Document new features and parameters
- Maintain backward compatibility

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

**IMPORTANT**: This EA is for educational and research purposes. Trading involves substantial risk of loss and may not be suitable for all investors. Past performance does not guarantee future results.

- Always test on demo accounts first
- Never risk more than you can afford to lose
- Understand the strategy before using real money
- Monitor your trades regularly
- Keep your MetaTrader platform updated

## 📞 Support

For support, questions, or suggestions:
- **GitHub Issues**: [Create an issue](https://github.com/Xtley001/High-Frequency-Grid-EA/issues)
- **Twitter**: [@xtley001](https://x.com/xtley001)
- **Email**: olubelachristley@gmail.com

## 🙏 Acknowledgments

- MetaQuotes for the MQL5 platform
- The trading community for strategy insights
- Beta testers and contributors

---

**Happy Trading! 📈**

*Remember: The best strategy is the one you understand and can manage effectively.*
