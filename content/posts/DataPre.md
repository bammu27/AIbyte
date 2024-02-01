+++
title = "Data Mining"
date = 2024-01-26T21:53:32+05:30
draft = false
tags = ["DataPreprocessing", "DataMining"]
categories = ["DataMining"]
+++


# Data Preprocessing in Data Mining

Data preprocessing is a crucial step in the data mining process, involving the cleaning, transforming, and integrating of raw data to make it suitable for analysis. The goal is to enhance data quality and prepare it for specific data mining tasks.

## Common Steps in Data Preprocessing:

### 1. Data Cleaning:

#### (a) Missing Data:

- **Ignore the tuples:** Suitable for large datasets with multiple missing values within a tuple.
- **Fill the missing values:** Options include manual filling, using attribute mean, or the most probable value.

#### (b) Noisy Data:

- **Binning Method:** Smooths data by dividing it into segments and applying methods like mean replacement or using boundary values.
- **Regression:** Fits data to a regression function for smoothing.
- **Clustering:** Groups similar data into clusters, helping identify and handle outliers.

### 2. Data Transformation:

- **Normalization:** Scales data to a common range, such as between 0 and 1 or -1 and 1.
- **Attribute Selection:** Constructs new attributes from the existing set to aid the mining process.
- **Discretization:** Converts continuous data into discrete categories using methods like equal-width binning or clustering.
- **Concept Hierarchy Generation:** Converts attributes from lower to higher levels in a hierarchy (e.g., converting "city" to "country").

### 3. Data Reduction:

Data reduction is vital for improving analysis efficiency and avoiding overfitting. Common steps include:

- **Feature Selection:** Choosing a subset of relevant features by analyzing correlations, mutual information, or using techniques like PCA.
- **Feature Extraction:** Transforming data into a lower-dimensional space while preserving essential information (e.g., PCA, LDA, NMF).
- **Sampling:** Selecting a subset of data points using methods like random, stratified, or systematic sampling.
- **Clustering:** Grouping similar data points to reduce dataset size (e.g., k-means, hierarchical clustering).
- **Compression:** Compressing the dataset for storage or transmission, preserving important information (e.g., wavelet compression, JPEG compression, gzip compression).

By performing these steps, data preprocessing ensures the quality of data, making the data mining process more efficient and results more accurate.

## Preprocessing in Data Mining

Data preprocessing is a technique in data mining that transforms raw data into a useful and efficient format.

### Steps Involved in Data Preprocessing:

1. **Data Cleaning:**
   - Handling irrelevant and missing parts in the data.
   - Methods include ignoring tuples with missing data and filling missing values using imputation or most probable values.
   
2. **Data Transformation:**
   - Converting data into a suitable format for analysis.
   - Involves normalization, attribute selection, discretization, and concept hierarchy generation.
   
3. **Data Reduction:**
   - Crucial for improving analysis efficiency.
   - Techniques include feature selection, feature extraction, sampling, clustering, and compression.

Data preprocessing is essential for ensuring the quality and accuracy of analysis results. Specific steps may vary based on data nature and analysis goals.

## Data Cleaning in Data Mining

Data cleaning is a crucial step in the data mining process, involving the removal of noisy, irrelevant, or incomplete data. It is vital for data quality and accuracy, ensuring that data is suitable for analysis.





### Missing Data:
- **Ignore the tuple:** Suitable for large datasets with multiple missing values within a tuple.
- **Fill the missing values:** Options include manual filling, using attribute mean, or the most probable value.
- **Predict the missing value:** Use machine learning algorithms to predict the missing value.

