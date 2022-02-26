# Neural Network Charity Analysis

## Neural Network Charity Analysis Overview
Use knowledge of machine learning and neural networks to analyze the features in a dataset containing more than 34,000 organizations that have received funding from Alphabet Soup over the years to create a deep learning neural network binary classifier model that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.

Analysis includes the following steps:
* Preprocessing Data for a Neural Network Model
* Compiling, Training, and Evaluating the Neural Network Model
* Optimizing the Neural Network Model
* Writing a Report on the Neural Network Model

## Neural Network Charity Analysis Results
Evaluation of the deep learning neural network model produced the following results:
### Data Preprocessing
* What variable(s) are considered the target(s) for your model? 

IS_SUCCESSFUL—Was the money used effectively

* What variable(s) are considered to be the features for your model? 

APPLICATION_TYPE—Alphabet Soup application type

AFFILIATION—Affiliated sector of industry

CLASSIFICATION—Government organization classification

USE_CASE—Use case for funding

ORGANIZATION—Organization type

STATUS—Active status

INCOME_AMT—Income classification

SPECIAL_CONSIDERATIONS—Special consideration for application

ASK_AMT—Funding amount requested

* What variable(s) are neither targets nor features, and should be removed from the input data?

EIN and NAME—Identification columns

### Compiling, Training, and Evaluating the Model
* How many neurons, layers, and activation functions did you select for your neural network model, and why?

As suggested by the starter code output summary below, the original model contains the following layers and neurons. The ReLu activation function was chosen for the input and hidden layers to capture maximum nonlinearity, and the Sigmoid activation function was chosen for the binary output layer.

![image](https://user-images.githubusercontent.com/92612370/155830033-f2adc166-3970-4993-a907-17b3e44c39cf.png)


* Were you able to achieve the target model performance?

The original model was unable to achieve target performance of 75% accuracy with the following results:

![image](https://user-images.githubusercontent.com/92612370/155830126-6988fab6-5db8-4e3d-b68e-7e3e4b976aac.png)


* What steps did you take to try and increase model performance?

Optimization of the original model includes the following step-by-step attempts and aggregated results:
- Noisy variables are removed from features: ASK_AMT removed from features and APPLICATION_TYPE and CLASSIFICATION feature value thresholds increased to reduce the number of bins
- Additional hidden layers are added: hidden layers increased from two to three
- Additional neurons are added to hidden layers: neuron per hidden layer increased from 80/30 to 140/140/140
- The activation function of hidden layers or output layers is changed for optimization: first hidden layer activtion function changed from ReLu to tanh
- Aggregated optimization results:

![image](https://user-images.githubusercontent.com/92612370/155830150-e87a2d5b-362d-47ec-922e-613b10dd1142.png)


- KerasTuner hyperparameter optimization framework search values and results:

![image](https://user-images.githubusercontent.com/92612370/155830183-9418037a-51f3-4666-ba37-b01192658c4a.png)


## Neural Network Charity Analysis Summary
The results of the analysis show that neither the model nor the KerasTuner hyperparameter optimization framework search was able to achieve accuracy greater than 73% or loss less than 56%, despite training at accuracy as high as 74% with loss less than 53%.

Given these fairly low success levels, I recommend using instead either a Support Vector Machine or Random Forest binary classifier model to solve this classification problem as they would likely achieve comparable predictive accuracy on large tabular data with less time and code required to build, train, and implement the model and faster performance evaluating the test data versus a comparable deep learning model.
