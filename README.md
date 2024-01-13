# Data Mining with National Crime Victimization Survey

## Data Introduction

Before loading any data into R, our first step was to read the provided NCVS codebook and become familiar
with the context of the study. This allowed us to build an understanding of the types of responses and what
we would need to be mindful of in the dataset. We found that the responses are all categorical-for example,
the field V2022 is for “Location of Phone” and has possible values ranging from 1 to 9. According to the
codebook, the responses will fall into one of the following categories:

• Valid values are usually in the range of smaller integer numbers. <br/>
• Explicit “don’t know” responses are ones that are clearly offered as a response type <br/>
• Blind “don’t know” responses are not offered but still accepted for most questions <br/>
• Refused response means the respondent chose not to answer <br/>
• “Residue” responses usually mean something is missing and are usually identified by ‘8’, ‘98’, ‘99’,
‘998’, etc. based on the length of an accepted response<br/>
• “Out of scope/universe” responses are those that are not applicable to the question<br/>

There are several reasons why a response might be blank, causing some ambiguity between blind “don’t
know” responses and refused responses. However, we can handle residue and out of scope responses in our
preprocessing.<br/>
Our initial dataset contains 4947 tuples of 204 variables before any preprocessing. In addition to the 203
training variables, the target variable is o_bullied - it has a value of 1 if the student experienced bullying
and 0 if they did not. Because we have a positive and negative class, we will be building binary classifiers.


## Data Mining Tools
• modeest <br>
• dplyr <br>
• e1071<br>
• caret<br>
• rsample<br>
• rpart<br>
• randomForest<br>
• xgboost<br>
• glmnet<br>
• pROC<br>
• class<br>
• nnet<br>

## Prprocessing
Since there are results that indicate non-answers, we will be avoiding including those in our training. There
are also several columns that are heavily populated by a single response. Our first step is to target low
variance and noisy data. One way to address these in bulk is to simply filter by number of factors. Variables
with only a few levels will not contain Residual or Out of universe responses

## Classification Algorithms
• Algorithm 1: Logistic Regression<br>
• Algorithm 2: Decision Tree/Random Forest<br>
• Algorithm 3: Gradient Boost (XGBoost)<br>
• Algorithm 4: Naive Bayes<br>
• Algorithm 5: K-Nearest Neighbors<br>
• Algorithm 6: Neural Network<br>
• Algorithm 7: SVM<br>

## Model Results and Evaluation
By creating a function to calculate the performance measures based on a given confusion matrix, we can
keep our calculations clean. By using class weights as function arguments, we can adjust as needed for
each model we train, giving us flexibility. Additionally, we have a function for identifying factor levels that
are not present in both tr and ts, since this may happen for some splits. See Appendix 1.1 for the full
calculate_measures function

## Conclusion

Out of our several models, the best performing would be Model 1.2. Using regularization with logistic regression fit the problem space well and plotting ROC was useful for tuning the model. After several iterations of data preprocessing, we found that too much and too little both negatively impacted performance significantly. Finding a balance of meaningful data while keeping the models performant and interpretable was the greatest challenge.

ROC curves for models is included in the Markdown PDF, along with other code explanation.
