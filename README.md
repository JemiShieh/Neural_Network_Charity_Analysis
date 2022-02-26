# Neural Network Charity Analysis

## Neural Network Charity Analysis Overview
Use knowledge of machine learning and neural networks to analyze the features in a dataset containing more than 34,000 organizations that have received funding from Alphabet Soup over the years to create a deep learning neural network binary classifier model that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.
Analysis includes the following steps:
* Preprocessing Data for a Neural Network Model
* Compiling, Training, and Evaluating the Neural Network Model
* Optimizing the Neural Network Model
* Writing a Report on the Neural Network Model

## Neural Network Charity Analysis Results
Evaluation of the neural network model produced the following results:
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

Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense (Dense)                (None, 80)                3520      
_________________________________________________________________
dense_1 (Dense)              (None, 30)                2430      
_________________________________________________________________
dense_2 (Dense)              (None, 1)                 31        
=================================================================
Total params: 5,981
Trainable params: 5,981
Non-trainable params: 0
______________________________

* Were you able to achieve the target model performance?
The original model was unable to achieve target performance with the following results:
268/268 - 1s - loss: 0.5865 - accuracy: 0.7250 - 603ms/epoch - 2ms/step
Loss: 0.5864637494087219, Accuracy: 0.7250145673751831

* What steps did you take to try and increase model performance?
Optimization of the original model includes the following step-by-step attempts and aggregated results:
- Noisy variables are removed from features: ASK_AMT was removed from features
- Additional hidden layers are added: increased from two to three
- Additional neurons are added to hidden layers: increased from 80/30 to 140/140/140
- The activation function of hidden layers or output layers is changed for optimization: first hidden layer changed from ReLu to tanh
- Optimization aggregated results:
268/268 - 0s - loss: 0.5964 - accuracy: 0.7255 - 312ms/epoch - 1ms/step
Loss: 0.5963667035102844, Accuracy: 0.7254810333251953

- KerasTuner hyperparameter optimization framework search values and results:
{'activation': 'relu',
 'first_units': 100,
 'num_layers': 3,
 'units_0': 140,
 'units_1': 110,
 'units_2': 80,
 'units_3': 110,
 'units_4': 80,
 'units_5': 90,
 'tuner/epochs': 20,
 'tuner/initial_epoch': 0,
 'tuner/bracket': 0,
 'tuner/round': 0}

268/268 - 0s - loss: 0.5695 - accuracy: 0.7291 - 368ms/epoch - 1ms/step
Loss: 0.5694971680641174, Accuracy: 0.7290962338447571

## Neural Network Charity Analysis Summary
The results of the analysis show that neither the model nor the KerasTuner hyperparameter optimization framework search was able to achieve accuracy greater the 73% or loss less than 56%, despite training at accuracy as high as 74% with loss less than 53%.

Given these fairly low success levels, I recommend using instead either a Support Vector Machine or Random Forest binary classifier model to solve this classification problem as they would likely achieve comparable predictive accuracy on large tabular data with less time and code required to build, train, and implement the model and faster performance evaluating the test data versus a comparable deep learning model.
