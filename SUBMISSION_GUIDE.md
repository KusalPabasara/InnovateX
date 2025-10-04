# Submission Guide

Complete this template before zipping your submission. Keep the file at the
project root.

## Team details
- Team name: Gmora
- Members: Pasindu Mihiranga, Kusal Pabasara, Thanoj Buddhima, Kavinu Saputhanthri
- Primary contact email: ipamihir2003@gmail.com

## Judge run command
Judges will `cd evidence/executables/` and run **one command** on Ubuntu 24.04:

```
python3 run_demo.py
```

The script will:
1. Install dependencies (Flask, flask-cors, Werkzeug)
2. Locate the data/input directory automatically
3. Copy source code from ../../src/
4. Run all 9 detection algorithms
5. Generate events.jsonl and summary.json in ./results/
6. Display summary statistics

**Note:** The script expects data to be available at ../../../../data/input (or similar relative paths from evidence/executables/).

## Output Location
All artifacts are written to `evidence/executables/results/`:
- `results/events.jsonl` - All detected events (sorted by timestamp)
- `results/summary.json` - Summary statistics and breakdowns

## Dashboard
To view the dashboard after running the demo:
```bash
cd ../../src
python3 dashboard.py ../evidence/executables/results/events.jsonl
```
Then access: http://localhost:5000

## Checklist before zipping and submitting
- Algorithms tagged with `# @algorithm Name | Purpose` comments: ✅ YES - All 9 algorithms properly tagged
- Evidence artefacts present in `evidence/`: ✅ YES
  - screenshots/ - Dashboard screenshots
  - output/test/events.jsonl - Test dataset results
  - output/final/events.jsonl - Final dataset results (to be generated)
  - executables/run_demo.py - Automated runner script
- Source code complete under `src/`: ✅ YES
  - main.py - CLI entry point
  - event_engine.py - Processing engine
  - algorithms.py - 9 tagged algorithms
  - data_loader.py - Data ingestion
  - config.py - Configuration
  - dashboard.py - Web UI and APIs