### Example of Missing Data:
```python
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f',
'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
print(df)
```
Output:
```python
        one       two     three
a  0.469112 -0.282863 -1.509059
b       NaN       NaN       NaN
c  1.212112 -0.173215  0.119209
d       NaN       NaN       NaN
e -1.044236 -0.861849 -2.104569
f  0.721555 -0.424972  0.567020
g       NaN       NaN       NaN
h  0.110923  0.375698 -0.600639
```
### Replacing Missing Values:
```python
print("NaN replaced with '0':")
print(df.fillna(0))
```
Output:
```python
        one       two     three
a  0.469112 -0.282863 -1.509059
b       0      0         0
c  1.212112 -0.173215  0.119209
d       0      0         0
e -1.044236 -0.861849 -2.104569
f  0.721555 -0.424972  0.567020
g       0      0         0
h  0.110923  0.375698 -0.600639
```
### Removing Missing Values:
```python
print("Row with nan is removed")
print(df.dropna())
print("Column with nan is removed")
print(df.dropna(axis=1))
```
Output:
```python
        one       two     three
a  0.469112 -0.282863 -1.509059
c  1.212112 -0.173215  0.119209
e -1.044236 -0.861849 -2.104569
f  0.721555 -0.424972  0.567020
h  0.110923  0.375698 -0.600639
```
### Missing value replaced with mean and mod

```python
import pandas as pd
import numpy as np

df.fillna(df.mean(axis=1), inplace=True)
print(df)
```
Output:
```python
        one       two     three
a  0.469112 -0.282863 -1.509059
b -0.282863 -0.282863 -0.282863
c  1.212112 -0.173215  0.119209
d -0.282863 -0.282863 -0.282863
e -1.044236 -0.861849 -2.104569
f  0.721555 -0.424972  0.567020
g -0.282863 -0.282863 -0.282863
h  0.110923  0.375698 -0.600639
```

### Noisy Data:
- **Binning Method:** Smooths data by dividing it into segments and applying methods like mean replacement or using boundary values.
### Types of binning:
-**Equal Frequency Binning**: bins have an equal frequency.

-**Equal Width Binning** : bins have equal width with a range of each bin are defined as [min + w], [min + 2w] …. [min + nw] where w = (max – min) / (no of bins).


### Example for each type of binning:

-**Equal Frequency Binning**:
[5, 10, 11, 13, 15, 35, 50, 55, 72, 92, 204, 215] 

Number of observations = 12
Number of Bins = 4
So, the frequency of each bin = 12/4 = 3
So, the bins according to equal frequency binning will be:
[5, 10, 11], [13, 15, 35], [50, 55, 72], [92, 204, 215]

-**Equal Width Binning**:
[5, 10, 11, 13, 15, 35, 50, 55, 72, 92, 204, 215]

Number of observations = 12
Number of Bins = 4
So, the width of each bin = (215 – 5)/4 = 52.5
So, the bins according to equal width binning will be:
[5, 57.5], [57.5, 110], [110, 162.5], [162.5, 215]

- **Smoothing by bin means:**

[5, 10, 11, 13, 15, 35, 50, 55, 72, 92, 204, 215]

Number of observations = 12
Number of Bins = 4

m1 = (5+10+11)/3 = 8.67
m2 = (13+15+35)/3 = 21
m3 = (50+55+72)/3 = 59
m4 = (92+204+215)/3 = 170.33

So, the bins according to bin means will be:
[8.67, 8.67, 8.67], [21, 21, 21], [59, 59, 59], [170.33, 170.33, 170.33]


- **Smoothing by bin median:**

[5, 10, 11, 13, 15, 35, 50, 55, 72, 92, 204, 215]

Number of observations = 12
Number of Bins = 4

m1 = 10
m2 = 15
m3 = 55
m4 = 92

So, the bins according to bin means will be:
[10, 10, 10], [15, 15, 15], [55, 55, 55], [92, 92, 92]


- **Smoothing by bin boundaries:**

[5, 10, 11, 13, 15, 35, 50, 55, 72, 92, 204, 215]

Number of observations = 12
Number of Bins = 4

So, the bins according to bin means will be:
[5, 11, 11], [13, 15, 15], [35, 55, 55], [72, 215, 215]


- **Regression:**
- Fits data to a regression function for smoothing.
- **Clustering:** Groups similar data into clusters, helping identify and handle outliers.



### Data  Transformation:

- **Normalization:** Scales data to a common range, such as between 0 and 1 or -1 and 1.

- **min-max normalization:**
- It is the simplest method and consists in rescaling the range of features to scale the range in [0, 1] or 
 Selecting the target range depends on the nature of the data. The general formula is given as:


dn = (d – min) / (max – min)

- **z-score normalization:**

- It is a normalization technique that rescales the distribution of values so that the mean of the values is 0 and the standard deviation is 1.

- The general formula is given as:

