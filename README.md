#This is by OEM# list with new_list_models

import pandas as pd

# Initial data
data1 = {'Make': ['POLARIS'], 'Model': ['all models'], 'Year': [1990], 'Vendor': ['NACH'], 'MPN': ['05-146-03'], 'AD Item Number': ['LP05920'], 'Vendor Notes': [pd.NA], 'NI#': ['05-146-03'], 'REF#': [pd.NA], 'OEM#': ['050156']}

# List of models
new_list_models = ['Big Boss 250 4x6', 
                   'Trail Blazer 250',
                   'Trail Boss 250 2x4', 
                   'Trail Boss 250 4x4', 
                   'Trail Boss 350L 2x4',
                   'Trail Boss 350L 4x4',
                   '400', 
                   '500', 
                   '500 SKS', 
                   '650', 
                   '500 SP', 
                   '650 SKS',
                   '650 RXL',
                   'Classic',
                   'Sport',
                   'Sport GT',
                   'Sprint ES',
                   'Star',
                   'Star Trak',
                   'Trail Super Trak',
                   'Trail Deluxe',
                   'Trail Wide Trak',
                   'Trail']

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
