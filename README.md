# Heart-Disease-Prediction-System-using-Logistic-Regression
A Heart Disease Prediction System built on machine learning 

## Principle 

This prediction system is based on ECG data on heart diseases of patients

#### What is ECG ??


<p align="center">
  <img width="650" height="400" src="https://user-images.githubusercontent.com/78251168/211028900-e320780a-23d4-44f8-962f-65348841b4ee.jpg">
</p>


An electrocardiogram (ECG) is a quick test that can be used to examine the electrical activity and rhythm of your heart.
The electrical signals that your heart beats out each time it beats are picked up by sensors that are affixed to your skin.
A machine records these signals, and a doctor examines them to see whether they are odd.

### Workflow of model

  - Data collection 
  - Split Features and Target set
  - Train-Test split
  - Model Training
  - Model Evaluation
  - Predicting Results

#### Columns Information
 - age
 - sex
 - Chest pain type (4 values)
 - Resting blood pressure
 - Serum cholestoral in mg/dl
 - Fasting blood sugar > 120 mg/dl
 - Resting electrocardiographic results (values 0,1,2)
 - Maximum heart rate achieved
 - Exercise induced angina
 - Oldpeak = ST depression induced by exercise relative to rest
 - The slope of the peak exercise ST segment
 - Number of major vessels (0-3) colored by flourosopy
 - Thal: 0 = normal; 1 = fixed defect; 2 = reversable defect


## Split Features and Target set

```
X = heart_data.drop(columns = 'target', axis = 1)
X.head()
# now X contains table without target column which will help for training the dataset
```

## Train Test Split

```
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size = 0.15, stratify = Y, random_state = 3 )
```
* here we have test data size is 20 percent of total data which is evenly distributed with degree of randomness = 3

## Model Training 

```
model = LogisticRegression()
model.fit(X_train.values, Y_train)
```

## Model Evaluation 

<p align="center">
  <img width="500" height="500" src="https://user-images.githubusercontent.com/78251168/211057178-3b209f44-9e51-4a6b-819b-019c9f4ddb10.png">
</p>


```
# accuracy of traning data
# accuracy function measures accuracy of model

X_train_prediction = model.predict(X_train.values)
training_data_accuracy = accuracy_score(X_train_prediction, Y_train)

print("The accuracy of training data : ", training_data_accuracy)
```

```
# accuracy of test data

X_test_prediction = model.predict(X_test.values)
test_data_accuracy = accuracy_score(X_test_prediction, Y_test)

print("The accuracy of test data : ", test_data_accuracy)
```

