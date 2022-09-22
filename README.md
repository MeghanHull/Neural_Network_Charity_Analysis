# Neural_Network_Charity_Analysis
<!-- Charity organization analysis using neural networks -->
## Project Overview
Alphabet Soup wants to use a binary classifier to predict whether applicants will be successful if funded, to better allocate investment funds.  The starting dataset consisted of a CSV of over 34,000 organizations that received funding from Alphabet Soup. The goal for model optimization is achieving a target predictive accuracy higher than 75%.

## Purpose
<!-- The purpose of this analysis is well defined (4 pt) -->
The purpose of this project is to use deep-learning neural networks with the TensorFlow platform in Python, to analyze and classify the success of charitable donations.

## Resources
### Data Sources & Bespoke Code
1. [charity_data.csv](Resources/charity_data.csv) [^1]
2. [AlphabetSoupCharity.ipynb](AlphabetSoupCharity.ipynb) [^2]
3. [AlphabetSoupCharity_Optimzation.ipynb](AlphabetSoupCharity_Optimzation.ipynb) [^2]

[^1]: Alphabet Soup Charity dataset  
[^2]: Jupyter Notebook

### Software & CDNs
***Table 1: Software & Library Versions***
| Software | Version |
| :--- | :---: |
| Python | 3.7.13 |
| Pandas | 1.3.5 |
| NumPy | 1.21.5 |
| SciPy | 1.7.3 |
| Scikit-learn | 1.0.2 |
| imbalanced-learn | 0.9.0 |
| Visual Studio Code | 1.70.2 |

# Results 
<!-- There is a bulleted list that answers all six questions (15 pt) -->
## Data Preprocessing
<!--What variable(s) are considered the target(s) for your model?
What variable(s) are considered to be the features for your model?
What variable(s) are neither targets nor features, and should be removed from the input data?-->
The columns in the dataset are described in ***Table 2***.  The column **IS_SUCCESSFUL** contains binary data refering to weither or not the charity donation was successful, is the target for this deep learning neural network.  Two columns of identification information were removed, and the other columns were considered as features.

***Table 2: Variable Descriptions***
| Variable | Description | Classification |
| :--- | :--- | :---: |
| EIN | Identification column | Removed |
| NAME | Identification column | Removed |
| APPLICATION_TYPE | Alphabet Soup application type | Feature |
| AFFILIATION | Affiliated sector of industry | Feature |
| CLASSIFICATION | Government organization classification | Feature |
| USE_CASE | Use case for funding | Feature |
| ORGANIZATION | Organization type | Feature |
| STATUS | Active status | Feature |
| INCOME_AMT | Income classification | Feature |
| SPECIAL_CONSIDERATIONS | Special consideration for application | Feature |
| ASK_AMT | Funding amount requested | Feature |
| IS_SUCCESSFUL | Was the money used effectively | Target |

Encoding of the categorical variables, spliting into training and testing datasets and standardization were applied to the features.

## Compiling, Training, and Evaluating the Model
<!--How many neurons, layers, and activation functions did you select for your neural network model, and why?
Were you able to achieve the target model performance?
What steps did you take to try and increase model performance?-->
A base model and three optimizations were analyzed as summarized in ***Table 3***.  All scenarios used 100 epochs.  Since the target is a binary classification, a Logistic (sigmoid) activation with one node was used for the output layer.  For the hidden layers, a Rectified Linear (ReLu) activation was selected to minimize the risk of problems during training (i.e. vanishing gradients).  One sensitivity was run using Logistic (sigmoid) activation for the hidden layers.  None of the models achieved the goal 75% accuracy.

The model weights were also saved every 5 epochs.  Reviewing the saved epochs didn't reveal any that met the 75% accuracy goal.

***Table 3: Optimization Summary***
| Scenario | Hidden Layers | Neurons | Input Activation | Output Activation | Loss | Accuracy |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Base Case | 2 | 80/30 | Rectified Linear (ReLu) | Logistic (Sigmoid) | 0.5576 | 0.7294 |
| Optimization 1 | 3 | 100/50/50 | Rectified Linear (ReLu) | Logistic (Sigmoid) | 0.5709 | 0.7271 |
| Optimization 2 | 5 | 100/100/50/50/50 | Rectified Linear (ReLu) | Logistic (Sigmoid) | 0.5708 | 0.7298 |
| Optimization 3 | 3 | 100/50/50 | Logistic (Sigmoid) | Logistic (Sigmoid) | 0.5611 | 0.7290 |

# Summary 
<!-- There is a summary of the results (2 pt) -->
<!-- There is a recommendation on using a different model to solve the classification problem, and justification (3 pt) -->
As summarized [Compiling, Training, and Evaluating the Model](#compiling-training-and-evaluating-the-model), the models did not achieve the goal 75% accuracy.  Changing the number of layers, neurons, and hidden layer activation functions had minimal effect.  Since the target is a binary classification, a supervised machine learning model such as the Random Forest Classifier may perform better than the deep learning models.
