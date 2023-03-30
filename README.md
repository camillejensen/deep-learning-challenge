# deep-learning-challenge
With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.


## Overview

Alphabet Soup, a nonprofit foundation needed a tool to help them select applicants for funding with the best change of success in their ventures. Using my knowledge of machine learning and neural networks, I took the data provided and used appropriate features to create a binary classifier to predict an applicants success. They wanted a target accuracy of 75% for the model. Alphabet Soup provided me with a CSV file consisting of 34,000 organizations that have received funding from Alphabet Soup over the years. The dataset contains a number of columns that capture metadata about each organization:

-EIN and NAME—Identification columns
-APPLICATION_TYPE—Alphabet Soup application type
-AFFILIATION—Affiliated sector of industry
-CLASSIFICATION—Government organization classification
-USE_CASE—Use case for funding
-ORGANIZATION—Organization type
-STATUS—Active status
-INCOME_AMT—Income classification
-SPECIAL_CONSIDERATIONS—Special considerations for application
-ASK_AMT—Funding amount requested
-IS_SUCCESSFUL—Was the money used effectively

## Results

### Data Preprocessing

-Began by dropping the 'EIN' and 'NAME' columns as they are not used as targets or features for this model
-Binned "rare" categorical variables together in a new value for columns: 'CLASSIFICATION' and 'APPLICATION_TYPE'
-Converted catergorical data to numeric with pandas module, pd.get_dummies to split columns into features and target
-Split data into training and testing datasets
-Target Variable for model: 'IS_SUCCESSFUL'
-Feature Variables for model: 
  'APPLICATION_TYPE'
  'AFFILIATION'
  'CLASSIFICATION'
  'USE_CASE'
  'ORGANIZATION'
  'STATUS'
  'INCOME_AMT'
  'SPECIAL_CONSIDERATIONS'
  'ASK_AMT'
  
### Compiling, Training, and Evaluating the Model
  
-First Model I used two hidden layers each using 'relu' activation as we usually do with our first model. The first layer had 80 nodes and the second had 30 nodes. 
-This model had just under a 73% accuracy. I attempted to add hidden layers, with varying amounts of nodes as well as change my activation from 'relu' to 'sigmoid'. 
-By manually adjusting my model, I was unable to reach above a 73% accuracy. 

#### Hyper Parameter Model

-I decided a more efficient way to achieve the desired accuracy score was to create a method to find the hyperparameters for a model. I imported keras-tuner and built a method to loop through each activation type, the inital hidden layer neuron number, and well ad additional hidden layers and neurons. 
-This method was computationally expensive, so I used a smaller number of epochs(50). 
-With this method, I still was not able to get the parameters to build a model that predicted an accuracy above 75%. The accuracy was about 74%. 
-If I had the time and computability to optimize this model I would likely next see how adding back in the columns I dropped effected the model. Potentially with an added feature, the model would be more accurate.  
-The optimized model had 4 hidden layers all using the sigmoid activation. The number of neurons per layer in order: 71,6,26,16,16. 

## Summary

The automatically optimized trained model using keras tuner acheived the highest accuracy of all my models. It still did not acheive a 75% accuracy. In order to solve this problem, I would reprocess my data and add in one or both of the columns I had dropped. I would likely begin adding the 'NAME' column in as that would provide the model with another feature to test on.
