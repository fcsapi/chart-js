# FCS API Chart - JavaScript

Advanced **JavaScript** charting library for **Forex**, **Cryptocurrency**, and **Stock** market data from [FCS API](https://fcsapi.com).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

## Features

- **Real-time Charts** - Live price updates via WebSocket
- **Multi-Market Support** - Forex, Crypto, and Stock data
- **60+ Technical Indicators** - RSI, MACD, Bollinger Bands, and more
- **Drawing Tools** - Trendlines, Fibonacci, shapes, and annotations
- **Multiple Chart Types** - Candlestick, OHLC, Line, Area, Heikin-Ashi
- **Customizable Themes** - Dark and Light themes
- **Responsive Design** - Works on desktop and mobile

## Installation

### CDN (Recommended)

```html
<!-- CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/fcsapi/chart-js/src/fcsapi-chart.css">

<!-- JavaScript -->
<script src="https://cdn.jsdelivr.net/gh/fcsapi/chart-js/src/fcsapi-chart.js"></script>
```

### Clone Repository

```bash
git clone https://github.com/fcsapi/chart-js.git
cd chart-js
```

### Local Files

```html
<link rel="stylesheet" href="src/fcsapi-chart.css">
<script src="src/fcsapi-chart.js"></script>
```

## Quick Start

```html
<!DOCTYPE html>
<html>
<head>
    <title>FCS Chart</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/fcsapi/chart-js/src/fcsapi-chart.css">
    <style>
        #fcs_chartparent { width: 100%; height: 100vh; }
    </style>
</head>
<body>
    <div id="fcs_chartparent">
        <div id="fcs_chart"></div>
    </div>

    <script src="https://cdn.jsdelivr.net/gh/fcsapi/chart-js/src/fcsapi-chart.js"></script>
    <script>
        const chart = new FCSAPIChart({
            container: document.getElementById('fcs_chart'),
            parentid: 'fcs_chartparent',
            accessKey: 'YOUR_API_KEY',
            symbol: 'BINANCE:BTCUSDT',
            period: '1H'
        });
    </script>
</body>
</html>
```

## Examples

| Example | Description |
|---------|-------------|
| [Simple Example](examples/simple.html) | Minimal setup - just 3 required settings |
| [Full Example](examples/index.html) | Complete chart with all configuration options |

## Configuration Options

### Required Settings

```javascript
const chart = new FCSAPIChart({
    container: document.getElementById('fcs_chart'),  // Chart container element
    parentid: 'fcs_chartparent',                      // Parent container ID
    accessKey: 'YOUR_API_KEY',                        // Your API access key
});
```

### Core Chart Settings

```javascript
{
    symbol: 'BINANCE:BTCUSDT',    // Default symbol (format: EXCHANGE:SYMBOL)
    period: '1H',                  // Timeframe: 1m, 5m, 15m, 30m, 1h, 4h, 1D, 1W, 1M
    length: 600,                   // Number of candles to load
    theme: 'dark',                 // 'dark' | 'light'
    defaultChartType: 'candlestick', // candlestick | bars | line | area | hollow | heikin-ashi
}
```

### WebSocket Settings

```javascript
{
    enableSocket: true,            // Enable live price updates
    socketApiKey: 'YOUR_SOCKET_KEY', // WebSocket API key
}
```

### UI Layout Toggles

```javascript
{
    displayMode: 'normal',         // 'normal' = full UI | 'chartonly' = chart only
    enableSidebar: true,           // Left sidebar with drawing tools
    enableToolbar: true,           // Top toolbar
    enableRangeSelector: true,     // Bottom time range selector
}
```

### Toolbar Controls

```javascript
{
    enableSearch: true,            // Symbol search
    enableIndicators: true,        // Indicators panel
    enableMultiChart: true,        // Multi-chart layouts
    enableReplay: true,            // Replay mode
    enableCapture: true,           // Screenshot/export
    enableUndoRedo: true,          // Undo/Redo (Ctrl+Z, Ctrl+Y)
    enableTemplates: true,         // Template save/load
    enableSettings: true,          // Settings panel
}
```

### Chart Features

```javascript
{
    enableContextMenu: true,       // Right-click context menu
    enableDrawingTools: true,      // Drawing tools
    enableGrid: false,             // Grid lines
    enableCrosshair: true,         // Crosshair on hover
    enablePriceLine: true,         // Current price line
    enableAskBidLines: false,      // Ask/Bid lines
    enableHighLowLabels: true,     // High/Low labels
    autoScale: true,               // Auto-scale price axis
    logScale: false,               // Logarithmic scale
}
```

### Color Settings

```javascript
{
    askLabelColor: '#00bcd4',      // Ask price label color
    bidLabelColor: '#ff9800',      // Bid price label color
    lastPriceLabelColor: null,     // Last price label (null = candle color)
}
```

### Timezone

```javascript
{
    timezone: 'local',             // 'local' | 'UTC' | '+05:00' | '-08:00'
}
```

## API Methods

### Symbol & Period

```javascript
chart.setSymbol('NASDAQ:AAPL');    // Change symbol
chart.setPeriod('4h');             // Change timeframe
```

### Theme & Chart Type

```javascript
chart.setTheme('light');           // 'dark' | 'light'
chart.setChartType('line');        // candlestick, bars, line, area, etc.
```

### Export

```javascript
chart.exportImage();               // Get chart as base64 image
```

### Resize & Cleanup

```javascript
chart.resize();                    // Recalculate after container resize
chart.destroy();                   // Remove chart and cleanup
```

### Horizontal Line API (for Brokers)

Add TP/SL/Entry price lines programmatically:

```javascript
// Add Take Profit line
const tpLine = await chart.addHorizontalLine({
    price: 45000,
    color: '#4caf50',
    label: 'TP',
    style: 'dashed'
});

// Add Stop Loss line
const slLine = await chart.addHorizontalLine({
    price: 42000,
    color: '#f44336',
    label: 'SL',
    style: 'dashed'
});

// Update line price
chart.updateHorizontalLine(tpLine, { price: 46000 });

// Remove line
chart.removeHorizontalLine(tpLine);

// Get all lines
const lines = chart.getHorizontalLines();

// Clear all lines
chart.clearHorizontalLines();
```

## Symbol Format

| Market | Format | Examples |
|--------|--------|----------|
| Forex | `FX:PAIR` | `FX:EURUSD`, `FX:GBPUSD` |
| Crypto | `EXCHANGE:PAIR` | `BINANCE:BTCUSDT`, `COINBASE:ETHUSD` |
| Stock | `EXCHANGE:SYMBOL` | `NASDAQ:AAPL`, `NYSE:TSLA` |

## Timeframes

| Period | Description |
|--------|-------------|
| `1m` | 1 minute |
| `5m` | 5 minutes |
| `15m` | 15 minutes |
| `30m` | 30 minutes |
| `1h` | 1 hour |
| `4h` | 4 hours |
| `1D` | 1 day |
| `1W` | 1 week |
| `1M` | 1 month |

## Chart Types

| Type | Description |
|------|-------------|
| `candlestick` | Japanese candlesticks |
| `bars` | OHLC bars |
| `line` | Line chart |
| `area` | Area chart |
| `hollow` | Hollow candlesticks |
| `heikin-ashi` | Heikin-Ashi candles |
| `high-low` | High-Low chart |
| `volume-candles` | Volume candles |

## Technical Indicators

The chart includes 60+ built-in technical indicators:

**Trend Indicators:**
- SMA, EMA, WMA, DEMA, TEMA
- Bollinger Bands, Keltner Channels
- Ichimoku Cloud, Parabolic SAR
- SuperTrend, ADX

**Oscillators:**
- RSI, Stochastic, MACD
- CCI, Williams %R, ROC
- Awesome Oscillator, CMO

**Volume Indicators:**
- OBV, Volume, VWAP
- Chaikin Money Flow, MFI
- Accumulation/Distribution

**Volatility:**
- ATR, Standard Deviation
- Bollinger Bandwidth

## File Structure

```
chart-js/
├── src/
│   ├── fcsapi-chart.js           # Main chart library
│   ├── fcsapi-chart.css          # Chart styles
│   └── chunks/                    # Lazy-loaded indicator modules
│       ├── indicator.technicals.*.js
│       ├── indicator.patterns.*.js
│       └── indicator.signals.*.js
├── examples/
│   ├── simple.html                # Simple example (minimal setup)
│   └── index.html                 # Full configuration example
├── README.md
└── LICENSE
```

## Get API Key

1. Visit [FCS API](https://fcsapi.com)
2. Sign up for a free account
3. Get your API key from the dashboard

## Documentation

- [FCS API Documentation](https://fcsapi.com/document)
- [Chart API Reference](https://fcsapi.com/document/stock-api#chart)

## Support

- Email: support@fcsapi.com
- Website: [fcsapi.com](https://fcsapi.com)

## License

MIT License - see [LICENSE](LICENSE) file for details.
