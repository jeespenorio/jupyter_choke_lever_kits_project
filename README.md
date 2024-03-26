#This is by OEM# list with new_list_models

import pandas as pd

# Initial data
data1 = {'Make': ['POLARIS'], 'Model': ['all models'], 'Year': [1994], 'Vendor': ['NACH'], 'MPN': ['05-146-03'], 'AD Item Number': ['LP05920'], 'Vendor Notes': [pd.NA], 'NI#': ['05-146-03'], 'REF#': [pd.NA], 'OEM#': ['050156']}

# List of models
new_list_models = [
'XLT SKS',
'Storm',
'Storm SKS',
'Starlite',
'Starlite GT',
'Super Sport',
'Sport',
'Sport SKS',
'Trail',
'Trail Deluxe',
'Classic',
'Classic Touring',
'Lite',
'Lite GT',
'Lite Deluxe',
'XLT SP Xtra',
'Wide Trak GT',
'Wide Trak LX',
'500 EFI',
'500 EFI SKS',
'600 XCR',
'650 RXL',
'650 RXL Touring',
'SL 650',
'SL 750',
'SLT 750']

# List of OEM numbers
oem_numbers = ['2200188', '7080290', '7081402', '05-146', '50156']

# Function to generate DataFrame for each model
def generate_df(model, data):
    data['Model'] = model
    return pd.DataFrame(data)

# Generate DataFrames for all sets of data
dfs = []
for oem in oem_numbers:
    data1['OEM#'] = oem
    df1 = pd.concat([generate_df(model, data1) for model in new_list_models], ignore_index=True)
    dfs.append(df1)

# Concatenate all DataFrames
final_df = pd.concat(dfs, ignore_index=True)

# Print the final DataFrame
print(final_df)
