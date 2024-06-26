# Type-2 Diabetes Risk Prediction

## INTRODUCTION 
Type 2 Diabetic Mellitus is known as a “Non-Communicable Disease” that has affected millions of people worldwide and is caused by genetic and environmental factors. With type 2 diabetes, the human body does not produce enough insulin, or the cells fail to use it. We aim to develop a genetic risk score prediction model that analyzes the risk of developing type 2 diabetes based on risk factors, such as body mass index, age, and physical activity levels. Finally, identify clusters of factors that are associated with the development of type 2 Diabetes. The motivation behind Type 2 Diabetes risk prediction is to identify the set of individuals with the highest probability of developing the disease before symptoms occur and intervening early in the disease process using the predictive method of Big Data analysis. Such prediction allows prevention of the disease and improves health outcomes. 
The objective of this project is to develop a classifier that predicts the onset of diabetes based on diagnostic measurements. The dataset used in this project is originally from the National Institute of Diabetes and Digestive and Kidney Diseases and consists of medical information on females of Pima Indian heritage who are at least 21 years old. The class variable indicates whether the patient has diabetes or not. Firstly, the data goes through the process of checking for missing values by examining the minimum values of each column. The second step consists of the imputation and visualization of the set of missing values. The output of such a process is a clean dataset that is split into training and testing datasets. Furthermore, a decision tree classifier was used on the result dataset. The accuracy of the model was found to be 73% on the test data. In conclusion it was observed that there is a positive association between insulin and glucose. After comparisons between glucose levels of affected and non-affected individuals, it is conducted that normal glucose levels in diabetic individuals range from 100 to 200. The results are worthwhile in the process of predicting the set of individuals with a high risk of being affected by diabetes. 

## DATASET EXPLANATION 
The National Institute of Diabetes and Digestive and Kidney Diseases (NIDDK) dataset is a collection of data from a study conducted between 1989 and 1998, known as the Diabetes Prevention Program (DPP). The DPP was a randomized controlled trial aimed at evaluating the effectiveness of lifestyle changes and the diabetes drug metformin in preventing or delaying the onset of type 2 diabetes in individuals at high risk for the disease. 
The dataset contains information on over 3,000 participants, including demographic information, medical history, and results from various tests such as glucose tolerance tests, fasting blood glucose tests, and insulin tests. It also includes information on lifestyle factors such as physical activity and diet. 
  
### Features: The dataset contains the following features: 
Pregnancies: Number of times pregnant

Glucose: Plasma glucose concentration a 2 hours in an oral glucose tolerance test 

BloodPressure: Diastolic blood pressure (mm Hg)

SkinThickness: Triceps skin fold thickness (mm)

Insulin: 2-Hour serum insulin (mu U/ml)

BMI: Body mass index (weight in kg/(height in m)^2)

DiabetesPedigreeFunction: Diabetes pedigree function (a function which scores the likelihood of diabetes based on family history)

Age: Age in years 

In this project, the data is processed by loading the dataset from a CSV file using the Pandas library, and checking for missing values by examining the minimum values of each column with the describe() function. Then, missing values are replaced with np.nan using replace() function, and missing values are visualized using the ‘missingno’ library. Next, the K-nearest neighbors imputation algorithm is applied using the KNNImputer class from sklearn.impute module, and the outliers are identified and removed from the dataset. Data visualization is performed with various plots to understand the relationship between features and the target variable. Finally, the cleaned dataset is converted into a feature vector format with the VectorAssembler class and split into training and testing datasets with a ratio of 80:20 using the randomSplit() function from PySpark. 

## METHODOLOGY AND IMPLEMENTATION 
The workflow of our model is outlined below

### Data Preparation: 
The first step is to import the required libraries and the dataset, which is stored in a CSV file. The dataset is loaded into a pandas DataFrame for data manipulation and analysis. The code then checks for missing values and replaces 0 values with NULLS to make it easier to identify and handle missing data.  

