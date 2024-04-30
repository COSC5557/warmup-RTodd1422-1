[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/cTzVmHky)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=14549912&assignment_repo_type=AssignmentRepo)
# Warmup

Download the [Wine Quality
dataset](https://archive-beta.ics.uci.edu/dataset/186/wine+quality). Choose the
one that corresponds to your preference in wine.

## Regression

Build a regression model to predict the wine quality. You can choose any model
type you like; the purpose of this exercise is to get you started. Evaluate the
performance of your trained model -- make sure to get an unbiased performance
estimate!

## Classification

Now predict the wine quality as a class, i.e. model the problem as a
classification problem. Evaluate the performance of your trained model again.

## Submission

Upload your code and a brief description of your results.



## Brief Report

The dataset I'm working with is the White Wine Quality dataset that is included in this repository. I first load it into a pandas dataframe while explicitly defining the delimiter/separator and setting the datatype for each feature. I did this because the automatic detection did not correctly detect the seperator or the types for csv input. 

I then look at the information provided by the pandas dataframe included methods so that I can be sure that the data was correctly imported. I also look to make sure that the dataset doesn't include any null values to ensure a complete dataset. I then produce a few graphs to look at the shape of the data for each feature and the distribution of the dataset with regard to the scoring/target feature, in this case quality. 

Next, I look at the correlation of the features so that I can see if there are highly correlated features. Since density and residual sugar are highly correlated to eachother, I can drop one of them to reduce the dimensionality of the dataset. Since density is less correlated with quality, as seen in the correlation plot, I chose to drop the density feature instead of the residual sugar feature.

I then created a new binary target feature called high quality. If a wine's quality is over 6, then it is marked as a high quality wine. This allows all four of the models (Logistic Regression, BayesianRidge, XGBClassifier, and SVC) to be compared to each other directly. I recognize that this is unlikely to be ideal but I rationalized that by thinking that this is the warmup.

I then split the dataset and then scale it using a MinMaxScaler. I then train the models and have each print out their training accuracy and validation accuracy using the roc_auc_score (area under curve) which is a decent way to score binary, multiclass, and multilabel models allowing them to be compared with an equivalent scoring method. To finish off the evaluation I then print the classification report for each model (except bayesian ridge, because it really didn't want to). From looking at all these outputs, it appears that the XGBClassifier scored the highest, but it also appears to have massively overfitted as it has a large difference between its training and validation accuracy. The other three models appear to avoided overfitting, but their scores are lower. In BayesianRidge's case it is only lower by a little bit. 
