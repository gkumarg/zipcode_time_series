# Forecasting National Home Values through Time Series Analysis

Using Facebook Prophet and ARIMA time series models to analyze and forecast US nationwide median home values by ZIP code. There is an associated blog post describing the results [here](https://medium.com/@wvsharber/forecasting-national-home-values-through-time-series-analysis-924ac911c5a4).

## Project Summary
### Methodology
Using approximately 20 years of published data from Zillow on the monthly median home sale price for nearly 15,000 ZIP codes across the U.S., we examine the projected growth in each ZIP code to see how that market is expected to change in five years. We first performed a five year forecast using the Facebook Profit model for each ZIP code, and then identified 5 candidate ZIP codes with at least 20 years of data and the largest five year percent growth. We performed cross-validation on the 5 candidate ZIP code models and forecasted the five year period with an ARIMA model to provide secondary evidence.

### Key Results 
From our analyses, the top five ZIP codes based on 5 year appreciation rates are as follows: 
  * 34982 - Fort Pierce, FL - projected 71% 5-year appreciation 
  * 33982 - Punta Gorda, FL - projected 66% 5-year appreciation 
  * 34951 - Fort Pierce, FL - projected 65% 5-year appreciation 
  * 37209 - Nashville-Davidson, TN - projected 65% 5-year appreciation 
  * 15201 - Pittsburgh, PA - projected 64% 5-year appreciation

The top three ZIP codes are located in coastal Florida communities. While these three ZIP codes have the largest percent growth, they have much larger confidence intervals than the last two, suggesting that Nashville and Pittsburgh may be “safer” investment opportunities. The large confidence intervals for the Florida communities may be a result of lingering effects from the 2008 recession.

## Repo Guide and Setup

Please clone this repo and then follow these instructions to set up the Python environment and source code.

### _Python environment_
This project relies on using the [`environment.yml`](environment.yml) file to recreate the `zipcode` conda environment. To do so, please run the following commands:

```bash
# create the zipcode conda environment
conda env create -f environment.yml

# activate the zipcode conda environment
conda activate zipcode

# make zipcode available to you as a kernel in jupyter
python -m ipykernel install --user --name zipcode --display-name "Python (zipcode)"
```

### _`.src` source code_

This project contains several .py modules in the `src/utilities` directory. Please use the following bash command to install the .src module:

``` bash
#install the .src modules
pip install -e .
```

### Data
The raw data is included in `/data/raw/zillow.csv`. This data was originally accessed via Zillow's data portal [here](https://www.zillow.com/research/data/).

In addition to the raw data, we include Python pickle files of the modeling results in `/data/processed/`. You can utilize these to avoid the long execution time of 

### Notebooks

In the `notebooks/` directory, you will find Jupyter notebooks containing both exploratory code and final results. These are organized as such:

 1. `notebooks/exploratory/EDA.ipynb`

     This notebook performs basic data munging and processing for Facebook Prophet modeling. 

2. `notebooks/exploratory/model_batch.ipynb`

    This streamlines the EDA notebook's process into a pipeline implementation to perform batch modeling on the nearly 15000 ZIP codes.
    
3. `notebooks/report/Prophet_Analysis.ipynb`

    This notebook builds the selection criteria and selects the top 5 ZIP codes. We then perform model cross-validation and analyze the forecasted median home values. 

4. `notebooks/report/ARIMA_Analysis.ipynb`

    This notebook builds a pipeline for ARIMA modeling. We feed the top 5 ZIP codes identified through Prophet analysis through this pipeline. 

5. `notebooks/report/ARIMA_Proph_comp.ipynb`

    This notebook produces visualizations to compare the ARIMA and Prophet model forecasts. 


### Reports
There is a one-page memo summarizing our project written for non technical stakeholders in `/reports/memo.md`. Additionally, there is a slide deck summarizing our project in `/reports/presentation.pdf`.




