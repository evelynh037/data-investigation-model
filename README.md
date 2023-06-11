# data-investigation-model

## Problem Identification


## Baseline Model
### Basic features of Model
We create a tree decision model for our baseline model. Before training the data, we split our dataset into 75% and 25% as training and testing dataset. There are 4 predictor variables included in this model. For quantitative variables, we directly derive 3 varibles from the dataset: 'minutes','n_steps', and'n_ingredients'. When thinking about categorical variables, we think that whether the users write review carefully can also be a factor related to the rating. Therefore, we choose to perform FunctionTransform on 'review', and choose 'review' as our categorical variable. We choose 3 as our depth when training the data. 
<br />
### How we encode categorical data

<br />
### Accuracy and Comments

<br />
## Final Model

## Fairness Analysis
