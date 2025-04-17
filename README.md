# Buy_Sell_Hold_ML_Prediction

🚀# Overview:


This an ML process that predicts and models the return distribution of the stock price of Apple(AAPL), Microsoft(MSFT), and S&P500(SPY), and predicts a BUY, SELL or HOLD. This is valuable to algorithmic traders and the like who are interested inculcating ML predictions to their processes and trades.

**Problems Encountered:**

1. The price distribution of apple, microsoft and the S&P500 exhibits multimodal distribution which gives the false impression of presence of large outliers. This is indicative of different market regimes at play, which can also be an important feature for  the model.
![image](https://github.com/user-attachments/assets/b2a00753-3870-4492-ad35-0619da374113)
![image](https://github.com/user-attachments/assets/ab0a0bfd-e7bf-4cf2-ad25-bf67856712a0)
![image](https://github.com/user-attachments/assets/adc02743-f079-44d0-a17e-6b7583c579aa)


2. Absolute Gamma Exposure value have few negative values present, which in practise in highly unlikely.
   ![image](https://github.com/user-attachments/assets/9afb4989-ebf8-41c0-aba0-791aec4bbff9)


4. Imbalanced classes after target and feature engineering; The ratio of Hold data points to buy/sell data points was like 8:1
   

**Solution:**
. I applied the Gaussian Mixture Model, a regime detection model. This identified the inherent regimes within the data.
. Negative gamma
Key Features: Bullet points of unique aspects.
