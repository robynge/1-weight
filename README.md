# ARK ETF Small Position Analysis

A comprehensive Python analysis framework for tracking and analyzing small positions (<1% weight) in ARK Invest ETFs.

## Overview

This project analyzes small positions in ARK ETFs to understand:
- Performance of positions under different weight thresholds
- Success rates of starter positions (new small entries)
- Recovery patterns of residual positions (fallen from larger weights)
- P&L contribution of various position categories

## Features

### Analysis Modules
- **Starter/Residual Analysis**: Identifies and tracks starter vs residual positions
- **P&L Analysis**: Calculates profit/loss for positions in specified weight ranges
- **Position Distribution**: Tracks position counts across weight ranges over time
- **Market Value Analysis**: Monitors market value allocation to small positions
- **Alternative Returns**: Compares ETF performance with/without small positions
- **Graduation Analysis**: Tracks positions that successfully grow from small to large

### Visualization
- P&L pie charts showing top contributors
- Daily and cumulative P&L line charts
- Market value trends over time
- Position distribution charts
- Alternative return comparisons

## Installation

1. Clone the repository:
```bash
git clone https://github.com/[your-username]/ark-etf-analysis.git
cd ark-etf-analysis
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

## Usage

### Basic Usage

Run the interactive menu:
```bash
cd code
python main.py
```

### Menu Options
- **0-4**: Run individual analysis modules
- **A**: Run all analyses for current weight range
- **B**: Batch process all weight ranges
- **R**: Select weight range (<1%, 1-2.5%, 2.5-5%, 5-7.5%, >7.5%)
- **D**: Select ETF data files

### Quick Run
Run all analyses for default weight range (<1%):
```bash
python main.py --all
```

Batch process all weight ranges:
```bash
python main.py --batch
```

## Data Requirements

Place ARK ETF historical data files in the project root directory:
- Format: `ARKX_historical data_YYYYMMDD.xlsx`
- Required columns: Date, Bloomberg Name, Company_Name, Position, Stock_Price, Weight, Market Value

## Output Structure

```
analysis_results/
├── 00_Starter_Residual_[range]/    # Starter/residual analysis
├── 01_PnL_Analysis_[range]/        # P&L calculations and charts
├── 02_Position_Analysis_[range]/    # Position distribution data
├── 02_Market_Value_Analysis_[range]/# Market value analysis
├── 03_Alternative_Returns_[range]/  # Alternative return comparisons
└── 04_Graduation_Analysis_[range]/  # Graduation tracking
```

## Key Findings

- **79.2%** of starter positions successfully graduate to >1% weight
- **87.8%** of residual positions recover to >1% weight
- Average incubation period: ~817 days for starters
- Technology/software stocks show highest graduation rates

## Configuration

Edit `config.py` to customize:
- Weight range thresholds
- Output directories
- Analysis parameters

## License

MIT License - See LICENSE file for details

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Disclaimer

This tool is for research and educational purposes only. Not financial advice.