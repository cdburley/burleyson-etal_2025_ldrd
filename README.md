# burleyson-etal_2025_ldrd

## Workflow
Use the following notebooks to rerun the analysis and reproduce the main and supplementary figures. The analysis is currently 
configured to run for eight Balancing Authorities (AZPS, BPAT, CISO, ERCO, FPL, ISNE, PJM, and SWPP) in the CONUS. The 
specific BAs the analysis uses are controlled in the `balancing_authority_modeled.yml` file in the `/data` directory. The
underlying machine learning models rely on functions within the Total ELectricity Loads (TELL) python package. Before 
running any of the scripts below you should install TELL using `pip install tell`.

| Notebook Order |              Script Name               |                                                       Description                                                        | 
|:--------------:|:--------------------------------------:|:------------------------------------------------------------------------------------------------------------------------:|
|       1        |    plot_ba_service_territory.ipynb     |                              Plots the service territory of the BAs used in this analysis.                               |
|       2        | plot_ba_load_weather_time_series.ipynb |                     Plots the raw time series of the load, weather, and population data for each BA.                     |
|       3        |     train_and_run_mlp_models.ipynb     | Iteratively trains the TELL MLP models using evolving time windows and uses the models to project loads forward in time. |
|       4        |    calculate_error_statistics.ipynb    |                             Calculates the error statistics for each of the trained models.                              |
|       5        |     plot_ba_error_evolution.ipynb      |                        Plots the evolution of errors by BA for each of the trained models.                               |

## Proposed next steps
* Replicate the initial analysis by confirming that you can run all the notebooks listed above.
* Retrain the MLP models to include total population in the BA as a predictive variable. There are two potential ways to do this:
    1) You should be able to do this by adding "Population" to the `x_variables` parameter list (e.g., x_variables = ["Hour", "Month", "Temperature", "Specific_Humidity", "Wind_Speed", "Longwave_Radiation", "Shortwave_Radiation", "Population"]) when calling the `tell.train` function in the `train_and_run_mlp_models.ipynb` notebook.
    2) Adding a linear model after the MLP model the regresses the population variable against the residual from the original MLP prediction. Aowabin might have some code to help with this.
* Try to explain why the prediction error grows over time and why it grows faster in some BAs (e.g., ERCOT) and slower in others (e.g., PJM):
    1) Explore the errors as a function of population (related to the suggestion above).
    2) Explore the errors as a function of the mean diurnal cycle of demand by season. I'm thinking of a plot where you show error as a function of time-of-day (x-axis) with different colors for the different meteorological seasons (DJF, MAM, JJA, SON).
    3) Explore the rate of growth of the errors during times of high load (e.g., error during the top X% of loads each year).