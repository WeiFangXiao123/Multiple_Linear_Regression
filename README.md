## Boston Housing Analysis with Linear and Non-Linear Regression Models
### Objective
The objective of this assignment is to apply **simple and multiple linear regression** techniques, as well as **non-linear modeling**, to analyze the Boston Housing dataset. The goal is to **understand the relationships between housing prices and various factors** such as distance to employment centers, tax rates, air quality, and socioeconomic indicators. Additionally, this project explores model performance through metrics like **Mean Squared Error (MSE)** and discusses implications for model selection.

### Dataset
The dataset consists of housing values in the suburbs of Boston based on the 1970 U.S. Census. Key variables include:
- **MEDV**: Median value of owner-occupied homes (in $1000’s) — Target variable
- **DIS**: Weighted distances to five Boston employment centers
- **TAX**: Full-value property-tax rate per $10,000
- **NOX**: Nitric oxides concentration (parts per 10 million)
- **LSTAT**: Percentage of population with low socioeconomic status

### Methodology
#### 1. Exploratory Visualization
A scatter plot of MEDV vs. DIS was created using ggplot2. A linear trendline indicates a positive, approximately linear relationship.

<img width="685" alt="Screenshot 2025-05-19 at 5 03 30 PM" src="https://github.com/user-attachments/assets/125e8d6f-b9a0-478a-bcfb-7feee421184b" />

#### 2. Simple Linear Regression
A baseline model (```lm_dis```) was estimated with DIS as the sole predictor. The MSE was calculated to evaluate model fit.

<img width="408" alt="Screenshot 2025-05-19 at 5 04 10 PM" src="https://github.com/user-attachments/assets/06d03e80-848a-4ff2-81d0-0c2d924a4448" />

#### 3. Overfitting Test with Random Predictors
Ten random variables were added to the dataset. A model (```lm_plus```) including these random variables showed a lower MSE than ```lm_dis```, illustrating how MSE alone can misleadingly favor more complex models due to overfitting.

#### 4. Multiple Linear Regression
Additional models were estimated by incrementally adding predictors:
- ```lm_tax```: adds TAX
- ```lm_nox```: adds NOX
- ```lm_ses```: adds LSTAT
  
The regression outputs were compared to assess how control variables affect the relationship between ```DIS``` and ```MEDV```.

#### 5. Non-linear Regression
A quartic model (```lm_dis_man```) was constructed manually using polynomial terms up to DIS⁴. This was compared to a model built using ```poly()``` (```lm_dis_poly```). Both produced identical predicted values, confirming **consistency**.

#### 6. Model Comparison via MSE
The MSE of both ```lm_dis_man``` (**non-linear**) and ```lm_ses``` (**multi-variable linear**) was computed and compared. Although the quartic model had a lower MSE, it may not generalize well due to higher complexity.

### Business Takeaway
- Distance to Employment Centers (DIS) has a significant positive relationship with housing prices

- Tax rates, air quality, and socioeconomic indicators meaningfully influence housing values when included as controls

- While adding predictors (even random ones) can **reduce MSE**, it does not guarantee better model performance in practice due to potential **overfitting**

- A **lower MSE does not always indicate a better model**; business context and predictive robustness should be considered when evaluating models

This analysis highlights the importance of **balancing model complexity** with interpretability and real-world relevance in property value prediction.