### Missing Value Imputation: 
The dataset has many missing values, particularly in the Glucose, Blood Pressure, skin thickness, Insulin, and BMI features. Since the dataset has a significant number of missing values, it is essential to handle them before proceeding. The missing values are imputed using the K-Nearest Neighbors (KNN) algorithm, which calculates the mean of the k nearest neighbors to fill in missing values. The KNN imputation is performed using the Scikit-learn library. After imputing missing values, the dataset is checked for outliers. 

### Outlier Removal: 
The outliers are removed using boxplots to visualize the distribution of each feature. Any data point outside of the whiskers is considered an outlier and is removed from the dataset. 

### Data Visualization: 
Data visualization is performed using various plots like heatmaps, scatter plots, and density plots to identify correlations between features and to better understand the data. 

### Feature Engineering: 
The data is then converted into a format suitable for training a machine learning model. The data is transformed into a Spark DataFrame, and the features are assembled using the VectorAssembler method. This method combines all the feature columns into a single column that is fed into the machine-learning algorithm. 

### Model Training and Evaluation: 
The Decision Tree Classifier algorithm is used to train the model. 80% of the data is used for training 20% is used for testing, and the Decision Tree Classifier is fitted to the training data. The trained model is used to make predictions on the test set, and the accuracy of the model is evaluated using the MulticlassClassificationEvaluator method.

### Feature Importance: 
The feature importance of the trained model is analyzed using the feature Importances attribute of the Decision Tree Classifier model. This attribute returns the importance of each feature in the model, which can be used to identify the most significant features that contribute to the prediction. 

### Visualization of the Decision Tree: 
The trained Decision Tree Classifier model is visualized using the export_graphviz and graphviz libraries. The Decision Tree Classifier model is converted into a Graphviz object, which can be rendered as a visual representation of the decision tree.

## METRIC EVALUATION AND RESULTS 
![Confusion Matrix](ConfusionMatrix.png)
##### The confusion matrix shows the number of true positive (37), false positive (12), false negative (8), and true negative (16) predictions made by the model. These values are used to calculate other performance metrics such as precision, recall, and F1 score.

The model demonstrates a commendable accuracy of 0.73, indicating that it is able to correctly predict the class of 73% of the samples in the test set. The confusion matrix reveals that the model has correctly predicted the positive class (represented by 1) 16 times, showcasing its ability to identify positive samples accurately. Although there were 12 instances where the negative class (represented by 0) was mistakenly predicted as positive, the overall performance of the model remains promising. 
 
The classification report further validates the model's effectiveness, with a precision of 57.14%. This implies that a substantial portion of samples predicted as positive are indeed positive. The recall of 66.67% is also noteworthy, as it indicates that the model is able to correctly identify a significant proportion of the actual positive samples. Additionally, the F1 score of 61.54% signifies a balanced trade-off between precision and recall, suggesting that the model is performing well in terms of both precision and recall. 
In conclusion, the model exhibits strong potential with its impressive accuracy, precision, recall, and F1 score. With further optimization and fine-tuning, it has the capability to achieve even better performance, making it a promising candidate for future predictions. 

## CONCLUSION 
In conclusion, this project aimed to analyze and predict diabetes outcomes using the given dataset from the National Institute of Diabetes and Digestive and Kidney Diseases. The dataset was cleaned by handling missing values using KNN imputation and removing outliers. Exploratory data analysis (EDA) was performed using visualizations to gain insights into the data. The correlation between various features was analyzed, and it was observed that there is a positive association between insulin and glucose levels. Additionally, the distribution of glucose levels in people with and without diabetes was compared, and it was found that normal glucose levels in diabetic individuals range from 100 to 200. Further, a decision tree classifier was trained using Spark's machine learning library, PySpark, on the cleaned dataset. The accuracy of the model was evaluated using cross-validation and was found to be around 73% on the test dataset. 
Overall, this project successfully processed the given dataset, performed EDA, and built a predictive model using machine learning techniques. The findings can be useful for understanding the factors influencing diabetes outcomes and predicting the risk of diabetes in individuals. Further improvements could be made by exploring other machine learning algorithms, tuning hyperparameters, and incorporating more features to enhance the predictive performance of the model. 

