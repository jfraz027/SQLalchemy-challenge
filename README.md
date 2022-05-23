# SQLalchemy-challenge

After making the decision to take some time off, it was decided to take a long holiday vacation in Honolulu, Hawaii! In preparation of the trip, planning was necessary to do some climate analysis on the area. The following steps were important to accomplish this task.

## Initial Step

# Climate Analysis and Exploration

To complete this part, Python and SQLAlchemy was used to perform basic climate analysis and data exploration of the climate database. Develop dnalysis through using SQLAlchemy ORM queries, Pandas, and Matplotlib.

* From provided [starter notebook](climate_starter.ipynb) and [hawaii.sqlite](Resources/hawaii.sqlite) files begin climate analysis and data exploration.

* Use SQLAlchemy’s `create_engine` to connect to SQLite database.

* Use SQLAlchemy’s `automap_base()` to reflect tables into classes and save a reference to those classes called `Station` and `Measurement`.

* Link Python to the database by creating a SQLAlchemy session.

* **Important:** Close out session at the end of the notebook.

# Precipitation Analysis

To perform an analysis of precipitation in the area, do the following:

* Find the most recent date in the dataset.

* Use this date to retrieve the previous 12 months of precipitation data by querying the 12 previous months of data. 
*   **Note:** Do not pass in the date as a variable into query.

* Select only the `date` and `prcp` values.

* Load the query results into a Pandas DataFrame, and set the index to the date column.

* Sort the DataFrame values by `date`.

* Plot the results by using the DataFrame `plot` method, as shown in the following image:

  ![precipitation](Images/precipitation.png)

* Use Pandas to print the summary statistics for the precipitation data.

# Station Analysis

To perform an analysis of stations in the area, do the following:

* Design a query to calculate the total number of stations in the dataset.

* Design a query to find the most active stations (the stations with the most rows).

    * List the stations and observation counts in descending order.

    * Which station id has the highest number of observations?

    * Using the most active station id, calculate the lowest, highest, and average temperatures.

    * Use functions such as `func.min`, `func.max`, `func.avg`, and `func.count` in the queries.

* Design a query to retrieve the previous 12 months of temperature observation data (TOBS).

    * Filter by the station with the highest number of observations.

    * Query the previous 12 months of temperature observation data for this station.

    * Plot the results as a histogram with `bins=12`, as shown in the following image:

    ![station-histogram](Images/station-histogram.png)

* Close out the session.

- - -

### Part 2: Design Climate App

After completion of initial analysis, design a Flask API based on the queries that were developed.

Use Flask to create the routes, as follows:

* `/`

    * Homepage.

    * List all available routes.

* `/api/v1.0/precipitation`

    * Convert the query results to a dictionary using `date` as the key and `prcp` as the value.

    * Return the JSON representation of the dictionary.

* `/api/v1.0/stations`

    * Return a JSON list of stations from the dataset.

* `/api/v1.0/tobs`

    * Query the dates and temperature observations of the most active station for the previous year of data.

    * Return a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

    * Return a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a given start or start-end range.

    * When given the start only, calculate `TMIN`, `TAVG`, and `TMAX` for all dates greater than or equal to the start date.

    * When given the start and the end date, calculate the `TMIN`, `TAVG`, and `TMAX` for dates from the start date through the end date (inclusive).

## Key steps

* Join the station and measurement tables for some of the queries.

* Use Flask `jsonify` to convert the API data into a valid JSON response object.

#### Bonus Temperature Analysis 1

Conduct an analysis to answer the following question: Hawaii is reputed to enjoy mild weather all year round. Is there a meaningful difference between the temperatures in, for example, June and December?

* Use Pandas to perform the following steps:

    * Convert the date column format from `string` to `datetime`.

    * Set the date column as the DataFrame index.

    * Drop the date column.

* Identify the average temperature in June at all stations across all available years in the dataset. Do the same for the temperature in December.

* Use the t-test to determine whether the difference in means, if any, is statistically significant. Will you use a paired t-test or an unpaired t-test? Why?

The larger the absolute value of the t-value, the smaller the p-value, the greater the evidence against the null hypothesis.
Use a paired t-test to compare the means of the same group. And the item under two separate scenarios. In this situation, 
Hawaii temperatures are viewed at different times of the year.
As inforamtion, an unpaired t-test compares the means of two independent or unrelated groups. 
In an unpaired t-test, the variance between groups will be assumed equal.

The null hypothesis assumes that the true mean difference between the paired samples is zero.
In this case, June temperature  differs December temperatures.

Interpreting the p value. The significance level views the probability of rejecting the null hypothesis when true.
For example, a significance level of 0.05 indicates a 5% risk of concluding that a difference exists when no actual difference exists.
Lower significance levels indicate the requirement of stronger evidence before rejecting the null hypothesis.
It can be concluded that a statistical difference between the Hawaii temperatures.

#### Bonus -Temperature Analysis 2

Planning for the trip dates of August 1 to August 7 of this year, but concerned that the weather will be less than ideal. Use historical data in the dataset to find out what the temperature has previously been for this timeframe.

**Note:** `calc_temps` will accept a start date and end date in the format `%Y-%m-%d`. The function will return the minimum, average, and maximum temperatures for that range of dates.

Complete the following steps:

* Use the `calc_temps` function to calculate the minimum, average, and maximum temperatures for your trip using the matching dates from a previous year (for example, use "2017-08-01").

* Plot the minimum, average, and maximum temperature from your previous query as a bar chart, as captured in the following steps and image:

    * Use "Trip Avg Temp" as the title.

    * Use the average temperature as the bar height (_y_ value).

    * Use the peak-to-peak (TMAX-TMIN) value as the _y_ error bar (YERR).

    ![temperature](Images/temperature.png)

#### Daily Rainfall Average

With an idea of the temperature, determine what the rainfall has been. To avoid experiencing rain the whole time! Complete the following steps:

* Calculate the rainfall per weather station using the previous year's matching dates.

    * Sort this in descending order by precipitation amount, and list the station, name, latitude, longitude, and elevation.

### Daily Temperature Normals

Calculate the daily normals for the duration of your trip. Normals are the averages for the minimum, average, and maximum temperatures.

`Daily_normals` that will calculate the daily normals for a specific date. This date string will be in the format `%m-%d`. Use all historic TOBS that match that date string.

Complete the following steps:

* Set the start and end date of the trip.

* Use the date to create a range of dates.

* Strip off the year, and save a list of strings in the format `%m-%d`.

* Use the `daily_normals` function to calculate the normals for each date string, and append the results to a list called `normals`.

* Load the list of daily normals into a Pandas DataFrame, and set the index equal to the date.

* Use Pandas to plot an area plot (`stacked=False`) for the daily normals, as shown in the following image:

![daily-normals](Images/daily-normals.png)

* Then complete by closing the session.
