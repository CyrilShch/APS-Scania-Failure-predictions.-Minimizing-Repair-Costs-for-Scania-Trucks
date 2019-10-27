# APS-Scania-Failure-predictions.-Minimizing-Repair-Costs-for-Scania-Trucks

**Short description of project life cycle and results at each stage of model development**

**Problem** 

≈ $347500
for trucks which need to be serviced
1. Unnecessary checks done by a mechanic - $10
2. Missing a faulty truck, which may cause a breakdown in the future - $500

**Our goal**

To build the ML model to reduce costs 

**Dataset preparation**

We decided to drop features which have missing values of more than 60%
Using median imputation [1].

Source [1]: 
https://www.researchgate.net/publication/309195602_Prediction_of_Failures_in_the_Air_Pressure_System_of_Scania_Trucks_Using_a_Random_Forest_and_Feature_Engineering

**Exploratory analysis of the data**

Using downsampling and upsampling to balance our dataset

Hypothesis 1 is the following: features with few unique values and little correlation with the target variable do not contain useful information and do not help classification.

Hypothesis 2 is the following: the features in the dataset are quite dependent on each other and their simultaneous presence is redundant.

**Building ML models for hypotheses validation**

Metrics:

The Fβ score, which uses the parameter β to control the balance of recall and precision. As β decreases, precision is given greater weight. With β = 1, we have the commonly used F1 score, which balances recall and precision equally and reduces to the simpler equation 2TP/(2TP + FP + FN).

Measure of quality:

cost associated with our model = 500*FN + 10*FP.

Comparison ML models performance: Best model performance is Random Forest => Using Random Forest further.

Building Random Forest to validate hypothesis 1 => conclusion: bad performance, our hypothesis 1 is wrong.

Building Random Forest to validate hypothesis 2, development of optimal threshold => conclusion: good performance, our hypothesis 2 is right.

**Obtained results*

Interesting findings: finding optimal threshold make great result, many highly correlated with the target features not useful together.
Remarks on ML experiments: non-linear models take large amount of time in comparison with linear, which can be used for changing the performance after manipulations with dataset
The applicability of the model in a real-life scenario: we have a working classifier which is able to tell a fleet operator whether or not a truck needs to be serviced, based solely on sensor readings from the APS, load program to computer in operator center, when the operator receives data from the truck sensor, the program based on our model analyzes them and in the case of unstable operation of this system and the risk of breakage associated with it , makes it possible to take the necessary measures and prevent breakdowns.

**Overall conclusions**

Main goal reached, obtained performance is good enough.
The cost reduction estimation: as you can see the difference between cost for working without model and with is huge. It means that problem solved and roughly the half of money saved.

**Costs without our model:**
≈ $347500
for trucks which need to be serviced
1. Unnecessary checks done by a mechanic - $10
2. Missing a faulty truck, which may cause a breakdown in the future - $500

**Costs with our model:**
≈ $196800
for trucks which need to be serviced

**Profit from implementation of our model:**
≈ $150700

