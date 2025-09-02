# 📁 Project File Structure

## 🗂️ Simplified Output Directory Organization

All analysis outputs are organized into 5 main folders under `analysis_results/`:

### 📊 PnL_Analysis/
All P&L related files (charts and data):
- `{ETF}_Small_Position_PnL.png` - Individual ETF P&L charts
- `Small_Position_PnL_Charts.png` - Combined P&L charts  
- `{ETF}_PnL_Pie_Chart.png` - P&L pie charts by ETF
- `All_ETFs_PnL_Pie_Charts.png` - Combined pie charts
- `{ETF}_PnL_Data.xlsx` - Calculated P&L data per ETF
- `All_ETFs_PnL_Tables.xlsx` - Combined P&L tables

### 📈 Market_Value_Analysis/
Market value visualizations and data:
- `{ETF}_Small_Position_Market_Value.png` - Individual ETF market value charts
- `Small_Position_Market_Value_Data.xlsx` - Weekly market value data

### 📉 Position_Analysis/
Position analysis charts and data:
- `{ETF}_Small_Positions_Chart.png` - Small positions chart per ETF (count & percentage)
- `Small_Positions_Data.xlsx` - Daily data with columns: Date | Small_Position_Count | Total_Position_Count | Small_Position_Percentage

### 💹 Alternative_Returns/
Alternative return analysis:
- `{ETF}_Alternative_Returns.png` - Individual ETF returns comparison (weekly)
- `Alternative_Returns_Data.xlsx` - Weekly returns data with/without <1% positions

### 🔍 Starter_Residual/
Starter and residual position analysis:
- `{ETF}_starter_residual_analysis.xlsx` - Analysis per ETF
- `ARK_All_Reappeared_Positions.xlsx` - Reappeared positions data

## 📜 Python Scripts

| Script | Description | Output Location |
|--------|-------------|-----------------|
| `00_starter_residual_analysis.py` | Analyze starter & residual positions | Starter_Residual/ |
| `01_calculate_pnl.py` | Calculate P&L for <1% positions | PnL_Analysis/ |
| `02_plot_position_trends.py` | Plot position trends over time | Position_Analysis/ |
| `03_plot_pnl_pie.py` | Create P&L pie charts | PnL_Analysis/ |
| `04_plot_pnl_line.py` | Create P&L line charts | PnL_Analysis/ |
| `05_create_pnl_tables.py` | Create P&L summary tables | PnL_Analysis/ |
| `06_plot_market_value.py` | Plot market value analysis | Market_Value_Analysis/ |
| `07_calculate_alternative_returns.py` | Calculate returns without <1% positions | Alternative_Returns/ |

## 🚀 Usage

1. **Run all analyses**: 
   ```bash
   python main.py
   # Select 'A' for all steps
   ```

2. **Run specific analysis**:
   ```bash
   python main.py
   # Select specific numbers (e.g., '1,3,5')
   ```

3. **Directory structure is automatically created** when running `main.py` or any individual script.

## 📝 Configuration

All output paths are configured in `config.py`. The simplified structure has:
- Only 5 main folders
- No subfolders for graphs/data (all files in same folder)
- No ETF-specific folders (ETF files are distinguished by filename)

## 🎨 Benefits of Simplified Structure

1. **Simplicity**: Only 5 main folders to navigate
2. **Flat Structure**: No nested subfolders
3. **Easy Access**: All related files in one place
4. **Clear Naming**: Files clearly named with ETF prefixes
5. **Minimal Navigation**: Less folder hierarchy to navigate

---
*Last Updated: 2025*