Z = (X – μ) / σ

- **Attribute Selection:** Constructs new attributes from the existing set to aid the mining process.

- **Discretization:** Converts continuous data into discrete categories using methods like equal-width binning or clustering.

- **Concept Hierarchy Generation:** Converts attributes from lower to higher levels in a hierarchy (e.g., converting "city" to "country").

### Data Reduction:

- Data reduction is vital for improving analysis efficiency and avoiding overfitting. Common steps include:

- **Feature Selection:** Choosing a subset of relevant features by analyzing correlations, mutual information, or using techniques like PCA.

- **Feature Extraction:** Transforming data into a lower-dimensional space while preserving essential information (e.g., PCA, LDA, NMF).

- **Sampling:** Selecting a subset of data points using methods like random, stratified, or systematic sampling.

- **Clustering:** Grouping similar data points to reduce dataset size (e.g., k-means, hierarchical clustering).

- **Compression:** Compressing the dataset for storage or transmission, preserving important information (e.g., wavelet compression, JPEG compression, gzip compression).


By performing these steps, data preprocessing ensures the quality of data, making the data mining process more efficient and results more accurate.



## Data Mining:

- Data mining is process of discovering interesting patterns and knowledge from large amounts of data.
- The data sources can include databases, data warehouses, the web, other information repositories or data that are streamed into the system dynamically.
- Data mining applications can be used to extract patterns from data sets and can be used to predict future trends and behaviors, allowing businesses to make proactive, knowledge-driven decisions.

### Why Data Mining?

- The explosive growth of data collected by businesses and the scientific community has fueled the need for data mining techniques that can extract useful knowledge from large volumes of data.
- Data mining techniques are used in many research areas, including mathematics, cybernetics, genetics and marketing.
- Data mining is also used in a variety of applications such as bioinformatics, medical diagnosis, machine fault diagnosis, and speech recognition.

### Types of Data can be mined:

- Databases
- Data warehouses
- Transactional databases
- Advanced DB and information repositories
- Object-oriented and object-relational databases
- Spatial databases
- Time-series databases
- Text databases and multimedia databases
- Heterogeneous and legacy databases
- Graph and World Wide Web
- Data streams and sensor data

### Types of Patterns:

- Classification
- Regression
- Clustering
- Summarization
- Dependency modeling
- Change and deviation detection
- Sequential patterns
- Prediction


### Types of DataMining

- Descriptive Data Mining
- Predictive Data Mining
- Prescriptive Data Mining
- Association Rule Learning
- Clustering


### Data Mining Technology:

- Weka
- RapidMiner
- Rattle GUI
- Orange
- Knime
- Apache Mahout

#### Machine Learning tools:
- Scikit-learn
- TensorFlow
- Keras
- PyTorch
- Theano

#### Data Visualization tools:
- Tableau
- QlikView
- Power BI
- Sisense
- D3.js


### Applications of Data Mining:

- Market Analysis and Management
- Corporate Analysis and Risk Management
- Fraud Detection
- Healthcare Management
- Other Applications

### Data Mining Process:

- Setting Objective
- Data Gathering
- Data Preparation
- Model Building
- Evaluation
- Deployment


### Challenges in Data Mining:
- Mining methodology and user interaction issues
- Performance and efficiency
- Data mining query languages and ad hoc data mining
- Operationalization of data mining
- Handling noisy or incomplete data
- Pattern evaluation
- Handling relational and complex types of data
- Handling data streams and sensor data


### Conclusion:
- Data mining is a powerful tool that can help businesses and scientific organizations make better decisions.
- Data mining techniques can be used to extract useful knowledge from large volumes of data.
- Data mining is also used in a variety of applications such as bioinformatics, medical diagnosis, machine fault diagnosis, and speech recognition.
- Data mining is a process of discovering interesting patterns and knowledge from large amounts of data.
- Data mining applications can be used to extract patterns from data sets and can be used to predict future trends and behaviors, allowing businesses to make proactive, knowledge-driven decisions.

## References:
- https://www.geeksforgeeks.org/data-preprocessing-in-data-mining/
- https://www.geeksforgeeks.org/data-cleaning-in-data-mining/
- https://www.geeksforgeeks.org/data-transformation-in-data-mining/






















