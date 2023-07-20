# Stock market prediction
Implemented a trading strategy using the S&P 500 data. By training a RandomForestClassifier on historical data and using the model to predict whether the stock price will increase or not on the next trading day. Then backtests the model on rolling windows of data to evaluate its performance.
## Libraries
* sys: Used to modify the system path to include additional directories for importing modules.
* yfinance: A library for fetching financial data from Yahoo Finance.
* pandas: Used for data manipulation and analysis.
* os: Provides a way to interact with the operating system and handle file paths.
## Data 
A CSV file named "sp500.csv" is used which must be downloaded in the local machine and reads the data into a DataFrame called sp500 using pandas Or else the S&P 500 data is fetched from Yahoo Finance using the yfinance library, saves it as "sp500.csv," and then reads it into the DataFrame.
## Data preprocessing and Feature Engineering
* The index of the sp500 DataFrame is converted to datetime format using pd.to_datetime().
* The "Dividends" and "Stock Splits" columns are deleted from the DataFrame using the del statement.
* A new column named "Tomorrow" is created by shifting the "Close" prices one step backward.
* A binary "Target" column is created to indicate whether the price will increase (1) or not (0) on the next day.
## Random Forest Classifier
* The RandomForestClassifier from the sklearn.ensemble module is imported.
* The model is initialized with n_estimators=100, min_samples_split=100, and random_state=1.
## Data splitting and model training
* The sp500 DataFrame is split into training and test sets.
* The predictors for the model are defined as ["Close", "Volume", "Open", "High", "Low"].
* The model is trained on the training data using the fit() method.
## Model Evaluation
* The model is used to predict the target variable on the test set.
* The predictions are evaluated using the precision_score from sklearn.metrics.
## Backtesting the model
* A function named predict is defined to make predictions using the trained model.
* Another function named backtest is defined to backtest the model on rolling windows of data.
* The backtest function is used to perform backtesting on the sp500 DataFrame with different horizons (2, 5, 60, 250, and 1000).
## Feature engineering with rolling averages and trends
New features are created for different horizons based on rolling averages and trends of the "Close" prices and the "Target" variable.
## Model update and thresholding
* The RandomForestClassifier model is updated with n_estimators=200 and min_samples_split=50.
* The predict function is modified to return probabilities and threshold the predictions at 0.6 to get binary values.
## Backtesting with new features
The updated model is backtested on the sp500 DataFrame with the new predictors.
## Model evaluation for backtesting results
Precision scores are calculated for the backtesting results to evaluate model performance.
