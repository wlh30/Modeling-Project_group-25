# Modeling-Project_group-25
## Group 25 project for DNSC 6301

### Basic Information

* **Person or organization developing model**: Group 25 (Melissa, 'mrwehumbiza@gwu.edu'; Danyu, 'dzhao22@gwu.edu'; Jinni, 'jinni.yang02@gmail.com'; Saloni, 'sharmasaloni987@gmail.com')
* **Model date**: August, 2022
* **Model version**: 1
* **License**: MIT 
* **Model implementation code**: https://github.com/mrwehumbiza/Modeling-Project_group-25

### Intended Use
**Primary intended uses**: This model determines the eligibility for a credit line increase.
**Primary intended users**: Professor Hall for grading in Bootcamp course.
**Out-of-scope use cases**:Any use beyond an educational example is out-of-scope.

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

* **Source of test data**: credit_line_increase.csv,GWU Blackboard, email  'mrwehumbiza@gwu.edu', 'dzhao22@gwu.edu', 'jinni.yang02@gmail.com', or 'sharmasaloni987@gmail.com' for more information
* **Number of rows in test data**: 7500 rows 
* **State any differences in columns between training and test data**: None
