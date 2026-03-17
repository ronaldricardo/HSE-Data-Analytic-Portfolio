# 🚀 On Hand Practice Class HSE Data Analytic - Google Colab Setup Guide
**Download dataset:** [here](https://github.com/ronaldricardo/HSE-Data-Analytic-Portofolio/dataset/Data_K3_Sintetis_1000.xlsx)

## 1. Mount Google Drive
```python
from google.colab import drive
drive.mount('/content/drive')

File path: /content/drive/MyDrive/HSE Data Viz 15 Maret/Data_K3_Sintetis_1000.xlsx 
```

## 2. Load All 13 Sheets
```python
import pandas as pd
excel_file_path = '/content/drive/MyDrive/HSE Data Viz 15 Maret/Data_K3_Sintetis_1000.xlsx'

try:
    xls = pd.ExcelFile(excel_file_path)
    sheet_names = xls.sheet_names
    loaded_dfs = {}
    
    print("Loading sheets from Excel file:")
    for sheet_name in sheet_names:
        if sheet_name.startswith('Data_'):
            df_var_name = 'df_' + sheet_name[len('Data_'):].lower()
            loaded_dfs[df_var_name] = pd.read_excel(excel_file_path, sheet_name=sheet_name)
            globals()[df_var_name] = loaded_dfs[df_var_name]
            print(f"  - Sheet '{sheet_name}' → DataFrame '{df_var_name}'")
    
    print("\n✅ All sheets loaded! Access: df_insiden, df_kpi, etc.")
except FileNotFoundError:
    print(f"❌ File not found: {excel_file_path}")
except Exception as e:
    print(f"❌ Error: {e}")

```

## 3. Verify Drive Path
```python
import os
drive_path = '/content/drive/MyDrive/'
print("MyDrive contents:")
for item in os.listdir(drive_path):
    print(f"- {item}")

hse_folder = '/content/drive/MyDrive/HSE Data Viz 15 Maret'
if os.path.exists(hse_folder):
    print(f"\nHSE folder contents:")
    for item in os.listdir(hse_folder):
        print(f"- {item}")
else:
    print(f"\n❌ HSE folder not found")
```

## 4. Check DataFrame Loaded
```python
try:
    print("df_insiden info:")
    df_insiden.info()
    print("✅ DataFrame ready!")
except:
    print("❌ df_insiden not found - check Step 2")
```

## 5. Run Pipeline
Continue progress in [here](https://github.com/ronaldricardo/HSE-Data-Analytic-Portofolio/note/Copy_of_Praktik_Hands_On.ipynb)
