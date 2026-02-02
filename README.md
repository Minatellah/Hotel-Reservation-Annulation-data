
## Dataset Description

- **Source**: Kaggle – Hotel Reservation Cancellation Dataset  
- **Task**: Binary classification (Canceled vs. Not Canceled)

---

## Data Cleaning and Exploratory Analysis

An initial exploratory analysis revealed several data quality issues that required careful preprocessing.

The variables `agent` and `company` contain a large number of missing values. Although this might suggest removing them, empirical experiments showed that retaining these variables led to better model performance. This indicates that the missingness itself carries informative patterns that the model can exploit.

The variable `children` contained only four missing values, which were imputed with zero, assuming the absence of children when the information was missing. The variable `country` had 488 missing values and was imputed using a default value to preserve the number of observations.

Additionally, 188 observations corresponded to invalid bookings where the number of adults, children, and babies were all equal to zero simultaneously. These rows were considered non-informative and were therefore removed from the dataset.

---

## Descriptive Insights

The dataset includes guests originating from 166 different countries, highlighting the international scope of hotel reservations. The majority of bookings originate from Portugal, followed by other European countries.

Clear seasonal patterns were observed. August is the month with the highest number of reservations, which is consistent with summer vacation effects. City hotels receive the largest share of bookings, and room type A is the most frequently reserved.

---

## Feature Selection

Several variables were identified as weakly informative with respect to the target variable or redundant given other features (low correlation with the target variable). These variables were removed to reduce noise and model complexity and to improve generalization performance. (avoid overfitting)

---

## Feature Transformation and Outlier Handling

Outliers were handled during preprocessing to reduce their influence on model training. Additionally, a log transformation was applied to numerical features because this consistently provided a better resulting performance of predictive models than both standard scaling and Min–Max scaling.

Since we cannot calculate a log of 0, one was added to the affected numerical features before transforming them via a log transformation. This transformation also reduced skewness and the impact of extreme values.

---

## Model Training Strategy

A neural network classifier was trained using the preprocessed dataset. To prevent overfitting, dropout regularization was applied, making it harder for the model to learn spurious patterns.

Early stopping was used during training to halt the optimization process once validation performance stopped improving. The model parameters corresponding to the lowest validation loss were retained, ensuring optimal generalization.

---

## Model Performance and Evaluation

Both training and validation metrics exhibit a consistent increase in accuracy alongside a decrease in binary cross-entropy loss, suggesting stable learning and limited overfitting.

The confusion matrix reveals strong predictive performance, with a high number of true positives and true negatives. False negatives—cases where a canceled reservation was incorrectly predicted as non-canceled—were particularly rare, which is desirable in the context of cancellation prediction.

Overall, the model demonstrates good generalization ability and balanced predictive performance.

---
