# GWU project
Project 1- Model credit
# Credit Line Increase Model Card

### Basic Information

* **Model date**: August, 2021
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [DNSC_6301_Project.ipynb](DNSC_6302_Project.ipynb)

### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data

* Data dictionary: 

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

* **Source of training data**: GWU Blackboard, email chauhayu2511@gwu.edu, nbarge96@gwmail.gwu.edu and himanvesh@gwu.edu for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email chauhayu2511@gwu.edu, nbarge96@gwmail.gwu.edu and himanvesh@gwu.edu for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None



### Model details


Input columns: 

| Name | Description|
| ---- | ---------- |
|**ID**| unique row indentifier |
| **LIMIT_BAL** | amount of previously awarded credit |
| **SEX** | demographic information |
| **RACE** | demographic information | 
| **EDUCATION** | demographic information | 
| **MARRIAGE** | demographic information | 
| **AGE** | demographic information | 
| **PAY_0** | the repayment status in September, 2005 | 
| **PAY_2** | the repayment status in August, 2005 | 
| **PAY_3** | the repayment status in July, 2005 | 
| **PAY_4** | the repayment status in June, 2005 | 
| **PAY_5** | the repayment status in May, 2005 | 
| **PAY_6** | the repayment status in April, 2005 | 
| **BILL_AMT1** | amount of bill statement in September, 2005 |
| **BILL_AMT2** | amount of bill statement in August, 2005 |
| **BILL_AMT3** | amount of bill statement in July, 2005 |
| **BILL_AMT4** | amount of bill statement in June, 2005 |
| **BILL_AMT5** | amount of bill statement in May, 2005 |
| **BILL_AMT6** | amount of bill statement in April, 2005 |
| **PAY_AMT1** | the repayment status in September, 2005 | 
| **PAY_AMT2** | the repayment status in August, 2005 | 
| **PAY_AMT3** | the repayment status in July, 2005 | 
| **PAY_AMT4** | the repayment status in June, 2005 | 
| **PAY_AMT5** | the repayment status in May, 2005 | 
| **PAY_AMT6** | the repayment status in April, 2005 | 


Output column: 
| Name | Description|
| ---- | ---------- |
| **DELINQ_NEXT**| whether a customer's next payment is delinquent (late) or on-time |


* **Type of model**: Decision-tree model
* **Software used to implement the model**: Colaboratory
* **Version of the modeling software**: Python 3.6.9
* **Hyperparameters or other settings of the model**: The cutoff of lending money is 0.12 below which the accuracy gets hampered for the given dataset.


### Quantitative analysis 
* **Metrics used to evaluate the final model**: Confusion metrics 
* **Final values of the metrics for all data**: 
  * Training AUC: 0.78
  * Validation AUC: 0.75
  * Test AUC: 0.74 
  * Asian-to-White AIR: 1.00
  * Black-to-White AIR: 0.85
  * Female-to-Male AIR: 1.02
  * Hispanic-to-White AIR: 0.83
 
### Plots 

* **Training decision tree**

![Graph 1](https://user-images.githubusercontent.com/89392789/131267465-0b5f8d90-6ce5-4d68-8472-7c5f26be7196.png)


* **Tree depth vs. training and validation AUC and AIR**


![image](https://user-images.githubusercontent.com/89392789/131266853-c3af72c9-1a94-48a9-9498-08015df2a1fb.png)

* Interpretation from the plot: Depth = 6 is the best choice



### Ethical considerations 
* **Potential negative impacts of using the model**:
  * Math or software problems: Different Software version can fetch different results leading to potential impacts on decision making. Some algorithms can give different results with the same dataset based on their nature(deterministic or stochastic)
  * Real-world risks: who, what, when or how: Bias in data can be augmented over time if the model trains itself on the same data. Taking decisions based on data requires the data to be regularly scrutinised for biases. This demands transparency which is beneficial to eliminate biases but can invite attacks/data poisoning incidents
* **Potential uncertainties relating to the impacts of using your model**: 
  * Math or software problems: Data security is uncertain, breaches can directly impact a lot of people
  
* **Real-world risks: who, what, when or how?**:
  * Using race/gender in the data can lead to ethnic or gender based profiling, which can impair decision making.

* **Any unexpected or results**:
  * female-to-male AIR: 1.06
  * hispanic-to-white AIR: 0.76




