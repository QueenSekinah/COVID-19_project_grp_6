# VISUALIZING COVID-19: PATTERNS, OUTLIERS, AND RECOMMENDATIONS FOR ACTION

## PROJECT REPORT

### Initialization Stage

The collaborative analysis of the COVID-19 dataset was initiated through the establishment of a dedicated GitHub repository named "COVID-19_project_grp_6." This repository serves as a centralized platform for all group members, facilitating seamless collaboration, version control, and efficient sharing of code and insights.

The primary objective of this analysis is to leverage data visualization techniques to gain a comprehensive understanding of COVID-19 trends across selected countries. The dataset is meticulously explored, and patterns, outliers, and actionable insights are derived through a series of data analysis and visualization steps.

### Steps

#### 1. Data Preparation and Cleaning

Pandas, matplotlib.pyplot, and seaborn libraries were imported as pd, plt, and sns, respectively, to harness their functionalities. The COVID-19 dataset was loaded from the provided URL, and countries assigned to the group were filtered.

```python
# Data Loading and Cleaning
df = pd.read_csv("https://raw.githubusercontent.com/QueenSekinah/COVID-19_project_grp_6/main/full_grouped%20-%20full_grouped.csv")

# Checking for Missing Values
missing_values = df.isnull().sum()
print("Missing values:\n", missing_values)

#Remove rows with missing values

df = df.dropna()
```

#### 2. Exploratory Data Analysis

The dataset was grouped by countries, aggregating the total number of confirmed cases, deaths, and recoveries for each country.

```python
# Grouping by Country and Calculating Totals
country_totals = group_data.groupby('Country/Region').agg({'Confirmed': 'sum', 'Deaths': 'sum', 'Recovered': 'sum'})
print("Total Cases, Deaths, and Recoveries by Country:\n", country_totals)
```

Visualizing the distribution of COVID-19 cases among different countries was achieved using a stacked bar chart.

```python
# Visualization: Distribution of COVID-19 Cases by Country
country_totals.plot(kind='bar', stacked=True)
plt.title('Distribution of COVID-19 Cases by Country')
plt.show()
```

#### 3. Pivot Tables and Time Series Analysis

A pivot table was created to showcase the total number of confirmed cases, deaths, and recoveries for each date and country.

```python
# Pivot Table: Confirmed Cases, Deaths, and Recoveries by Date and Country
date_country_pivot = pd.pivot_table(group_data, values=['Confirmed', 'Deaths', 'Recovered'], index=['Date', 'Country/Region'], aggfunc='sum')
```

Time series analysis was performed to observe the trends in the number of confirmed cases over time for each country, visualized through a line plot.

```python
# Time Series Analysis: Confirmed Cases Over Time
time_series_plot = group_data.pivot(index='Date', columns='Country/Region', values='Confirmed').plot(figsize=(12, 8))
plt.title('Confirmed Cases Over Time')
plt.show()
```

#### 4. Individual Country Analysis

A focused analysis on a specific country (e.g., the United States) was conducted, revealing the trend of confirmed cases over time.

```python
# Individual Country Analysis: Confirmed Cases Over Time for the United States
specific_country_data = group_data[group_data['Country/Region'] == 'US']
plt.plot(specific_country_data['Date'], specific_country_data['Confirmed'], label='US')
plt.title('Confirmed Cases Over Time for US')
plt.xlabel('Date')
plt.ylabel('Confirmed Cases')
plt.legend()
plt.show()
```

#### 5. Cross-Country Comparison

A bar chart was utilized to compare the number of confirmed cases among different countries.

```python
# Cross-Country Comparison: Comparison of COVID-19 Among Countries
comparison_plot = country_totals.plot(kind='bar', stacked=True, figsize=(12, 8))
plt.title('Comparison of COVID-19 Cases Between Countries')
plt.xlabel('Countries/Regions')
plt.ylabel('Confirmed Cases')
plt.show()
```

#### 6. Bonus Tasks: Outliers and Correlation Matrix

A check for outliers in the dataset was conducted, and a correlation matrix was visualized using a heatmap.

```python
# Bonus Tasks: Outliers and Correlation Matrix
correlation_data = df[['Confirmed', 'Deaths', 'Recovered']]
correlation_matrix = correlation_data.corr()

plt.figure(figsize=(10, 8))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f', linewidths=.5)
plt.title('Correlation Matrix of COVID-19 Variables')
plt.show()
```

### Recommendations for Action

The comprehensive analysis of COVID-19 patterns has provided valuable insights into the dynamics of the pandemic across assigned countries. To enhance the depth of the analysis and further contribute to actionable recommendations, consider the following:

1. **Geospatial Analysis:** Explore geospatial visualizations to map the distribution of cases, deaths, and recoveries on a global scale.

2. **Epidemiological Trends:** Investigate epidemiological factors influencing the observed trends, considering variables such as population density, healthcare infrastructure, and government response measures.

3. **Forecasting Models:** Implement time series forecasting models to predict future trends in COVID-19 cases, enabling proactive decision-making.

4. **Public Health Interventions:** Propose evidence-based interventions based on the observed patterns, targeting areas with high case numbers and identifying potential areas for resource allocation.

5. **Data Enrichment:** Consider incorporating external datasets to enhance the analysis, including demographic data, climate conditions, and socioeconomic factors.

### Group Members

- Yetunde Kabiawu
- Tessy E
- Okoni Samuel
- Oladele Sekinat
- Olalekan Abdul
- Olawuyi Abdulqo
- Oluwafemi Awotimiro
- Oluwamurewa Ode
- Omolo Ouma Rona
- Paul Aderoju
- Shiloh Oni
- Sonia Ezike
- Teopolina Nantinda
