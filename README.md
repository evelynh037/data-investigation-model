# data-investigation-model

## Problem Identification


## Baseline Model
### Basic features of Model
We create a tree decision model for our baseline model. Before training the data, we split our dataset into 75% and 25% as training and testing dataset. There are 4 predictor variables included in this model. For quantitative variables, we directly derive 3 varibles from the dataset: 'minutes','n_steps', and'n_ingredients'. When thinking about categorical variables, we think that whether the users write review carefully can also be a factor related to the rating. Therefore, we choose to perform FunctionTransform on 'review', and choose 'review' as our categorical variable. We choose 3 as our depth when training the data.
<br />
### How we encode categorical data
When looking closely into the dataset, we found that most of the users fill the 'review' with the rating, and thus, whether they fill the 'review' will not be a useful criteria.Then, we found that some users only fill in one word or two into the 'review'. So we choose to categorize 'reivew' into: word counts over 3 and word counts less or equal to 3. If they fill the 'review' with word count over 3, we will categorize it as a careful review, and vice versa. We design a FunctionTransformer, which employs a lambda function to split the 'review' and return Ture if length of the words over 3 and False if less or equal to 3. Then, we use a pipeline to transform and then one-hot encode it.
<br />
### Accuracy and Comments
We run the accuracy several times on the trained dataset, and the accuracy rate remains about 0.77. Also, the tested data shows a constant accuracy rate of about 0.77. However, when we get the distribution of the values, the rating of 5 has the distribution of 0.77. That is, if the model predict all the outcome is 5, it can have an accuracy score of 0.77. Therefore, we don't think that this baseline model is a good one.
<br />

## Final Model

## Fairness Analysis
