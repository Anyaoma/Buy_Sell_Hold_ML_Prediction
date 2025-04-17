# Buy_Sell_Hold_ML_Prediction

🚀# Overview:


This an ML process that predicts and models the return distribution of the stock price of Apple(AAPL), Microsoft(MSFT), and S&P500(SPY), and predicts a BUY, SELL or HOLD. This is valuable to algorithmic traders and the like who are interested inculcating ML predictions to their processes and trades.

**Problems Encountered: Data Cleaning and Exploration**

1. The price distribution of apple, microsoft and the S&P500 exhibits multimodal distribution which gives the false impression of presence of large outliers. This is indicative of different market regimes at play, which can also be an important feature for  the model.
![image](https://github.com/user-attachments/assets/b2a00753-3870-4492-ad35-0619da374113)
![image](https://github.com/user-attachments/assets/ab0a0bfd-e7bf-4cf2-ad25-bf67856712a0)
![image](https://github.com/user-attachments/assets/adc02743-f079-44d0-a17e-6b7583c579aa)


2. Absolute Gamma Exposure value have few negative values present, which in practise in highly unlikely.
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
2. 
