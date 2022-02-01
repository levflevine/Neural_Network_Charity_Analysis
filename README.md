# Neural_Network_Charity_Analysis

## Overview of the Analysis

### Purpose

Create a neural network solution that can evaluate donation applications submitted to Alphabet Sour, a charitable organization, to determine, whether or not an application should be supported based on the predicted outcomes.  

### Approach

Apply machine learning and neural networks leveraging the Tensoflow library to the features in the provided dataset to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.  

### Deliverables: 

1. Preprocessing Data for a Neural Network Model
2. Compile, Train, and Evaluate the Model
3. Optimize the Model
4. A Written Report on the Neural Network Model 

### Tools and Data Sources

#### Tools

- Python Scripts
- Pandas Library
- Sklearn Library
- Tensorflow Library

#### Data Sources

- [Charity Dataset](https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-online/module_19/charity_data.csv)

## Results

### Data Preprocessing

#### What variable(s) are considered the target(s) for the model?

**IS_SUCCESSFUL** is the taget for the model - we are predictiong whether or not the donation application will be successful.

![Target_Variable](/Resources/target_variables.png)

#### What variable(s) are considered to be the features for the model?

There are 9 variables used as features for the NN Model. as follows.

- **APPLICATION_TYPE**            
- **AFFILIATION**               
- **CLASSIFICATION**              
- **USE_CASE**                    
- **ORGANIZATION**                
- **STATUS**                      
- **INCOME_AMT**                  
- **SPECIAL_CONSIDERATIONS**      
- **ASK_AMT**                   

![Feature_Variable](/Resources/feature_variables.png)

#### What variable(s) are neither targets nor features, and should be removed from the input data?

There were 2 variables that were neither targets nor features that were removed from the input data, as follows.

- **EIN**
- **NAME**

### Compiling, Training, and Evaluating the Model

#### How many neurons, layers, and activation functions were selected for the neural network model, and why?

- The input layer used **9 input neurons**. Since we have got 9 features in our model, they are used as input neurons.
- **2 hidden layers**  used the **Rectified Linear Unit (ReLu) activation function**. The ReLU activation function was used to allow our hidden layer to identify and train on nonlinear relationships in the dataset.
- First hidden layer used **80 neurons**. 80 neurons were used in the first hidden layer to achieve the initial model performance accuracy.
- Second hidden layer used **30 neurons**. 30 neurons were used in the second hidden layer to achieve the inital model performance accuracy.
- The Output layer used **Sigmoid activation function** on **1 output neuron**. The Sigmoid activation function was used to produce a probability output for the binary classifier.

![NN_Model](/Resources/model.png)

#### Was the target model performance achieved?

The **target model performance was 75.0%**. Initially the model achieved an **62.9% accuracy**, hence **the target model performance was not achieved**.

![Initial_Performance](/Resources/init_perf.png)

#### What steps were taken to try and increase model performance?

A number of steps were taken to increase the model performance as follows.

1. The **INCOME_AMT** feature was converted from string ranges to numeric values based on the the middle of the range intervals

![INCOME_AMT](/Resources/INCOME_AMT.png)

2. A new combined feature was introduced: a ratio of **INCOME_AMT** / **ASK_AMT** that reflected the potential risks of the donation. The individual **INCOME_AMT** and **ASK_AMT** features were dropped.

![new_feature](/Resources/new_feature.png)

3. The number of **APPLICATION_TYPE** bins have been increase to **10** by reducing the **Other** bin cutoff to 70.

![app_bins](/Resources/app_bins.png)

4. The number of **CLASSIFICATION** bins have been increase to **12** by reducing the **Other** bin cutoff to 100.

![clas_bins](/Resources/clas_bins.png)

5. **Two mode hidden layers were added to the model** with **ReLu** and **Sigmoid activation functions**

6. **Number of neurons have been inceased** for each hidden layer as follows.

- **200** - first layer
- **100** - second layer
- **40** - third layer
- **10** - fouth layer

![new_model](/Resources/new_model.png)

7. **Number of epochs** have been increased to **100**

![epochs](/Resources/epochs.png)

## Summary

Since the initial model did not reach the target accuracy, **the optimized model** was developed over the course of **7 iterations (attempts)** by optimizing the parameters described in the **Steps** section above. 

The optimized model has **improved the accuracy to 72.3%**. It still **has not achieved the target** 75.0% accuracy.

![opt_results](/Resources/opt_results.png)

Further work is needed on the model. The following potential improvements could enable reaching the target performance: 

1. Additional exploratory analysis of the dataset to better understand the significance of the features and how they could be transformed and/or dropped to better fit the model
2. Other combinations of activation functions could be applied to the hidden layers and the output layer to improve the performance
3. If an additional dataset could be obtained it could help improve the model training
4. Comparign the performance of the NN model to the ML models, such as Random Forest.