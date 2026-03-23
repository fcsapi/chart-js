# FCS Chart - Free JavaScript Financial Charting Library

Lightweight, high-performance **JavaScript charting library** for building interactive **financial charts** — **Forex charts**, **cryptocurrency charts**, and **stock market charts** with **real-time data**, **60+ technical indicators**, and **advanced drawing tools**. A powerful open-source **TradingView alternative** for web developers and brokers.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![CDN](https://img.shields.io/badge/CDN-jsDelivr-blue.svg)](https://www.jsdelivr.com/package/gh/fcsapi/chart-js)

> Build professional trading charts for your website, trading platform, or broker application with just a few lines of code. No frameworks required — works with vanilla JavaScript, React, Vue, Angular, or any web stack.

## Why FCS Chart?

| Feature | FCS Chart | Other Libraries |
|---------|-----------|-----------------|
| Real-time WebSocket data | Yes | Often paid/separate |
| 60+ Technical indicators | Built-in | Limited or plugin-based |
| Drawing tools (Fibonacci, Trendlines) | Built-in | Rarely included |
| Forex + Crypto + Stocks | All-in-one | Usually single market |
| Mobile responsive | Yes | Varies |
| Bundle size | Lightweight | Often heavy |
| Pricing | Free / MIT License | Often commercial |

## Features

- **Real-time Trading Charts** — Live candlestick price updates via WebSocket connection
- **Multi-Market Data** — Forex currency pairs, cryptocurrency (Bitcoin, Ethereum, etc.), and stock market data (NASDAQ, NYSE)
- **60+ Technical Analysis Indicators** — RSI, MACD, Bollinger Bands, EMA, SMA, Ichimoku Cloud, Stochastic, ATR, VWAP, and more
- **Professional Drawing Tools** — Trendlines, Fibonacci retracement, horizontal lines, shapes, text annotations, and XABCD patterns
- **8 Chart Types** — Candlestick, OHLC bars, Line, Area, Heikin-Ashi, Hollow candles, High-Low, Volume candles
- **Dark & Light Themes** — Customizable color schemes for any UI
- **Responsive Design** — Optimized for desktop, tablet, and mobile browsers
- **Multi-Chart Layouts** — Display multiple charts side by side with different symbols or timeframes
- **Chart Replay Mode** — Replay historical price action for backtesting strategies
- **Screenshot & Export** — Export charts as images for reports and sharing
- **Broker Integration** — Add TP/SL/Entry price lines programmatically via API
- **Undo/Redo Support** — Full undo/redo for all drawing operations (Ctrl+Z, Ctrl+Y)
- **Keyboard Shortcuts** — Professional keyboard shortcut support
- **Timezone Support** — Local, UTC, or custom timezone offsets
- **No Dependencies** — Pure JavaScript, no jQuery or external frameworks required

## Demo

See the live chart in action: [FCS API Chart Demo](https://fcsapi.com/crypto-chart)

## Installation

### CDN (Recommended)

The fastest way to get started — add two lines to your HTML:

```html
<!-- FCS Chart CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/fcsapi/chart-js@latest/src/fcsapi-chart.css">

<!-- FCS Chart JavaScript -->
<script src="https://cdn.jsdelivr.net/gh/fcsapi/chart-js@latest/src/fcsapi-chart.js"></script>
```

### Pin a Specific Version

| Version | Status |
|---------|--------|
| `@latest` | Recommended — always up to date |
| `@4.0.3` | Current stable release |
| `@4.0.2` | Previous stable |
| `@4.0.1` | Previous stable |

```html
<!-- Pin to version 4.0.3 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/fcsapi/chart-js@4.0.3/src/fcsapi-chart.css">
<script src="https://cdn.jsdelivr.net/gh/fcsapi/chart-js@4.0.3/src/fcsapi-chart.js"></script>
```

### Install via Git

```bash
git clone https://github.com/fcsapi/chart-js.git
cd chart-js
```

### Self-Hosted / Local Files

```html
<link rel="stylesheet" href="src/fcsapi-chart.css">
<script src="src/fcsapi-chart.js"></script>
```

## Quick Start — Create Your First Chart

Get a chart running in under 2 minutes:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Trading Chart</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/fcsapi/chart-js@latest/src/fcsapi-chart.css">
    <style>
        #fcs_chartparent { width: 100%; height: 100vh; }
    </style>
</head>
<body>
    <div id="fcs_chartparent">
        <div id="fcs_chart"></div>
    </div>

    <script src="https://cdn.jsdelivr.net/gh/fcsapi/chart-js@latest/src/fcsapi-chart.js"></script>
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
| [Simple Chart](examples/simple.html) | Minimal setup — just 3 required settings to render a chart |
| [Full Configuration](examples/index.html) | Complete trading chart with all configuration options |

## Configuration Reference

### Required Settings

Only 3 settings are required to create a chart:

```javascript
const chart = new FCSAPIChart({
    container: document.getElementById('fcs_chart'),  // Chart container element
    parentid: 'fcs_chartparent',                      // Parent container ID
    accessKey: 'YOUR_API_KEY',                        // Get free key at fcsapi.com
});
```

### Chart Settings

```javascript
{
    symbol: 'BINANCE:BTCUSDT',      // Symbol to display (format: EXCHANGE:SYMBOL)
    period: '1H',                    // Timeframe: 1m, 5m, 15m, 30m, 1h, 4h, 1D, 1W, 1M
    length: 600,                     // Number of candles to load
    theme: 'dark',                   // 'dark' | 'light'
    defaultChartType: 'candlestick', // candlestick | bars | line | area | hollow | heikin-ashi
}
```

### Real-time WebSocket Settings

```javascript
{
    enableSocket: true,              // Enable live price updates
    socketApiKey: 'YOUR_SOCKET_KEY', // WebSocket API key
}
```

### UI & Layout Options

```javascript
{
    displayMode: 'normal',           // 'normal' = full UI | 'chartonly' = embeddable chart only
    enableSidebar: true,             // Left sidebar with drawing tools
    enableToolbar: true,             // Top toolbar with controls
    enableRangeSelector: true,       // Bottom time range selector
}
```

### Toolbar Controls

```javascript
{
    enableSearch: true,              // Symbol search bar
    enableIndicators: true,          // Technical indicators panel
    enableMultiChart: true,          // Multi-chart layout selector
    enableReplay: true,              // Historical replay mode
    enableCapture: true,             // Screenshot & image export
    enableUndoRedo: true,            // Undo/Redo (Ctrl+Z, Ctrl+Y)
    enableTemplates: true,           // Save/load chart templates
    enableSettings: true,            // Settings panel
}
```

### Chart Features

```javascript
{
    enableContextMenu: true,         // Right-click context menu
    enableDrawingTools: true,        // Drawing & annotation tools
    enableGrid: false,               // Grid lines
    enableCrosshair: true,           // Crosshair on hover
    enablePriceLine: true,           // Current price line
    enableAskBidLines: false,        // Ask/Bid price lines
    enableHighLowLabels: true,       // High/Low price labels
    autoScale: true,                 // Auto-scale price axis
    logScale: false,                 // Logarithmic price scale
}
```

### Color Customization

```javascript
{
    askLabelColor: '#00bcd4',        // Ask price label color
    bidLabelColor: '#ff9800',        // Bid price label color
    lastPriceLabelColor: null,       // Last price label (null = candle color)
}
```

### Timezone Configuration

```javascript
{
    timezone: 'local',               // 'local' | 'UTC' | '+05:00' | '-08:00'
}
```

## API Methods

### Change Symbol & Timeframe

```javascript
chart.setSymbol('NASDAQ:AAPL');      // Switch to Apple stock
chart.setSymbol('FX:EURUSD');        // Switch to EUR/USD forex pair
chart.setSymbol('BINANCE:ETHUSDT');  // Switch to Ethereum
chart.setPeriod('4h');               // Change to 4-hour timeframe
```

### Theme & Chart Type

```javascript
chart.setTheme('light');             // Switch to light theme
chart.setChartType('line');          // Switch to line chart
chart.setChartType('candlestick');   // Switch to candlestick chart
```

### Export Chart as Image

```javascript
const imageData = chart.exportImage(); // Returns base64 image string
```

### Resize & Cleanup

```javascript
chart.resize();                      // Recalculate after container resize
chart.destroy();                     // Remove chart and free memory
```

### Horizontal Line API — For Brokers & Trading Platforms

Programmatically add Take Profit, Stop Loss, and entry price lines:

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

// Update line price (e.g., drag TP/SL)
chart.updateHorizontalLine(tpLine, { price: 46000 });

// Remove a specific line
chart.removeHorizontalLine(tpLine);

// Get all horizontal lines
const lines = chart.getHorizontalLines();

// Clear all lines
chart.clearHorizontalLines();
```

## Supported Markets & Symbol Format

| Market | Format | Examples |
|--------|--------|----------|
| **Forex** | `FX:PAIR` | `FX:EURUSD`, `FX:GBPUSD`, `FX:USDJPY`, `FX:AUDUSD` |
| **Crypto** | `EXCHANGE:PAIR` | `BINANCE:BTCUSDT`, `BINANCE:ETHUSDT`, `COINBASE:ETHUSD` |
| **Stocks** | `EXCHANGE:SYMBOL` | `NASDAQ:AAPL`, `NASDAQ:TSLA`, `NASDAQ:GOOGL`, `NYSE:MSFT` |

## Supported Timeframes

| Period | Description |
|--------|-------------|
| `1m` | 1 Minute chart |
| `5m` | 5 Minute chart |
| `15m` | 15 Minute chart |
| `30m` | 30 Minute chart |
| `1h` | 1 Hour chart |
| `4h` | 4 Hour chart |
| `1D` | Daily chart |
| `1W` | Weekly chart |
| `1M` | Monthly chart |

## Chart Types

| Type | Description |
|------|-------------|
| `candlestick` | Japanese candlestick chart |
| `bars` | OHLC bar chart |
| `line` | Line chart |
| `area` | Area / Mountain chart |
| `hollow` | Hollow candlestick chart |
| `heikin-ashi` | Heikin-Ashi smoothed candles |
| `high-low` | High-Low range chart |
| `volume-candles` | Volume-weighted candle chart |

## Technical Indicators (60+)

Full list of built-in technical analysis indicators for trading:

**Trend Indicators:**
SMA (Simple Moving Average), EMA (Exponential Moving Average), WMA (Weighted Moving Average), DEMA (Double EMA), TEMA (Triple EMA), Bollinger Bands, Keltner Channels, Ichimoku Cloud, Parabolic SAR, SuperTrend, ADX (Average Directional Index)

**Oscillators:**
RSI (Relative Strength Index), Stochastic Oscillator, MACD (Moving Average Convergence Divergence), CCI (Commodity Channel Index), Williams %R, ROC (Rate of Change), Awesome Oscillator, CMO (Chande Momentum Oscillator)

**Volume Indicators:**
OBV (On Balance Volume), Volume, VWAP (Volume Weighted Average Price), Chaikin Money Flow, MFI (Money Flow Index), Accumulation/Distribution Line

**Volatility Indicators:**
ATR (Average True Range), Standard Deviation, Bollinger Bandwidth

## Drawing Tools

Professional-grade drawing and annotation tools:

- **Lines** — Trendlines, horizontal lines, vertical lines, ray lines
- **Fibonacci** — Fibonacci retracement, extension, fan, arcs, time zones
- **Patterns** — XABCD harmonic patterns
- **Shapes** — Rectangle, ellipse, triangle
- **Text & Labels** — Text annotations, price labels, callouts
- **Measurement** — Price range, date range, price & date range

## Use Cases

- **Trading Platforms** — Embed professional charts in your web-based trading platform
- **Broker Websites** — Add interactive financial charts with TP/SL line support
- **Crypto Dashboards** — Real-time Bitcoin, Ethereum, and altcoin price charts
- **Forex Portals** — Live currency pair charts with technical analysis tools
- **Stock Market Apps** — Interactive stock charts with indicators for financial websites
- **Financial News Sites** — Embed responsive charts alongside market news
- **Education & Research** — Teaching technical analysis with interactive chart tools
- **Portfolio Trackers** — Visualize asset performance with historical charts

## Project Structure

```
chart-js/
├── src/
│   ├── fcsapi-chart.js              # Main chart library
│   ├── fcsapi-chart.css             # Chart styles
│   └── chunks/                       # Lazy-loaded modules (loaded on demand)
│       ├── indicator.technicals.*.js # Technical indicator calculations
│       ├── indicator.patterns.*.js   # Pattern recognition modules
│       └── indicator.signals.*.js    # Signal generation modules
├── examples/
│   ├── simple.html                   # Simple example (minimal setup)
│   └── index.html                    # Full configuration example
├── README.md
└── LICENSE
```

## Get Your Free API Key

1. Visit [FCS API](https://fcsapi.com)
2. Create a free account
3. Copy your API key from the dashboard
4. Start building charts!

## Documentation & Resources

- [FCS API Documentation](https://fcsapi.com/document) — Full API reference
- [Chart API Guide](https://fcsapi.com/document/stock-api#chart) — Chart-specific documentation
- [FCS API Dashboard](https://fcsapi.com/dashboard) — Manage your API keys

## Browser Support

| Browser | Version |
|---------|---------|
| Chrome | 60+ |
| Firefox | 55+ |
| Safari | 12+ |
| Edge | 79+ |
| Mobile Chrome | 60+ |
| Mobile Safari | 12+ |

## Support & Community

- **Email:** support@fcsapi.com
- **Website:** [fcsapi.com](https://fcsapi.com)
- **Issues:** [GitHub Issues](https://github.com/fcsapi/chart-js/issues)

## Keywords

`javascript chart library`, `financial chart`, `trading chart`, `stock chart`, `forex chart`, `crypto chart`, `candlestick chart`, `technical analysis`, `real-time chart`, `websocket chart`, `TradingView alternative`, `open source chart`, `OHLC chart`, `bitcoin chart`, `market data visualization`, `broker chart widget`, `embeddable chart`, `lightweight chart`, `charting library`, `interactive chart`

## License

MIT License — see [LICENSE](LICENSE) file for details.

Free to use in personal and commercial projects.
