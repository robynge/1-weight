# ARK ETF Dynamic Weight Range Analysis - Modular Code System

This project analyzes ARK Invest ETF positions across configurable weight ranges, tracking their performance and P&L outcomes over time.

## Overview

The analysis identifies and tracks positions in ARK ETFs across 5 configurable weight ranges:
- **<1%**: Ultra-small positions
- **1-2.5%**: Small positions
- **2.5-5%**: Medium positions  
- **5-7.5%**: Large positions
- **>7.5%**: Very large positions

Key analysis features:
- **Starter Positions**: New stocks entering the portfolio within weight range
- **Residual Positions**: Stocks that fell from higher to lower weight ranges
- **P&L Analysis**: Profit and loss tracking for positions in selected range
- **Position Evolution**: Time series tracking and distribution visualization
- **Graduation Analysis**: Track positions that move to higher weight tiers

## 📁 Project Structure

```
1 percent v4/
├── code/                           # All analysis scripts
│   ├── main.py                    # Master script with weight range selection
│   ├── config.py                  # Weight range configuration
│   ├── data_config.py             # Data file paths
│   ├── 00_starter_residual_analysis.py  # Identify starter/residual positions
│   ├── 01_calculate_pnl.py        # Calculate P&L for positions in range
│   ├── 02_plot_position_trends.py # Position trends + stacked distribution charts
│   ├── 03_plot_pnl_pie.py        # Generate P&L pie charts
│   ├── 04_plot_pnl_line.py       # Generate P&L line charts
│   ├── 05_create_pnl_tables.py   # Generate P&L tables
│   ├── 06_plot_market_value.py   # Market value analysis
│   ├── 07_calculate_alternative_returns.py # Alternative returns analysis
│   └── 08_graduation_analysis.py # Graduation performance tracking
├── analysis_results_{range}/      # Output folders per weight range
└── *.xlsx                        # ETF historical data files
```

## 🚀 Quick Start

### Run for Single Weight Range
```bash
cd code
python main.py --all  # Runs all modules for default (<1%) range
```

### Run for All Weight Ranges (Batch)
```bash
python main.py --batch  # Runs all modules for all 5 weight ranges
```

### Interactive Mode
```bash
python main.py  # Opens menu to select weight range and modules
```

## 📊 Analysis Modules

### Module 00: Starter/Residual Analysis
```bash
python 00_starter_residual_analysis.py
```
- Identifies starter positions (new entries <1%)
- Identifies residual positions (fell from >1% to <1%)
- Tracks reappeared positions
- Outputs: Excel files with position classifications

### Module 01: P&L Calculation
```bash
python 01_calculate_pnl.py
```
- Calculates daily and cumulative P&L for <1% positions
- Tracks position-level profit/loss
- Outputs: `ARKX_PnL_Data.xlsx` for each ETF

### Module 02: Position Trend Charts
```bash
python 02_plot_position_trends.py
```
- Creates time series charts showing position counts in selected weight range
- **NEW**: Generates stacked area charts showing distribution across ALL weight tiers
- Outputs: 
  - Individual position trend charts for selected range
  - Stacked area distribution charts (always shows all 5 tiers)

### Module 03: P&L Pie Charts
```bash
python 03_plot_pnl_pie.py
```
- Shows top 10 P&L contributors for each ETF
- Color-coded by ETF with gradient effects
- Outputs: Individual and combined pie charts

### Module 04: P&L Line Charts
```bash
python 04_plot_pnl_line.py
```
- Tracks cumulative P&L over time
- Shows performance trends from 2020-2024
- Outputs: Time series P&L charts

### Module 05: P&L Tables
```bash
python 05_create_pnl_tables.py
```
- Creates detailed tables matching pie chart data
- Shows top 10 P&L contributors + "Others" category
- Includes percentage breakdowns and rankings
- Outputs: 
  - Individual ETF tables (`ARKX_PnL_Table.xlsx`)
  - Combined summary (`All_ETFs_PnL_Tables.xlsx`)

### Module 06: Market Value Analysis
```bash
python 06_plot_market_value.py
```
- Analyzes market value of positions in weight range
- Tracks total market value over time
- Outputs: Market value trend charts

