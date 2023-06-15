# data-investigation-model

## Framing the Problem
<br />
In today's health-conscious world, there is a growing demand for dietary recipes that cater to specific dietary needs and preferences. Therefore, this model is built helping to predict whether or not one recipe would be tagged with the label "dietary" in food.com given features "ingredients"(ingredients used in the recipe), "minutes"(minutes to prepare recipe), "description"(user-provided description to the recipe), "protein (PDV)", "carbohydrates (PDV)" and "calories (#)".
<br />
<br />
Our response variable would be "if dietary", either "would be tagged as dietary" or "would not be tagged as dietary" which can be extracted from their tags from the existing dataset for modeling. The reason why we picked this variable is because people are now focusing more and more on their health, and our model aimed to better help the website label their dietary recipe for user who are on diets.
<br />
<br />
Morover, this label also have many unique characteric in either menu description, ingredients used and also nutrition facts. The reason why we choose those features is that dietary recipes are tended to have special ingredients(vegetables, fruits, whole grains) and without certain ingredients(chocolate, sugar), are less time-consuming, have a good balance of nutrition components, and have likely to have certain words in the recipe descriptions. 
<br />
<br />
Since the prediction only involves yes and no questions, it would be a binary classification problem. The matrices we are using to evaluate our model are F1 since there is class imbalance between the "would be tagged as dietary" or "would not be tagged as dietary" two class, we would taken account of the TP(True positive),TN(True negative),FP(False positive),FN(False negative) of the model. By doing this,it would result in a more fair evaluation of our model and avoid misleads.
<br />
<br />

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
