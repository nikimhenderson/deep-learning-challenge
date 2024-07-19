# Alphabet Soup Funding Predictor

## Overview
The goal of this project was to create a neural network model to predict the success of 
applicants to the fictional non-profit foundation, Alphabet Soup.

## Process
A CSV containing data on more than 34,000 organizations that have received funding from Alphabet Soup over the years was provided.

### Preprocessing
The data was preprocessed by:
1. Dropping non-beneficial identifier columns
2. Cleaning the APPLICATION_TYPE and CLASSIFICATION data to ensure that only those data that were most often reported were used
  * APPLICATION_TYPE below 500 were given the new value "Other"
  * CLASSIFICATION below 1800 were given the new value "Other"
3. Used pd.get_dummies() to convert categorical data to numeric
4. Divided the data into a target array (IS_SUCCESSFUL) and features array (all other variables)
5. Applied the train_test_split to create a testing and training dataset
6. Used StandardScaler to scale the training and testing sets

The resulting data included 44 features.

### Compiling, Training and Evaluating the Model
The target predictive accuracy for the model was greater than 75%. Three official attempts were made using the neural networks.
They all resulted in around a 72% accuracy, which is short of the target accuracy.

## Results
### Preprocessing
1. What variables are the targets for your model? The IS_SUCESSFUL variable
2. What variables are the features for your model?
    * APPLICATION_TYPE—Alphabet Soup application type
    * AFFILIATION—Affiliated sector of industry
    * CLASSIFICATION—Government organization classification
    * USE_CASE—Use case for funding
    * ORGANIZATION—Organization type
    * STATUS—Active status
    * INCOME_AMT—Income classification
    * SPECIAL_CONSIDERATIONS—Special considerations for application
    * ASK_AMT—Funding amount requested
3. What variables should be removed from the input data because they are neither targets nor features? In future exploration of this model I believe it would be beneficial to do an accounting of the weights of each of the features in order to determine how beneficial each is to the model. However just from looking at the variables, I think that the STATUS and SPECIAL_CONSIDERATIONS variables could be removed because they seem to have very little influence logically over whether funding is successful.
### Compiling, Training, Evaluating
**Attempt #1**<br/>
The first attempt resulted in an accuracy of 72.59%. This means that 72.59% of the model's predicted values align with the dataset's true values.
The parameters used were:
  * layers = 2
      * layer1 = 80 neurons and 'relu' activation function
      * layer2 = 30 neurons and 'relu' activation function
  * epochs = 100 <br/>
These parameters were used because they were predetermined by the challenge.

**Attempt #2** <br/>
The second attempt resulted in an accuracy of 72.62%. This means that 72.62% of the models predicted values align with the dataset's true values.
The parameters used were:
  * layers = 1
      * layer 1 = 60 neurons and 'tanh' activation function
  * epochs = 100 <br/>
These parameters were used because a general rule of thumb for determining the correct number of neurons in a hidden layer should be between the size of the input layer and the size of the output layer. Also a different activation function was attempted to see if the activation function brought up the accuracy at all and it appears to make a very miniscule improvement.

**Attempt #3** <br/>
The third attempt resulted in an accuracy of 72.26%. This means that 72.26% of the model's predicted values align with the dataset's true values.
The parameters used were:
  * layers = 1
      * layer 1 = 44 neurons and 'tanh' activation function
  * epochs = 100 <br/>
These parameters were used because there were 44 features in the dataset, indicating that the input layer is 44. If a general rule of thumb is that the size of the hidden layer should be between that of the input layer and the output layer, this should improve accuracy. Instead the accuracy is lower than the previous attempts, indicating that reducing the hidden layer too much reduces accuracy.

## Summary
After attempting optimization of the model 3 times, accuracy was never seen above 72.62%. Optimization indicates that a tanh activation function is beneficial for this model (as compared to relu). However no optimization resulted in the target accuracy of above 75%, therefore I would suggest use of another classification model to predict successful funding for Alphabet Soup.
  
