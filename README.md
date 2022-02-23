# Neural Network Charity Analysis

## Overview
We have been tasked with predicting whether applicants will be successful if funded by Alphabet Soup. Using Alphabet Soup Charity's dataset and our knowledge of machine learning and neural networks, we created a model to make our predictions.

## Results


### Data Preprocessing
- What variables are considered your targets for your model?
  - The "IS_SUCCESSFUL" varible is considered our target. We are looking for a binary yes (1) or no (0) output.
- What variables are considered to be the features for your model?
  - The variables/columns that are features are "APPLICATION_TYPE", "AFFILIATION", "CLASSIFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", and "ASK_AMT". All of these are independent variables and will factor into our model.
- What variables are neither targets nor features, and should be removed from the input data?
  - "EIN" and "NAME" are variables that are neither targets nor features, and should be removed from the input data.

### Compiling, Training, and Evaluating the Model
- How many neurons, layers, and activation functions did you select for your neural network model, and why?
  - For the model that achieved peak accuracy (Trial 2), I selected neurons of 160 for layer 1, and 60 for layer 2. I selected 2 layers, and used activation functions of "selu" and "relu" for layers 1 and 2, respectively. These specifications were selected by trial and error, testing out the different settings one at a time to see if it improved the model's performance or not.
- Were you able to achieve the target model performance?
  - I was only able to achieve 72.63% accuracy, under the target accuracy of 75%.
- What steps did you take to try and increase model performance?
  - The steps I took to try and increase model performance included, adding more neurons, adding more layers, and testing different activation functions.


## Summary
While the results of the model were not able to hit 75% accuracy as desired, I theorize that this is due more to the limitations of the data than the model. The data comes pre-binned for the column "INCOME_AMT", which is less than desireable to say the least. Income may be the biggest factor in if a loan gets approved, and to bin the amounts, in different ranges, severely limits the model. For example, there is a bin for income for any amount between $1 and $10,000, but there is also a bin for an amount between $100,000 and $500,000. Clearly the difference between $500,000 and $100,000 is significant, especially when we consider that "ASK_AMT" is a quantitative value that is not pre-binned. The data limits the model to not be able to make the distincion between two orgnanizations that can have very different incomes. For example lets look at two organizations, say Organization A and Organization B. Lets also say that the two organizations are completely identical except Organization A's income is $499,999 and Organization B's income is $100,000. Lets also say they ask amount is $1 million. Organization A takes about 2 years to make that amount, while Organization B takes about 10 years to make that amount. Because the data is previously binned, the model has to make the same decision when determining approval for Organization A and Organization B, but that may not be best practice. We could have achieved over 75% accuracy had we kept testing different parameters, but we also may overfit the data. I would recommend testing a simpler model, such as BalancedRandomForestClassifier to see if the results would be similar. BalancedRandomForestClassifier has pretty good results and takes much less time and resources than the deep learning model.
