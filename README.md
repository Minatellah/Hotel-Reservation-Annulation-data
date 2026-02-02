# Prediction of Hotel Reservation Cancellations  
*A Study on the Impact of Data Preprocessing Strategies*

---

## Abstract

This project focuses on predicting hotel reservation cancellations using the *Hotel Reservation Cancellation* dataset from Kaggle.  
Beyond predictive performance, the main objective is to analyze how different **data preprocessing techniques** affect model accuracy and generalization. Several preprocessing pipelines were tested, and the final model corresponds to the configuration that achieved the best performance while limiting overfitting.

---

## Dataset Description

- **Source**: Kaggle – Hotel Reservation Cancellation Dataset  
- **Task**: Binary classification (Canceled vs. Not Canceled)  
- **Features**:  
  Booking information, customer characteristics, temporal variables, agent and company identifiers, and reservation status details.

---

## Methodology

### 1. Temporal Variable Processing

The variable `reservation_status_date` contains important temporal information.

- Dropping this variable without feature extraction led to **overfitting**.
- To preserve its informational content, the variable was processed separately by extracting relevant components (year, month).
- This approach improved generalization and model stability.

---

### 2. Handling Missing Values (`agent` and `company`)

- The variables `agent` and `company` contain a large proportion of missing values.
- Instead of removing these variables, they were retained.
- Empirical results indicate that the model benefits from these features, suggesting that **missingness itself carries predictive information**.

---

### 3. Feature Transformation

Several scaling and transformation techniques were evaluated:

- Standard scaling  
- Min–Max scaling  
- Logarithmic transformation  

Among these, **log transformation produced the highest accuracy**.  
It reduced skewness in numerical variables and improved the learning process.

---

### 4. Outlier Treatment

- Outliers were initially handled using standard preprocessing techniques.
- In addition, log transformation further **reduced the influence of extreme values**, contributing to improved robustness.

---

### 5. Encoding of Categorical Variables

- One-Hot Encoding was avoided due to the high dimensionality it would introduce.
- Instead, categorical variables were encoded using alternative encoding techniques, allowing the model to remain parsimonious while preserving predictive power.

---

## Model Training and Evaluation

- Multiple preprocessing pipelines and model configurations were tested.
- Model selection was based on validation performance, with particular attention to overfitting.
- The final pipeline corresponds to the preprocessing strategy described above and achieved the best predictive accuracy.

---

## Conclusion

This project highlights the critical role of **careful data preprocessing** in applied machine learning.  
In particular, the treatment of temporal variables, missing data, feature transformations, and categorical encodings significantly influences model performance and generalization.

---

## Tools and Libraries

- Python  
- pandas  
- numpy  
- scikit-learn  

---

## References

- Kaggle: Hotel Reservation Cancellation Dataset

