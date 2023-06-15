# Recipe labeling specifically for label "Dietary" 
# if the recipe would be labled as "dietary" or not?


## Framing the Problem
### our prediction problem
In today's health-conscious world, there is a growing demand for dietary recipes that cater to specific dietary needs and preferences. Therefore, this model is built helping to predict whether or not one recipe would be tagged with the label "dietary" in food.com given features "ingredients"(ingredients used in the recipe), "minutes"(minutes to prepare recipe), "description"(user-provided description to the recipe), "protein (PDV)", "carbohydrates (PDV)" and "calories (#)".
<br />
### why this variable and these features?
Our response variable would be "if dietary", either "would be tagged as dietary" or "would not be tagged as dietary" which can be extracted from their tags from the existing dataset for modeling. The reason why we picked this variable is because people are now focusing more and more on their health, and our model aimed to better help the website label their dietary recipes for users who are on diets. These are features that would be available upon time of prediction since the labeling happened after we gain all the information about the recipe, once the user successfully and fully put in all required elements to build the recipe. 
<br />
Moreover, dietary labeled recipes can also have many unique characteristics in menu descriptions, ingredients used, and also nutrition facts. The reason why we choose those features is that dietary recipes are tended to have special ingredients and without certain ingredients, are less time-consuming, have a good balance of nutrition components, and have likely to have certain words in the recipe descriptions. 
<br />
### why F1 as metrics?
Since the prediction only involves yes and no questions, it would be a binary classification problem. The matrices we are using to evaluate our model are F1 since there is a class imbalance between the "would be tagged as dietary" or "would not be tagged as dietary" two classes, we would take account of the TP(True positive), TN(True negative), FP(False positive),FN(False negative) of the model. By doing this, it would result in a more fair evaluation of our model and avoid misleads.
<br />
## Baseline Model
### about our model
We create a tree decision model for our baseline model. Before training the data, we split our dataset into 75% and 25% as training and testing datasets. The hyperparameter we picked are max_depth = 6, criterion = "gini",min_samples_split = 100 since there are 6 features, and "gini" work well with imbalanced data.
<br />
The features we took into our model are "ingredients", "minutes", "description", "protein (PDV)", "carbohydrates (PDV)","calories (#)" which would all be available if at the time of prediction. Among those features, we have 2 categorical and 4 numerical, ingredients(list with ingredients as elm), "description"(a string describing the recipe) are nominal features, and the rest("minutes", "protein(PDV","carbohydrates (PDV)","calories (#)" are quantitative features.
<br />
### how do we encode categorical data?
Before building our baseline model, we first conducted feature engineering on the two nominal features("description" and "ingredients"). 
<br />
For "description", we found that words like "healthy", "low-calorie","gluten-free" and "organic" are likely to be in dietary recipes, therefore we wrote our own FunctionTransformer to transform the "description" feature into True for "having one of these words in the description" and False for "do not have any of them in the description". *True and false can be evaluated as 1 and 0
<br />
For "ingredients", we found that dietary recipes are not likely to have "chocolate" or "bacon" as ingredients. Therefore, we then wrote our own FunctionTransformer to transform the "ingredients" feature into the total occurrence of these two words appearing in the recipes. We use a pipeline to transform and also one-hot encode it.
<br />
### accuracy and comments
We run the F1 score several times on the trained dataset, and the F1 remains at about 0.7013. Also, the tested data shows a constant accuracy rate of about 0.7092. However, when we calculate the proportion of recipes that have dietary as lable, the proportion is 69%. That is, if the model predicts all the outcome is 5, it can have an accuracy score of 0.69. Our model has a similar F1 score for the testing set(1% higher) and also 1% higher than the model which always predicts as "would be labeled as "dietary" for the testing set which is not very optimal.
<br />

## Final Model

## Fairness Analysis

grid-search result {'criterion': 'gini', 'max_depth': 10, 'min_samples_split': 200}

accuracy {'train': 0.702019613780894, 'test': 0.7218413320274242} 用这个
