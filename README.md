# NYC-oil-gas-Data-Analysis
NYC Oil & Gas Production Data Analysis

📌 Project Overview

This project performs exploratory data analysis (EDA) on New York State oil and gas production data. The dataset contains information about oil and gas wells, production volumes, injection and disposal wells, operators, fields, formations, and locations.

The analysis focuses particularly on field-wise production and well statistics to identify fields with significant oil and gas production activity.

---

🎯 Objectives

The main objectives of this project are:

- Load and inspect the NYC oil and gas production dataset.
- Understand the structure and characteristics of the dataset.
- Analyze oil and gas wells across different fields.
- Aggregate well counts and production data at the field level.
- Generate descriptive statistics for field-wise production.
- Identify fields having a significant number of active oil wells.
- Examine the distribution of active gas wells across different fields.
- Identify major oil- and gas-producing fields.

---

📊 Dataset

The project uses the following dataset:

"NYC_production_data.csv"

The dataset contains information about oil and gas production activities in New York.

Important Features

Column| Description
"Production Year"| Year in which production was recorded
"Production Date Entered"| Date when production information was entered
"Operator"| Company/operator responsible for the wells
"County"| County where the field is located
"Town"| Town where the field is located
"Field"| Name of the oil/gas field
"Producing Formation"| Geological formation producing hydrocarbons
"Active Oil Wells"| Number of active oil wells
"Inactive Oil Wells"| Number of inactive oil wells
"Active Gas Wells"| Number of active gas wells
"Inactive Gas Wells"| Number of inactive gas wells
"Injection Wells"| Number of injection wells
"Disposal Wells"| Number of disposal wells
"Self-use Well"| Indicates whether the well is used for self-consumption
"Oil Produced, bbl"| Oil production in barrels
"Gas Produced, Mcf"| Gas production in thousand cubic feet
"Water produced, bbl"| Water production in barrels
"Taxable Gas, Mcf"| Taxable gas production in Mcf
"Purchaser Codes"| Codes identifying purchasers
"Location"| Field/town location and geographical coordinates

---

🛠️ Technologies Used

- Python
- NumPy – Numerical operations
- Pandas – Data manipulation and analysis
- Matplotlib – Data visualization
- Seaborn – Statistical visualization
- Google Colab – Development environment

Libraries

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline

---

🔍 Project Workflow

1. Import Required Libraries

The project starts by importing the Python libraries required for data analysis and visualization.

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline

---

2. Load the Dataset

The production dataset is loaded using Pandas.

df = pd.read_csv('NYC_production_data.csv')

---

3. Inspect the Dataset

The first two rows of the dataset are displayed to understand its structure.

df.head(2)

The dataset contains information about:

- Oil and gas wells
- Production volumes
- Operators
- Fields
- Counties and towns
- Producing formations
- Injection and disposal wells

---

4. Examine Dataset Columns

The names of all columns are obtained using:

df.columns

This provides an overview of the variables available for analysis.

---

📈 Field-Level Analysis

A major part of the project is analyzing production and well information at the field level.

The dataset is grouped according to the "Field" column:

df_fieldwise = df.groupby('Field').sum()[[
    'Active Oil Wells',
    'Inactive Oil Wells',
    'Active Gas Wells',
    'Inactive Gas Wells',
    'Injection Wells',
    'Disposal Wells',
    'Oil Produced, bbl',
    'Gas Produced, Mcf',
    'Water produced, bbl'
]]

This aggregates the production and well-related variables for each field.

The resulting DataFrame is then converted back to a regular DataFrame:

df_fieldwise = df_fieldwise.reset_index()

---

📊 Descriptive Statistics

Descriptive statistics are generated using:

df_fieldwise.describe()

There are 229 fields in the resulting field-level dataset.

The analysis provides statistics such as:

- Mean
- Standard deviation
- Minimum
- 25th percentile
- Median
- 75th percentile
- Maximum

for the different well and production variables.

---

🛢️ Active Gas Well Analysis

The number of active gas wells for each field is sorted in descending order:

df_fieldwise['Active Gas Wells'].sort_values(
    ascending=False
).values

This helps identify fields with unusually large numbers of active gas wells.

The analysis shows a highly uneven distribution, with most fields having relatively few active gas wells while a small number of fields contain very large numbers of gas wells.

For example, the field with the highest value has 62,112 active gas wells according to the aggregated dataset.

---

🛢️ Fields with Significant Active Oil Wells

The project also identifies fields containing at least 35 active oil wells:

df_fieldwise[df_fieldwise['Active Oil Wells'] >= 35]

This produces a subset of fields with relatively high active-oil-well counts.

Some of the fields identified include:

- ALMA
- ANDOVER
- BEECH HILL-INDEPENDENCE
- BRADFORD
- BROWNING
- BUSTI
- CHIPMUNK
- FIVE MILE
- FORD'S BROOK
- FULMER VALLEY
- LAKESHORE
- MARSH
- RICHBURG
- SCIO
- WIRT

These fields can be investigated further to understand their production characteristics.

---

🔑 Key Observations

From the exploratory analysis:

1. The dataset contains production information from 229 distinct fields after field-level aggregation.

2. The number of wells varies considerably between fields.

3. Many fields have zero active oil wells, indicating that oil production is concentrated in a smaller number of fields.

4. Active gas wells also show a highly skewed distribution, with a few fields having exceptionally large numbers of active gas wells.

5. "LAKESHORE" has the largest number of active gas wells in the field-level dataset, with 62,112 active gas wells.

6. "BRADFORD" has 39,932 active oil wells in the aggregated dataset.

7. Production volumes also vary significantly between fields, indicating that hydrocarbon production is concentrated in particular fields.

---

📌 Possible Further Analysis

The current analysis can be extended with additional exploratory data analysis and visualization.

Possible improvements include:

Production Analysis

- Top 10 oil-producing fields
- Top 10 gas-producing fields
- Top water-producing fields
- Oil-to-water production ratios
- Oil-to-gas production comparison

Well Analysis

- Active vs inactive oil wells
- Active vs inactive gas wells
- Injection wells by field
- Disposal wells by field
- Relationship between number of wells and production

Geographic Analysis

- Production by county
- Production by town
- Mapping oil and gas fields using latitude and longitude
- Geographic distribution of active wells

Time-Series Analysis

- Annual oil production
- Annual gas production
- Changes in active wells over time
- Production trends by field

---

🚀 How to Run the Project

Option 1: Google Colab

1. Open the notebook in Google Colab.
2. Upload "NYC_production_data.csv".
3. Run the cells sequentially.

Option 2: Local Python Environment

Clone/download the project and place the dataset in the same directory as the Python notebook.

Install the required libraries:

pip install numpy pandas matplotlib seaborn

Then run the notebook using Jupyter Notebook or JupyterLab.

---

📁 Project Structure

NYC-Oil-Gas-Production-Analysis/
│
├── NYC_production_data.csv
├── NYC_production_analysis.ipynb
└── README.md

---

📜 Conclusion

This project provides an exploratory analysis of New York oil and gas production data. By aggregating well and production information at the field level, it becomes easier to compare fields and identify areas with significant oil and gas activity.

The analysis establishes a foundation for further work involving data visualization, production forecasting, geographic analysis, statistical analysis, and machine learning.
