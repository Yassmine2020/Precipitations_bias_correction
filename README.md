# Statistical Methods for Processing and Analyzing Geo-dated Data


## Project Overview

Natural disasters are increasingly frequent and devastating. By accurately predicting these events, we can implement preventive measures that significantly reduce loss of human life. However, existing forecasting methods often have errors or biases. This is where our project becomes crucial. We utilize ERA5 data, which provides both monthly precipitation forecasts and actual observed precipitation. Our goal is to correct the bias and minimize the discrepancy between predictions and reality. 


## Data Description

The project uses ERA5 Seasonal Forecast data, which provides seasonal predictions for various meteorological parameters. The dataset includes:

- Estimated precipitation data for October, November, and December
- Observed precipitation data for the corresponding months
- Data focused on the geographical area of Morocco
- Lead time of 6 months for predictions, meaning:
  - The October dataset contains precipitation data from October to March
  - The November dataset contains precipitation data from November to April
  - The December dataset contains precipitation data from December to May

**Here's a graph showing the statistical distribution of the predicted and observed values for the December dataset:**

![december stat distribu](https://github.com/user-attachments/assets/1d024d8a-af6d-4c9d-84ec-f7f757642217)

**The evaluation metric for this project is the Root Mean Square Error (RMSE):**

RMSE = √(Σ(predicted - observed)² / n)
Where:

predicted: the forecasted precipitation value
observed: the actual observed precipitation value
n: number of data points

**Here is the initial RMSE map for the December data and its lead time:**

![rmse decembre](https://github.com/user-attachments/assets/0914c00b-de3c-40c7-aa9a-036121a203a9)

**And here is the general heatmap before correcting the bias:**

![heatmap](https://github.com/user-attachments/assets/0ac23264-b3c9-4972-8be7-5afd69332e2e)


## Methods Used


1. **eQM (empirical Quantile Mapping) Delta-proportion method**: Adjusts the quantile distributions of predicted values to match observed data.

3. **eQM Delta-proportion with correction coefficient**: An enhanced version of eQM that introduces a multiplicative coefficient to modulate the adjustment.

4. **Machine Learning methods**: Various ML models were tested, with LightGBM Regressor showing the best performance.

PS: For more details, please refer to the code and the generated graphs and diagrams that demonstrate the effectiveness of each method.


## Key Findings

- The eQM method with a correction coefficient performed better than the standard eQM, providing more homogeneous RMSE values.
- 
**Here is the different RMSE heatmap of eQm with vs without coef**

  ![eqm sanscoef](https://github.com/user-attachments/assets/d92abad3-250e-43b1-8387-aa4de35c0bef)

  ![eqm aveccoef](https://github.com/user-attachments/assets/24148aee-b4eb-4f90-b37b-b6403a7325d6)
  
- LightGBM showed the best correction compared to other ML methods, displaying a non-homogeneous correction over time.

  ![newplot](https://github.com/user-attachments/assets/99513c2d-56ff-42ae-be0d-054d9792e910)

## Repository Structure

```
DATASET/
├── RMSE_bias/            
├── dataset_csv/
├── dataset_test2023/
├── for_heatmap/           # Data prepared for heatmap visualization
├── obs_est_merged/        # Merged observed and estimated data
├── submission/            # Final results for submission
├── train_test/            # Training and testing datasets
ML/                        # Machine Learning models and analysis
├── ML_dec.ipynb
├── ML_nov.ipynb
├── ML_oct.ipynb
└── RL.ipynb
QMBC/                       # Quantile Mapping Bias Correction
├── dec_average.csv
├── eQM_sanscoef_dec.ipynb
├── eQM_sanscoef_nov.ipynb
├── eQM_sanscoef_oct.ipynb
├── qmbc_aveccoef_dec.ipynb
├── qmbc_aveccoef_nov.ipynb
└── qmbc_aveccoef_oct.ipynb
heatmap_generation.ipynb     # Script for generating heatmaps
processing_init.ipynb        # Initial data processing script
```
