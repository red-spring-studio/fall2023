# Exploring the decline of Monarch Butterfly populations with Python

![A Monarch Butterfly](https://assets.codepen.io/6566924/Monarch-Butterfly+%283%29.jpeg)

Images by Adobe Stock. [See License information](https://stock.adobe.com/license-terms)

> [Exploring the decline of Monarch Butterfly populations with Python](#exploring-the-decline-of-monarch-butterfly-populations-with-python)
> **Version 1.0: Last updated by K.S. on September 22, 2023.**
  - [Part 1 Analysis](#part-1-analysis)
  - [References](#references)
  - [Analysis of Monarch Butterfly Population Decline](#analysis-of-monarch-butterfly-population-decline)
  - [Dataset Overview](#dataset-overview)
  - [1. Loading the Data](#1-loading-the-data)
  - [2. Data Preprocessing](#2-data-preprocessing)
  - [3. Exploratory Data Analysis (EDA)](#3-exploratory-data-analysis-eda)
    - [3.1. Overall Monarch Butterfly Count Trend](#31-overall-monarch-butterfly-count-trend)
    - [3.2. Sites with Highest Butterfly Counts](#32-sites-with-highest-butterfly-counts)
    - [3.3. Counties with Highest Butterfly Counts](#33-counties-with-highest-butterfly-counts)
  - [4. Conclusions](#4-conclusions)
  - [Resources Cited](#resources-cited)

---

## Analysis of Monarch Butterfly Population Decline

`README.md`

**Version 1.0: Last updated by K.S. on September 22, 2023.**

*This document provides a walkthrough of the steps taken to analyze the decline in the Monarch Butterfly population, utilizing a dataset that captures the count of butterflies across various sites over the years.*

## Dataset Overview

The dataset contains the following columns:

- `SITE ID`: Identifier for the site.

- `SITE NAME`: Name of the site.

- `COUNTY`: County where the site is located.

- Yearly columns from `1997` to `2022`: Count of Monarch Butterflies for each respective year.

- New Year's counts (e.g., `NY 2018-19`): Count of Monarch Butterflies for the New Year's period for the respective year.

## 1. Loading the Data

The first step in any data analysis is to load the dataset into a suitable environment for processing. Here, we use Python's Pandas library to load the dataset.

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

yearly_columns =  list(range(1997,  2023))

data[yearly_columns] = data[yearly_columns].fillna(0)

# Drop rows with missing values in specific columns

data_cleaned = data.dropna(subset=['SITE ID',  'SITE NAME',  'COUNTY'])
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

The population of Monarch Butterflies has experienced a decline due to rapid environmental changes that have surpassed their ability to adapt. If the milkweed plant, which serves as a crucial source of food and habitat for these butterflies, continues to decrease, the species may face the threat of extinction. Therefore, it is necessary to take action and implement conservation measures to protect the Monarch Butterfly population and maintain the delicate balance between evolution and natural selection. The analysis highlighted a concerning decline in the Monarch Butterfly population over the past few decades. Some sites and counties emerged as significant habitats, providing a direction for conservation efforts.

## Resources Cited

- Larsen, C. S. (2019). Our Origins (5th ed.). W. W. Norton.
- Xerces Society Western Monarch Count, 2022. *Western Monarch Thanksgiving Count and New Year’s Count Data. Last updated by The Western Monarch Count on August 1, 2023. [www.westernmonarchcount.org](https://www.westernmonarchcount.org/)
**Please note before using this data:**
Check back periodically to make sure that you have the most recent version.
[Download data for all years (1997-2023)](https://www.westernmonarchcount.org/wp-content/uploads/2023/09/ThanksgivingCount-and-NewYearsCount_WMC-Data_2022-23_UPDATED-9-6-23.xlsx)
