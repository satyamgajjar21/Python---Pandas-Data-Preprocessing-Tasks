# 📊 Data Visualization with Python  
### 🧾 Cheat Sheet: Data Preprocessing Tasks in Pandas  

This cheat sheet summarizes essential **Pandas** operations for data preprocessing and an overview of popular **Python plotting libraries** for data visualization.  

---

## 🧠 Pandas Data Preprocessing Tasks

| **Task** | **Syntax** | **Description** | **Example** |
|-----------|-------------|-----------------|--------------|
| **Load CSV data** | `pd.read_csv('filename.csv')` | Read data from a CSV file into a DataFrame | `df_can = pd.read_csv('data.csv')` |
| **Handling Missing Values** | `df.dropna()`<br>`df.fillna(value)` | Drop rows with missing values or fill them with a specified value | `df_can.dropna()`<br>`df_can.fillna(0)` |
| **Removing Duplicates** | `df.drop_duplicates()` | Remove duplicate rows | `df_can.drop_duplicates()` |
| **Renaming Columns** | `df.rename(columns={'old':'new'})` | Rename one or more columns | `df_can.rename(columns={'Age':'Years'})` |
| **Selecting Columns** | `df['col']` or `df.col`<br>`df[['col1','col2']]` | Select single or multiple columns | `df_can.Age`<br>`df_can[['Name','Age']]` |
| **Filtering Rows** | `df[df['col'] > value]` | Filter rows based on condition | `df_can[df_can['Age'] > 30]` |
| **Applying Functions** | `df['col'].apply(func)` | Apply a function to transform column values | `df_can['Age'].apply(lambda x: x + 1)` |
| **Creating New Columns** | `df['new'] = expression` | Create new column derived from existing ones | `df_can['Total'] = df_can['Quantity'] * df_can['Price']` |
| **Grouping and Aggregating** | `df.groupby('col').agg({'x':'sum','y':'mean'})` | Group rows by a column and apply aggregate functions | `df_can.groupby('Category').agg({'Total':'mean'})` |
| **Sorting Rows** | `df.sort_values('col', ascending=True/False)` | Sort rows based on a column | `df_can.sort_values('Date', ascending=True)` |
| **Displaying First / Last n Rows** | `df.head(n)`<br>`df.tail(n)` | Show top or bottom n rows of a DataFrame | `df_can.head(3)`<br>`df_can.tail(3)` |
| **Checking for Null Values** | `df.isnull()` | Identify null/missing values | `df_can.isnull()` |
| **Selecting Rows by Index** | `df.iloc[index]`<br>`df.iloc[start:end]` | Select rows by integer index or range | `df_can.iloc[3]`<br>`df_can.iloc[2:5]` |
| **Selecting Rows by Label** | `df.loc[label]`<br>`df.loc[start:end]` | Select rows by index label | `df_can.loc['Label']`<br>`df_can.loc['Age':'Quantity']` |
| **Summary Statistics** | `df.describe()` | Generate descriptive statistics for numeric columns | `df_can.describe()` |

---

## 📈 Cheat Sheet: Python Plot Libraries

| **Library** | **Main Purpose** | **Key Features** | **Language** | **Customization** | **Dashboard Capabilities** | **Common Plot Types** |
|--------------|------------------|------------------|---------------|------------------|----------------------------|------------------------|
| **Matplotlib** | General-purpose plotting | Comprehensive and highly customizable | Python | ⭐⭐⭐⭐ | Requires extra setup | Line, scatter, bar, histogram, pie, box, heatmap |
| **Pandas** | Quick plotting on DataFrames | Simple syntax built on Matplotlib | Python | ⭐⭐⭐ | Can integrate with web dashboards | Line, scatter, bar, pie, box |
| **Seaborn** | Statistical visualization | Stylish statistical plots with color themes | Python | ⭐⭐⭐ | Works with other libs for dashboards | Heatmap, violin, bar, scatter, count |
| **Plotly** | Interactive visualization | Web-based, interactive and animated | Python, R, JS | ⭐⭐⭐⭐⭐ | ✅ Built-in via Dash framework | Line, scatter, bar, pie, 3D, choropleth |
| **Folium** | Geospatial visualization | Interactive and customizable maps | Python | ⭐⭐⭐ | Can embed maps in dashboards | Choropleth, point maps, heatmaps |
| **PyWaffle** | Waffle charts | Visualize proportions as grids | Python | ⭐⭐ | Combines with other libs | Waffle, square pie, donut charts |

---

## 🧩 Example: Basic Data Preprocessing and Plotting

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df_can = pd.read_csv('data.csv')

# Clean data
df_can.dropna(inplace=True)
df_can.rename(columns={'Age': 'Years'}, inplace=True)

# Group and aggregate
summary = df_can.groupby('Category').agg({'Sales': 'sum'})

# Visualize
summary.plot(kind='bar')
plt.title('Total Sales by Category')
plt.ylabel('Sales')
plt.show()
