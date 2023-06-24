# Week_14_Challenge
USYD FinTech Bootcamp Week 14 Homework
*Coded in Jupyter Notebook using Python*


# Section 1: Establish a Baseline Performance

**Parameters:**
short window: 4
long window: 100
training data offset: 3 months

![Strategy Returns](/Images/Strategy_Returns.png "Strategy Returns")

## Classification report associated with the SVC model predictions
                precision    recall  f1-score   support

        -1.0       0.43      0.04      0.07      1804
         1.0       0.56      0.96      0.71      2288

    accuracy                           0.55      4092
   macro avg       0.49      0.50      0.39      4092
weighted avg       0.50      0.55      0.43      4092

![Actual vs Strategy Returns](/Images/Actual_vs_Strategy_Returns.png "Actual vs Strategy Returns")

# Section 2: Tune the Baseline Trading Algorithm

## Step 1: Adjusting the size of the training dataset
**Parameters:** training data offset: 6 months

                precision    recall  f1-score   support

        -1.0       0.44      0.02      0.04      1732
         1.0       0.56      0.98      0.71      2211

    accuracy                           0.56      3943
   macro avg       0.50      0.50      0.38      3943
weighted avg       0.51      0.56      0.42      3943

![Actual vs Strategy Returns - Extended Training Data](/Images/Actual_vs_Strategy_Returns_Extended_Training_Data.png "Actual vs Strategy Returns - Extended Training Data")

**Parameters:** training data offset: 1 month

                precision    recall  f1-score   support

        -1.0       0.37      0.03      0.06      1828
         1.0       0.56      0.96      0.70      2324

    accuracy                           0.55      4152
   macro avg       0.47      0.49      0.38      4152
weighted avg       0.48      0.55      0.42      4152

![Actual vs Strategy Returns - Reduced Training Data](/Images/Actual_vs_Strategy_Returns_Reduced_Training_Data.png "Actual vs Strategy Returns - Reduced Training Data")


**What impact resulted from increasing or decreasing the training window?** Increasing the training window, improved the fit of the model earlier in the data whilst under performing the returns immediately after and exaggerate the returns from 2020 onward. The impact on precisions and recall metrics were not too significant and so the test will proceed with leaving the window at 3 months.

## Step 2: Adjusting the SMA input features
**Parameters:**
short window: 20
long window: 100
*The model did not work with these parameters*


**Parameters:**
short window: 50
long window: 200

                precision    recall  f1-score   support

        -1.0       0.45      0.20      0.28      1740
         1.0       0.56      0.81      0.67      2227

    accuracy                           0.54      3967
   macro avg       0.51      0.51      0.47      3967
weighted avg       0.52      0.54      0.50      3967

![Actual vs Strategy Returns - Increased SMA Windows 50 & 200](/Images/Actual_vs_Strategy_Returns_Increased_SMA_Windows_50_200.png "Actual vs Strategy Returns - Increased SMA Windows 50 & 200")

**Parameters:**
short window: 4
long window: 80

                precision    recall  f1-score   support

        -1.0       0.41      0.06      0.10      1806
         1.0       0.56      0.93      0.70      2289

    accuracy                           0.55      4095
   macro avg       0.48      0.50      0.40      4095
weighted avg       0.49      0.55      0.43      4095

![Actual vs Strategy Returns - Increased SMA Windows 4 & 80](/Images/Actual_vs_Strategy_Returns_Increased_SMA_Windows_4_80.png "Actual vs Strategy Returns - Increased SMA Windows 4 & 80")



**What impact resulted from increasing or decreasing either or both of the SMA windows?** Increasting the SMA windows reduced the fit of the model, however, decreasing the long window resulted in a better overall fit, specially around the bigger dips and gains in the graph.

## Step 3: The set of parameters that best improved the trading algorithm returns
Based on the tests above the below parameters are chosen for the trading algorthims. Further test of the training data and SMA windows can further improve this model.

**Parameters:**
training data offset: 3 months
short window: 4
long window: 80

                precision    recall  f1-score   support

        -1.0       0.41      0.06      0.10      1806
         1.0       0.56      0.93      0.70      2289

    accuracy                           0.55      4095
   macro avg       0.48      0.50      0.40      4095
weighted avg       0.49      0.55      0.43      4095

![Actual vs Strategy Returns - Increased SMA Windows 4 & 80](/Images/Actual_vs_Strategy_Returns_Increased_SMA_Windows_4_80.png "Actual vs Strategy Returns - Increased SMA Windows 4 & 80")

# Section 3: Evaluate a New Machine Learning Classifier

