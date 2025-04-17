# Buy_Sell_Hold_ML_Prediction

🚀# Overview:


This an ML process that predicts and models the return distribution of the stock price of Apple(AAPL), Microsoft(MSFT), and S&P500(SPY), and predicts a BUY, SELL or HOLD. This is valuable to algorithmic traders and the like who are interested inculcating ML predictions to their processes and trades.

**Problems Encountered: Data Cleaning and Exploration**

1. The price distribution of apple, microsoft and the S&P500 exhibits multimodal distribution which gives the false impression of presence of large outliers. This is indicative of different market regimes at play, which can also be an important feature for  the model.
![image](https://github.com/user-attachments/assets/b2a00753-3870-4492-ad35-0619da374113)
![image](https://github.com/user-attachments/assets/ab0a0bfd-e7bf-4cf2-ad25-bf67856712a0)
![image](https://github.com/user-attachments/assets/adc02743-f079-44d0-a17e-6b7583c579aa)
![image](https://github.com/user-attachments/assets/1654c8fb-2a72-4c31-8224-9e6848b3f86f)



3. Absolute Gamma Exposure value have few negative values present, which in practise in highly unlikely.
   ![image](https://github.com/user-attachments/assets/9afb4989-ebf8-41c0-aba0-791aec4bbff9)


4. Imbalanced classes after target and feature engineering; The ratio of Hold data points to buy/sell data points was like 8:1
   


**Solutions:**

1. I applied the Gaussian Mixture Model, a regime detection model. This identified the inherent regimes within the data. Additionally, the 90th and 10th quantile values were also derived from each regime in order to treat returns based on applicable regime. This eliminates the removal of extremely high returns which arent outliers.

2. Negative gamma was taken out from the data across all assets.
3. Highly imbalanced classes in any model will prevent the model from learning actual patterns for the undersamples classes, thereby favouring the oversampled set. I applied the undersampling technique of data removal. I reduced the HOLD class to a ratio of 0.98:1 of buy and sell. 
![image](https://github.com/user-attachments/assets/01537db6-6d82-489b-afda-2de8d57bd386)


**Target Engineering:**

The label of the prediction is based on the quantile values within identified regime. Buy is next 10 period return is greater than the 90th percentile of return distriution within said regime. Sell if next 10 period return is less than the 10th of return distriution within said regime, and Hold if otherwise.

**Feature Engineering:**

The derived features for the modelling process includes:
1. Log of close price:
2. Past 10 periods return
3. Rolling standard deviation
4. candle way:
5. Relative difference between the past 10 & 30 periods Rate of change
6. Relative Difference between the past 10 & 30 periods momentum
7. stochastic Oscilator
8. smoothed stochatic oscilator
9. Relative Difference between the past 10 & 30 periods stochastic oscilator
10. Relative Difference between the past 10 & 30 periods smoothed stochastic oscilator
11. Kama moving average
12. kama market regime indicator
13. Relativs stochastic index (RSI)
14. log of absolute gamma exposure
15. log of net gamma exposure
16. Parkinson volatility
17. Relative Difference between the past 10 & 30 periods parkinson volatility
18. Relative Difference between the past 10 & 30 periods closed net gamma exposure
19. Relative Difference between the past 10 & 30 periods closed absolute gamma exposure
20. the direction or sign of the net gamma exposure.


**Multicollinearity & Correlation with Response:**

![image](https://github.com/user-attachments/assets/9242bef2-6d0a-4b24-b2df-88c6e25a43df)
Observed correlation among features is fair. However, features dont exhibit very strong linear movement with the response variable

All assets correlation with features:
![image](https://github.com/user-attachments/assets/31f4fcb9-c852-47fa-a997-e7f55a8c129d)



**Market Regime Detection:**

The Gaussian mixture model identified 3 regimes: 0,1,2. The QUANTILE VALUES OF REGIME identified are:
![image](https://github.com/user-attachments/assets/2083b669-917a-4a1e-bdc2-62bddbcd1453)



**MODEL PERFORMANCE DURING CROSS VALIDATION:**

LR: 0.840966 (0.094231) :Linear Regression
CART: 0.938713 (0.138179) : Decision Tree classifier
RF: 0.928015 (0.130977)    : Random Forest Classifier

![image](https://github.com/user-attachments/assets/cee94c2c-6525-4966-bf73-95096457e69d)

**Hyperparameter Tuning:** 

The Random forest was tuned and produced the following model parameters as optimal:


Best: 0.930693 using {'criterion': 'entropy', 'max_depth': 10, 'n_estimators': 80}


**Model Performance Across Unseen Test Set:**


![image](https://github.com/user-attachments/assets/36f82f4c-ed8e-461d-8cbd-e5195de66874)

