# Data Processing

## 1. Data Type

### Categorical

#### Binary (gender)
#### Nominal (Status)
#### Ordinal (ranking)
##### order matter but not difference between values

### Numerical

#### Discrete (score)
#### Continuous
##### Interval(year)
###### Where the difference between two values is meaningful
##### Ratio(age, height)
###### has interval variables features + a clear definition of 0

## 2. Data Exploration

### Univariate Analysis

#### For continuous features
##### Mean, Median, Min, Max, Range, STD
##### Quartile, IQR, Variance, Skewness, Histogram, Box Plot
#### For catgorical features
##### Frequency, Histogram
### Bi-variate analysis(to see correlation)
#### Histogram + Chart
#### Chi-Square test
#### T-test
#### ANOVA

## 3. Feature Selection
### Correlation / Covariance
#### Features should be uncorrelated together and highly correlated to what we want to predict
### Importance
#### Filter methods
##### Correlation(*)
##### Linear Discriminant Analysis
##### ANOVA
##### Chi-Square
#### Wrapper methods
#### Embedded methods

## 4. Feature Cleaning
### Target
#### Missing values (e.g., unknown values inchleding 9, NaN, etc...)
#### Special value (Inf, NA, NaN)
#### Outliers (out of range)

### Options
#### Remove feature from dataset
#### Impute
##### Hot-deck: replace by the cell value immediately prior to the data
##### Cold-deck
##### Mean substition
#### Regression: to predict the cell value

## 5. Feature Engineering
### Employ domain knowledge
### Extract features from raw data, improve predictions
### Decompose
#### Separate a feature into multiple features
### Discretization
#### Example for continuous features: partition of K is for a percent of [K, K+1)
#### Example for categorical features: combine multiple values into a single one
### Compose
#### But require expertise knowledge

## 6. Feature Encoding
### All features must be number (not string)
### One-hot encoding for categorical features
#### Must ensure that all features are linearly independent

## 7. Feature scaling and normalization

## 8. Dimensionality Reduction (often the last steps)

## 9. Dataset Construction
### Divide dataset into 3 sets: training/val/test sets
### Dividing Method
#### Small dataset: 70/30 without test set
#### Medium dataset: 60/20/20
#### Large Dataset: Validation and test set are big enough to evaluate methods (e.g., 10,000 over 1,000,000 image dataset)
### Cross validation