# aae-dsa-water
## Advanced Analytics and Evaluation Data Science Accelerator - Water Project

The [Division of Drinking Water](https://www.waterboards.ca.gov/drinking_water/programs/) (DDW) at the [California State Water Resources Control Board](https://www.waterboards.ca.gov/) regulates 2800 Community Water Systems (CWS) throughout the state. Some of these CWS risk running out of water during the dry summer season. To solve this problem, we created a machine learning model that predicts which CWS face the highest risk of running out of water. The model is intended to run in production on a monthly basis, producing predictions for at-risk CWS within the subsequent ninety days. 

## Contents
* `water.ipynb`: A Jupyter notebook with code to generate the machine learning model.
* `environment.yml`: To use `water.ipynb` notebooks together with all the requisite Python packages, create a new conda environment called `water` using the provided environment file by running this command: `conda env create -f environment.yml`.
