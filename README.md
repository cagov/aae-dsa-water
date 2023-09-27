# aae-dsa-water
## Advanced Analytics and Evaluation Data Science Accelerator - Water Project

The [Division of Drinking Water](https://www.waterboards.ca.gov/drinking_water/programs/) (DDW) at the [California State Water Resources Control Board](https://www.waterboards.ca.gov/) regulates 2866 Community Water Systems (CWS) throughout the state. Some of these CWS risk running out of water during the dry summer season. To address this problem, we created a machine learning model that forecasts which CWS face the highest risk of running out of water. The model is intended to run in production on a monthly basis, producing forecasts for at-risk CWS within the subsequent ninety days. 

## Contents
This repository includes data, code, environment files, and a file containing all the forecasts.
* **Data** - The repository /data includes all the data used for this model.
* **Code** - The Jupyter notebook titled `water.ipynb` includes all code to generate the machine learning model.
* **Environment Files** - The environment files include all the Python packages necessary to run the code. To reproduce the original environment exactly, use the OSX-specific environment file called `environment.yml`. To use a platform-agnostic environment file, use `environment_cross_compatible.yml`. 
* **Forecast** - The file `Forecast_2023.csv` includes all the CWS forecasted to experience some form of drought impact.
* **Docs** - This folder contains two documents. One, called `Data_Quality.md`, lists all the data sources that went into the machine learning model, describe any data have quality and integrity issues with each source, and provides solutions to address these issues. The second document, called `Future_Research_Ideas.md`, lists all the research ideas, including algorithms and tools, that might be useful to explore in the future.


## Running the Model
The following steps describe exactly how to use the data, code, and envrionment file together to build and run the model using [Jupyter Lab](https://jupyter.org/install). This will generate a .csv file of drought-impacted CWSs ranked by probability (see the column  `Expected`).

1. First, install conda. Conda is a tool that creates environments, or a collection of version-specific and OS-specific Python packages. This allows enables reproducibility. Using a different verson of a Python package than the original developer might produce differing results. It is best practice to use the same environment as the developer. Follow [these installation instructions](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) to install conda. Installing miniconda is sufficient for this purpose.
2. Clone this Github repository using the command `git clone https://github.com/cagov/aae-dsa-water.git`.
3. For macOS, create the environment using the command `conda env create -f environment.yml`. This environment file will install OSX-specific packages, and will reproduce the original environment exactly. To create an enviroment file on a Linux or Windows machine, use the file called `environment_cross_compatible.yml`.
4. Open Jupyter Lab by typing `jupyter-lab` in the terminal.
5. Navigate to the list of files and open `water.ipynb`.
6. Under the tab Run, select 'Run all cells'. This will produce a .csv file called `Forecast_2023.csv`.

Note: It is also possible to bypass Steps 3-6 and, instead, run the `water.ipynb` file directly within [Visual Studio Code](https://code.visualstudio.com/).