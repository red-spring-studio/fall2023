`Documentation.md`

### ANTH 103-M01 Response Paper: Evolution

**Version 1.0: Last updated by K.S. on September 22, 2023.**

# Analysis of Monarch Butterfly Population Decline

*This document provides a walkthrough of the steps taken to analyze the decline in the Monarch Butterfly population, utilizing a dataset that captures the count of butterflies across various sites over the years.*
  
## Dataset Overview


The dataset contains the following columns:

- `SITE ID`: Identifier for the site.

- `SITE NAME`: Name of the site.

- `COUNTY`: County where the site is located.

- Yearly columns from `1997` to `2022`: Count of Monarch Butterflies for each respective year.

- New Year's counts (e.g., `NY 2018-19`): Count of Monarch Butterflies for the New Year's period for the respective year.

## 1. Loading the Data
 
The first step in any data analysis is to load the dataset into a suitable environment for processing. I'm using Python's Pandas library to load the dataset.

```python

import pandas as pd

  

# Load the dataset

data = pd.read_excel("/path/to/dataset.xlsx")

```

## 2. Data Preprocessing

Given the nature of the dataset, it was observed that there were missing values, especially in the yearly count columns. These missing values were treated as follows:

- For yearly count columns: Missing values were replaced with zeros, indicating no count or that no count was conducted.

- For `SITE ID`, `SITE NAME`, and `COUNTY` columns: Rows with missing values were dropped.

```python

# Fill NaN values in yearly columns with zeros

yearly_columns = list(range(1997, 2023))

data[yearly_columns] = data[yearly_columns].fillna(0)

# Drop rows with missing values in specific columns

data_cleaned = data.dropna(subset=['SITE ID', 'SITE NAME', 'COUNTY'])

```
  

## 3. Exploratory Data Analysis (EDA)

  

With the data preprocessed, the next step was to perform exploratory data analysis to draw insights.

### 3.1. Overall Monarch Butterfly Count Trend

To understand how the butterfly count changed over the years, the counts for each year were aggregated and visualized. 

```python

# Aggregating the counts for each year

yearly_counts = data_cleaned[yearly_columns].sum()

  

# Visualization code would be placed here

```
  
### 3.2. Sites with Highest Butterfly Counts

To identify significant habitats, the dataset was aggregated by site to determine the top sites with the highest cumulative counts.  

```python

# Aggregating counts for each site

site_counts = data_cleaned.groupby('SITE NAME').sum()[yearly_columns].sum(axis=1)

top_sites = site_counts.sort_values(ascending=False).head(10)

```

### 3.3. Counties with Highest Butterfly Counts  

To guide regional conservation efforts, the dataset was aggregated by county.

```python

# Aggregating counts for each county

county_counts = data_cleaned.groupby('COUNTY').sum()[yearly_columns].sum(axis=1)

top_counties = county_counts.sort_values(ascending=False)

```

## 4. Conclusions

The analysis highlighted a concerning decline in the Monarch Butterfly population over the past few decades. Some sites and counties emerged as significant habitats, providing a direction for conservation efforts.

----------

Exploring the decline of the Monarch Butterfly population using Python involved several steps, including data acquisition, data preprocessing, visualization, and analysis. Here's a step-by-step guide to help you get started if you are interested in having a go at this project yourself:


1. **Data Acquisition**:

- First, you need to source the data. A variety of governmental, academic, and non-profit organizations often collect data on endangered species, including the Monarch Butterfly.

- Download datasets related to Monarch Butterfly population counts, migration patterns, or any other pertinent data.

- Load the data into Python using libraries like `pandas`.

  

2. **Data Preprocessing**:

- Clean the data: Handle missing values, outliers, or any inconsistencies in the dataset.

- Convert data types, if necessary.

- Normalize or standardize data, especially if you plan on using any machine learning techniques later on.

  

3. **Exploratory Data Analysis (EDA)**:

- Start by getting a general feel for the data using `data.describe()` and `data.info()`.

- Check for correlations between different variables. For instance, you might want to see if there's a correlation between pesticide use and Monarch population decline.

- Visualize trends over time using line plots.

- Examine distributions using histograms or KDE plots.

  

4. **Visualization**:

- Use libraries like `matplotlib` and `seaborn` for visualization.

- Plot time series data to observe the decline over the years.

- Visualize geographic data on maps using libraries like `folium` or `geopandas` to see if certain regions are more affected than others.

  

5. **Statistical Analysis**:

- Depending on your data, you might want to use statistical tests to determine if observed trends are significant.

- For instance, you could perform a regression analysis to see if there's a significant decline over time.

  

6. **Advanced Analysis** (Optional):

- Use machine learning to predict future populations or to determine the most important features contributing to the decline.

- Cluster analysis might help in segmenting data into different groups, which could provide insights into regions or time periods that are particularly problematic.

  

7. **Conclusions**:

- Summarize your findings.

- Determine the primary causes of decline based on your analysis.

- Propose solutions or further areas of research.

  

8. **Communication**:

- Share your findings with stakeholders or the public.

- Visualizations, interactive dashboards (using tools like `Plotly` or `Bokeh`), or reports can be effective ways to convey your insights.

  

***While data analysis can provide valuable insights into the decline of the Monarch Butterfly population, it's also important to consult with experts in the field to ensure the accuracy and relevance of your conclusions!***
