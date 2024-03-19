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

### Check data/target leakage: information about the target accidentally leaks into the features.

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
### Imbalanced data
#### Upsampling (Source: CH4/8 Upsampling)
##### Steps:
###### 1. Split the training sample into negative and positive observations;
###### 2. Duplicate the positive observations several times;
###### 3. Create a new training sample based on the data obtained;
###### 4. Shuffle the data: identical questions following one another will not help the training.
#### Downsampling (Source: CH4/8 Downsampling)
##### Steps:
###### 1. Split the training sample into negative and positive observations;
###### 2. Randomly drop a portion of the negative observations; `features_train.sample(frac=0.1, random_state=12345)`
###### 3. Create a new training sample based on the data obtained;
###### 4. Shuffle the data. Make sure the positive data doesn't follow the negative data: this will make it harder for the algorithms to learn.

## 6. Feature Encoding
### Purpose: 1. All features must be number (not string), 2. Must ensure that all features are linearly independent
### Methods
#### <p>One-hot encoding (OHE) for categorical features<br>(Source: CH2/8 One-hot Encoding)</p>
##### <p>Dummy feature trap<br>(Source: CH2/8 Dummy Trap)</p>: One of columns will be calculate by others, needs to be dropped. `drop_first=True`
#### Not for Tree-based models. Not for ordinal variables. Not for high cardinality variable
#### <p>Label Encoding<br>(Source: CH2/8 Label Encoding)</p>
##### Only for tree-based models, bad for Logistic/Linear Regression. Tree-based models can process the only 1 feature at a time.
##### `sklearn.preprocessing.LabelEncoder` for encoding a single column
##### `sklearn.preprocessing.OrdinalEncoder` for encoding two or more columns at a time
#### <p>Ordinal Encoding<br>(Source: CH2/8 Ordinal Encoding)</p>
##### Order matters: "excellent," "good," and "bad."
##### Method 1: <p><code class="language-python">temperature_dict = {'cold': 0, 'warm': 1, 'hot': 2}<br>df['temperature'] = df['temperature'].map(temp_dict)</code></p> 
##### Method 2: `sklearn.preprocessing.OrdinalEncoder` and specify the categories parameters

## 7. Feature scaling and normalization
### All features should be considered equally important before the algorithm's execution.
### Min-Max Scaling: return [0, 1]
### Standardization: return N(0, 1)

## 8. Dimensionality Reduction (often the last steps)

## 9. Dataset Construction
### Randomness in Learning Algorithms (Source: Sprint7/CH03)
#### `random_state`
### Divide dataset into 3 sets: training/val/test sets (Source: CH4/7 Validation Dataset)
### Dividing Method (Source: CH4/7 Splitting Data into Two Sets)
#### Small dataset: 70/30 without test set
#### Medium dataset: 60/20/20
#### Large Dataset: Validation and test set are big enough to evaluate methods (e.g., 10,000 over 1,000,000 image dataset)
### Cross validation