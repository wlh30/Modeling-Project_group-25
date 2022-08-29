# Credit Line Increase Model Card

## Modeling Project_Group25

### Basic Information

* **Person or organization developing model**: Group 25 (Melissa, 'mrwehumbiza@gwu.edu'; Danyu, 'dzhao22@gwu.edu'; Jinni, 'jinni.yang02@gmail.com'; Saloni, 'sharmasaloni987@gmail.com')
* **Model date**: August, 2022
* **Model version**: 1
* **License**: MIT 
* **Model implementation code**: [Modeling Project_Group 25.ipynb](https://colab.research.google.com/drive/1osIMllwG6KZvSV7J4mqd7qMzAoLQH8QN#scrollTo=1E5B9hqpZrJr)

### Intended Use
* **Primary intended uses**: This model determines the eligibility for a credit line increase.
* **Primary intended users**: Professor Hall for grading in Bootcamp course.
* **Out-of-scope use cases**:Any use beyond an educational example is out-of-scope.

### Training Data

* **Source of training data**: GWU Blackboard, email  'mrwehumbiza@gwu.edu', 'dzhao22@gwu.edu', 'jinni.yang02@gmail.com', or 'sharmasaloni987@gmail.com' for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500
* **Data dictionary**:

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

###  Test data 
* **Source Data**:
In computer programming, source data or data source is the primary location from where data comes. The data source is a database, a dataset, a spreadsheet or even hard-coded data. When data is displayed, it is retrieved from its data source. The software processes this data internally, performing additional calculations if necessary, formats it, and updates the application window.
* **Test Data**:
Test Data is data that is used to execute the tests on testware. Test data needs to be precise and exhaustive to uncover the defects.Test Data is the input given to a software program during test execution. It represents data that affects or is affected by software execution while testing. Test data is used for both positive testing to verify that functions produce expected results for given inputs and for negative testing to test software ability to handle unusual, exceptional or unexpected inputs.

* **Source of test data**: credit_line_increase.csv,GWU Blackboard
* **Number of rows in test data**: 7500 rows 
* **State any differences in columns between training and test data**: None

###   Model details:
* **Columns used as inputs in the final model**: 'LIMIT_BAL',
       'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1',
       'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6',
       'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6'
* **Column(s) used as target(s) in the final model**: 'DELINQ_NEXT'
* **Type of model**: Decision Tree 
* **Software used to implement the model**: Python, scikit-learn
* **Version of the modeling software**: Python version: 3.7.13, sklearn version: 1.0.2
* **Hyperparameters or other settings of your model**: 
```
DecisionTreeClassifier(ccp_alpha=0.0, class_weight=None, criterion='gini',
                       max_depth=6, max_features=None, max_leaf_nodes=None,
                       min_impurity_decrease=0.0, min_impurity_split=None,
                       min_samples_leaf=1, min_samples_split=2,
                       min_weight_fraction_leaf=0.0, presort='deprecated',
                       random_state=12345, splitter='best')

```

### Quantitative analysis:

#### Metrics used to evaluate your final model: AUC and AIR
 * Training AUC: 0.7837
 * Validation AUC: 0.7496
 * Test AUC: 0.7438
 * AIR in Bias testing:

| hispanic-to-white AIR |black-to-white AIR | asian-to-white AIR | female-to-male AIR |
| ------ | ------- | -------- | -------- |
| 0.76 | 0.82  | 1.00 | 1.06 |
* AIR in Bias Remediation:

| hispanic-to-white AIR |black-to-white AIR | asian-to-white AIR | female-to-male AIR |
| ------ | ------- | -------- | -------- |
| 0.83 | 0.85  | 1.00 | 1.02 |


#### Plots related to model training:
####  The histograms for all the columns in the data
From the histogram, we can intuitively see the group attribute bias in our data—young, unmarried, highly educated women. You can also see the data distribution of each variable. For example, we found that in DELINQ_NEXT, the number of people who paid on time far exceeded those who delayed. This is helpful for comparing results on our training data.

![图片1](https://user-images.githubusercontent.com/111601038/187104499-a8dfbabf-bfc4-4f20-84f0-6b01dae28ae0.png)
![图片2](https://user-images.githubusercontent.com/111601038/187104504-a6d73eba-d3a5-4327-ae84-97c0151be251.png)


####  Correlation Heatmap
In the heatmap, we find that the corresponding colors between the variables are dark and light. The lighter the color area, the stronger the relationship between the variables, which means that the variables influence each other; the darker the color area, the weaker the relationship between the variables.
From the figure, we can see that “history of past payment” has a certain influence on our target variable(DELINQ_NEXT), while race has almost no effect on the result of the target variable.

![图片3](https://user-images.githubusercontent.com/111601038/187104514-c89cb505-0d8d-4095-9af0-321a0749aebe.png)


####  Iteration Plot （Training the model by decision tree）:
By feeding the model training set and validation set, the AUC indicator is used to evaluate the degree of model learning, and the above figure is obtained. Through the plot function, we can intuitively see that the model has the best learning results when the tree depth=6, which helps us to define the training parameters of the model as 6.

![图片4](https://user-images.githubusercontent.com/111601038/187104539-61c0f73f-17c0-40bd-803f-2c8c8a682f6c.png)


####  Decision Tree:（Draw a decision tree with a depth of 6）
![下载](https://user-images.githubusercontent.com/111601038/187104693-404d00ae-155a-4779-a8e6-b46c3f55adfb.png)

####  Variable Importances:
The variables are sorted by importance by the importances.sort_values() function. It can be seen from the figure that the range of factors affecting the target variable(DELINQ_NEXT) is narrowed down to pay_0 (the repayment status in September).

![图片5](https://user-images.githubusercontent.com/111601038/187104554-b987660d-17ce-48ef-84ec-057e3a77c690.png)


####  Final Iteration Plot with AIR:
We added new information (race, sex) to train the model again, in order to get our desired AIR value (greater than 0.8). From the figure, we can see that the model with a tree depth of 6 works well by combining the indicators of AUC and AIR.

![图片6](https://user-images.githubusercontent.com/111601038/187104562-8107a413-0f8f-4c28-b9f8-df849e9834c5.png)


### Ethical considerations:
* **Math or software problems**

* The results of using a model is simply a measure, there is not a way to account for bias. Naturally, bias is built into a model and may lead to the model missing any relevant relationships between data inputs and the predictions. The model is very dependent on the status of the immediate payment, this could negatively impact the model depending on an individual's previous payment history. 

* Using a decision tree model creates a biased tree due to the dominance of certain categories, which affects the accuracy of the target variable. Therefore, we should balance the data before fitting it with a decision tree model, addressing the so-called bias problem from the outset.

* We found that in our model, the hyperparameters class_weight and max_leaf_nodes are all none, which will cause the data volume of the leaf nodes to be too large or too small, so that the data cannot be summarized well, thus affecting the prediction results of the next layer of leaf nodes. 

* **Real-world risks: who, what, when or how**

* Because the decision tree model relies too much on the “pay 0” variable in the data (that is, the last repayment status), this is not in line with real life. For example: I have repaid and paid off the loan several times before, but only recently failed to repay the loan on time by accident. According to the logic of the decision tree model, I cannot enjoy the increase in credit card limit. Then there will be people who only choose to pay off the bill on time for the last time in order to obtain a credit card with a higher limit.
