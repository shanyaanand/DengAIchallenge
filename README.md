# DengAIchallenge

DengAIchallenge is a competition to use open data to predict the occurrence of Dengue based on climatological data

## Installation

Use the package manager [pip] to install required packages.

```bash
pip install -r requirements.txt
```

## File structure
1. ./main.ipynb: notebook file where the code is present
2. ./checkpoint: folder to save the model
3. ./data-processed: folder to store data
4. ./data-processed/benchmark.csv: output file

## Description

Data is a time series data which contains 21 features. The objective of the project is use the given features to identify the number of total cases in a given week. 

## Observation

1. There is weak correlation of total_cases with other features
2. Used only features that have correlation above a certain threshold (approx 0.18)
3. There trend and seasonality present in the time series data
4. Trend is non-linear in nature
5. Seasonality is well defined with period approx 69 - 70 data points
6. Total_cases has pretty good correlation with its past values

## Action

1. Since only few features have correlation with the total_cases above a certain threshold, thus it makes sense to use selected features only for prediction(to avoid noise)
2. Since data shows trend and seasonality, we should use model which will use these behaviours to do the prediciton
3. Seasonality is well defined but trend is non-linear in nature, thus using model which will treat trend as non-linear will help us
4. Prophet considers trend in piece wise manner thus we can capture non-linear trend also using prophet model
5. Since total_cases depends on its previous values thus we should use past values of total_cases as input
6. During training we can assume that the model is 100% accuracte thus lagged_total_cases can we the real true total_cases value(inspired from Transformer training) but during testing we will use previous prediction value as the lagged_total_cases feature

## Usage

```
jupyter-notebook
```