### Module 07: Alternative Returns Analysis
```bash
python 07_calculate_alternative_returns.py
```
- Calculates returns if only holding positions in weight range
- Compares to actual ETF returns
- Outputs: Dual panel charts (weekly + cumulative returns)

### Module 08: Graduation Analysis
```bash
python 08_graduation_analysis.py
```
- Tracks positions that "graduate" to higher weight tiers
- Analyzes post-graduation performance
- Calculates graduation success rates
- Outputs: Graduation analysis Excel reports

## 📈 Key Findings

### Overall Performance
- **79.2%** of starter positions successfully graduate to >1% weight
- **87.8%** of residual positions recover to >1% weight
- Average incubation period: ~817 days for starters

### ETF Performance Ranking (by success rate)
1. **ARKQ** - 86.0% (Autonomous & Robotics, most efficient)
2. **ARKW** - 84.0% (Internet & Software)
3. **ARKK** - 81.7% (Flagship Innovation)
4. **ARKG** - 76.0% (Genomics, achieves highest max weight 4.06%)
5. **ARKF** - 63.3% (Fintech, affected by currency positions)

### P&L Performance Summary
| ETF  | Total P&L | Worst Performer | Loss |
|------|-----------|-----------------|------|
| ARKF | -$225.7M  | BASE Inc | -$21.8M |
| ARKG | -$1,164.9M | BUTTERFLY NETWORK | -$108.6M |
| ARKK | -$2,849.6M | Materialise NV | -$217.5M |
| ARKQ | -$272.0M | Vuzix Corp | -$33.0M |
| ARKW | -$662.5M | Nano Dimension Ltd | -$66.6M |
| **TOTAL** | **-$5,174.6M** | | |

### Key Insights
- All ETFs show negative cumulative P&L from <1% positions
- Peak performance occurred around 2021, followed by significant declines
- Technology/software stocks show highest graduation rates
- Biotech positions require patience but achieve highest weights

## 📋 Output Files

Outputs are organized by weight range in separate folders:

### Folder Structure
- `analysis_results/PnL_Analysis_under_1pct/` - For <1% range
- `analysis_results/PnL_Analysis_1_to_2.5pct/` - For 1-2.5% range
- `analysis_results/PnL_Analysis_2.5_to_5pct/` - For 2.5-5% range
- `analysis_results/PnL_Analysis_5_to_7.5pct/` - For 5-7.5% range
- `analysis_results/PnL_Analysis_over_7.5pct/` - For >7.5% range

### Key Output Files
- `{ETF}_PnL_Data.xlsx` - Detailed P&L data
- `{ETF}_{range}_Positions_Chart.png` - Position count trends
- `{ETF}_Position_Distribution_Stacked.png` - **NEW**: Distribution across all tiers
- `{ETF}_Alternative_Returns.png` - Alternative returns analysis
- `{ETF}_Market_Value.png` - Market value trends
- Graduation analysis reports and summary tables

## 🛠️ Requirements

```bash
pip install pandas numpy openpyxl matplotlib seaborn
```

## 📝 Data Quality Notes

The analysis includes automatic detection and correction for:
- Stock split data anomalies (e.g., SHOP on 2022-06-29)
- Erroneous 100% weight values for individual stocks
- Mixed decimal/percentage format handling
- Exclusion of cash equivalents and money market funds

## 🔄 Module Execution Order

When running individual modules, follow this order:
1. `00_starter_residual_analysis.py` (optional - for classification)
2. `01_calculate_pnl.py` (required - generates P&L data)
3. `02_plot_position_trends.py` (position trends + stacked distribution)
4. `03_plot_pnl_pie.py` (P&L pie charts)
5. `04_plot_pnl_line.py` (P&L line charts)
6. `05_create_pnl_tables.py` (P&L tables)
7. `06_plot_market_value.py` (market value analysis)
8. `07_calculate_alternative_returns.py` (alternative returns)
9. `08_graduation_analysis.py` (graduation tracking)

## 👨‍💻 Author

Analysis framework developed with Claude Code assistance.

## 📄 License

For internal research use only.