Increasing classifier performance using data categorisation
========================================================
author: Paul Carter
date: 05/12/2016
autosize: true


NaiveBayes with "Raw" Heart Dataset 
========================================================
<div align="center">
<img src="paul_confusion.png" width=400 height=500> <br />

</div>



Categorising Variables 
========================================================
Now let's see if the performance is better with other categorised columns 

- Age from 41 values => 7 (<40, {41-46}, {47-52}, {53-58}, {59-64}, {65-70}, 71+)
- RestBP from 50 Values => 4 (Low, Ideal, Pre-High & High)
- Chol from 152 Values => 3 (Desirable, Borderline-High, High)
- MaxHR from 91 Values => 2 (Average, High)

=========================================================

<div align="center">
<img src="paul_MaxHR.png" width= 800 height=500>
</div>


Categorising Variables 2
========================================================

<div align="center">
<img src="paul_PieHeart.png" width=500 height=400>
<img src="paul_PieCat.png" width=500 height=400>


</div>

- A fully categorised RestBP variable 



Analysing NaiveBayes
=========================================================

```r
NBClassifier.alt <- naiveBayes(HDisease ~., data = NBdata3)
NBClassifier.alt
```
<div align="center">
<img src="paul_NBAge.png" width=1200 height=200>
</div>

- Those aged between 53-58 are at the highest risk of developing heart disease

Analysing Results 2
=========================================================
<div align="center">
<img src="paul_NBSex.png" width=250 height=100> 
<img src="paul_NBChestPain.png" width=500 height=100>  
<img src="paul_NBRestBP.png" width=500 height=100> 
<img src="paul_NBChol.png" width=500 height=100> 
<img src="paul_NBMaxHR.png" width=300 height=100> 
<img src="paul_NBThal.png" width=400 height=100> 
</div>


Categorising Results (NaiveBayes)
========================================================



<div align="center">
<img src="paul_confusion.png" width=350 height=400>
<img src="paul_confusion3.png" width=350 height=400>
</div>

- Decreased Accuracy
- Higher Sensitivity 

KNN Results 
========================================================
- KNN improved performance against "raw" heart data set (72.1%)
- However performed worse against NaiveBayes

<div align="center">
<img src="paul_confusion3.png" width=300 height=400>
<img src="paul_confusion4.png" width=300 height=400>
</div>


Converting KNN to Integer + Rescaling 
========================================================

<div align="center">
<img src="paul_confusion6.png" width=400 height=500>
</div>

Feature Selection
========================================================


```r
library(mlbench)
weights <- chi.squared(HDisease~., KNNdata3)
print(weights)
```

<div align="center">
<img src="paul_FeatureSel.png" width=800 height=50>
</div>

<div align="center">
<img src="paul_confusion7.png" width=250 height=300>
</div>
