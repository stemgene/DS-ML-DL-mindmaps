# Data Preprocessing

# Model
## Regression
### <p>Linear Regression<br>(Source1: CH5/7 Linear Regression)</p>
#### Can access to the whole spectrum of features at once. 
##### <p>$w = (X^TX)^{-1}X^Ty$<br>(Source: CH5/11 Training Linear Regression)</p>
##### Computational complexity : T(n, p) ~ np^2 (n is observations, p is features)
#### <p>Gradient Descent:<br>(Source 3/12 Gradient Descent)</p> 
##### An iterative algorithm for finding the loss function minimum. It moves in the direction of the negative gradient and gradually approximates the minimum.
##### <p>$x^t=x^{t-1}-\eta\nabla(x^{t-1})$</p>
###### <p>For each iteration, the computation complicity of gradient is O(np)<br>(Source: CH4/12 GD for LR)</p>
##### Advantages:
###### It works faster with large datasets in linear regressions with the MSE loss function.
###### It is also suitable for linear regressions with other loss functions (not all of them have formulas).
###### It can be used for training neural networks which also lack direct formulas.
##### <p>Stochastic Gradient Descent<br>(Source: CH4/12 SGD)</p>
###### Using random mini-batch rather than whole dataset
## Classification
### <p>Logistic Regression<br>(Source1: CH4/7 Logistic Regression)</p>
#### Sigmoid function
## Both regression and classification models
### <p>Decision Tree<br>(Source1: CH2/7 Models and Algorithms)<br>(Source: Sprint7/CH03 Experiments with Decision Trees)</p>
### <p>Random Forest: Vote by multiple trees and get the average assessment<br>(Source1: CH4/7 New Models: Random Forest)</p>
### Boosting models: AdaBoost, Gradient Boosting Machine(GBM),XGBoost, LightGBM
#### <p>Gradient Boosting <br>(Source CH5/12)</p>
##### $Y_N=argminL(y,a_{N-1}(x)+Yb_N(x))$
##### Suitable for different loss function that have derivatives, both regression and logarithmic in a binary classification task
##### <p>Gradient Boosting Regularization<br>(Source CH5/12)</p>
###### Step size reduction: $$Y_N=argminL(y,a_{N-1}(x)+\eta Yb_N(x))$$
###### SGB (Stochastic GB): working with subsamples rather than the whole set. 
### <p>Neural Network<br>(Source: CH4/12)</p>
## Loss Function 
### Loss Function (single sample) vs Cost Function (Avg at whole dataset)
## Optimizer
### SGD (Stochastic Gradient Descent)
#### with Momentum (with EWMA)
#### RMSprop (Root Mean Square propagation)
#### ADAM (Adaptive moment estimate algorithm)
### Learning Rate
#### With rate decay

# Train and validate

# Evaluate
## Metrics
### Accuracy = corrects / dataset size
### Classification Metrics
#### Confusion Matrix
##### <p>Precision: Minimize errors when finding the positive observations, detects whether the model is overdoing it by assigning too many positive labels. = TP/TP+FP<br>(Source: CH3/7 Evaluation Metrics<br>(Source: CH3/8 Precision)</p>
##### <p>Recall: Priority to find all positive observations = TP/TP+FN<br>(Source: CH3/7 Evaluation Metrics<br>(Source: CH3/8 Recall)</p>
##### F1-score: 2\*precision\*recall/(precision+recall)
##### PR-curve (Source: CH4/8)
##### FPR = FP/N, TPR = TP/P (SOurce: CH4/8): won't imply division by zero.
###### If decrease the threshold, FPR and TPR will increase
##### ROC curve (Source: CH4/8)
###### X-axis: FPR, Y-axis: TPR
###### AUC-ROC value (Area Under Curve ROC) 
#### Deal with imbalanced data
##### Upsampling & Downsampling (Source: CH4/8)
##### Adjust threshold (Source: CH4/8 Threshold adjustment)

### Regression Metrics
#### <p>Mean Square Error (MSE/RMSE) <br>(Source: CH5/7 Mean Square Error)<br>(Source: CH5/7 MSE Calculation)<br>(Source: CH5/7 MSE Interpretation)<br>(Source: CH5/8 MSE in a regression task)</p>
##### <p>more sensitive to large values: significant errors strongly affect the final RMSE value.<br>(Source: CH5/8 The Effect of Dispersion on Metrics)</p>
#### <p>$R^2 metric = 1 - \frac{Model MSE}{Mean MSE}$<br>(Source: CH5/8 Coefficient of Determination)</p>
##### To avoid constantly comparing the model to the mean
##### R2 equals one only if the MSE value is zero. Such model would perfectly predict all the answers.
##### R2 is zero: the model works as well as the mean.
##### When R2 is negative, the model quality is very low.
##### R2 can't have values greater than one.
#### <p>$MAE = \frac{1}{N}\sum{|y_i - \hat{y_i}|}$<br>(Source: CH5/8 Mean Absolute Error)</p>
- Not sensitive to abnormal values

## Bias & Variance
### High Bias: Underfitting (Source: CH3/7 Underfitting and overfitting)
### High Variance: Overfitting (Source: CH3/7 Underfitting and overfitting)

# Model Improvements
## Hyperparameters (Source: CH4/7 Hyperparameters)
## <p>Cross-Validation: assess and improve the performance of a predictive model by iteratively training and evaluating it on different subsets of the data.<br>(Source: CH4/9)</p>
### ![Cross_validation]("./assets/Supervised_Learning/cross-validation.png")
## Reduce Overfitting
### Regularization (Source: CH4/12 LR Regularization)
#### lower the weight value including the scalar product of the weights in the loss function formula
## Ensemble (Source: CH05/12 Ensembles and Boosting)
### mean error of a group of models is less significant than their individual errors.
### Methods: Voting, Average, Bagging, Random Forest
## Boosting
### sequentially trains a series of models. Each model attempts to correct the errors made by the previous model and each model is weighted based on the performance of the previous models, allowing misclassified samples from earlier models to receive more attention in subsequent models.
### $a_N(x)=a_{N-1}(x)+y_Nb_N(x)$, where $b(x)$ is the base learner prediction

# Deploy