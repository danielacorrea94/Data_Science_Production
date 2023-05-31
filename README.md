![image](https://github.com/danielacorrea94/Kaggle-Rossman-Sales-Prediction/assets/87499730/da6ec725-87c5-444a-a8e4-85177ad068b2)


# Rossmann stores #

### Disclaimer: this project was inspired by the "Rossmann Store Sales" challenge published on kaggle (https://www.kaggle.com/c/rossmann-store-sales). It is a fictitious project but with all the steps of a real project.

## Project Development Method

The project was developed based on the CRISP-DS (Cross-Industry Standard Process - Data Science, a.k.a. CRISP-DM) project management method, with the following steps:

- Business Understanding;
- Data Collection;
- Data Cleaning;
- Exploratory Data Analysis (EDA);
- Data Preparation;
- Machine Learning Modelling and fine-tuning;
- Model and Business performance evaluation / Results;
- Model deployment.
 
An end-to-end Data Science project with a regression adapted for time series as solution was created four machine learning models to forecast the sales. Predictions can be accessed by users through a bot from the smartphone app Telegram. 

## Results

- Exploratory Data Analysis and Preparation

![image](https://github.com/danielacorrea94/Kaggle-Rossman-Sales-Prediction/assets/87499730/a0f61d89-9daa-4764-b6dd-59da5e0ad7de)

- Machine Learning Model Performance

The Random Forest Regressor was the model that performed best, with a Mean Average Percentage Error (MAPE) of 12%. However, since the XGBoost Regressor is known to train data fastly than random forest algorithms, I decided to use the XGBoost regressor as the main machine learning model for the project and after crossvalidation it performed the best over the Random Forest Regressor.

![image](https://github.com/danielacorrea94/Kaggle-Rossman-Sales-Prediction/assets/87499730/21324a03-24ee-473b-a1a2-6572cf8d89a6)

Using the optimal set of parameters, we obtained the following results with the XGBoost model: 

![image](https://github.com/danielacorrea94/Kaggle-Rossman-Sales-Prediction/assets/87499730/89747b7f-5c85-4b1b-bf96-2fc93f2457c7)

- Business Results

Scenarios were created to reflect MAPE variations.

![image](https://github.com/danielacorrea94/Kaggle-Rossman-Sales-Prediction/assets/87499730/c5b46db2-a3a3-4420-97d5-14ea457e47e1)

- Telegram Bot


![image](https://github.com/danielacorrea94/Kaggle-Rossman-Sales-Prediction/assets/87499730/16a88403-702f-473d-a25b-b441abdcfc8b)


*How does it works?*

- A user send a text to a Telegram Bot with a store number it intends to receive the sales prediction;
- The Rossmann API (rossmann-bot.py) receives the request and access all the data related to this store from the test data;
- The Rossmann API sends the data to the Handler API (handler.py);
- The Handler API calls the data preparation class (Rossmann.py) to proccess the raw data and use the trained XGBoost model and return its prediction to Rossmann API;
- The API returns the total sales prediction for the next six weeks of the store.

## Important Notes
- The exploratory data analysis provides important insights to the business problem, many of which contradict the initial hypothesis. This information is valuable for the understanding of business and for planning future actions. This step also provides a preview of the result of the feature selection step.
- This predict problem was solved by using a Regression adaptaded to Time-Series method
- The choice of machine learning model used must consider the generalizability of the model, but also the cost of its deployment.

## References

- stores.csv from Kaggle (https://www.kaggle.com/c/rossmann-store-sales/data?select=store.csv)
- train.csv from Kaggle (https://www.kaggle.com/c/rossmann-store-sales/data?select=train.csv)
- test.csv from Kaggle (https://www.kaggle.com/c/rossmann-store-sales/data?select=test.csv)
- Telegram API documentation (https://core.telegram.org/)
