# Deep Learning Challenge

## Overview of the Analysis

* The purpose of this analysis is to use the deep learning models and neural networks to predict/classify the if applicants of a nonprofit foundation Alphabet Soup would be successful if they were given funding. 

## Results

* Data Preprocessing

    * This dataset contained in the "Resources" folder has columns labelled `EIN`, `NAME`, `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, `ASK_AMT`, and `IS_SUCCESSFUL`. This final column has values `0` for successful ventures and `1` for unsuccesful ventures and were the target variables for our analysis. In our first analysis, the `EIN` and `NAME` columns were dropped as they were identification columns and deemed to be non-beneficial.

    * The first task was to inspect the data to be placed in bins to reduce the amount of unique values. Then, the categorical data was converted to numerical data with the `pd.get_dummies` function. Here, the data was scaled and split into training and testing sets to be passed into our model.

* Compiling, Training, and Evaluating the Model 

    * The next task was to create the Keras sequential model imported from the Tensorflow module, setting basical parameters such as two hidden layers, 100 epochs, and activation values `relu` and `sigmoid`. Then, we fit the model with our training data to evaluate with the test data. This resulted in an accuracy score of 72.7%. The model's result was then exported to an HDF5 file.

    * Finally, we were tasked with optimizing the model to achieve an accuracy of at least 75%. To do so, we chose to include the `NAME` and `ASK_AMT` columns to inspect and place their values in bins. The number of layers and input features were increased (3 hidden layers from 2 and [90,30,10] input features from [16,16] ) as well as changing most of the activation values to `sigmoid`. This resulted in an increased accuracy score of 77.8%, exceeding our desired goal of 75%. For the sake of comparison, we imported and used SKLearn's `DecisionTreeClassifier` model to fit our trained dataset and predict the test dataset. Using this model, we achieved an accuracy score of 77.7%, which is nearly identical to our previous model. It should be noted that this model took a significantly less amount of time to run and produce similar results.

## Summary

When optimized, this model has a 77.8% chance of correctly classifying if an applicant will be successful in their ventures. Since this is over the 75% threshold, Alphabet Soup can be recommended to trust the model with handling their decision to approve funding to the applicants. Additionally, Alphabet Soup may be recommended the Decision Tree Classifier model as its performance is on par with the optimized model all while saving time and processing power.