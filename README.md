# Extract Web Services

## Overview

This Jupyter Notebook script is designed to compare two Excel files containing web services data from already set up Business Central web services. The script utilizes the pandas library for data manipulation and comparison.

## Requirements

- [pandas](https://pandas.pydata.org/): Ensure that the pandas library is installed before running the script. You can install it using the following command:

    ```bash
    pip install pandas
    ```

## How to Use

1. Open the Jupyter Notebook in your Jupyter environment.
2. Replace the placeholder file paths and column name with your actual file paths and column name in the script.
3. Run each cell step by step to execute the code.

### Script Explanation

The script consists of a Python function `compare_excel_files` and the main code to call this function. Here's a breakdown:

```python
import pandas as pd

def compare_excel_files(file1, file2, output_csv, check_column):
    # Read Excel files into dataframes
    df1 = pd.read_excel(file1)
    df2 = pd.read_excel(file2)

    # Find values in df1 that are not in df2 based on the specified column
    result_df = df1[~df1[check_column].isin(df2[check_column])]

    # Write the result to a CSV file
    result_df.to_csv(output_csv, index=False)
    print(f"Comparison results saved to {output_csv}")

# Specify the file paths and column name
file1_path = "Chuka.xlsx"
file2_path = "Aiu.xlsx"
output_csv_path = "output.csv"
checking_column = "Object Name"

compare_excel_files(file1_path, file2_path, output_csv_path, checking_column)

# Read the CSV file and display the first 100 rows
dfResult = pd.read_csv("output.csv")
dfResult.head(100)

This script compares two Excel files (extracted from bussiness central web services) based on the "Object Name" column and outputs the differences to a CSV file (output.csv). The resulting CSV file is then read into a dataframe (dfResult), and the first 100 rows are displayed.
