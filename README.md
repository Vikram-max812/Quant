Quant Task 3: Regime-Aware Volatility Prediction — Interview Presentation
Objective
The goal of this task is to predict the 5-day forward volatility of a stock or index by identifying different market regimes using clustering on technical indicators. Each regime has a dedicated model trained on its historical behavior, making the pipeline adaptive and behavior-aware.
Pipeline Overview
1. Data Collection:
- Fetched OHLCV data from Yahoo Finance for ^NSEI from 2022 to 2024.

2. Feature Engineering:
- Computed technical indicators: RSI, MACD Histogram, ADX, Bollinger Band Width, Volume % change.

3. Regime Detection:
- Normalized regime indicators.
- Used KMeans clustering with silhouette scores to find optimal number of regimes (typically 3).
- Labeled each row with a market regime (0, 1, 2, etc.).

4. Target Variable:
- Computed 5-day forward volatility using rolling standard deviation of log returns.

5. Model Training:
- Split data by regime.
- Trained one Linear Regression model per regime.
- Saved each model using pickle.

6. Live Inference:
- Extracted the latest indicators.
- Predicted the current regime using saved KMeans model.
- Loaded the corresponding regression model to forecast future volatility.

7. EDA:
- Visualized correlation heatmap of all features.
- Inspected distribution of target volatility.
Key Highlights & Learnings
- Regime-awareness significantly improves modeling by reducing behavioral noise.
- Yang-Zhang volatility added robustness as a feature without being used as the target.{the yang-Zhang model was calculated separately, but not added in the final algo}
- Separate models for different market moods outperformed single-model approaches.
- Pipeline is modular, interpretable, and scalable to other indices and time frames.
Conclusion
This project demonstrates a practical and robust application of machine learning in financial time series, combining technical analysis, clustering, and model specialization. The regime-based architecture enables dynamic adaptation to changing market conditions, improving forecast reliability and interpretability.
Files: Quant_Predicting_Future_Volatility.ipynb
README.md - this file
