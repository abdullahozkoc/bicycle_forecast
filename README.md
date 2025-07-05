-----

# Bicycle Traffic Prediction with Linear Regression

This Jupyter Notebook demonstrates a practical application of linear regression to predict bicycle traffic on Seattle's Fremont Bridge. It integrates various real-world factors like day of the week, holidays, daylight hours, and weather conditions to build a robust predictive model. The analysis is based on publicly available data from the Fremont Bridge counter and Seattle weather archives.

-----

## Notebook Contents

  * **Data Acquisition**: Downloads bicycle count data from Fremont Bridge and Seattle weather data from specified URLs.
  * **Data Preprocessing**:
      * Filters data to a specific date range (before 2020).
      * Resamples bicycle counts to daily totals.
      * Adds binary indicators for each day of the week.
      * Incorporates US federal holidays as a binary feature.
      * Calculates daily daylight hours based on latitude and date.
      * Processes weather data to include average temperature, rainfall, and a 'dry day' indicator.
      * Combines all features into a single Pandas DataFrame.
      * Adds an 'annual' feature representing the number of years since the start of the data.
      * Handles any missing values by dropping corresponding rows.
  * **Linear Regression Model**:
      * Defines features (`X`) and target (`y`) variables.
      * Initializes and trains a `LinearRegression` model from `scikit-learn` without an intercept.
      * Generates predictions based on the trained model.
      * Visualizes actual vs. predicted bicycle traffic.
  * **Parameter Analysis**:
      * Extracts and displays the learned coefficients (parameters) of the linear model for each feature.
      * Performs a bootstrap resampling (1000 iterations) to estimate the standard error of each parameter, providing insights into their statistical significance and robustness.

-----

## How it Works

The core idea is to model the daily total bicycle traffic (`Total`) as a linear combination of various influential factors.

1.  **Data Integration**: The notebook starts by fetching two primary datasets: bicycle counts and weather records. These are then meticulously joined and aligned by date.
2.  **Feature Engineering**: Crucial to the model's performance is the creation of relevant features:
      * **Temporal Features**: Day-of-week indicators capture weekly patterns. Federal holidays are included to account for expected dips in commuter traffic.
      * **Astronomical Feature**: `daylight_hrs` is a calculated feature reflecting the varying amount of daylight throughout the year, which intuitively influences cycling activity.
      * **Weather Features**: Average daily temperature, total rainfall, and a binary 'dry day' flag directly account for environmental conditions impacting cyclists.
      * **Annual Trend**: An `annual` feature is added to capture any long-term trends or changes in cycling popularity over the years.
3.  **Model Training**: A `LinearRegression` model is trained on the prepared dataset. The `fit_intercept=False` argument suggests that the model is designed to pass through the origin when all features are zero, or that the features already capture the baseline.
4.  **Prediction & Visualization**: Once trained, the model predicts bicycle counts, and these predictions are plotted against the actual counts to visually assess the model's fit.
5.  **Parameter Interpretation**: The coefficients of the linear model indicate the estimated impact of each feature on the total bicycle traffic. For example, a positive coefficient for 'dry day' suggests that bicycle traffic tends to be higher on dry days. The bootstrap resampling provides an error estimate for these coefficients, helping to understand their reliability.

-----

## Requirements

This notebook requires the following Python libraries:

  * `pandas`
  * `numpy`
  * `matplotlib`
  * `scikit-learn`

You can install them using pip:

```bash
pip install pandas numpy matplotlib scikit-learn
```

-----

## Usage

To run this notebook:

1.  Ensure you have all the [Requirements](https://www.google.com/search?q=%23requirements) installed.
2.  Open the `.ipynb` file using Jupyter Notebook or Google Colab.
3.  Run all cells sequentially.

The notebook will automatically download the necessary data, process it, train the model, and display the results, including plots and the estimated effects of each variable.

-----
