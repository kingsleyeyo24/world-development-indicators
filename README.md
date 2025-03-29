# World Development Indicators Analysis

### Project Overview

This project explores global development trends using World Development Index (WDI) data, with a focus on economic growth, health, population changes, and energy use. By applying data analytics, we aim to uncover patterns, regional differences, and key factors that shape development across various income groups.

### Data Source
 
This dataset was sourced from **Maven Analytics** and is available at: [Maven Analytics Data Playground](https://mavenanalytics.io/data-playground?page=3&pageSize=5).

### Tools

- Python (JupyterLab)
- Microsoft PowerBI
- Tableau

### Imports

Here’s a quick rundown of why I’m importing these:  

- **`pandas`** – For handling and analyzing structured data efficiently.
- **`csv`** – For custom CSV file handling when needed.
- **`display`** – For better DataFrame presentation in Jupyter.
- **`matplotlib.pyplot`** – For creating visualizations.
- **`matplotlib.ticker`** – For customizing plot labels.
- **`seaborn`** – For better-looking statistical plots.
- **`numpy`** – For fast numerical computing.
- **`math`** – For additional mathematical functions.  

![Image](https://github.com/user-attachments/assets/5bbf4f6f-43d0-4236-81b6-af930fa3996e)

### Data Wrangling

The `wrangle` function is designed to clean and preprocess the dataset, ensuring that the data used for analysis is complete and reliable. Here’s a breakdown of the key steps taken:  

1. **Loading the Data:**  
   - The function begins by reading the dataset from an Excel file into a Pandas DataFrame.  

2. **Removing Columns with Excessive Missing Data:**  
   - Columns with more than 50% missing values, such as **"Individuals using the Internet (% of population)"** and **"Unemployment (% of total labor force)"**, are dropped. Retaining them would introduce too much uncertainty into the analysis.  

3. **Ensuring Chronological Order and Consistency:**  
   - The data is sorted by **Country Name** and **Year** to maintain proper chronological order.  
   - **Forward fill** is applied to GDP to ensure each country has continuous data, filling missing values with the most recent available data.  

4. **Handling Missing Values for Key Indicators:**  
   - Forward fill is used for **birth rate, death rate, life expectancy, GDP per capita, infant mortality rate, and population density**, ensuring each country’s data remains consistent.  
   - **Electric power consumption** undergoes both forward fill and backward fill to minimize missing values while preserving trends.  

5. **Dropping Countries with Insufficient GDP or Birth/Death Rate Data:**  
   - Countries with no recorded GDP data are removed.  
   - Countries like **Northern Mariana Islands, Turks and Caicos Islands, and Tuvalu**, which lack birth and death rate data, are also excluded.  

6. **Interpolating Infant Mortality Rate Data:**  
   - Linear interpolation is applied to fill gaps in the **infant mortality rate**, ensuring smoother trends without introducing abrupt changes.  

7. **Final Adjustments:**  
   - A **backward fill** is applied to **life expectancy and population density** to complete any remaining gaps in the dataset.  

![Image](https://github.com/user-attachments/assets/047c9995-5920-45c3-9e33-379feb223a3d)


