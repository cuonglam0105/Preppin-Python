# Preppin' Data Challenges Solutions

This repository contains my solutions to the Preppin' Data challenges. 

[Preppin' Data](https://preppindata.blogspot.com/p/the-challenge-index.html) is a weekly challenge for data analysts and data scientists to hone their data processing skills using Tableau. Each challenge consists of a scenario and a dataset, and the objective is to clean, transform, and analyze the data to generate the desired output.

I have decided to solve these challenges using Python and SQL, and I have uploaded my solutions to this repository. My solutions include Python scripts, Jupyter notebooks, and SQL scripts that demonstrate how to manipulate and analyze the given datasets to generate the desired outputs.

Each challenge has its own folder, and the folder contains the challenge description, the input dataset, and the output dataset. The Jupyter notebooks are named after the challenge number, and the SQL scripts are named using the format "YYYY_WX.sql" (ie: 2021_W1.sql). The output datasets are named using the format "YYYY_WX.csv".

I hope that my solutions will be helpful to those who are looking to improve their data processing skills using Python and SQL, and I welcome any feedback or suggestions on how to improve my solutions.

# Requirements
To run the Python scripts and Jupyter notebooks, you need to have Python 3 installed along with the following libraries:

- pandas
- numpy
- datetime

To run the SQL scripts, you need to have a SQL client installed, such as MySQL Workbench, Microsoft SQL Server Management Studio, or SQLiteStudio.

# Usage

To run the Python scripts and Jupyter notebooks, simply navigate to the corresponding challenge folder and run the script using the Python interpreter or the Jupyter notebook server.

To run the SQL scripts, open the script in your SQL client and execute the script against the database of your choice.

## 2021 Solution

| Challenge   | Python |
| ----------- | ----------- |
| [Week 01](https://preppindata.blogspot.com/2021/01/2021-week-1.html)      | [:snake:](https://github.com/cuonglam0105/Preppin-Python/blob/main/2021_W1/2021_W1.ipynb)  |
| [Week 02](https://preppindata.blogspot.com/2021/01/2021-week-2.html)      | [:snake:](https://github.com/cuonglam0105/Preppin-Python/blob/main/2021_W2/2021_W2.ipynb)  |
| [Week 03](https://preppindata.blogspot.com/2021/01/2021-week-3.html)      | [:snake:](https://github.com/cuonglam0105/Preppin-Python/blob/main/2021_W3/2021_W3.ipynb)  |
| [Week 04](https://preppindata.blogspot.com/2021/01/2021-week-4.html)      | [:snake:](https://github.com/cuonglam0105/Preppin-Python/blob/main/2021_W4/2021_W4.ipynb)  |

# Disclaimer

The solutions provided in this repository are my own and may not be the most efficient or optimal solutions to the challenges. They are intended to showcase how to solve the challenges using Python and SQL and should not be used for production purposes without proper testing and validation. The datasets used in the challenges are the property of Preppin' Data and are used under fair use for educational purposes only.



# :snake: Python Snippets

### Read all Excel tabs and concat as one dataframe
```
all_tabs = pd.read_excel('folder\\filename.xlsx', sheet_name=None)
```

### DataFrame Transformations
Unioning dataframes together with concat
```
import pandas as pd
df_total = pd.concat([df1,df2,df3])
```

Joining tables
```
output = pd.merge(left=df_pivot, right=target, on=['Quarter', 'Store'], how='inner')
```

Replacing null values with zero, blank, previous or preceeding values
```
import pandas as pd

# replace nulls with zeroes
df['Column with nulls'] = df['Column with nulls'].fillna(0)

# replace nulls with empty string (blank)
df['Column with nulls'] = df['Column with nulls'].fillna('')

# replace nulls with previous non-null value
df['Column with nulls'] = df['Column with nulls'].fillna(method='ffill')

# replace nulls with next non-null value
df['Column with nulls'] = df['Column with nulls'].fillna(method='bfill')
```

### Aggregrating data
Create aggregrated columns grouped by other columns
```
import pandas as pd
df = df.groupby(['Col1','Col2']).agg(col3_min=('Col3','min'),col3_max=('Col3','max'),col3_sum=('Col3','sum')).reset_index()
```

Ranking column | Example:
```
output['Rank'] = output.groupby('group_col')['order_by_col'].rank(method='dense', ascending=False)
```

### Data Clean-up
Rename single column
```
import pandas as pd
df.rename( columns={'Col1':'Col1_New_Name'}, inplace=True )
```

