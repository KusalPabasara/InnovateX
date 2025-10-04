# Project Sentinel - Retail Intelligence System

## Overview

Project Sentinel is an advanced retail intelligence system designed for real-time fraud detection and operational optimization in self-checkout environments. The system integrates multiple data sources including RFID, POS transactions, computer vision, and queue monitoring to identify security threats and improve customer experience.

## Team

Team Gmora
- Pasindu Mihiranga
- Kusal Pabasara
- Thanoj Buddhima
- Kavinu Saputhanthri

## Key Features

### Fraud Detection
- Scanner avoidance detection using RFID-POS correlation
- Barcode switching identification through computer vision analysis
- Weight discrepancy monitoring for theft prevention
- Real-time alert system with confidence scoring

### Operational Intelligence
- Queue length monitoring and optimization
- Customer wait time analysis
- System health monitoring and crash detection
- Intelligent staffing recommendations
- Dynamic checkout station allocation

### Inventory Management
- Real-time inventory reconciliation
- Automated discrepancy detection
- Stock level monitoring with 10-minute intervals

## System Architecture

```
TeamGmora_sentinel/
├── src/                      Source code
│   ├── algorithms.py         Detection algorithms (10 tagged)
│   ├── config.py             Configuration settings
│   ├── data_loader.py        Data ingestion module
│   ├── event_engine.py       Event processing engine
│   ├── dashboard.py          Web dashboard server
│   └── main.py               CLI entry point
├── evidence/
│   ├── executables/
│   │   └── run_demo.py      Automated demo script
│   └── output/
│       ├── test/            Test dataset results
│       └── final/           Final dataset results
└── requirements.txt         Python dependencies
```

## Quick Start

### Prerequisites
- Python 3.9 or higher
- pip package manager

### Installation

Navigate to the executables directory and run the automated demo:

```bash
cd evidence/executables
python run_demo.py
```

The script will automatically:
1. Install required dependencies
2. Process input data from the data directory
3. Generate detection results
4. Create events.jsonl output file

### Manual Setup

```bash
pip install -r requirements.txt
cd src
python main.py --data-dir path/to/data --output events.jsonl
```

### Dashboard

Start the web dashboard to visualize results:

```bash
cd src
python dashboard.py --events-file ../evidence/output/final/events.jsonl
```

Access the dashboard at http://localhost:5000

## Detection Algorithms

The system implements 10 detection algorithms, each tagged for automated evaluation:

1. Scanner Avoidance Detection
2. Barcode Switching Detection
3. Weight Discrepancy Detection
4. Queue Length Monitoring
5. Wait Time Analysis
6. System Health Monitoring
7. Long Queue Detection
8. Inventory Discrepancy Detection
9. Staffing Optimization
10. Station Activation Logic

## Data Sources

The system processes seven heterogeneous data streams:

- RFID readings (JSONL format, 5-second intervals)
- Queue monitoring data (JSONL format, 5-second intervals)
- POS transactions (JSONL format, real-time)
- Product recognition analytics (JSONL format, real-time)
- Inventory snapshots (JSONL format, 10-minute intervals)
- Product catalog (CSV format)
- Customer database (CSV format)

## Output Format

All detected events are saved in JSONL format:

```json
{
  "timestamp": "2025-08-13T16:00:00",
  "event_id": "E001",
  "event_data": {
    "event_name": "Scanner Avoidance",
    "station_id": "SCC1",
    "customer_id": "C004",
    "product_sku": "PRD_S_04"
  }
}
```

## Dashboard Features

- Real-time event monitoring with automatic updates
- Interactive charts and analytics
- Event filtering and search
- Light and dark mode support
- Six tabbed views: Overview, Self-Checkout, Fraud Detection, Inventory, Analytics, and Insights
- Predictive analytics for future fraud risk assessment

## Configuration

Detection thresholds can be adjusted in `src/config.py`:

```python
THRESHOLDS = {
    "weight_tolerance_percent": 15,
    "product_recognition_confidence": 0.75,
    "queue_length_alert": 5,
    "wait_time_alert": 300
}
```

## Testing

Run unit tests to verify algorithm functionality:

```bash
cd src
python test_algorithms.py
```

## Performance Metrics

- Processing speed: 1000+ events per second
- Detection latency: Sub-100ms real-time processing
- Multi-source data synchronization
- Robust error handling and data validation

## Technical Stack

- Python 3.9+
- Flask for web dashboard
- Chart.js for visualizations
- Tailwind CSS and Daisy UI for interface
- JSONL for event storage

## License

This project was developed for the Project Sentinel Competition.

## Documentation

Additional documentation is available in:
- SUBMISSION_GUIDE.md - Competition submission details
- src/algorithms.py - Detailed algorithm documentation
- src/config.py - Configuration options
