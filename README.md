# Credit Risk Analysis

## Overview
This project's purpose was to determine if supervised machine learning techniques were an accurate way to determine credit risk. Given that there are very few defaults in the many many credit transactions, the data set is inherently unbalanced. To try to mitigate this imbalance, we will oversample, undersample and combination sample prior to training the model, as well as running two ensemble algorithms. After running all six models, we will determine which performs best, and if it is accurate enough to be considered useful.
## Results
### Oversampling
* Random OverSampler
    * Perhaps not a horrible start, but while it is able to acurately predict 72% of the high risk scenarios, it also mis-classifies low risk 40% of the time.
<img src= "https://raw.githubusercontent.com/AlexisBurton/Src-images/master/17/ROSData.png">
    * From a creditor's standpoint, this would likely both carry too much risk by mislabeling a quarter of potentially high risk cases as low risk, and create too great an opportunity loss by mislabeling much of the low risk as high.
    
* SMOTE
    * Similar to the Random OverSampler, it's not horrible, but still not great. Compared to the Random OverSampler, both True Positive and False Positive went down. 
<img src= "https://raw.githubusercontent.com/AlexisBurton/Src-images/master/17/SMOTEData.png">
    * Again from a creditor's standpoint, there is too much risk. However given SMOTE's average f1 score of 0.81, it is preferable to Random Oversampling, which has an f1 of 0.74 <br/>
### UnderSampling
* Cluster Centroid
    * Undersampling proved very unreliable in accurately predicting risk. With high and low risk recalls of 0.69 and 0.4 respectively, cluster centroid sampling was similarly accurate at predicting high risk, but also misclassified the majority (60%) of low risk samples as high risk.
<img src= "https://raw.githubusercontent.com/AlexisBurton/Src-images/master/17/CCData.png">
    * With an average f1 score of 0.56, the only way a creditor would consider using this method is if their previous approval model had been a coin flip.<br/>
### Combination Sampling
* SMOTEEN
    * Combination sampling was able to improve the high risk recall as compared to over- or under- sampling, but did nothing to improve the false positive rate, with a low risk recall of 0.59 being in between the other recall rates.
<img src= "https://raw.githubusercontent.com/AlexisBurton/Src-images/master/17/SMOTEENData.png">
    * The overall numbers for SMOTEEN sampling were very similar to the Random OverSampler, so again there is too much risk for a creditor for the same reasons.
### Ensemble Testing
* Balanced Random Forest Classifier
    * Here we see the first significant improvement in low risk recall at 0.87. The high risk recall of 0.7 is similar to the over/ under- sampling methods.
<img src= "https://raw.githubusercontent.com/AlexisBurton/Src-images/master/17/BRFData.png">
    * With a balanced accuracy score of 0.789 and an average f1 of 0.93, this method is one a creditor could use with a fair amount of confidence, but would likely want to use it as a preliminary filter, with additional test criteria to be used on the "approved" group.
* Easy Ensemble Ada Boost Classifier
    * This is the first test to show true promise. With a balanced accuracy score of 0.932, high and risk recalls of 0.92 & 0.94 respectively, and and acverage f1 of 0.97, this model could be used as a stand alone test for credit worthiness.
<img src= "https://raw.githubusercontent.com/AlexisBurton/Src-images/master/17/EECData.png">


## Summary
While certainly not perfect, the Easy Ensemble Ada Boost Classifier would be an acceptable model to use. It is able to accurately predict the majority of the high risk scenarios while keeping the false positives under 10 %. Compared to the other methods, Easy Ensemble is able to best weed out the high risk samples, while not needlessly reducing business by mislabeling a large percentage of low risk opportunities as high risk.