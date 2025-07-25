# Commodity Price Prediction, Penyisihan Datavidia 9
## Overview
As global food markets experience increasing volatility, accurately predicting commodity prices has become a critical challenge for policymakers, businesses, and researchers. This Food Commodity Price Prediction competition offers participants the opportunity to analyze factors that influence price fluctuations in food commodities. The provided dataset includes historical price trends, market conditions, and economic indicators that play a role in food price changes across different regions. By applying data science techniques, participants can uncover valuable insights into the market dynamics underlying price movements.
## Problem Statement
The fluctuation of food commodity prices has significant economic and social impacts, ranging from household budgeting to global trade policies. In this competition, participants are challenged to develop predictive models that estimate commodity prices based on historical data. The dataset includes various features such as past prices, currency exchange rates, global supply trends, and macroeconomic indicators. Using this data, participants are expected to build models capable of predicting the price of each commodity for specific dates within a given timeframe with high accuracy.
## Objective
The objective of this competition is to encourage data scientists to sharpen their skills in building accurate predictive models. By participating, contestants contribute to a deeper understanding of food price movements and their implications for food security and economic stability. In addition to enhancing technical capabilities, this competition emphasizes the importance of data-driven decision-making in managing food supply chains and reducing the risks of price volatility.

---

## Evaluation
### Mean Absolute Percentage Error (MAPE)
Submissions are evaluated using the Mean Absolute Percentage Error (MAPE), which in the scikit-learn library is defined as follows:

![image](https://github.com/user-attachments/assets/62462714-0345-4022-b227-62dbbc2a18dd)

Where yi is the actual value (ground truth) and ŷi is the predicted value for each observation i
```
import numpy as np

def mape(y_true: np.ndarray, y_pred: np.ndarray) -> float:
    """
    Calculate the Mean Absolute Percentage Error (MAPE).

    Parameters:
    y_true (array-like): True values.
    y_pred (array-like): Predicted values.

    Returns:
    float: The calculated MAPE.
    """
    return np.mean(np.abs((y_true - y_pred) / y_true))

```

Alternatively, MAPE can be calculated using the scikit-learn library:
```
from sklearn.metrics import mean_absolute_percentage_error
mape = mean_absolute_percentage_error(y_true, y_pred)
```

### Why MAPE?
MAPE is chosen because it provides an intuitive percentage-based error metric, making it highly effective for this competition where accurate commodity price prediction is crucial. Given the influence of economic and market factors on commodity price fluctuations, participants are expected to develop models that consistently produce smaller percentage errors.
---

## Results & Discussion 
The time series analysis conducted is a multivariate analysis, using several attributes as predictors for forecasting time series data.

From the available datasets, we chose to use the prices of six global commodities and the exchange rate of the Indonesian Rupiah to the US Dollar. The global commodity price data includes the following columns:
- price: market closing price
- open: market opening price
- high: highest price of the day
- low: lowest price of the day
- vol.: the number of contracts traded
- change %: percentage change in price compared to the previous day's close

We decided to use only the exchange rate of the Indonesian Rupiah to the US Dollar. After performing a correlation heatmap analysis to determine the Pearson correlation between food commodity prices and currency exchange rates, we found that only the exchange rate of the Indonesian Rupiah to the US Dollar significantly affected food commodity prices — specifically for medium rice, premium rice, and consumer sugar.

The columns in the currency exchange rate dataset include:
- open: indicates the first price of the day
- high: shows the highest price reached during the day
- low: shows the lowest price reached during the day
- close: indicates the final price before the market closed
- adj close: the adjusted closing price and is equal to close for currencies
- volume: indicates the number of units traded on that day. We chose to use only the close column as it most accurately represents the exchange rate for that day.
We selected only the close value, as it most accurately represents the exchange rate for a given day.

We opted not to use the Google Trends dataset due to a high number of missing values and the difficulty of sourcing both past and future covariate data.

The hyperparameter n_estimators in the Random Forest Regressor determines the number of decision trees to be used. Through hyperparameter tuning with n_estimators = 50, 100, and 200, we found that n_estimators = 100 yielded the best predictions, based on the lowest MAPE value. The resulting MAPE for sugar in the Aceh region was 0.063.
---

## Competition Link
https://www.kaggle.com/competitions/comodity-price-prediction-penyisihan-arkavidia-9

## Citation
Datavidia. Commodity Price Prediction, Penyisihan Datavidia 9. https://kaggle.com/competitions/comodity-price-prediction-penyisihan-arkavidia-9, 2025. Kaggle.
