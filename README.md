# CCD Events Monitor

Provide two API endpoints. One to record CCD events and one to get all CCD events.

![alt text](image.png)     

A professional, real-time HMI (Human-Machine Interface) web application for monitoring and visualizing CCD (Charge-Coupled Device) inspection events in industrial production environments.


## 🎯 Overview

The CCD Events Monitor provides a modern, business-professional interface for tracking quality control events from multiple CCD systems. It features synchronized timeline visualizations, real-time data updates, and comprehensive event tracking to help operators and engineers monitor production quality at a glance.

## ✨ Key Features

### 📊 Real-Time Monitoring
- **Auto-refresh every 5 seconds** from your data pipeline
- **Live status indicators** showing system health and event count
- **Configurable data endpoint** with bearer token authentication support

### 🎨 Visual Timeline
- **Synchronized multi-timeline view** when monitoring multiple CCD sources
- **Solid colored segments** (green for OK, red for NOK) showing event results
- **Shared X-axis** with encoder values for easy cross-system comparison
- **Interactive tooltips** with detailed event information

### 📈 Statistics Dashboard
- **Per-CCD metrics**: Total events, OK count, NOK count, success rate
- **Horizontal status bars** showing OK/NOK ratio at a glance
- **Comprehensive event tables** with filtering and sorting

### ⚙️ Flexible Configuration
- **CCD source selector** - view all sources or filter by specific CCD
- **Configurable base URL** and endpoint path
- **HTTP method selection** (POST/GET)
- **Optional bearer token authentication**
- **Settings persistence** via localStorage

## 🚀 Getting Started

### Prerequisites

- A web browser (Chrome, Firefox, Edge, Safari)
- Access to a data pipeline endpoint that provides CCD events

### Installation

1. Clone the repository:
```bash
git clone https://github.com/gangsterke/CCD-event-reporting-Monitoring-using-API-endpoints-with-HighByte.git
```

2. Open `ccd-events-hmi.html` in your web browser:
```bash
start ccd-events-hmi.html
```

3. Configure your data source in the application settings.

### Configuration

1. Click on **⚙️ Configuration** to expand the settings panel
2. Set your **Base URL** (default: `http://127.0.0.1:8885`)
3. Set the **Endpoint Path** (default: `/data/v1/pipelines/getCCDEvents/value`)
4. Select **HTTP Method** (POST or GET)
5. Add a **Bearer Token** if your endpoint requires authentication
6. Settings are automatically saved to your browser

## 📋 Data Format

The application expects JSON data in the following format:

```json
[
  {
    "encoderValue": 92,
    "result": "OK",
    "NOKReason": "001",
    "timestamp": "2025-12-06 12:57:58.710 UTC",
    "CCDsource": "CCD1"
  },
  {
    "encoderValue": 108,
    "result": "NOK",
    "NOKReason": "002",
    "timestamp": "2025-12-06 12:58:33.618 UTC",
    "CCDsource": "CCD2"
  }
]
```

### Field Descriptions

| Field | Type | Description |
|-------|------|-------------|
| `encoderValue` | Number | Position/index of the inspected item |
| `result` | String | Inspection result: "OK" or "NOK" |
| `NOKReason` | String | Reason code for failed inspections |
| `timestamp` | String | ISO 8601 timestamp of the event |
| `CCDsource` | String | Identifier for the CCD system (e.g., "CCD1", "CCD2") |

## 🎨 Features in Detail

### Timeline Visualization

The timeline shows events as colored segments:
- **Green segments**: Successful inspections (OK)
- **Red segments**: Failed inspections (NOK)
- **Horizontal layout**: Encoder values on X-axis
- **Synchronized views**: Multiple CCDs aligned for comparison

### CCD Source Selection

Use the dropdown to:
- View **All CCD Sources** with synchronized timelines
- Filter by **specific CCD** for focused analysis
- Automatically populates based on available data

### Event Tables

Each CCD panel includes a detailed table showing:
- Encoder value
- Result (OK/NOK badge)
- NOK reason code
- Formatted timestamp
- Sorted by most recent events first

### Status Overview

Quick statistics at the top of each panel:
- **Total**: Number of events recorded
- **OK**: Count of successful inspections
- **NOK**: Count of failed inspections
- **Success Rate**: Percentage of OK events

## 🔧 API Integration

### Endpoint Requirements

Your data endpoint should:
- Accept POST or GET requests
- Return JSON array of event objects
- Support optional bearer token authentication
- Respond within reasonable time (< 2 seconds recommended)

### Example cURL Request

```bash
# POST request
curl -X POST http://127.0.0.1:8885/data/v1/pipelines/getCCDEvents/value \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN_HERE" \
  -d '{}'

# GET request
curl -X GET http://127.0.0.1:8885/data/v1/pipelines/getCCDEvents/value \
  -H "Authorization: Bearer YOUR_TOKEN_HERE"
```

## 🛠️ Customization

### Changing Refresh Rate

Edit the `REFRESH_RATE` constant in the HTML file (default: 5000ms):

```javascript
const REFRESH_RATE = 5000; // 5 seconds
```

### Styling

The application uses a modern gradient color scheme. To customize:

1. Locate the CSS section in `ccd-events-hmi.html`
2. Modify color variables:
```css
/* Header gradient */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* OK color */
background: #48bb78;

/* NOK color */
background: #f56565;
```


## 🐛 Troubleshooting


## 👥 Authors


**Built with ❤️ for industrial quality control**