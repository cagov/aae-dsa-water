## Future Ideas

The following describes a number of ideas that could improve the machine learning model.


### Data

The biggest improvement in model performance will come from improving the data. See the data quality document, also in this directory, for detailed suggestions on how to address data quality issues.

- **Consider how to pose the problem.** What time scales are we considering? Right now, we consider two different time scales – a calendar year and a water year. We calculate the Drought Severity and Coverage Index (DSCI) variable using a water year, which spans 12 months from May to April. We calculate the rest of the variables using a calendar year, which spans 12 months from January to December. To deal with this discrepancy in alignment, we create a macro-year that spans 16 months from January to April. While this approach works, it blurs a lot of the time variation in the data. A better approach would be to create smaller units of time, such as quarters or months, and align all the data to those time scales.
- **Consider the outcome label.** What are we trying to predict? Right now, the outcome label includes a variety of outcomes. Predicting whether a water system petitions for exemption from curtailment, for example, is quite different from predicting whether a water system violates a drought order. Identify a clear and simple definition of drought impact.
- **Consider the ratio of static to time-varying data sources.** Right now, the only time-varying data source includes the DSCI. However, additional time-varying sources will help the model generate different predictions from year to year. The heavy reliance on static variables in this model biases the model toward predicting the same outcome year after year.
- **Consider observational data (versus indices)**. Index values such as the DSCI, as well as score values such as CDAG and SAFER, contain a weighted blend of multiple observational data sources into an index. While this may be predictive, it is not very interpretable. For example: If the DSCI is highly predictive, we still do not know which constituent element of the DSCI is strongly correlated with failing water systems. Incorporating additional satellite and ground-based observations (such as relative soil moisture and stream flow measurements) instead of relying on index data, which are not in physical units, will enable more interpretable models.
- **Consider the physical processes to model.** Different physical processes govern groundwater and surface water flows, yet we model them as one process. This likely introduces noise into the model. If at all possible, separate multiple physical processes into different models.


### Algorithms

- **Consider complex networks (e.g. **[**Albert et al. 2001**](https://doi.org/10.1103/RevModPhys.74.47)**).** Algorithms like [NetworkX](https://networkx.org/documentation/latest/) can model the dynamics of an infrastructure system by accounting for the number of connections per node. The [2023 SAFER Drinking Water Needs Assessment](https://www.waterboards.ca.gov/drinking_water/certlic/drinkingwater/documents/needs/2023needsassessment.pdf) noted that a number of systems fail because they rely on only a single source for water ([Mullin 2020](https://doi.org/10.1126/science.aba7353)). Right now, the model includes the number of water sources per system, but the model does not include how these systems connect to one another. This missing information is critical to a successful model.
- **Consider local spatial autocorrelation (e.g. **[**Rey et al. 2020**](https://geographicdata.science/book/intro.html)**)**. Right now, the model considers latitude and longitude as two independent variables. Of course, latitude and longitude are coupled. Consider these as geospatial points, rather than independent features, that together correlate with the behavior of water systems.
- **Consider interpretable machine learning methods (e.g. **[**Molnar 2023**](https://christophm.github.io/interpretable-ml-book/)**)**. Right now, the code in this repository includes a simple method called counterfactual examples to probe why the model forecasts that drought will impact any given water system. Counterfactual examples perturb the input data until the model produces a different outcome for the example (e.g. [DiCE](https://github.com/interpretml/DiCE/), [Mothilal et al. 2020](https://doi.org/10.1145/3351095.3372850)). By looking at the difference in the original and perturbed input data, we can quantify the change in probability per change in value for any given feature. There are other local and global model-agnostic methods worth considering.
- **Consider time-series models (e.g. ARIMA).** Right now, the dataset only includes one example per community water system per year. After collecting higher-cadence data, time series models will likely improve performance. 


### Software

- **Store data in a centralized database.** Adhere to standard data types, formats, and naming conventions.
- **Develop an API to query all relevant data directly from the database or original sources.** Relying on secondary sources of many manual steps will lead to errors.
- **Adhere to coding standards.** Version control code. Use unit tests. Use linters. Review code. Use continuous integration to make sure each new piece of code works seamlessly with the code base. Without automation and testing, errors will creep in. These errors will negatively impact model performance and reproducibility.
- **Consider a tool for tracking experiments.** [MLflow](https://mlflow.org/) is a good option for tracking experiments, sharing models and data, and selecting a model to deploy to production.
