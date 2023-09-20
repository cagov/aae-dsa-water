# aae-dsa-water
## Advanced Analytics and Evaluation Data Science Accelerator - Water Project

The [Division of Drinking Water](https://www.waterboards.ca.gov/drinking_water/programs/) (DDW) at the [California State Water Resources Control Board](https://www.waterboards.ca.gov/) regulates 2866 Community Water Systems (CWS) throughout the state. Some of these CWS risk running out of water during the dry summer season. To address this problem, we created a machine learning model that forecasts which CWS face the highest risk of running out of water. The model is intended to run in production on a monthly basis, producing forecasts for at-risk CWS within the subsequent ninety days. 

## Contents
This repository includes data, code, and environment files.
* **Data** - The repository /data includes all the data used for this model.
* **Code** - The Jupyter notebook titled `water.ipynb` includes all code to generate the machine learning model.
* **Environment Files** - The environment files include all the Python packages necessary to run the code. To reproduce the original environment exactly, use the OSX-specific environment file called `environment.yml`. To use a platform-agnostic environment file, use `environment_cross_compatible.yml`. 
* **Forecast** - The file `Forecast_2023.csv` includes all the CWS forecasted to experience some form of drought impact.

## Running the Model
The following steps describe exactly how to use the data, code, and envrionment file together to build and run the model. This will generate a .csv file of drought-impacted CWSs ranked by probability (see the column  `Expected`).

1. First, install conda. Conda is a tool that creates environments, or a collection of version-specific and OS-specific Python packages. This allows us to reproduce our work exactly. Imagine you use a different verson of a Python package than someone else, or on a different environment -- this might produce differing results from the original developer. Therefore, it is best practice to use the same environment as the developer. Follow [these installation instructions](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html).
2. Create the environment using the command `conda env create -f environment.yml`. This environment file will install OSX-specific packages, and will reproduce the original environment exactly. To create an enviroment file on a Linux or Windows machine, use the platform-agnostic envrionment file called `environment_cross_compatible.yml`.
3. Open Jupyter Lab by typing `jupyter-lab` in the terminal.
4. Navigate to the list of files and open `water.ipynb`.
5. Under the tab Run, select 'Run all cells'. This will produce a .csv file called `Forecast_2023.csv`.