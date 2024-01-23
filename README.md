# aae-dsa-water
## Advanced Analytics and Evaluation Data Science Accelerator - Water Project

The [Division of Drinking Water](https://www.waterboards.ca.gov/drinking_water/programs/) (DDW) at the [California State Water Resources Control Board](https://www.waterboards.ca.gov/) regulates 2866 Community Water Systems (CWS) throughout the state. Some of these CWS risk running out of water during the dry summer season. To address this problem, the [Data Science Accelerator](https://docs.data.ca.gov/odi-data-services-dif/data-science-accelerator) at the [Office of Data and Innovation](https://innovation.ca.gov/) collaborated with the Division of Drinking Water to create a machine learning model that forecasts which CWS face the highest risk of running out of water. The model is intended to run in production on a monthly basis, producing forecasts for at-risk CWS within the subsequent ninety days.

## Development Status
Release [v0.1.0](https://github.com/cagov/aae-dsa-water/releases/v0.1.0) contains the results of the collaboration between DDW and ODI. For more up-to-date development on this project, see the [Division of Drinking Water Github repository](https://github.com/CAWaterBoardDataCenter/ODA-Drought-RA-2023).

## Contents
This repository includes data, code, environment files, and a file containing all the forecasts.
* **Data** - The repository /data includes all the data used for this model.
* **Code** - The Jupyter notebook titled `water.ipynb` includes all code to generate the machine learning model.
* **Environment Files** - The environment files include all the Python packages necessary to run the code. To reproduce the original environment exactly, use the OSX-specific environment file called `environment.yml`. To use a platform-agnostic environment file, use `environment_cross_compatible.yml`. 
* **Forecast** - The file `Forecast_2023.csv` includes all the CWS forecasted to experience some form of drought impact.
* **Docs** - This folder contains two documents. One, called `Data_Quality.md`, lists all the candidate data sources for the machine learning model, describes any data quality and integrity issues with each source, and provides solutions to address these issues. The second document, called `Future_Ideas.md`, lists research ideas, as well algorithms and tools, that might be useful to explore in the future. These documents may be useful for future roadmaps. 

## Citation

If you use any of this code or results, please consider citing our paper (TBD):

```
@article{Placeholder text}
```

## Running the Model
The following steps describe exactly how to use the data, code, and envrionment file together to build and run the model using [Jupyter Lab](https://jupyter.org/install). This will generate a .csv file of drought-impacted CWSs ranked by probability (see the column  `Expected`).

### To Do Only Once
The first two steps only need to be executed once.
1. First, install conda. Conda is a tool that creates environments, or a collection of version-specific and OS-specific Python packages. This allows enables reproducibility. Using a different verson of a Python package than the original developer might produce differing results. It is best practice to use the same environment as the developer. Follow [these installation instructions](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) to install conda. Installing miniconda is sufficient for this purpose.
2. Clone this Github repository using the command `git clone https://github.com/cagov/aae-dsa-water.git`.
3. For macOS, create the environment using the command `conda env create -f environment.yml`. This environment file will install OSX-specific packages, and will reproduce the original environment exactly. To create an enviroment file on a Linux or Windows machine, use the file called `environment_cross_compatible.yml`.

### To Do Every Time
4. Make sure your cloned version of the Github repository is up-to-date. Run the command `git pull origin main`. **Note:** If you are developing, make sure to commit your changes before pulling.
5. Activate the conda environment by using the command `conda activate water`.
6. Open Jupyter Lab by typing `jupyter-lab` in the terminal.
7. Navigate to the list of files and open `water.ipynb`.
8. Under the tab Run, select 'Run all cells'. This will produce a .csv file called `Forecast_2023.csv`.
