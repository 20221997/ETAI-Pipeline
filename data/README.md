# Baseline Predictive Pipeline -- ETAI - Exploratory Topics of Artificial Intelligence.
### 20221997 - Suelen Karina Faruk 

## Week 2 - Conclusions:
#### Logistic Regression before cleaning the data:
Logistic Regression:
Train accuracy: 0.679
Test accuracy:  0.680
Gap (train - test): -0.001

#### Conclusions:
This model performs well on training but also performs well on testing with these results we can say that the model is less likely to overfit as the gap between train and test is very low.

#### Decision Three after cleaning the data:
Decision Three: 
Train accuracy: 0.829
Test accuracy:  0.626
Gap (train - test): +0.203


#### Conclusions:
This model performs well on the training data, although the gap between the training and test accuracy gives us evidence of possible overfitting. The test accuracy shows that the model is also able to make predictions on unseen data, although its performance is lower than on the training data.

#### Best Model:
Based on test accuracy and the train-test gap, Logistic Regression performs better than the Decision Tree in these experiments. It achieves higher test accuracy and has a much smaller gap between training and test performance, giving us less evidence of overfitting. Besides the smaller gap(train-test), the model has similar scores in train and test which gives us further evidence that the model will be less likely to overfit.


## Week 3 - Conclusions:
#### Logistic Regression after cleaning the data: 
Logistic Regression:
Train accuracy: 0.678
Test accuracy:  0.655
Gap (train - test): +0.023 

#### Conclusions:
The gap increased enough to say Although the model has an overall test accuracy of 65.5%, it's recall for people who actually reoffended is only 51%. Therefore, the overall accuracy does not mean that the model identifies reoffenders particularly well.
The model has similar performance on the training and test data.The small train-test gap is another metric that gives us less evidence of overfitting, as the model's performance does not decrease substantially when applied to unseen data.


#### Decision Three after cleaning the data:
Decision Three: 
Train accuracy: 0.691
Test accuracy:  0.642
Gap (train - test): +0.049

#### Conclusions:
The training accuracy decreased, but the test accuracy increased. This suggests that the model was fitting the training data less closely and was able to generalize better to unseen data, but if we had just the train-test gap result I would say that here this model is less likely to overfit.

#### Best model:
The Logistic Regression that I run before cleaning it has the strongest results among all the models tested.

Compared with Logistic Regression after cleaning, the model has a higher test accuracy (68.0% vs. 65.5%) and a smaller train-test gap (-0.001 vs. +0.023). Compared with the Decision Tree after cleaning, it also has a higher test accuracy (68.0% vs. 64.2%) and a smaller train-test gap (-0.001 vs. +0.049). These results give us less evidence of overfitting and indicate that the model generalizes more consistently to unseen data.

## Week 4 - Conclusions:

### Model Results after cross-validation:

### Logistic Regression:

Train accuracy: 0.675
Validation accuracy: 0.672
Gap (train - validation): +0.003

### Conclusions:

The Logistic Regression model has a validation accuracy of 67.2%. The train-validation gap is very small (+0.003), which gives little evidence of overfitting. The model also has similar performance across the five validation folds, with a validation standard deviation of 0.013.

However, the classification report shows that the recall for people who actually reoffended (class 1) is only 51%. Therefore, the overall accuracy does not mean that the model identifies reoffenders particularly well.

### Random Forest:

Train accuracy: 0.733
Validation accuracy: 0.650
Gap (train - validation): +0.083

### Conclusions:

The Random Forest has a higher training accuracy than Logistic Regression (73.3%), but its validation accuracy is lower at 65.0%. The train-validation gap of +0.083 gives more evidence of overfitting than the Logistic Regression model.

However, the Random Forest has a higher recall for people who actually reoffended, at 58%, compared with 51% for Logistic Regression. This means that although its overall validation accuracy is lower, it identifies a larger proportion of the actual reoffenders in these cross-validation results.


### Decision Tree:

Train accuracy: 0.694
Validation accuracy: 0.605
Gap (train - validation): +0.089

### Conclusions:

The Decision Tree has a training accuracy of 69.4%, but its validation accuracy decreases to 60.5%. The train-validation gap is +0.089, which gives evidence of overfitting.

