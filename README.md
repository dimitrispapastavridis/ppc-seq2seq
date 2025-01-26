# README

## Here you can find our Presentation on YouTube. [Click Here](https://www.youtube.com/watch?v=V9rFwTO73Ak)

## Data Collection

### Open EDA Jupyter
  
- We received forecasted price data from 3 different providers for each country in CSV format:
  - **Provider 1 files**:
    - `provider1_GR.csv`
    - `provider1_BG.csv`
    - `provider1_ITSUD.csv`
    - `provider1_RO.csv`
  
  - **Provider 2 files**:
    - `provider2_GR.csv`
    - `provider2_BG.csv`
    - `provider2_ITSUD.csv`
    - `provider2_RO.csv`
  
  - **Provider 3 files**:
    - `provider3_GR.csv`
    - `provider3_BG.csv`
    - `provider3_ITSUD.csv`
    - `provider3_RO.csv`

  - We used the ENTSO API to retrieve the actual energy prices for each of the countries (Greece, Bulgaria, Romania, Italy) for the hours we are analyzing. These actual prices were stored in the following DataFrames:
   - `actual_greece`  
   - `actual_bulgaria`
   - `actual_romania`
   - `actual_italy`

### Data Merging Process
   
1. **Merging Forecast and Actual Data**:  
   For each country, we combined the actual price data from ENTSO with the forecasted price data from the 3 different providers. We performed a `concatenate` operation to merge the forecasts and actual data for each country. The merged data was stored in the following DataFrames:
   - `greece`
   - `bulgaria`
   - `romania`
   - `italy`
   
2. **Saving the Merged Data**:  
   Finally, we saved each of these merged DataFrames as CSV files for later use in model training and evaluation. The saved files are named as follows:
   - `greece.csv`
   - `bulgaria.csv`
   - `romania.csv`
   - `italy.csv`

### Columns Description

- **For forecasted data (from providers)**:
  - `datetime`: The timestamp
  - `provider1`, `provider2`, `provider3`: Forecasted energy prices from each of the 3 providers for each country.

- **For actual data (from ENTSO)**:
  - `datetime`: The timestamp
  - `actual_bulgaria`, `actual_greece`, `actual_romania`, `actual_italy`: The actual energy price for each country.

### Notes
- Ensure that all timestamps in the merged data are continuous, with no missing hours.
- The merged data must contain both the actual and forecasted prices for the same timestamp, ensuring alignment between actual and forecasted data.

## Model Training and Predictions

### Jupyter Notebooks

- For each model (LSTM, GRU, Seq2Seq), we use the previously saved CSV files for each country to perform our predictions.
  
- The files used for each model include:
  - `greece.csv`
  - `bulgaria.csv`
  - `romania.csv`
  - `italy.csv`

### Time Series Models

For training and predictions, we used three types of models for each country:

1. **LSTM (Long Short-Term Memory)**
2. **GRU (Gated Recurrent Unit)**
3. **Seq2Seq (Sequence-to-Sequence)**

### Modeling Process

1. **Data Loading**:  
   For each model and each country, we load the corresponding CSV files that contain the actual data and the forecasts from the 3 providers (e.g., `greece.csv`, `bulgaria.csv`, etc.).

2. **Model Training**:  
   Each model (LSTM, GRU, Seq2Seq) is trained using the mixture of actual data and forecasts from the providers.

3. **Predictions**:  
   After training, we use the model to predict future energy prices for each country. These predictions are saved into new CSV files for each country.

### Prediction Output Files
- The prediction files generated from each model were saved based on the respective model and country:
  - `LSTM - Greece.ipynb`
  - `LSTM - Bulgaria.ipynb`
  - `LSTM - Romania.ipynb`
  - `LSTM - Italy.ipynb`
  
  - `GRU - Greece.ipynb`
  - `GRU - Bulgaria.ipynb`
  - `GRU - Romania.ipynb`
  - `GRU - Italy.ipynb`

  - `Seq2seq - Greece.ipynb`
  - `Seq2seq - Bulgaria.ipynb`
  - `Seq2seq - Romania.ipynb`
  - `Seq2seq - Italy.ipynb`

### Ensure
- All CSV files used for training must have continuous time periods without missing hourly values.
- Predictions are saved separately for each country and model, allowing for individual analysis.



