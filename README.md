# Exploring the decline of Monarch Butterfly populations

![A Monarch Butterfly](https://assets.codepen.io/6566924/Monarch-Butterfly+%283%29.jpeg)

Image by Adobe Stock. [See License information](https://stock.adobe.com/license-terms)

## Part 1: Analysis

## Step 1: Choose 1 of the following animal situations to discuss:

 - [ ]  Anaconda invasion in the Everglades.
 - [ ]  The platypuses uniqueness
 - [ ]  Asian Carp invasion in the United States.
 - [X]  Monarch Butterfly population decline.
 - [ ] The Okapi uniqueness
 - [ ] The Aye-Aye's unique digit and eyes

## Step 2: Selected Situation: Monarch Butterfly population decline

## Step 3: Definitions:

### Natural Selection: 
Natural selection is a fundamental process in evolution. It refers to individuals' differential survival and reproduction in a population based on variations in their inherited traits. Individuals with traits that increase their chances of survival and reproduction in a particular environment are more likely to pass on their genes to the next generation. This process can lead to an increase in the frequency of advantageous traits in the population over time.(Larsen, 2019, p. 28).

### Evolution:
Evolution is the process of biological populations inheriting and adapting new characteristics over generations through natural selection, mutation, genetic drift, and gene flow, leading to the emergence of new species and adaptations to the environment.(Larsen, 2019, p. 27).



## Step 4: Analysis of Monarch Butterfly Population Decline





> [Exploring the decline of Monarch Butterfly population](#exploring-the-decline-of-monarch-butterfly-populations-with-python)
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


`README.md` 
Version 1.0: Last updated by K.S. on September 22, 2023.

## **Analysis of Monarch Butterfly Population Decline Using Python** 

![A Monarch Butterfly](https://assets.codepen.io/6566924/Monarch-Butterfly+%283%29.jpeg)


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


---
  
## Part 2: Questions

  

1. Linnaean classification, named after the Swedish botanist Carl Linnaeus, is a hierarchical system used for organizing and categorizing living organisms. It's based on a series of ranked levels starting from the broadest to the most specific: Kingdom, Phylum, Class, Order, Family, Genus, and Species. Each level in this hierarchy is termed a taxonomic rank. A key feature of Linnaean taxonomy is the binomial nomenclature, wherein each species is given a two-part name: the genus name followed by the species descriptor (e.g., Homo sapiens for humans). This system provides a universally accepted framework for the classification of organisms, ensuring clarity and consistency across scientific studies (Larsen, 2019, p.32).

  

2. The selected situational animal in this analysis is the Monarch Butterfly. Butterflies are insects and belong to the class *Insecta*. They do not possess the characteristics of mammals, such as hair, mammary glands, or three middle ear bones. Therefore, the Monarch Butterfly would not be classified in the class Mammalia

  

3. In the 1700s, the prevailing belief was that of catastrophism, suggesting that Earth's landscapes were shaped by great cataclysmic events. This was countered by the principle of uniformitarianism in the 19th century, which proposed that Earth's features were shaped by the same natural processes still in operation today, operating at similar intensities. The concept of evolution itself underwent significant changes. Jean-Baptiste Lamarck introduced an early theory of evolution in the early 1800s, known as Lamarckism, which proposed that organisms could pass on traits acquired during their lifetimes to their offspring. However, it was Charles Darwin's theory of natural selection in the mid-1800s that revolutionized evolutionary thought. Darwin proposed that species evolve over time through the differential survival and reproduction of individuals due to variations in their inherited traits. The 20th century saw the fusion of Mendelian genetics with Darwinian evolution, leading to the modern evolutionary synthesis, which describes the connection between the genotype and phenotype and shows how genetic variations lead to evolutionary change (Larsen, 2019)

  

4.Two scientific theories of evolution pre-Darwin that do not involve natural selection are Catastrophism and Lamarckism.

  

- Catastrophism: “catastrophism: The doctrine asserting that cataclysmic events (such as volcanoes, earthquakes, and floods), rather than evolutionary processes, are responsible for geologic changes throughout Earth’s history.” (Larsen, 2019, p.53).

  

This theory, primarily associated with the work of Georges Cuvier, posited that Earth's geology and biology were shaped by sudden, short-lived, and violent events. These catastrophic events were believed to have caused the extinction of species, which were then replaced by new species

  

- Lamarckism: Proposed by Jean-Baptiste Lamarck, this theory suggested that an organism could change during its lifetime in response to its environment. These changes were then passed on to its offspring. For instance, the continuous use or disuse of an organ would lead to it being strengthened or weakened in subsequent generations. “Lamarckism: First proposed by Lamarck, the theory of evolution through the inheritance of acquired characteristics in which an organism can pass on features acquired during its lifetime.” (Larsen, 2019, p.53).

  

6. Charles Darwin was hesitant to publish his theory of evolution by natural selection due to potential backlash from the religious community and the revolutionary nature of his ideas. He was aware that his findings would challenge the established beliefs about creation. Additionally, Darwin's grandfather, Erasmus Darwin, had earlier proposed a similar theory of evolution, which was met with criticism. This might have added to his hesitance. Furthermore, when Alfred Russel Wallace, a fellow naturalist, sent Darwin a manuscript outlining a similar theory of evolution through natural selection, Darwin was prompted to publish his findings. Wallace's work made Darwin realize the importance of presenting his extensive research to the public, which he did jointly with Wallace in 1858, followed by the publication of "On the Origin of Species" in 1859. “Charles Darwin’s observations provided the groundwork for his theory of natural selection, the basis of his 1859 book, On the Origin of Species.” (Larsen, 2019, p. 27).

## Resources Cited

-   Larsen, C. S. (2019). Our Origins (5th ed.). W. W. Norton.
    

Xerces Society Western Monarch Count, 2022. *Western Monarch Thanksgiving Count and New Year’s Count Data. Last updated by The Western Monarch Count on August 1, 2023. [www.westernmonarchcount.org](https://www.westernmonarchcount.org/)Please note before using this data: Check back periodically to make sure that you have the most recent version. [Download data for all years (1997-2023)](https://www.westernmonarchcount.org/wp-content/uploads/2023/09/ThanksgivingCount-and-NewYearsCount_WMC-Data_2022-23_UPDATED-9-6-23.xlsx)
Table of Contents

  

- [Exploring the decline of Monarch Butterfly populations](#exploring-the-decline-of-monarch-butterfly-populations)
  - [Part 1: Analysis](#part-1-analysis)
  - [Step 1: Choose 1 of the following animal situations to discuss:](#step-1-choose-1-of-the-following-animal-situations-to-discuss)
  - [Step 2: Selected Situation: Monarch Butterfly population decline](#step-2-selected-situation-monarch-butterfly-population-decline)
  - [Step 3: Definitions:](#step-3-definitions)
    - [Natural Selection:](#natural-selection)
    - [Evolution:](#evolution)
  - [Step 4: Analysis of Monarch Butterfly Population Decline](#step-4-analysis-of-monarch-butterfly-population-decline)
  - [**Analysis of Monarch Butterfly Population Decline Using Python**](#analysis-of-monarch-butterfly-population-decline-using-python)
  - [Dataset Overview](#dataset-overview)
  - [1. Loading the Data](#1-loading-the-data)
  - [2. Data Preprocessing](#2-data-preprocessing)
  - [3. Exploratory Data Analysis (EDA)](#3-exploratory-data-analysis-eda)
    - [3.1. Overall Monarch Butterfly Count Trend](#31-overall-monarch-butterfly-count-trend)
    - [3.2. Sites with Highest Butterfly Counts](#32-sites-with-highest-butterfly-counts)
    - [3.3. Counties with Highest Butterfly Counts](#33-counties-with-highest-butterfly-counts)
  - [4. Conclusions](#4-conclusions)
  - [Resources Cited](#resources-cited)
  - [Part 2: Questions](#part-2-questions)
  - [Resources Cited](#resources-cited-1)
  - [1.1. Part 1 Analysis](#11-part-1-analysis)
  - [1.2. Analysis of Monarch Butterfly Population Decline](#12-analysis-of-monarch-butterfly-population-decline)
  - [1.3. Dataset Overview](#13-dataset-overview)
  - [1.4. Loading the Data](#14-loading-the-data)
  - [1.5. Data Preprocessing](#15-data-preprocessing)
  - [1.6. Exploratory Data Analysis (EDA)](#16-exploratory-data-analysis-eda)
    - [1.6.1. Overall Monarch Butterfly Count Trend](#161-overall-monarch-butterfly-count-trend)
    - [1.6.2. Sites with Highest Butterfly Counts](#162-sites-with-highest-butterfly-counts)
    - [1.6.3. Counties with Highest Butterfly Counts](#163-counties-with-highest-butterfly-counts)
  - [1.7. Conclusions](#17-conclusions)
  - [1.8. Resources Cited](#18-resources-cited)
  - [Part 2: Questions](#part-2-questions-1)

  
  

---

  

## 1.1. Part 1 Analysis

Step 1: Choose 1 of the following animal situations to discuss:

  

Anaconda invasion in the Everglades.

The platypuses uniqueness

Asian Carp invasion in the United States.

Monarch Butterfly population decline.

The Okapi uniqueness

The Aye-Aye's unique digit and eyes

  
  
  
  
  

## 1.2. Analysis of Monarch Butterfly Population Decline

  

`README.md`

  

**Version 1.0: Last updated by K.S. on September 22, 2023.**

  

*This document provides a walkthrough of the steps taken to analyze the decline in the Monarch Butterfly population, utilizing a dataset that captures the count of butterflies across various sites over the years.*

  

## 1.3. Dataset Overview

  

The dataset contains the following columns:

  

-  `SITE ID`: Identifier for the site.

  

-  `SITE NAME`: Name of the site.

  

-  `COUNTY`: County where the site is located.

  

- Yearly columns from `1997` to `2022`: Count of Monarch Butterflies for each respective year.

  

- New Year's counts (e.g., `NY 2018-19`): Count of Monarch Butterflies for the New Year's period for the respective year.

  

## 1.4. Loading the Data

  

The first step in any data analysis is to load the dataset into a suitable environment for processing. Here, we use Python's Pandas library to load the dataset.

  

```python

import pandas as pd

  

# Load the dataset

  

data = pd.read_excel("/path/to/dataset.xlsx")

```

  

## 1.5. Data Preprocessing

  

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

  

## 1.6. Exploratory Data Analysis (EDA)

  

With the data preprocessed, the next step was to perform exploratory data analysis to draw insights.

  

### 1.6.1. Overall Monarch Butterfly Count Trend

  

To understand how the butterfly count changed over the years, the counts for each year were aggregated and visualized.

  

```python

  

# Aggregating the counts for each year

  

yearly_counts = data_cleaned[yearly_columns].sum()

  

# Visualization code would be placed here

```

### 1.6.2. Sites with Highest Butterfly Counts

  

To identify significant habitats, the dataset was aggregated by site to determine the top sites with the highest cumulative counts.

  

```python

  

# Aggregating counts for each site

  

site_counts = data_cleaned.groupby('SITE NAME').sum()[yearly_columns].sum(axis=1)

  

top_sites = site_counts.sort_values(ascending=False).head(10)

```

  

### 1.6.3. Counties with Highest Butterfly Counts

  

To guide regional conservation efforts, the dataset was aggregated by county.

  

```python

# Aggregating counts for each county

  

county_counts = data_cleaned.groupby('COUNTY').sum()[yearly_columns].sum(axis=1)

  

top_counties = county_counts.sort_values(ascending=False)

```

  

## 1.7. Conclusions

  

The population of Monarch Butterflies has experienced a decline due to rapid environmental changes that have surpassed their ability to adapt. If the milkweed plant, which serves as a crucial source of food and habitat for these butterflies, continues to decrease, the species may face the threat of extinction. Therefore, it is necessary to take action and implement conservation measures to protect the Monarch Butterfly population and maintain the delicate balance between evolution and natural selection. The analysis highlighted a concerning decline in the Monarch Butterfly population over the past few decades. Some sites and counties emerged as significant habitats, providing a direction for conservation efforts.

  

## 1.8. Resources Cited

  

- Larsen, C. S. (2019). Our Origins (5th ed.). W. W. Norton.

- Xerces Society Western Monarch Count, 2022. *Western Monarch Thanksgiving Count and New Year’s Count Data. Last updated by The Western Monarch Count on August 1, 2023. [www.westernmonarchcount.org](https://www.westernmonarchcount.org/)

**Please note before using this data:**

Check back periodically to make sure that you have the most recent version.

[Download data for all years (1997-2023)](https://www.westernmonarchcount.org/wp-content/uploads/2023/09/ThanksgivingCount-and-NewYearsCount_WMC-Data_2022-23_UPDATED-9-6-23.xlsx)

  --- 

- Image by Adobe Stock. [See License information](https://stock.adobe.com/license-terms)

## Part 2: Questions

1. Linnaean classification, named after the Swedish botanist Carl Linnaeus, is a hierarchical system used for organizing and categorizing living organisms. It's based on a series of ranked levels starting from the broadest to the most specific: Kingdom, Phylum, Class, Order, Family, Genus, and Species. Each level in this hierarchy is termed a taxonomic rank. A key feature of Linnaean taxonomy is the binomial nomenclature, wherein each species is given a two-part name: the genus name followed by the species descriptor (e.g., Homo sapiens for humans). This system provides a universally accepted framework for the classification of organisms, ensuring clarity and consistency across scientific studies (Larsen, 2019, p.32).

2. The selected situational animal in this analysis is the Monarch Butterfly. Butterflies are insects and belong to the class *Insecta*. They do not possess the characteristics of mammals, such as hair, mammary glands, or three middle ear bones. Therefore, the Monarch Butterfly would not be classified in the class Mammalia

3. In the 1700s, the prevailing belief was that of catastrophism, suggesting that Earth's landscapes were shaped by great cataclysmic events. This was countered by the principle of uniformitarianism in the 19th century, which proposed that Earth's features were shaped by the same natural processes still in operation today, operating at similar intensities. The concept of evolution itself underwent significant changes. Jean-Baptiste Lamarck introduced an early theory of evolution in the early 1800s, known as Lamarckism, which proposed that organisms could pass on traits acquired during their lifetimes to their offspring. However, it was Charles Darwin's theory of natural selection in the mid-1800s that revolutionized evolutionary thought. Darwin proposed that species evolve over time through the differential survival and reproduction of individuals due to variations in their inherited traits. The 20th century saw the fusion of Mendelian genetics with Darwinian evolution, leading to the modern evolutionary synthesis, which describes the connection between the genotype and phenotype and shows how genetic variations lead to evolutionary change (Larsen, 2019)

4.Two scientific theories of evolution pre-Darwin that do not involve natural selection are Catastrophism and Lamarckism.

- Catastrophism: “catastrophism: The doctrine asserting that cataclysmic events (such as volcanoes, earthquakes, and floods), rather than evolutionary processes, are responsible for geologic changes throughout Earth’s history.” (Larsen, 2019, p.53). This theory, primarily associated with the work of Georges Cuvier, posited that Earth's geology and biology were shaped by sudden, short-lived, and violent events. These catastrophic events were believed to have caused the extinction of species, which were then replaced by new species

- Lamarckism: Proposed by Jean-Baptiste Lamarck, this theory suggested that an organism could change during its lifetime in response to its environment. These changes were then passed on to its offspring. For instance, the continuous use or disuse of an organ would lead to it being strengthened or weakened in subsequent generations. “Lamarckism: First proposed by Lamarck, the theory of evolution through the inheritance of acquired characteristics in which an organism can pass on features acquired during its lifetime.” (Larsen, 2019, p.53).

6. Charles Darwin was hesitant to publish his theory of evolution by natural selection due to potential backlash from the religious community and the revolutionary nature of his ideas. He was aware that his findings would challenge the established beliefs about creation. Additionally, Darwin's grandfather, Erasmus Darwin, had earlier proposed a similar theory of evolution, which was met with criticism. This might have added to his hesitance. Furthermore, when Alfred Russel Wallace, a fellow naturalist, sent Darwin a manuscript outlining a similar theory of evolution through natural selection, Darwin was prompted to publish his findings. Wallace's work made Darwin realize the importance of presenting his extensive research to the public, which he did jointly with Wallace in 1858, followed by the publication of "On the Origin of Species" in 1859. “Charles Darwin’s observations provided the groundwork for his theory of natural selection, the basis of his 1859 book, On the Origin of Species.” (Larsen, 2019, p. 27).