Its recall for people who actually reoffended is 50%, which is similar to the Logistic Regression model's 51% but with lower overall validation accuracy. The Decision Tree therefore shows a larger difference between training and validation performance than Logistic Regression.

### Dummy:

Train accuracy: 0.549
Validation accuracy: 0.549
Gap (train - validation): 0.000

### Conclusions:

The Dummy model provides a baseline of 54.9% validation accuracy. It has a gap of approximately zero because it always predicts the majority class.

However, its recall for class 1 is 0%, meaning that it does not identify any of the people who actually reoffended. Therefore, accuracy alone is not sufficient to evaluate the performance of this type of classification problem.

## Week 6 - Conclusions:

### Model Results after Cross-Validation:

All models were evaluated using 5-fold stratified cross-validation with accuracy as the evaluation metric. The development set contained 5,771 observations, while 1,443 observations were reserved for the locked test set and were not used for model evaluation or selection.

### Logistic Regression:

Train accuracy: 0.675  
Validation accuracy: 0.672  
Gap (train - validation): +0.003  
Validation standard deviation: 0.013

#### Conclusions:

Logistic Regression achieved a validation accuracy of 67.2%, with a very small train-validation gap of +0.003. This suggests that the model generalizes consistently across the validation folds, with little evidence of overfitting.

However, its recall for class 1 is only 51%, meaning that it correctly identifies approximately half of the people who actually reoffended.

### Decision Tree:

Train accuracy: 0.693  
Validation accuracy: 0.605  
Gap (train - validation): +0.088  
Validation standard deviation: 0.020

#### Conclusions:

The Decision Tree achieved a training accuracy of 69.3%, but its validation accuracy decreased to 60.5%. The train-validation gap of +0.088 suggests overfitting, since the model performs noticeably better on the training folds than on unseen validation observations.

Its recall for class 1 is 50%, which is lower than that of the other ensemble models tested.

### Random Forest:

Train accuracy: 0.733  
Validation accuracy: 0.650  
Gap (train - validation): +0.083  
Validation standard deviation: 0.018

#### Conclusions:

Random Forest achieved a training accuracy of 73.3%, but its validation accuracy was 65.0%. The gap of +0.083 suggests that the model is fitting the training data more closely than it generalizes to unseen observations.

However, its recall for class 1 was 58%, higher than Logistic Regression's 51%. Therefore, although Random Forest has lower overall validation accuracy, it identifies a larger proportion of actual reoffenders.

### Oblique Random Forest:

Train accuracy: 0.761  
Validation accuracy: 0.647  
Gap (train - validation): +0.114  
Validation standard deviation: 0.011

#### Conclusions:

Oblique Random Forest achieved the highest training accuracy among the evaluated models, at 76.1%, but its validation accuracy was only 64.7%.

The train-validation gap of +0.114 is the largest among the models, suggesting stronger overfitting. This indicates that higher training accuracy does not necessarily result in better generalization to unseen data.

Its recall for class 1 was 57%, which is higher than Logistic Regression's recall but slightly lower than Random Forest's.

### AdaBoost:

Train accuracy: 0.682  
Validation accuracy: 0.676  
Gap (train - validation): +0.006  
Validation standard deviation: 0.012

#### Conclusions:

AdaBoost achieved the highest validation accuracy among the evaluated models, at 67.6%. Its training accuracy was 68.2%, resulting in a small train-validation gap of +0.006, which gives little evidence of overfitting.

Its recall for class 1 was 54%, higher than Logistic Regression's 51%, although lower than Random Forest's 58%.

These results suggest that AdaBoost provides a good balance between validation accuracy, generalization, and the ability to identify people who actually reoffended.

### Best Model:

Based on the current cross-validation results, AdaBoost is the leading candidate, with the highest validation accuracy (67.6%) and a small train-validation gap (+0.006).

However, its advantage over Logistic Regression is only 0.4 percentage points, which is smaller than the validation standard deviation of either model. Therefore, we cannot conclude that AdaBoost is clearly superior based on these results alone.

Random Forest achieves the highest recall for class 1 (58%), which is also important because the objective is to identify people who actually reoffended.

For now, I would choose AdaBoost based on validation accuracy and its small generalization gap, while keeping Logistic Regression as a strong alternative. The final decision should also consider nested cross-validation, fairness, and performance on the locked test set after model selection is complete.
