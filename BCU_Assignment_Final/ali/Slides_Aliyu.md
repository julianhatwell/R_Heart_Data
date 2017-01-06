

Predictive Analysis Using kNN an Naive Bayes
========================================================
author: Aliyu S. Sambo
date: 9th Dec. 2016
autosize: true
<div>
</div>

Initial Naive Bayes Predictive Analysis Result
========================================================
<div >
Initial Naive Bayes prediction performance for Fbs (Fasting Blood Sugar) was poor.
</div>
<div >
Below shows a comparison of the result for Fbs and Heart Disease predictions using the same model.
</div>
<div >
 
</div>
<div align="center">
<img src="AS_NB_1.png">
</div>


Initial kNN  Predictive Analysis Result
========================================================
<div>
Below are the prediction results using a kNN model for both Fbs and Heart Disease prediction.
The result of the Fbs prediction showed very poor performance and predict all as false. While the heart disease showed a decent level of performance.

<div>
<div align="center">
<img src="AS_knn_1.png">
</div>


<div class="footer" >
This indicates that the problem was not with the models but with the data.
</div>

Improvement Efforts
========================================================
Feature Selection:

The RELIEF and RELIEFCAT algorithms were used to identify features that features that were key.

<div align="center">
<img src="AS_IMFS_1.png" height=400>
</div>
Result of Using only key attributes:

There was marginal improvements but not significant.



Improvement Efforts (Contd)
========================================================

Some improvement efforts showed marginal improvement on the Naive Bayes but the kNN result for Fbs was still very poor. Examples are as follows:

- Optimal K parameter was chosen for the model. This was done by testing for odd numbers around the square root of the number of rows of the training data.


 

 
 ```r
 round(sqrt(nrow(heart.train)))
 ```
 
 ```
 [1] 15
 ```

Therefore tried k= c(7, 9, 11, 13, 15, 17, 19). There was some improvement when k=13 was used.

- Rescaling of Numeric Attribute

- Binning of Numeric Attributes and apply knncat (a knn algorithm that handles categorical data)

Identified Main Cause of Poor Performance
========================================================


'Class Imbalance' was identified as the cause of poor result for predicting Fbs. Many predictive models perform best when the distribution is close to 50% by 50%.  


<div>
Below shows that Fbs has an 85% to 15% distribution. While the Heart Disease factor has 59% by 41% .
</div>
<div>
  
</div>




```r
table(heart$Fbs)
```

```

  0   1 
258  45 
```

```r
table(heart$HDisease)
```

```

 No Yes 
164 139 
```

Solution
========================================================
<div>
There are two class imbalance mitigation approaches:
- Cost function based approaches
- Sampling based approaches: Oversampling/Undersampling/Hybrid


Oversampling (adding more of the minority class) was implemented using a function in ROSE package.
<div align="left">
<img src="AS_Os_1.png" height=400>
</div>
</div>

Result After Mitigating for Class Imbalance
========================================================
<div>
Naive Bayes model now has a fair prediction after addressing for class imbalance.

<div align="center">
<img src="AS_Fin_1.png" height=550>
</div>
</div>


