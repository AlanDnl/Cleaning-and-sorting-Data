# Cleaning and sorting-Data
This repository collect various types of dataset to later clean and sort them

## Table of contents
- [Project overview](#project-overview)
- [Data sources](#data-sources)
- [Tools](#tools)
- [Data cleaning/preparation](#data-cleaning/preparation)
- [Data Analysis](#data-analysis)
- [References](#references)

## Project overview
------

This data analysis project aims to clean and sort datasets using distinct methodologies and applying Python, SQL server and in some examples Excel.

So, the methodology involves standard, clean and analyize the information due to some of the columns were in different format dates.

## Data Sources
FIFA 2021: The first dataset used for this project was "fifa21 raw data v2.csv" file, which contain detalied information about each player in the 2021 year. It involves personal information, professional deportive information and information regarding to skills and other parameters according soccer in a professional level.

## Tools
- Excel: Data sorting and cleaning
- Python: Data cleaning and data analysis
- SQL server: Data cleaning and data analysis

## Data cleaning/preparation
1. Data loading and inspection
2. Handling missing values
3. Data cleaning and formatting

## Data Analysis
Include some interesting code/features worked with
``` Python
def extract_contract_info(contract):
    if contract == 'Free' or 'On Loan' in contract:
        start_date = np.nan
        end_date = np.nan
        contract_lenght = 0
    else:
        start_date, end_date = contract.split(' ~ ')
        start_year = int(start_date[:4])
        end_year = int(end_date[:4])
        contract_lenght = end_year - start_year
        
    return start_date, end_date, contract_lenght

# Apply the fn to contract columns and create new columns
new_cols = ['Start date', 'End date', 'Contract length(years)']
new_data = fifa['Contract'].apply(lambda x: pd.Series(extract_contract_info(x)))

for i in range(len(new_cols)):
    fifa.insert(loc = fifa.columns.get_loc('Contract')+1+i, column = new_cols[i], value = new_data[i])
```

## References
- Data Cleaning Project in Python [https://www.youtube.com/watch?v=7mYbrpfAU6k]

