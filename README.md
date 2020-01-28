# Diabetes-Prediction-Model
This has a python code which uses a data-set to predict diabetes without using Insullin
## About the Dataset
The Dataset was obtained from UCI repository. It has some 1 lakh data points, with 55 features. Some of the features are listed below-
* Encounter_id - Unique identifier of an encounter
* Patient Number - Unique identifier of a paitient
* Race - Race of the paitient
* Age - Weight of the paitient
* Weight - Weight of the paitient
* Race - Race of the paitient
* Gender - Gender of the paitient
* Race - Race of the paitient
* Admission type - 9 different values based on on what state they were admitted
* Discharge disposition - 29 different values corresponding to how their treatment ended up with
* Time in hospital - Time till which the patient was admitted
* Payer code - 29 different values based on payment type. Lots of missing data
* Medical Speciality - Specification of the doctor. 129 unique values
* Number of Procedures - Total number of procedures that had to be conducted
* Number of Lab Procedures - Total number of lab procedures that had to be conducted
* Number of Medication Visits - Total number of times patient had to meet the doctor in past. 
* Diagonosis1/2/3 - First three caharcters of ICD-9 codes for the first, second and the third diagnosis
* Number of Diagonoses- Total Number of Diagnosis conducted
* Glucose Serum Test - Test vales. 4 unique values
* Change - If there was a change in dosage of medicines
* 24 Biological Features - These have relative values of different hormones.
* Diabetes Medication - This is the target variable. Having the need to take medicines is a representation of being Diabetic.
* Readmitted - Whether the patient was readmitted

## Data Preprocessing
The ID features were removed because of very low correlation with the target variable. Payer code had to be removed because it had too many unique values and relatively less data. Diagnoses had to unfortunately be removed because one-hot encoding with 1000 unique features created 3000 features, and it became comoutationally very expensive. For physical features, age was given in age classes like 10-20, 20-30, etc. They were replaced by the means i.e. 15,25 etc.
Weight had to be removed because 97% data was missing.  
The missing values in Gender were filled as Female to balance out the data points
For filling the Race feature, we employed a two way correlation with Gender and Age, and finally the values were rounded off to the nearest integer. 
Insulin was dropped. The reason for this being the fact that Insulin is directly corelated with the target variable: Presence of Diabetes. Input of Insulin as a feature was resulting in overfitting over the dataset by the model.

We also tried using oversampling techinques like SMOTE to balance the data, but the performance metrics did not increase much. 


## Model Building
Starting off with Logistic Regression we applied different algorithms like SVM, Decision Tree and Random Forest.
Initially, we got an accuracy and f1 score of 100% with the algorithms. We realised that the presence of Insulin as a feature, which had high correlation with the target was causing overfitting. 
On removal of “Insulin” as a feature, the metrics dropped down to reasonable values. Our baseline model had an accuracy of 77% and F1 score at 80%. 
With Random Forest, we tuned the hyperparameters using Randomised Search and found the best parameters for our final model.
With the accuracy at 81% and F1 score at 86%, and with the bias of data being at 74%, the model is decently successful.

## Feature Engineering
We tried to build and incorporate new features into our model but were unable to increase the perfomance metrics substantially. Also, in somecases, the metrics got worsened.

## Model Fine Tuning
We tried using some fine tuning techniques like Stacking, Bagging, Ensemble Learning, etc. However, unfortunately, our PC processors were unable to train complex models over such large datasets.

# Conclusion
Our model can be made more robust and reliable by collecting local data from hospitals to account for geographic variation. Obtaining more domain knowledge and getting assistance from doctors can help getting more insights from the data about the feature importances. 
